---
title: Adblock Detector Ala Petani Kode
date: 2021-03-07 17:12:00 Z
layout: post
author: irfnrdh
summary: 
---

Jika kamu pernah mengunjungi website dan terlihat sama seperti dibawah ini sama seperti mengunjungi petani kode akhir-akhir ini akan muncul sebuah count down yang tujuannya membuat kita kesel hingga mematikan adblock karena ada muncul gambar seperti dibawah ini:
![picture 1](../images/e3b23244e2e640f2c3a48c53cad18a13f5a9e0269b6d663be6cdb601dc559cfe.png)  

Hal itu juga pertanda bahwa browser kamu sudah berusaha untuk memblok iklan yang ada dan dengan Adblock Detektor usaha browser kamu pun terdeteksi di sisi client website yang sedang kamu kunjungi seperti petanikode diatas.

Pada kesempatan ini saya akan berbagi cara mendeteksi adblock pada browser client dengan adblock detektor yang di inisialisasikan pada website ataupun blog kamu.
## Oh ya, apaan sih kegunaannya ini?  

hal yang paling sangat dibutuhkan dari adanya iklan kan "uang" jadi jika iklan tidak muncul di sisi pengakses website maka tidak ada pemasukan dari iklan yang diklik ataupun lainnya. Intinya menyangkut kerugian sepihak terhadap pemilik website yang sedang mencari nafkah tambahan dengan websitenya.

## Bagaimana cara agar bisa menambahkan Adblock Detector pada website saya?

Langkah yang harus dilakukan pertama sekali adalah menginstall sebuah pakage yang bernama "Just-Detect-Adblock" yang digunakan sama percis oleh petanikode.

