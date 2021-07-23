---
createdAt: 2021-07-23T14:52:49.775Z
title: Membuat Transparent Background Images dengan CSS
---
Jadi gak ada opsi untuk buat transparasi pada background tapi kita bisa ngakalinnya dengan psudo after dengan posisi absolut, Seperti berikut ini:

```css
body{
		background-color: #1E2530;
	}
body::after {
        content: "";
        background: url(bg.jpg);
        background-size: cover;
        background-attachment: fixed;
        opacity: 0.5;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        position: absolute;
        z-index: -1;   
  }
```