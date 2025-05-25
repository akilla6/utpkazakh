<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>UTM Drone Kazakhstan — одностраничный сайт</title>
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet" />
<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  * { box-sizing: border-box; }
  body {
    margin: 0; font-family: 'Roboto', sans-serif; background-color: #f4f9ff; color: #1a2e5c;
  }
  header {
    background-color: #003f87; padding: 15px 30px; color: #fff;
    display: flex; justify-content: space-between; align-items: center;
  }
  .logo {
    font-weight: 700; font-size: 1.4rem; text-decoration: none; color: #e1f0ff; cursor: pointer;
  }
  nav ul {
    list-style: none; display: flex; gap: 20px; margin: 0; padding: 0;
  }
  nav ul li a {
    color: #cfe6ff; text-decoration: none; font-weight: 500; padding: 8px 12px;
    border-radius: 4px; transition: background-color 0.3s ease;
    cursor: pointer;
  }
  nav ul li a.active, nav ul li a:hover {
    background-color: #0a63c3; color: #fff;
  }
  .container {
    max-width: 1000px; margin: 30px auto; padding: 0 20px;
  }
  h1,h2,h3 {
    color: #003f87;
  }
  h1 {
    font-size: 2.5rem; margin-bottom: 10px;
  }
  h2 {
    font-size: 1.8rem; margin-bottom: 15px;
    border-bottom: 2px solid #0a63c3; padding-bottom: 6px;
  }
  h3 {
    margin-top: 20px; margin-bottom: 12px;
  }
  .hero {
    text-align: center; margin-bottom: 40px;
  }
  .hero .subtitle {
    font-size: 1.2rem; color: #0a63c3; margin-top: 10px; margin-bottom: 25px;
  }
  .hero-img {
    background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
    background-position: center; background-size: cover;
    height: 300px; border-radius: 15px;
    box-shadow: 0 8px 15px rgba(0, 63, 135, 0.3);
    margin: 0 auto; max-width: 900px;
  }
  .content-block {
    background: white; padding: 25px 30px; border-radius: 12px;
    margin-bottom: 30px; box-shadow: 0 2px 8px rgba(0,63,135,0.1);
  }
  .features-list {
    list-style: none; padding-left: 0;
  }
  .features-list li {
    font-size: 1.1rem; margin-bottom: 12px;
    display: flex; align-items: center; gap: 12px;
  }
  .features-list .icon {
    color: #0a63c3; font-size: 1.4rem;
  }
  .problem-visual {
    display: flex; justify-content: center; gap: 40px; margin-top: 20px;
  }
  .problem-visual img {
    width: 130px;
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.1));
    border-radius: 10px;
  }
  table {
    width: 100%; border-collapse: collapse; margin-top: 12px;
  }
  table th, table td {
    border: 1px solid #0a63c3; padding: 10px; text-align: center; font-weight: 500;
  }
  table thead {
    background-color: #0a63c3; color: white;
  }
  ul {
    padding-left: 20px;
  }
  footer {
    background-color: #003f87; color: #cfe6ff;
    text-align: center; padding: 15px 10px;
    margin-top: 60px; font-size: 0.9rem;
  }
  /* Форма регистрации */
  form {
    display: flex; flex-direction: column; max-width: 400px; margin-top: 15px;
  }
  label {
    margin: 12px 0 5px; font-weight: 600;
  }
  input[type="text"] {
    padding: 10px; border: 1.5px solid #0a63c3; border-radius: 6px;
    font-size: 1rem; transition: border-color 0.3s ease;
  }
  input[type="text"]:focus {
    outline: none; border-color: #004aad; box-shadow: 0 0 6px #0a63c3aa;
  }
  button {
    margin-top: 25px; padding: 12px; background-color: #0a63c3;
    border: none; border-radius: 8px; color: white;
    font-size: 1.1rem; font-weight: 600; cursor: pointer;
    transition: background-color 0.3s ease;
  }
  button:hover {
    background-color: #004aad;
  }
  .form-message {
    margin-top: 15px; font-weight: 600;
  }
  /* Кнопки в личном кабинете */
  .profile-actions button {
    background-color: #0a63c3; color: white; border: none;
    padding: 10px 18px; font-size: 1rem; border-radius: 6px;
    cursor: pointer; display: inline-flex; align-items: center;
    gap: 8px; margin-top: 15px; transition: background-color 0.3s ease;
  }
  .profile-actions button:hover {
    background-color: #004aad;
  }
  /* Карта */
  #mapid {
    height: 600px; border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2); margin-top: 20px;
  }
  /* Скрываем все страницы кроме активной */
  section.page {
    display: none;
  }
  section.page.active {
    display: block;
  }
  /* Данные в личном кабинете */
  .profile-data {
    background: #f0f7ff;
    padding: 20px;
    border-radius: 8px;
    margin-top: 20px;
  }
