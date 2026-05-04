# yacht-calc

Многоязычный калькулятор стоимости аренды яхты для [yacht.az](https://yacht.az).

Один HTML-блок с встроенным CSS и JS. Тянет цены и яхты из публичной Google Sheet, поддерживает RU / EN / AZ, валюты AZN / USD / RUB с живым курсом.

## Использование на Tilda (через jsDelivr)

В блок T123 (HTML Embed) или T669 (Popup) на любой странице вставить:

```html
<div id="yz-calc-mount"></div>
<script>
(function(){
  var url = 'https://cdn.jsdelivr.net/gh/Profbroker/yacht-calc@main/tilda-calc-block.html';
  fetch(url).then(function(r){ return r.text(); }).then(function(html){
    var mount = document.getElementById('yz-calc-mount');
    mount.innerHTML = html;
    mount.querySelectorAll('script').forEach(function(old){
      var s = document.createElement('script');
      s.textContent = old.textContent;
      old.parentNode.replaceChild(s, old);
    });
  });
})();
</script>
```

Калькулятор сам определит язык страницы по URL (`/ru/`, `/en/`, `/az/`).

## Прямой URL для разработки

```
https://cdn.jsdelivr.net/gh/Profbroker/yacht-calc@main/tilda-calc-block.html
```

jsDelivr кэширует ~5–10 минут после пуша в `main`. Для мгновенного обновления использовать конкретный коммит-хэш вместо `main`:

```
https://cdn.jsdelivr.net/gh/Profbroker/yacht-calc@<commit-sha>/tilda-calc-block.html
```

## Источник данных

- **Google Sheets (yachts):** опубликованная таблица с яхтами, ценами, сезонностью
- **Курсы валют:** [open.er-api.com](https://open.er-api.com) (бесплатный)

## Лицензия

MIT — см. [LICENSE](./LICENSE).
