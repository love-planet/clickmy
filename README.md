
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Open Link</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: linear-gradient(to right bottom, rgb(26, 32, 44), rgb(74, 29, 150), rgb(91, 33, 182));
      color: #fff;
      font-family: Arial, sans-serif;
      height: 100vh;
      text-align: center;
    }
    #container {
      max-width: 600px;
      margin: 0 auto;
    }
    h1 {
      font-size: 3rem;
      margin: 0;
    }
    .button-container {
      margin-top: 20px;
    }
    button {
      padding: 1rem 2rem;
      font-size: 1.2rem;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin: 0.5rem;
      animation: pulse 2s infinite;
    }
    button:hover {
      background-color: #45a049;
    }
    select {
      font-size: 1.2rem;
      padding: 0.5rem;
      margin-top: 20px;
    }
    img {
      width: 100px;
      margin-top: 20px;
      cursor: pointer;
    }
    @keyframes pulse {
      0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(76, 175, 80, 0.4); }
      70% { transform: scale(1.1); box-shadow: 0 0 0 10px rgba(76, 175, 80, 0); }
      100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(76, 175, 80, 0); }
    }

    /* Modal */
    #modal {
      display: none;
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.6);
      justify-content: center;
      align-items: center;
      z-index: 999;
    }

    #modalContent {
      background: white;
      color: black;
      padding: 20px 30px;
      border-radius: 10px;
      text-align: center;
    }

    #modalContent p {
      margin-bottom: 20px;
    }

    #modalContent button {
      background-color: #007AFF;
      font-size: 1rem;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 8px;
      color: white;
    }
  </style>
</head>
<body>
  <div id="container">
    <h1>Смелее</h1>

    <select id="languageSelect" onchange="changeLanguage()">
      <option value="en">English</option>
      <option value="ru">Русский</option>
    </select>

    <div class="button-container">
      <button id="openLinkBtn" onclick="openLink()">Open</button>
      <img id="iosImg" src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Apple_logo_black.svg" alt="iOS Icon" />
    </div>
  </div>

  <!-- Modal -->
  <div id="modal">
    <div id="modalContent">
      <p>Открыть в Safari?</p>
      <button onclick="confirmOpen()">Открыть</button>
    </div>
  </div>

  <script>
    const offers = [
      "https://grzvkg.trueamouronline.com/?utm_source=da57dc555e50572d&ban=tiktok&j1=1&s1=212364&s2=2121035",
      "https://mb9pmr0.vipsthelovehaven.com/lw4h4aw?s1=testTT",
      "https://mb9pmr0.meethotlove.com/lwyrlwm?s1=testTT2",
      "https://prev.affomelody.com/VgeE8p"
    ];
    const selectedOffer = offers[Math.floor(Math.random() * offers.length)];
    const telegramIOS = "https://t.me/+2qVpuj3dWAw2ZmEy";
    const telegramOthers = "https://t.me/+VZ2a5LQI3whjYjgy";

    let longPressTimer;

    function changeLanguage() {
      const lang = document.getElementById('languageSelect').value;
      if (lang === 'ru') {
        document.getElementById('openLinkBtn').textContent = 'Открыть';
        document.querySelector('h1').textContent = 'Жми на кнопку там 18+';
        document.querySelector('#modalContent p').textContent = 'Открыть в Safari?';
        document.querySelector('#modalContent button').textContent = 'Открыть';
      } else {
        document.getElementById('openLinkBtn').textContent = 'Open';
        document.querySelector('h1').textContent = 'Click on the 18+ button';
        document.querySelector('#modalContent p').textContent = 'Open in Safari?';
        document.querySelector('#modalContent button').textContent = 'Open';
      }
    }

    document.addEventListener("DOMContentLoaded", () => {
      const userLang = navigator.language || navigator.userLanguage;
      document.getElementById('languageSelect').value = userLang.includes('ru') ? 'ru' : 'en';
      changeLanguage();

      const iosImg = document.getElementById('iosImg');
      iosImg.addEventListener('touchstart', startLongPress);
      iosImg.addEventListener('mousedown', startLongPress);
      iosImg.addEventListener('touchend', cancelLongPress);
      iosImg.addEventListener('mouseup', cancelLongPress);
      iosImg.addEventListener('mouseleave', cancelLongPress);
    });

    function startLongPress() {
      longPressTimer = setTimeout(() => {
        document.getElementById('modal').style.display = 'flex';
      }, 800);
    }

    function cancelLongPress() {
      clearTimeout(longPressTimer);
    }

    function confirmOpen() {
      window.location.href = selectedOffer;
    }

    function openLink() {
      const isAndroid = /Android/i.test(navigator.userAgent);
      const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);

      if (isAndroid) {
        const formattedUrl = selectedOffer.replace(/^https?:\/\//, '');
        window.location.href = `intent://${formattedUrl}#Intent;scheme=https;package=com.android.chrome;end`;
      } else if (isIOS) {
        window.location.href = telegramIOS;
      } else {
        window.location.href = telegramOthers;
      }
    }
  </script>
</body>
</html>
