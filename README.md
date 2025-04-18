<?php
$offers = [
  "https://grzvkg.trueamouronline.com/?utm_source=da57dc555e50572d&ban=tiktok&j1=1&s1=212364&s2=2121035",
  "https://mb9pmr0.vipsthelovehaven.com/lw4h4aw?s1=testTT",
  "https://mb9pmr0.meethotlove.com/lwyrlwm?s1=testTT2",
  "https://prev.affomelody.com/VgeE8p"
];

$randomIndex = rand(0, count($offers) - 1);
$selectedOffer = $offers[$randomIndex];

// Уникальный параметр, чтобы TikTok не кэшировал
$selectedOffer .= (strpos($selectedOffer, '?') === false ? '?' : '&') . 'ref=' . uniqid();

header("Location: $selectedOffer", true, 301);
exit();
?>