Kamu dapat melihat deskripsi lengkapnya pada [halaman githubnya](https://github.com/wmcmurray/just-detect-adblock).

### Fitur yang tersedia ?

Adapun fitur yang tersedia diantaranya mendeteksi:
- Browser extensions detection (like AdBlock, Adblock Plus, uBlock, etc.)
- Brave browser shields detection
- Opera browser adblocker detection

### Cara meggunakannya ?

Pertama sekali kita harus panggil dulu javascriptnya seperti dibawah ini letakkan di atas penutup body `</body>`  

```html
 <script type="text/javascript">
      // librari dasar untuk mendeteksinya
      !function(t,e){"object"==typeof exports&&"undefined"!=typeof module?module.exports=e():"function"==typeof define&&define.amd?define(e):(t="undefined"!=typeof globalThis?globalThis:t||self).justDetectAdblock=e()}(this,(function(){"use strict";function t(){return void 0!==navigator.brave&&void 0!==navigator.brave.isBrave}function e(){return"string"==typeof navigator.userAgent&&navigator.userAgent.match(/Opera|OPR\//)}function n(){return new Promise((function(t,e){var n=new XMLHttpRequest;n.onreadystatechange=function(){4==n.readyState&&t(n)},n.open("GET","https://raw.githubusercontent.com/wmcmurray/just-detect-adblock/master/baits/pagead2.googlesyndication.com",!0),n.send()}))}function o(t){return 200===t.status&&!t.responseText.match(/^thistextshouldbethere(\n|)$/)}function i(t){return 0===t.status&&!t.responseText.match(/^thistextshouldbethere(\n|)$/)}function r(){if(null!==window.document.body.getAttribute("abp"))return!0;var t=function(){var t=document.createElement("div");return t.setAttribute("class","pub_300x250 pub_300x250m pub_728x90 text-ad textAd text_ad text_ads text-ads text-ad-links ad-text adSense adBlock adContent adBanner"),t.setAttribute("style","width: 1px !important; height: 1px !important; position: absolute !important; left: -10000px !important; top: -1000px !important;"),t}();window.document.body.appendChild(t);var e=function(t){if(null===t.offsetParent||0==t.offsetHeight||0==t.offsetLeft||0==t.offsetTop||0==t.offsetWidth||0==t.clientHeight||0==t.clientWidth)return!0;if(void 0!==window.getComputedStyle){var e=window.getComputedStyle(t,null);if(e&&("none"==e.getPropertyValue("display")||"hidden"==e.getPropertyValue("visibility")))return!0}return!1}(t);return window.document.body.removeChild(t),e}var u;return{detectAnyAdblocker:function(){return new Promise((function(u,d){if(r())return u(!0);t()||e()?n().then((function(n){return t()?u(o(n)):e()?u(i(n)):void u(!1)})):u(!1)}))},detectDomAdblocker:(u=r,function(){var t=arguments;return new Promise((function(e,n){e(u.apply(this,t))}))}),detectBraveShields:function(){return new Promise((function(e,i){t()?n().then((function(t){e(o(t))})):e(!1)}))},detectOperaAdblocker:function(){return new Promise((function(t,o){e()?n().then((function(e){t(i(e))})):t(!1)}))},isDetected:function(t,e){return function(){return console.warn("just-detect-adblock : "+(e||"This method is deprecated.")),t.apply(this,arguments)}}(r,"The `isDetected()` method is now deprecated, please use `detectAnyAdblocker()` instead, which returns a Promise and can detect more stuff (like Brave Shields).")}}));
      
      // pemanggilan
      justDetectAdblock.detectAnyAdblocker().then(function(detected) {
        // jika terdeteksi
        if(detected){
          const $antiadblock = document.getElementById("antiadblock");
            const $countdown = document.getElementById("countdown");
            // jumlah hitung mundurnya
            let countdown = 20;
            // memanggil class display none bawaan dari bootstrap untuk menghilangkannya
            $antiadblock.classList.toggle("d-none");
            const intervalId = setInterval(() => {
              countdown--;
              $countdown.innerText = countdown;
              if (countdown <= 0) {
                clearInterval(intervalId);
                $antiadblock.classList.toggle("d-none");
              }
            }, 1e3);
        }
      });
    </script>
```
diatas saya tidak menggunakan external javascript agar load lebih cepat tapi kamu juga bisa menambahkan external seperti berikut diatas logika adblock detektornya

```html
<script type="text/javascript" src="https://raw.githubusercontent.com/wmcmurray/just-detect-adblock/master/dist/bundle.umd.js"></script>
```
selanjutnya juga kita harus menambahkan style untuk antiadblock nya agar pop-upnya muncul dan berjalan dengan lancar. Jika html tersebut belum menggunakan bootstrap kamu terpaksa harus tambahkan bootstrap agar classnya bisa berjalan, kalau tidak harus dibuat class sendiri dengan penamaan sama ataupun berbeda.

Letakkan di dalam head jika bisa di atas style yang sudah ada.

```html
  
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous">
  
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ho+j7jyWK8fNQe+A12Hb8AhRq26LrZ/JpcUGGOn+Y7RsweNrtN/tE3MoK7ZeZDyx" crossorigin="anonymous"></script>
```

baru selanjutnya letakkan berikut ini dibawah tag `<body>` tujuannya untuk memunculkan peringatan setiap kali adblock tersebut terdeteksi sesuai dengan logika dibuat.

```html
<div id=antiadblock class="bg-white w-100 h-100 position-fixed d-none"
        style=top:0;left:0;opacity:.925;z-index:999999>
        <div class="w-100 h-100 d-flex justify-content-center">
            <div class="col-md-4 my-auto rounded p-4 text-center bg-dark text-white">
                <p>Tunggu sebentar..<br>Kamu terdeteksi menggunakan Adblock</p>
                <p class=display-1 id=countdown>0</p>
                <p class=lead>Tidak mau menunggu?<br>Matikan Adblock!</p>
            </div>
        </div>
    </div>
```

Alhasil jadinya bergini

![picture 1](../images/7b875673359b7097905e0f36f5ac8e36620b69e9e298024a3f85ea61c652b000.png)  