</style>
</head>
<body>
<header>
  <nav>
    <a class="logo" onclick="navigateTo('home')">🚁 UTM Drone Kazakhstan</a>
    <ul class="nav-links">
      <li><a onclick="navigateTo('home')" id="nav-home" class="active">Главная</a></li>
      <li><a onclick="navigateTo('register')" id="nav-register">Регистрация дрона</a></li>
      <li><a onclick="navigateTo('map')" id="nav-map">Карта запретных зон</a></li>
      <li><a onclick="navigateTo('profile')" id="nav-profile">Личный кабинет</a></li>
    </ul>
  </nav>
</header>

<main class="container">
  <!-- Главная -->
  <section id="home" class="page active">
    <section class="hero">
      <h1>🚁 UTM-система для управления дронами в Казахстане</h1>
      <p class="subtitle">Концепция мониторинга БПЛА с проверкой запретных зон</p>
      <div class="hero-img"></div>
    </section>

    <section class="content-block">
      <h2>📍 Проблема</h2>
      <p>В 2023 году в Казахстане зарегистрировано <strong>127 инцидентов с дронами</strong> вблизи аэропортов. Отсутствует централизованная система контроля их движения, что создает серьёзные риски для гражданской авиации.</p>
      <div class="problem-visual">
        <img src="https://cdn-icons-png.flaticon.com/512/1077/1077063.png" alt="Рост дронов" />
        <img src="https://cdn-icons-png.flaticon.com/512/809/809957.png" alt="Дрон запретная зона" />
      </div>
    </section>

    <section class="content-block">
      <h2>📌 Как работает наша UTM-система?</h2>
      <ul class="features-list">
        <li><i class="fa-solid fa-computer icon"></i> Пилот подает заявку через веб-интерфейс</li>
        <li><i class="fa-solid fa-map icon"></i> Система проверяет маршрут на карте</li>
        <li><i class="fa-solid fa-circle-exclamation icon"></i> При нарушении — мгновенное оповещение</li>
      </ul>
    </section>

    <section class="content-block">
      <h2>💻 Технологии</h2>
      <p>Мы используем бесплатные и современные инструменты для быстрого прототипирования и масштабируемости системы:</p>
      <ul>
        <li>Диаграммы архитектуры для понимания процессов</li>
        <li>Алгоритмы проверки маршрутов и безопасности</li>
        <li>Firebase для аутентификации и базы данных</li>
        <li>Leaflet для визуализации карт и зон</li>
      </ul>
    </section>

    <section class="content-block">
      <h2>🎥 Демонстрация работы</h2>
      <p>Видео и скриншоты показывают, как система отслеживает полеты и отправляет предупреждения при пересечении запретных зон.</p>
      <p><strong>Пример:</strong> Дрон пересек красную зону → система отправила alert.</p>
    </section>

    <section class="content-block">
      <h2>📊 Почему это важно?</h2>
      <p>По данным ICAO, внедрение UTM снижает риски авиационных происшествий на <strong>68%</strong>.</p>
      <table>
        <thead>
          <tr>
            <th>Без UTM</th>
            <th>С UTM</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Ручной контроль за полетами</td><td>Автоматическая проверка маршрутов</td></tr>
          <tr><td>Нет трекинга в реальном времени</td><td>Отображение маршрута на карте</td></tr>
        </tbody>
      </table>
    </section>

    <section class="content-block">
      <h2>📈 Планы на будущее</h2>
      <ul>
        <li>2024 — тесты с 5 дронами</li>
        <li>2025 — подключение Министерства транспорта</li>
        <li>2026 — национальное внедрение UTM-системы</li>
      </ul>
    </section>
  </section>

  <!-- Регистрация дрона -->
  <section id="register" class="page">
    <h2>Регистрация дрона</h2>
    <form id="registerForm">
      <label for="droneId">Идентификатор дрона (ID):</label>
      <input type="text" id="droneId" name="droneId" required placeholder="Введите ID дрона" />

      <label for="pilotName">Имя пилота:</label>
      <input type="text" id="pilotName" name="pilotName" required placeholder="Введите ваше имя" />

      <label for="route">Маршрут полета:</label>
      <input type="text" id="route" name="route" required placeholder="Координаты или описание маршрута" />

      <button type="submit">Зарегистрировать</button>
    </form>
    <div class="form-message" id="registerMessage"></div>
  </section>

  <!-- Карта -->
  <section id="map" class="page">
    <h2>Карта запретных зон</h2>
    <div id="mapid"></div>
  </section>

  <!-- Личный кабинет -->
  <section id="profile" class="page">
    <h2>Личный кабинет пилота</h2>
    <div id="profileContent">
      <p>Здесь будет информация о вашем дроне и полетах.</p>
      <div class="profile-data" id="profileData" style="display: none;">
        <h3>Ваши данные:</h3>
        <p><strong>ID дрона:</strong> <span id="displayDroneId"></span></p>
        <p><strong>Имя пилота:</strong> <span id="displayPilotName"></span></p>
        <p><strong>Маршрут:</strong> <span id="displayRoute"></span></p>
      </div>
    </div>
    <div class="profile-actions">
      <button onclick="editProfile()">
        <i class="fa-solid fa-pen"></i> Изменить данные
      </button>
      <button onclick="deleteProfile()">
        <i class="fa-solid fa-trash"></i> Удалить регистрацию
      </button>
    </div>
  </section>
