---
title: Display Flex center
date: 2020-12-06 07:44:00 Z
categories:
- pertama
tags:
- HTML
- Flexbox
author: irfnrdh
comment: true
layout: post
---

Membuat konten menjadi ketengah keknya memang menjadi kebutuhan seorang yang sedang utak-atik front end.

dengan display flex cara membuat sepenuhnya ketengah jadi lebih mudah baik itu horizontal dan vertikal.

```css
.tengah {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

atau jika menggunakan bootstrap cukup dengan 

```html
<div class="col-lg-6 d-flex justify-content-center align-items-center bg-white">
Konten
</div>
```