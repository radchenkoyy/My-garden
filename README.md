<!DOCTYPE html>
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
      lat: 55.751320,
      lng: 37.618550,
      year: '2024',
      rootstock: 'Айва',
      watering: '2 раза в неделю',
      pruning: 'апрель',
      description: 'Неприхотливый летний сорт груши.',
      image: 'https://upload.wikimedia.org/wikipedia/commons/c/cf/Pears.jpg',
      page: 'https://ru.wikipedia.org/wiki/Груша'
    },

    {
      name: '🍒 Вишня Молодежная',
      lat: 55.751180,
      lng: 37.618300,
      year: '2023',
      rootstock: '—',
      watering: 'умеренный',
      pruning: 'февраль',
      description: 'Компактная и урожайная вишня.',
      image: 'https://upload.wikimedia.org/wikipedia/commons/b/bb/Cherry_Stella444.jpg',
      page: 'https://ru.wikipedia.org/wiki/Вишня'
    }
  ];

  // Добавление деревьев на карту
  trees.forEach(tree => {
    const popupContent = `
      <div class="tree-popup">
        <img src="${tree.image}" alt="${tree.name}">

        <div class="tree-title">${tree.name}</div>

        <div class="tree-info"><b>Год посадки:</b> ${tree.year}</div>
        <div class="tree-info"><b>Подвой:</b> ${tree.rootstock}</div>
        <div class="tree-info"><b>Полив:</b> ${tree.watering}</div>
        <div class="tree-info"><b>Обрезка:</b> ${tree.pruning}</div>

        <div class="tree-info">${tree.description}</div>

        <a class="tree-link" href="${tree.page}" target="_blank">
          Подробнее о сорте
        </a>
      </div>
    `;

    L.marker([tree.lat, tree.lng])
      .addTo(map)
      .bindPopup(popupContent);
  });
</script>

</body>
</html>