</main>

<footer>
  <p>© 2025 UTM Drone Kazakhstan | Все права защищены</p>
</footer>

<!-- Leaflet CDN -->
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.3/dist/leaflet.css"
  integrity="sha256-sA+4t2t0DlI2Ry+ZvLv+Me33qO8E+zj61zD2f+v5S7o="
  crossorigin=""
/>
<script
  src="https://unpkg.com/leaflet@1.9.3/dist/leaflet.js"
  integrity="sha256-nrD7NwRqMkXgIJr2V6sJkPoFfu6jQ6tHRg5v7sjo0uM="
  crossorigin=""
></script>

<script>
  // Сохраненные данные
  let droneData = JSON.parse(localStorage.getItem('droneData')) || null;
  
  // Переключение секций
  function navigateTo(pageId) {
    const pages = document.querySelectorAll('section.page');
    pages.forEach((p) => p.classList.remove('active'));
    document.getElementById(pageId).classList.add('active');

    // Обновляем активный класс меню
    document.querySelectorAll('nav ul li a').forEach(link => {
      link.classList.remove('active');
      if (link.id === 'nav-' + pageId) {
        link.classList.add('active');
      }
    });

    // Инициализируем карту при переходе
    if (pageId === 'map') {
      initMap();
    }
    
    // Обновляем данные в личном кабинете
    if (pageId === 'profile') {
      updateProfile();
    }
  }

  // Обработка формы регистрации
  document.getElementById('registerForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const droneId = this.droneId.value.trim();
    const pilotName = this.pilotName.value.trim();
    const route = this.route.value.trim();

    if (!droneId || !pilotName || !route) {
      showMessage('registerMessage', 'Пожалуйста, заполните все поля', true);
      return;
    }

    // Сохраняем данные
    droneData = { droneId, pilotName, route };
    localStorage.setItem('droneData', JSON.stringify(droneData));
    
    showMessage('registerMessage', `Дрон с ID ${droneId} успешно зарегистрирован!`, false);
    this.reset();
    
    // Обновляем профиль
    updateProfile();
  });

  function showMessage(id, message, isError = false) {
    const el = document.getElementById(id);
    el.textContent = message;
    el.style.color = isError ? 'red' : 'green';
  }

  // Инициализация карты Leaflet
  let map;
  function initMap() {
    if (map) return;
    
    map = L.map('mapid').setView([48.0, 68.0], 6);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18,
      attribution: '© OpenStreetMap'
    }).addTo(map);

    // Пример запретных зон
    const restrictedZones = [
      { name: 'Аэропорт Алматы', lat: 43.3523, lon: 77.0400, radius: 5000 },
      { name: 'Аэропорт Нур-Султан', lat: 51.0225, lon: 71.4669, radius: 4000 }
    ];

    restrictedZones.forEach(zone => {
      L.circle([zone.lat, zone.lon], {
        color: 'red',
        fillColor: '#f03',
        fillOpacity: 0.3,
        radius: zone.radius
      }).addTo(map).bindPopup(`<b>${zone.name}</b><br>Запретная зона`);
    });
  }

  // Обновление данных в профиле
  function updateProfile() {
    const profileData = document.getElementById('profileData');
    if (droneData) {
      document.getElementById('displayDroneId').textContent = droneData.droneId;
      document.getElementById('displayPilotName').textContent = droneData.pilotName;
      document.getElementById('displayRoute').textContent = droneData.route;
      profileData.style.display = 'block';
    } else {
      profileData.style.display = 'none';
    }
  }

  // Редактирование профиля
  function editProfile() {
    if (droneData) {
      document.getElementById('droneId').value = droneData.droneId;
      document.getElementById('pilotName').value = droneData.pilotName;
      document.getElementById('route').value = droneData.route;
      navigateTo('register');
    } else {
      alert('Нет сохраненных данных для редактирования');
    }
  }

  // Удаление профиля
  function deleteProfile() {
    if (confirm('Вы уверены, что хотите удалить регистрацию дрона?')) {
      localStorage.removeItem('droneData');
      droneData = null;
      updateProfile();
      alert('Регистрация удалена');
    }
  }

  // Инициализация при загрузке
  document.addEventListener('DOMContentLoaded', function() {
    updateProfile();
    
    // Если сразу открыта вкладка карты
    if (document.getElementById('map').classList.contains('active')) {
      initMap();
    }
  });
</script>
</body>
</html>
