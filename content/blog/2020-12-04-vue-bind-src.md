---
title: Cara memanggil data gambar di VueJs
date: 2020-12-04 17:00:00 Z
categories:
- pertama
author: irfnrdh
layout: post
---

jika langsung menggunakan `<img src="{{gambarnya}}">`
pada data berikut

```
export default {
    name: 'gambar',
    data: function(){
      return{
        gambarnya: "https://piranhasmartcenter.com/img/logo.png"
      }
    }
}
```

maka akan tampil **error**.

nah disini menggunakan bind dengan `:src`

jadi `<img :src="gambarnya" alt="keterangan gambar">`

atau juga dengan button dinamis dengan method

```
export default {
    name: 'NavBar',
    data: function(){
      return{
        logo: null
      }
    },
    methods: {
      dapatGambar () {
        this.logo = 'https://avatars2.githubusercontent.com/u/7637012?s=460&amp;u=d7acae821b506d5dda36e417bb83b97eafa473e6&amp;v=4'
      }
    }
}
```

lalu dipanggil dengan ` <a @click="dapatGambar()" href="#">Lihat Gambar</a>`

dan bisa di hilangkan blocknya dengan `v-if`

seperti ini 
```
<span v-if="logo">
<img :src="logo" alt="Createx Logo" width="230">
</span>
```

jadi logo akan muncul ketika di klik.

Selamat mencoba!
