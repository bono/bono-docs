# Instalasi

Pastikan kalian memiliki `gem` terinstal baik di sistem kalian, cek dengan menjalankan perintah ini di terminal:

```sh
gem --version # output => 1.8.23.2
```

Kemudian install `bundler`, dengan menjalankan perintah:

```sh
gem install bundler
```

Cek instalasi `bundler` dengan:


```sh
bundle --version # output => Bundler version 1.7.6
```

Clone repository ini:

```sh
git clone git@github.com:bono/bono-docs.git
```

Lakukan instalasi kebutuhan untuk deployment ke Github Pages:

```sh
bundle install
```

Jika semua dependensi sudah terpenuhi, jalankan perintah ini untuk melakukan deployment:

```sh
bundle exec jekyll serve
```

Kemudian buka page [localhost:4000][localhost] untuk melihat page. Setiap ada perubahan terjadi pada source code, project
akan melakukan rebuild secara otomatis. Ubah dokumentasi, tulis beberapa hal mengagumkan tentang [Bono][bono], kemudian commit
dan push.

# Contributing

- Fork repo ini
- Clone repo kamu yang baru saja kamu fork
- Lakukan perubahan
- Commit
- Push ke origin kalian
- Buat permintaan pull
- Jika permintaan pull sudah diterima, lakukan merging dengan menambahkan repo ini ke dalam remote git kamu. Caranya `git remote add upstram git@github.com:bono/bono-docs.git`
- Merge upstream ke lokal repo `git pull upstram master`
- Push lokal repo kalian ke Github repo `git push origin master`

Read the docs: https://bono.github.io

[localhost]: http://localhost:4000
[bono]: https://github.com/xinix-technology/bono

