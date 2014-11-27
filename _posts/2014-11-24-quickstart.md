---
layout: page
title: "Quickstart"
className: "quickstart"
category: doc
date: 2014-11-24 14:07:26
---

### Kebutuhan Sebelum Menggunakan Bono PHP Framework
- Composer
- Git (sebuah *Version Controll System*)
- PHP >= 5.4
- PHP `mcrypt` extension

### Langkah Tercepat (Gunakan Archetype)

- Clone repo `bono-arch` dengan perintah `git clone https://github.com/reekoheek/bono-arch my-awesome-project`
- Pindah ke direktori `my-awesome-project` dengan perintah `cd my-awesome-project`
- Jalankan perintah `composer install -vvv`
- Setelah selesai, pindah ke folder `www` dengan perintah `cd www`
- Jalankan perintah `php -S 0.0.0.0:8000`
- Buka browser dan arahkan ke alamat url [http://localhost:8000][url]

### Routing

Pertama kali membuka halaman [http://localhost:8000][url], kalian pasti bertanya-tanya darimana tampilan ini datang. Tampilan ini di-render oleh [middleware][middleware] bernama `Bono\Middleware\StaticPageMiddleware`. `StaticPageMiddleware` bekerja dengan cara: Jika *end-point routing* yang belum digunakan dia akan mencoba mencari sebuah template file di dalam folder `templates/static`. Jika halaman `index` (permintaan ke *root path*) belum digunakan dia akan mencari file template `templates/static/index.php` untuk di-render. Untuk menghilangkan *behavior* ini, kalian harus mengubah routing pada file `www/index.php`. Sebelum baris ini:

```php
$app->run();
```

Sisipkan *code* berikut:

```php
$app->get('/', function () {
    echo 'Hello, world';
});
```

Code ini berarti:

> Jika ada permintaan menuju *root path* dengan *method* `GET`, maka tampilkan pesan `Hello, world!`.

Baca lebih lanjut tentang *routing* [di sini][routing].

### View

Untuk membuat *view* / *template*, pastikan kalian membuatnya di dalam folder `templates/`. Buat satu file template dengan nama `home.php` di dalam folder `templates/`:

```html
<h2>Hai, kalian!</h2>

<p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum, quidem laborum aut atque blanditiis molestias ipsam quos reprehenderit, fuga repellendus autem officia praesentium ea veniam ducimus nam esse accusantium reiciendis?
</p>
```

Lalu pada routing, ubah baris *code* berikut:

```php
$app->get('/', function () use ($app) {
    $app->response->template('home');
});
```

Kemudian reload halaman [http://localhost:8000][url] untuk melihat hasilnya.

#### Memasukkan Variabel ke Dalam View

Ubah template kalian menjadi seperti ini:

```html
<h2><?php echo $hello ?></h2>

<p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum, quidem laborum aut atque blanditiis molestias ipsam quos reprehenderit, fuga repellendus autem officia praesentium ea veniam ducimus nam esse accusantium reiciendis?
</p>
```

Lalu pada routing, ganti menjadi:

```php
$app->get('/', function () use ($app) {
    $app->response->data(array('hello' => 'Salam hangat!'));
    $app->response->template('home');
});
```
Kemudian reload halaman [http://localhost:8000][url] untuk melihat hasilnya. Baca lebih lanjut tentang *view* [di sini][view].

[url]: http://localhost:8000
[middleware]: {{ site.url }}/doc/middleware
[routing]: {{ site.url }}/doc/routing
[view]: {{ site.url }}/doc/view
