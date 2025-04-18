<script>
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

  function getRandomOffer() {
    const index = Math.floor(Math.random() * offers.length);
    const randomSuffix = Math.random().toString(36).substring(2, 10);
    const url = offers[index];
    const separator = url.includes("?") ? "&" : "?";
    return url + separator + "ref=" + randomSuffix;
  }

  document.getElementById("redirectBtn").addEventListener("click", function () {
    let offerUrl = isMobile() ? getRandomOffer() : desktopRedirect;

    if (/Android/i.test(navigator.userAgent)) {
      // Android — открыть через Chrome
      const chromeIntent = `intent://${offerUrl.replace(/^https?:\/\//, '')}#Intent;scheme=https;package=com.android.chrome;end`;
      window.location = chromeIntent;
    } else if (/iPhone|iPad|iPod/i.test(navigator.userAgent)) {
      // iOS — попытка открыть через Safari
      const safariHack = `x-web-search://?url=${encodeURIComponent(offerUrl)}`;
      window.location = safariHack;

      // fallback — откроет обычную ссылку, если safariHack не сработает
      setTimeout(() => {
        window.location = offerUrl;
      }, 500);
    } else {
      // Десктоп
      window.location = desktopRedirect;
    }
  });
</script>
