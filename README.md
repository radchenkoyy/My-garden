<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>

  <title>Мой сад</title>

  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet/dist/leaflet.css"
  />

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f4f4f4;
    }

    header {
      background: #2e7d32;
      color: white;
      text-align: center;
      padding: 16px;
      font-size: 24px;
      font-weight: bold;
    }

    #map {
      width: 100%;
      height: calc(100vh - 60px);
    }

    .popup {
      width: 220px;
    }

    .popup img {
      width: 100%;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    .title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 8px;
    }

    .info {
      margin-bottom: 6px;
    }

    .link {
      display: inline-block;
      margin-top: 10px;
      color: #2e7d32;
      text-decoration: none;
      font-weight: bold;
    }

    .link:hover {
      text-decoration: underline;
    }
  </style>
</head>

<body>

<header>
  🌳 Мой сад
</header>

<div id="map"></div>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<script>

  // Создание карты

  const map = L.map('map').setView([55.751244, 37.618423], 18);

  // Подключение карты

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap'
  }).addTo(map);

  // База деревьев

  const trees = [

    {
      name: '🍎 Яблоня Антоновка',
      lat: 55.751244,
      lng: 37.618423,
      year: '2025',
      rootstock: '54-118',
      watering: '1 раз в неделю',
      pruning: 'март',
      description: 'Классический зимний сорт яблони.',
      image: 'https://upload.wikimedia.org/wikipedia/commons/5/5b/Antonovka_apples.jpg',
      page: 'https://ru.wikipedia.org/wiki/Антоновка'
    },

    {
      name: '🍐 Груша Чижовская',
      lat: 55.751330,
      lng: 37.618560,
      year: '2024',
      rootstock: 'Айва',
      watering: '2 раза в неделю',
      pruning: 'апрель',
      description: 'Популярный летний сорт груши.',
      image: 'https://upload.wikimedia.org/wikipedia/commons/c/cf/Pears.jpg',
      page: 'https://ru.wikipedia.org/wiki/Груша'
    },

    {
      name: '🍒 Вишня Молодежная',
      lat: 55.751150,
      lng: 37.618290,
      year: '2023',
      rootstock: '—',
      watering: 'умеренный',
      pruning: 'февраль',
      description: 'Компактный урожайный сорт.',
      image: 'https://upload.wikimedia.org/wikipedia/commons/b/bb/Cherry_Stella444.jpg',
      page: 'https://ru.wikipedia.org/wiki/Вишня'
    }

  ];

  // Вывод деревьев на карту

  trees.forEach(tree => {

    const popup = `
      <div class="popup">

        <img src="${tree.image}" alt="${tree.name}">

        <div class="title">${tree.name}</div>

        <div class="info">
          <b>Год посадки:</b> ${tree.year}
        </div>

        <div class="info">
          <b>Подвой:</b> ${tree.rootstock}
        </div>

        <div class="info">
          <b>Полив:</b> ${tree.watering}
        </div>

        <div class="info">
          <b>Обрезка:</b> ${tree.pruning}
        </div>

        <div class="info">
          ${tree.description}
        </div>

        <a class="link" href="${tree.page}" target="_blank">
          Подробнее
        </a>

      </div>
    `;

    L.marker([tree.lat, tree.lng])
      .addTo(map)
      .bindPopup(popup);

  });

</script>

</body>
</html>
