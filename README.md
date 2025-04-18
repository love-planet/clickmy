<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Redirecting...</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      margin-top: 20%;
      padding: 0 20px;
      background-color: #f9f9f9;
    }

    h2 {
      margin-bottom: 30px;
    }

    button {
      padding: 15px 30px;
      font-size: 18px;
      background-color: #00aaff;
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      animation: pulse 1.8s infinite;
      box-shadow: 0 0 0 rgba(0, 170, 255, 0.4);
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.05);
    }

    @keyframes pulse {
      0% {
        transform: scale(1);
        box-shadow: 0 0 0 0 rgba(0, 170, 255, 0.4);
      }
      70% {
        transform: scale(1.08);
        box-shadow: 0 0 0 10px rgba(0, 170, 255, 0);
      }
      100% {
        transform: scale(1);
        box-shadow: 0 0 0 0 rgba(0, 170, 255, 0);
      }
    }
  </style>
</head>
<body>
  <h2 id="headline">Нажмите кнопку ниже, чтобы открыть </h2>
  <button id="redirectBtn">Открыть</button>

  <script>
    const translations = {
      ru: {
        headline: "Нажмите кнопку ниже, чтобы открыть",
        button: "Открыть"
      },
      en: {
        headline: "Tap the button below to open ",
        button: "Open"
      }
    };

    const userLang = navigator.language.startsWith("ru") ? "ru" : "en";

    document.getElementById("headline").innerText = translations[userLang].headline;
    document.getElementById("redirectBtn").innerText = translations[userLang].button;

    function isMobile() {
      return /Android|iPhone|iPad|iPod|Opera Mini|IEMobile|Mobile/i.test(navigator.userAgent);
    }

    const offers = [
      "https://grzvkg.trueamouronline.com/?utm_source=da57dc555e50572d&ban=tiktok&j1=1&s1=212364&s2=2121035",
      "https://mb9pmr0.vipsthelovehaven.com/lw4h4aw?s1=testTT",
      "https://mb9pmr0.meethotlove.com/lwyrlwm?s1=testTT2",
      "https://prev.affomelody.com/VgeE8p"
    ];

    const desktopRedirect = "https://www.instagram.com/men.click_here0?igsh=d2tleGZ1MzE1eGV4";

    document.getElementById("redirectBtn").addEventListener("click", function () {
      let targetUrl;

      if (isMobile()) {
        const randomIndex = Math.floor(Math.random() * offers.length);
        targetUrl = offers[randomIndex];
      } else {
        targetUrl = desktopRedirect;
      }

      window.open(targetUrl, "_blank");

      setTimeout(() => {
        window.location.href = targetUrl;
      }, 1500);
    });
  </script>
</body>
</html>
