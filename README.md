<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>AurumMotors.kz - Премиум Аукционы</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    .fade-in {
      animation: fadeIn 0.8s ease forwards;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body class="bg-[#1B1B1B] text-white font-sans">

<!-- Шапка -->
<header class="flex justify-between items-center px-8 py-6 bg-[#121212]">
  <div class="flex items-center gap-2">
    <img src="https://via.placeholder.com/100x40?text=Logo" alt="AurumMotors.kz" class="h-10">
    <span class="text-2xl font-bold">AURUMMOTORS.KZ</span>
  </div>
  <nav class="hidden md:flex gap-8 text-lg">
    <a href="#" class="hover:text-yellow-400">Каталог</a>
    <a href="#" class="hover:text-yellow-400">Аукционы</a>
    <a href="#advantages" class="hover:text-yellow-400">Преимущества</a>
    <a href="#about" class="hover:text-yellow-400">О нас</a>
    <a href="#reviews" class="hover:text-yellow-400">Отзывы</a>
    <a href="#faq" class="hover:text-yellow-400">FAQ</a>
    <a href="login.html" class="bg-[#D4AF37] text-black px-4 py-2 rounded hover:bg-yellow-300">Вход</a>
  </nav>
</header>

<!-- Лучшие предложения недели -->
<section class="py-16 px-8 max-w-7xl mx-auto">
  <h2 class="text-3xl font-bold mb-8">Лучшие предложения недели</h2>

  <!-- Фильтр -->
  <div class="flex gap-4 mb-8">
    <button onclick="filterCars('Все')" class="bg-[#333] px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Все</button>
    <button onclick="filterCars('Porsche')" class="bg-[#333] px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Porsche</button>
    <button onclick="filterCars('BMW')" class="bg-[#333] px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">BMW</button>
    <button onclick="filterCars('Audi')" class="bg-[#333] px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Audi</button>
  </div>

  <div id="carGrid" class="grid grid-cols-1 md:grid-cols-4 gap-8">
    <!-- Карточки будут загружаться динамически -->
  </div>

  <div class="text-center mt-8">
    <button onclick="loadMoreCars()" class="bg-yellow-500 text-black px-6 py-3 rounded hover:bg-yellow-400 font-bold">Показать ещё</button>
  </div>
</section>

<!-- Модальное окно -->
<div id="modal" class="hidden fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50 p-4">
  <div class="bg-[#1F1F1F] rounded-lg w-full max-w-4xl p-6 relative overflow-y-auto max-h-[90vh]">
    <button onclick="closeModal()" class="absolute top-4 right-4 text-2xl text-gray-400 hover:text-white">&times;</button>
    <div class="grid md:grid-cols-2 gap-8">
      <div>
        <img id="modalImage" src="" alt="Car" class="rounded-lg mb-4 w-full">
      </div>
      <div class="flex flex-col justify-between">
        <div>
          <h2 id="modalTitle" class="text-3xl font-bold mb-2"></h2>
          <div class="grid grid-cols-2 gap-4 mb-6 text-gray-400 text-sm">
            <div>
              <p>Год выпуска: <span class="text-white font-semibold">2021</span></p>
              <p>Пробег: <span class="text-white font-semibold">15 000 км</span></p>
              <p>Топливо: <span class="text-white font-semibold">Бензин</span></p>
            </div>
            <div>
              <p>Привод: <span class="text-white font-semibold">Полный</span></p>
              <p>Кузов: <span class="text-white font-semibold">Купе</span></p>
            </div>
          </div>
          <div class="bg-[#2C2C2C] p-4 rounded-lg mb-6">
            <p class="text-sm text-gray-400 mb-2">Текущая ставка:</p>
            <p id="modalPrice" class="text-2xl font-bold"></p>
            <p class="text-sm mt-2 text-yellow-400" id="countdownTimer">Загрузка таймера...</p>
          </div>
          <button class="w-full bg-[#c9a539] text-black font-bold py-3 rounded hover:bg-yellow-300">
            Сделать ставку
          </button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Наши Преимущества -->
<section id="advantages" class="py-16 px-8 max-w-7xl mx-auto">
  <h2 class="text-3xl font-bold mb-8 text-center">Наши преимущества</h2>
  <div class="grid md:grid-cols-3 gap-8 text-center">
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <img src="https://img.icons8.com/ios/100/ffd700/speed.png" class="w-16 mx-auto mb-4" alt="Быстрая продажа">
      <h3 class="text-xl font-bold mb-2">Быстрая продажа</h3>
      <p class="text-gray-400">Оперативные торги без долгого ожидания.</p>
    </div>
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <img src="https://img.icons8.com/ios/100/ffd700/cheap-2.png" class="w-16 mx-auto mb-4" alt="Выгодные цены">
      <h3 class="text-xl font-bold mb-2">Выгодные цены</h3>
      <p class="text-gray-400">Покупайте автомобили дешевле рынка.</p>
    </div>
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <img src="https://img.icons8.com/ios/100/ffd700/guarantee.png" class="w-16 mx-auto mb-4" alt="Гарантии">
      <h3 class="text-xl font-bold mb-2">Прозрачность</h3>
      <p class="text-gray-400">Честные торги и полная информация об авто.</p>
    </div>
  </div>
</section>

<!-- О нас -->
<section id="about" class="py-16 px-8 max-w-5xl mx-auto">
  <h1 class="text-4xl font-bold mb-8 text-center">О нас</h1>
  <p class="text-lg text-gray-300 mb-6">
    Добро пожаловать в <span class="text-yellow-400 font-semibold">AurumMotors.kz</span> — первый аукционный проект нового поколения в Казахстане! Мы переосмыслили привычный формат автомобильных торгов и внедрили технологии искусственного интеллекта.
  </p>
  <h2 class="text-2xl font-bold mb-4 text-yellow-400">Чем мы отличаемся:</h2>
  <ul class="list-disc list-inside space-y-3 text-gray-300 mb-8">
    <li>Интеллектуальные алгоритмы торгов.</li>
    <li>Локальная казахстанская команда.</li>
    <li>Доступ к лучшим автомобилям выгодно.</li>
  </ul>
  <h2 class="text-2xl font-bold mb-4 text-yellow-400">Наша миссия:</h2>
  <p class="text-lg text-gray-300">
    Сделать доступ к премиальным автомобилям проще и безопаснее для всех.
  </p>
</section>

<!-- Отзывы клиентов -->
<section id="reviews" class="py-16 px-8 max-w-7xl mx-auto">
  <h2 class="text-3xl font-bold mb-8 text-center">Отзывы клиентов</h2>
  <div class="grid md:grid-cols-3 gap-8">
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <p class="text-gray-300 mb-4">"Спасибо AurumMotors.kz! Машину купил выгодно и быстро!"</p>
      <h3 class="text-lg font-bold text-yellow-400">Иван Петров</h3>
    </div>
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <p class="text-gray-300 mb-4">"Очень удобный сервис, качественные автомобили!"</p>
      <h3 class="text-lg font-bold text-yellow-400">Асель Нурланова</h3>
    </div>
    <div class="bg-[#2C2C2C] p-6 rounded-lg">
      <p class="text-gray-300 mb-4">"Лучшая платформа для покупки авто в Казахстане!"</p>
      <h3 class="text-lg font-bold text-yellow-400">Дмитрий Иванов</h3>
    </div>
  </div>
</section>

<!-- Часто задаваемые вопросы (FAQ) -->
<section id="faq" class="py-16 px-8 max-w-5xl mx-auto">
  <h2 class="text-3xl font-bold mb-8 text-center">FAQ — Часто задаваемые вопросы</h2>
  <div class="space-y-6">
    <details class="bg-[#2C2C2C] p-4 rounded-lg">
      <summary class="cursor-pointer font-bold">Как участвовать в аукционе?</summary>
      <p class="mt-2 text-gray-300">Просто зарегистрируйтесь и сделайте ставку на понравившийся автомобиль.</p>
    </details>
    <details class="bg-[#2C2C2C] p-4 rounded-lg">
      <summary class="cursor-pointer font-bold">Есть ли гарантия на авто?</summary>
      <p class="mt-2 text-gray-300">Да, каждый автомобиль проходит проверку перед аукционом.</p>
    </details>
    <details class="bg-[#2C2C2C] p-4 rounded-lg">
      <summary class="cursor-pointer font-bold">Как оплатить покупку?</summary>
      <p class="mt-2 text-gray-300">После выигрыша аукциона с вами свяжется менеджер для оформления сделки.</p>
    </details>
  </div>
</section>

<!-- Футер -->
<footer class="bg-black py-8 text-center text-gray-400">
  <p>&copy; 2025 AurumMotors.kz. Все права защищены.</p>
  <div class="flex justify-center gap-8 mt-4 text-sm">
    <a href="#" class="hover:text-yellow-400">Каталог</a>
    <a href="#" class="hover:text-yellow-400">Аукционы</a>
    <a href="#" class="hover:text-yellow-400">Контакты</a>
    <a href="#" class="hover:text-yellow-400">Instagram</a>
    <a href="#" class="hover:text-yellow-400">Telegram</a>
  </div>
</footer>

<!-- Скрипты -->
<script>
let cars = [
  {brand: "Porsche", model: "911", price: "$50,000", img: "https://yandex.ru/images/touch/search?pos=1&img_url=https%3A%2F%2Fblogger.googleusercontent.com%2Fimg%2Fb%2FR29vZ2xl%2FAVvXsEhFzowGgRG-e-r-1bz61Zy-2AdYKDbkmanXuR3b0yxgcHlpVbo7MZsctex9T6JBNT9tK3zbq2G_zIElw1WAY56wyUbrKXw7e24hRjrPbJL-zmPpnbJrLiY6sRi0jGxhrGQgAfylxQNWf4iTtp7ggLdE4Jk_y_5MUPaGxC_ilwdlxSrdXhj1T8PNADYffhXR%2Fs2294%2FPorsche%2520911%2520S-T%252020244.png&text=%D0%BF%D0%BE%D1%80%D1%88+911+%D1%84%D0%BE%D1%82%D0%BE&rpt=simage&source=tabbar&lr=10309"},
  {brand: "BMW", model: "M3", price: "$52,500", img: "https://via.placeholder.com/300x200?text=BMW+M3"},
  {brand: "Audi", model: "A6", price: "$23,000", img: "https://via.placeholder.com/300x200?text=Audi+A6"},
  {brand: "Chevrolet", model: "Camaro", price: "$35,000", img: "https://via.placeholder.com/300x200?text=Chevrolet+Camaro"},
  {brand: "Toyota", model: "Corolla", price: "$15,000", img: "https://via.placeholder.com/300x200?text=Toyota+Corolla"},
  {brand: "Honda", model: "Civic", price: "$14,500", img: "https://via.placeholder.com/300x200?text=Honda+Civic"},
  {brand: "Nissan", model: "Altima", price: "$18,000", img: "https://via.placeholder.com/300x200?text=Nissan+Altima"},
  {brand: "Ford", model: "Focus", price: "$13,000", img: "https://via.placeholder.com/300x200?text=Ford+Focus"},
];

function renderCars(list) {
  const grid = document.getElementById('carGrid');
  grid.innerHTML = '';
  list.forEach(car => {
    const card = document.createElement('div');
    card.className = "bg-[#2C2C2C] p-4 rounded-lg shadow-lg text-center fade-in";
    card.innerHTML = `
      <img src="${car.img}" alt="${car.model}" class="mb-4 rounded">
      <h3 class="font-bold text-xl mb-2">${car.model}</h3>
      <p class="text-gray-400 mb-4">${car.price}</p>
      <button onclick="openModal('${car.model}', '${car.img}', '${car.price}')" class="bg-[#c9a539] text-black px-4 py-2 rounded hover:bg-yellow-300">Сделать ставку</button>
    `;
    grid.appendChild(card);
  });
}

function filterCars(brand) {
  if (brand === 'Все') {
    renderCars(cars);
  } else {
    renderCars(cars.filter(car => car.brand === brand));
  }
}

function loadMoreCars() {
  renderCars(cars);
}

function openModal(title, image, price) {
  document.getElementById('modalTitle').textContent = title;
  document.getElementById('modalImage').src = image;
  document.getElementById('modalPrice').textContent = price;
  document.getElementById('modal').classList.remove('hidden');
  startTimer();
}

function closeModal() {
  document.getElementById('modal').classList.add('hidden');
}

function startTimer() {
  let countdown = 7200; // 2 часа
  const timerElement = document.getElementById('countdownTimer');
  function updateTimer() {
    let hours = Math.floor(countdown / 3600);
    let minutes = Math.floor((countdown % 3600) / 60);
    let seconds = countdown % 60;
    timerElement.textContent = `${hours}ч ${minutes}м ${seconds}с до окончания`;
    countdown--;
    if (countdown >= 0) {
      setTimeout(updateTimer, 1000);
    }
  }
  updateTimer();
}

renderCars(cars);
</script>

</body>
</html>
