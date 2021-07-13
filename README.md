# DrawerJS (UG Demo)

Ini adalah [DrawerJS](https://github.com/carstenschaefer/DrawerJs) yang sudah dimodifikasi untuk tujuan pembelajaran.

## Petunjuk Instalasi

Unduh repo ini, bisa dengan `git clone` atau unduh ZIP. Susunan direktori harusnya seperti di bawah:

```bash
gp@pop-os-3770k:~/Devel/html_canvas/drawerJS_GIT$ tree .
.
├── assets
│   ├── border-dashed-bold.png
│   ├── border-dashed-thin.png
│   ├── border.gif
│   ├── border-solid-bold.png
│   ├── border-solid-thin.png
│   ├── cursor-fa-eraser.cur
│   ├── cursor-fa-pencil.cur
│   ├── pencil-square-o.32.png
│   └── transparent.png
├── canvas
│   ├── canvas.css.map
│   ├── canvasLocalization.js
│   ├── canvas.min.css
│   ├── canvas.standalone.js.map
│   └── canvas.standalone.js.min.js
├── canvasConfig.js
├── fonts
│   ├── font-awesome
│   │   └── font-awesome.min.css
│   └── fonts
│       └── fontawesome-webfont.woff2
├── images
│   └── drawer.jpg
├── jQuery
│   └── jquery-3.4.1.min.js
└── README.md

7 directories, 20 files
```

Kemudian buatlah sebuah file HTML, misalnya `index.html`.

Pada bagian `<head>`, muat resource yang diperlukan (minified CSS):

```html
<link rel="stylesheet" href="fonts/font-awesome/font-awesome.min.css" />
<link rel="stylesheet" href="canvas/canvas.min.css" />
```

Di bagian `<body>`, buatlah `<div>` baru yang nantinya akan di-append elemen canvas bawaan DrawerJS, lalu muat resource JS yang dibutuhkan:

(perhatikan `id` pada `<div>` yang disebutkan di atas.)

```html
<h1>UTS</h1>
<div id="canvas-editor" style="margin-top: 100px;"></div>

<script src="jQuery/jquery-3.4.1.min.js"></script>
<script src="canvas/canvas.standalone.js.min.js"></script>
<script src="canvas/canvasLocalization.js"></script>
<script src="canvasConfig.js"></script>
```

Bagian paling penting: kode initialization untuk canvas (dengan JQuery). Perhatikan id selector `$('#canvas-editor')`:

```javascript
$(document).ready(function () {
    var drawer = new DrawerJs.Drawer(null, {
        texts: customLocalization,
        plugins: drawerPlugins,
        defaultImageUrl: '/images/drawer.jpg',
        defaultActivePlugin: { name: 'Pencil', mode: 'lastUsed' },
    }, 600, 600);
    $('#canvas-editor').append(drawer.getHtml());
    drawer.onInsert();
});
```

Tambahkan style seperlunya (di bagian `<head>`):

```css
#canvas-editor {
    margin-top: 50px;
    margin-left: 50px;
}

img {
    margin-top: 5rem;
    display: block;
    margin-left: 5rem;
}
```

Selesai