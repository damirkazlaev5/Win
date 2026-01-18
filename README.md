
<html lang="ru">
<head>
  <meta charset="utf-8" />
  <title>Windows 2001</title>
  <style>
    * {margin:0;padding:0;box-sizing:border-box}
    body {font:12px Arial,sans-serif;color:#000;background:#C0C0C0;height:100vh;padding:4px}
    .w {position:absolute;background:#FFF;border:2px solid #000080;min-width:400px;max-width:800px;overflow:hidden}
    .tb {background:#000080;color:#FFF;padding:4px 8px;font-weight:bold;display:flex;justify-content:space-between;align-items:center;cursor:move}
    .btn {width:16px;height:14px;margin-left:4px;text-align:center;line-height:14px;font:10px/14px Arial;color:#FFF;border:1px solid #808080;background:#606060;cursor:pointer}
    .ct {padding:16px;overflow-y:auto;height:calc(100% - 48px)}
    h1 {font:16px Arial;margin:0 0 12px;color:#800000}
    h2 {font:14px Arial;margin:12px 0 8px;color:#000080}
    a {color:#0000FF;text-decoration:none}
    a:hover {text-decoration:underline}
    .btn2 {background:#E0E0E0;border:1px solid #808080;padding:2px 8px;cursor:pointer;font:12px Arial;margin:4px 0}
    .tabs {display:flex;border-bottom:1px solid #808080;background:#D0D0D0}
    .tab {padding:4px 12px;cursor:pointer;border:1px solid #808080;border-bottom:none;background:#F0F0F0;margin-right:-1px}
    .tab.active {background:#FFF;border-bottom:1px solid #FFF}
    .footer {text-align:center;margin-top:16px;color:#666;font:11px Arial;border-top:1px solid #C0C0C0;padding-top:8px}
  </style>
</head>
<body>
  <div id="desk" style="height:100%">
    <div class="w" id="win" style="width:700px;height:500px;top:50px;left:50px">
      <div class="tb" id="title">
        <div>Мой сайт — Windows 2001</div>
        <div>
          <div class="btn" onclick="minimizeWindow()">_</div>
          <div class="btn" onclick="maximizeWindow()">□</div>
          <div class="btn" onclick="closeWindow()">×</div>
        </div>
      </div>
      <div class="tabs">
        <div class="tab active" onclick="showTab('home')">Главная</div>
        <div class="tab" onclick="showTab('about')">О сайте</div>
        <div class="tab" onclick="showTab('contacts')">Контакты</div>
        <div class="tab" onclick="showTab('news')">Новости</div>
      </div>
      <div class="ct" id="content">
        <div id="home" class="tc">
          <h1>Добро пожаловать!</h1>
          <p>Это пример сайта в стиле Windows начала 2000‑х.</p>
          <h2>Возможности</h2>
          <ul><li>Перетаскивание</li><li>Управление окном</li><li>Вкладки</li><li>Рабочие кнопки</li></ul>
          <button class="btn2" onclick="alert('Работает!')">Нажать</button>
        </div>
        <div id="about" class="tc" style="display:none">
          <h1>О сайте</h1>
          <p>Реализованы классические элементы Windows XP/2000:</p>
          <ul><li>Шрифт Arial 12px</li><li>Синяя панель</li><li>Серые кнопки</li><li>Синий цвет ссылок</li></ul>
        </div>
        <div id="contacts" class="tc" style="display:none">
          <h1>Контакты</h1>
          <h2>Связь</h2>
          <ul>
            <li><a href="" target="_blank">RuTube</a></li>
          </ul>
  
        </div>
        <div id="news" class="tc" style="display:none">
          <h1>Новости</h1>
          <p>Обновления:</p>
          <ul>
            <li><b>15.01.2001</b> — Запуск сайта</li>
            <li><b>10.01.2001</b> — Дизайн готов</li>
            <li><b>05.01.2001</b> — Начало разработки</li>
          </ul>
        </div>
        <div class="footer">© 2001 Мой сайт. Все права защищены.</div>
      </div>
    </div>
  </div>

  <script>
    const win = document.getElementById('win');
    const title = document.getElementById('title');
    let isDragging = false, offsetX, offsetY;

    title.onmousedown = (e) => {
      isDragging = true;
      offsetX = e.clientX - win.getBoundingClientRect().left;
      offsetY = e.clientY - win.getBoundingClientRect().top;
    };

    document.onmousemove = (e) => {
      if (isDragging) {
        win.style.left = (e.clientX - offsetX) + 'px';
        win.style.top = (e.clientY - offsetY) + 'px';
      }
    };

    document.onmouseup = () => isDragging = false;

    function minimizeWindow() { win.style.display = 'none'; }
    function maximizeWindow() { win.style.width = '100%'; win.style.height = '100%'; win.style.top = '0'; win.style.left = '0'; }
    function closeWindow() { win.remove(); }
    function showTab(id) {
      document.querySelectorAll('.tab').forEach(t => t.classList.toggle('active', t.innerText.toLowerCase() === id));
      document.querySelectorAll('.tc').forEach(c => c.style.display = c.id === id ? 'block' : 'none');
    }
  </script>
</body>
</html>
