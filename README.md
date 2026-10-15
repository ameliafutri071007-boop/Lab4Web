# Laporan Praktikum Lab4Web

**Nama:** Amelia Futri
**Mata Kuliah:** Pemrograman Web  
**Nim:** 312510348

| | |
|---|---|
| **Nama** | Amelia Futri|
| **NIM** | 312510348 |
| **Kelas** | I251A|
| **Matkul** | Pemrograman Web |

## Daftar Isi

- [1. Tujuan Praktikum](#1-tujuan-praktikum)
- [2. Dasar Teori](#2-dasar-teori)
- [3. Alat dan Bahan](#3-alat-dan-bahan)
- [4. Struktur Folder](#4-struktur-folder)
- [5. Hasil dan Pembahasan](#5-hasil-dan-pembahasan)
- [6. Kendala dan Catatan](#6-kendala-dan-catatan)
- [7. Kesimpulan](#7-kesimpulan)

##  Tujuan Praktikum

- Memahami struktur dasar pembuatan layout web.
- Memahami konsep *box element* (content, padding, border, margin).
- Memahami CSS Floating (`float` dan `clear`).
- Memahami elemen semantik HTML5.
- Membuat layout web sederhana yang terdiri dari header, navigasi, hero panel, konten utama, sidebar, dan footer.


## Struktur Folder

```text
Lab4Web/
├── README.md              <- laporan ini
├── lab4_box.html          <- latihan box element, float, dan clear
├── lab4_layout/
│   ├── home.html          <- layout sederhana (halaman Home)
│   ├── about.html         <- tugas 1: halaman About
│   ├── kontak.html        <- tugas 2: halaman Kontak (form)
│   └── style.css          <- seluruh CSS layout
└── screenshots/           <- screenshot hasil setiap langkah
```


#### 1 Persiapan dokumen HTML

Langkah pertama adalah membuat folder `Lab4Web` dan file `lab4_box.html` berisi kerangka HTML5. Di dalam `<body>` ditambahkan elemen semantik `<header>` yang memuat judul `<h1>`. Tag `<meta name="viewport">` ditambahkan agar halaman tampil proporsional di berbagai ukuran layar.

**![gambar1.png](screenshots/gambar1.png)**
![hasil1.png](screenshots/hasil1.png)
> *Gambar 1. Dokumen dasar lab4_box.html (baru berisi header)*

**Analisis:** pada tahap ini halaman hanya menampilkan judul "Box Element" karena belum ada konten lain.

#### 2 Membuat box element dengan tag div (tanpa float)

Selanjutnya dibuat tiga buah `<div>` di dalam `<section>`, masing-masing dengan class `div1`, `div2`, dan `div3`. CSS diberikan lewat tag `<style>` pada `<head>`: padding `10px` untuk semua `div` dan warna latar merah, kuning, hijau.

> **[Tempel screenshot di sini]**
>![gambar2.png](screenshots/gambar2.png)
>![hasil2.png](screenshots/hasil2.png)
> *Gambar 2. Element div tanpa float (tersusun vertikal)*

**Analisis:** `<div>` adalah elemen *block-level*, sehingga secara default lebarnya memenuhi seluruh lebar induk dan setiap div berada di baris baru. Ketiga kotak karenanya tersusun ke bawah.

#### 3 CSS Float Property

Agar ketiga kotak berjajar ke samping, ditambahkan `float: left;` pada selector `div`.

> **[Tempel screenshot di sini]**
>![gambar3.png](screenshots/gambar3.png)
>![hasil3.png](screenshots/hasil3.png)
> *Gambar 3. Box element dengan float: left (berjajar horizontal)*

**Analisis:** elemen yang di-*float* dikeluarkan dari alur normal dokumen. Lebarnya menyesuaikan isi (*shrink-to-fit*), lalu elemen digeser ke kiri sehingga Div 1, Div 2, dan Div 3 tampil berdampingan. Akibat sampingannya, tinggi `<section>` menjadi nol karena semua anaknya mengambang.

#### 4 Mengatur clearfix element

Ditambahkan elemen `div4` setelah `div3`. Agar Div 4 tidak ikut naik ke samping float sebelumnya, diberikan `clear: left;` dan `float: none;`.

> **[Tempel screenshot di sini]**
>![gambar4.png](screenshots/gambar4.png)
>![hasil4.png](screenshots/hasi4.png)
> *Gambar 4. Hasil clear: left pada Div 4*

**Analisis:** `clear: left` memerintahkan elemen untuk turun sampai tidak ada lagi float kiri di atasnya. Hasilnya Div 4 berada di baris baru di bawah Div 1-3 dan membentang selebar penuh.


### Bagian Layout Web Sederhana (`lab4_layout`)

#### 5. Kerangka HTML dan elemen semantik

Dibuat folder `lab4_layout` berisi `home.html` dan `style.css`. File HTML dihubungkan dengan CSS memakai `<link rel="stylesheet" href="style.css">`. Seluruh isi halaman dibungkus oleh `<div id="container">` agar mudah diatur lebarnya. Di dalam container dibuat kerangka dengan elemen semantik: `<header>`, `<nav>`, `<section id="hero">`, `<section id="wrapper">` (berisi `<section id="main">` dan `<aside id="sidebar">`), serta `<footer>`.

> **[Tempel screenshot di sini]**
> ![gambar5.png](screenshots/gambar5.png)
>![hasil5.png](screenshots/hasi5.png)
> *Gambar 7. Tampilan kerangka layout (belum diberi CSS)*

**Analisis:** tanpa CSS, browser hanya menampilkan gaya bawaan: judul, link navigasi berjajar sebaris, dan teks footer. Struktur HTML sudah benar, tinggal diberi tampilan.

#### 6. CSS dasar, container, dan header

Pada `style.css` ditambahkan: (1) `@import` Google Font *Open Sans*; (2) *reset CSS* `* { margin: 0; padding: 0; }` untuk menghapus margin dan padding bawaan browser; (3) gaya `body` (font, ukuran, warna teks); (4) `#container` selebar `980px`, diposisikan di tengah dengan `margin: 0 auto` dan diberi bayangan `box-shadow`; (5) gaya `header` dan `header h1`.

> **[Tempel screenshot di sini]**
>![gambar6.png](screenshots/gambar6.png)
>![hasil6.png](screenshots/hasil6.png)
> *Gambar 8. Tampilan header layout*

**Analisis:** container kini berada di tengah halaman dengan bayangan tipis di kiri-kanan. Judul memakai warna abu-abu muda dan font Open Sans. Navigasi dan footer masih tampil polos karena belum diberi CSS.

#### 7. Membuat navigasi

`nav` dibuat berlatar biru. Link `a` dijadikan `inline-block` agar bisa diberi padding, sehingga area klik lebih luas dan menu tetap berjajar horizontal. Link yang aktif (`a.active`) dan saat disorot mouse (`a:hover`) diberi warna latar lebih terang.

> **[Tempel screenshot di sini]**
>![gambar7.png](screenshots/gambar7.png)
>![hasil7.png](screenshots/hasil7.png)
> *Gambar 9. Tampilan navigasi*

**Analisis:** menu Home, Artikel, About, Kontak tampil sebagai bilah biru. Menu Home terlihat aktif karena memiliki class `active`.

#### 8. Membuat hero panel

Hero panel adalah area sorotan di bawah navigasi. Isinya judul, paragraf, dan link "Learn more", lalu diberi CSS latar abu-abu, padding, dan jarak bawah (`margin-bottom`).

> **[Tempel screenshot di sini]**
>![gambar8.png](screenshots/gambar8.png)
>![hasil8.png](screenshots/hasil8.png)
> *Gambar 10. Tampilan hero panel*

**Analisis:** hero tampil sebagai blok abu-abu selebar container. Tombol "Learn more" pada tahap ini masih berupa link biasa karena class `btn` belum didefinisikan (lihat langkah 5.14).

#### 9 Mengatur layout main dan sidebar (float) serta widget

Kolom konten utama (`#main`) dan sidebar (`#sidebar`) dibuat berdampingan dengan `float: left`. Lebar total harus pas dengan container: `#main` 640px + padding 2x20px = 680px, `#sidebar` 260px + padding 2x20px = 300px, jumlahnya **980px**. Jika lebih dari itu, sidebar akan turun ke bawah.

Sidebar kemudian diisi dua widget (`widget-box`): daftar link dan teks, dengan CSS judul berlatar biru, daftar tanpa bullet, dan efek *hover* pada link.

> **[Tempel screenshot di sini]**
>![gambar9.png](screenshots/gambar9.png)
> *Gambar 11. Tampilan sidebar widget (footer belum di-clear)*

**Analisis:** sidebar berada di kanan, sedangkan kolom main masih kosong. Perhatikan teks footer yang "naik" dan menimpa area di bawah sidebar. Ini terjadi karena `#main` dan `#sidebar` sama-sama float, sehingga tinggi `#wrapper` runtuh menjadi nol dan footer tidak tahu harus mulai di mana. Masalah ini diselesaikan pada langkah berikut.

#### 10 Mengatur footer

Footer diberi `clear: both;` agar berada di bawah semua elemen float, serta latar gelap dan teks terang.

> **[Tempel screenshot di sini]**
>![gambar10.png](screenshots/gambar10.png)
> *Gambar 12. Tampilan footer setelah clear: both*

**Analisis:** footer kini tampil sebagai bilah hitam di dasar halaman, di bawah sidebar. Inilah contoh nyata penggunaan `clear` untuk mengatasi float (clearfix).

#### 11 Menambahkan elemen pada main content (3 kolom box)

Di dalam `#main` ditambahkan `div.row` berisi tiga `div.box`. Setiap box memuat gambar placeholder berbentuk lingkaran, heading, deskripsi, dan tombol "View detail". Tiap box memakai `float: left` dengan lebar `33.333333%` sehingga terbentuk tiga kolom sama lebar. `box-sizing: border-box` membuat padding tidak menambah lebar box. `.row` diberi margin `0 -10px` untuk mengimbangi padding box di tepi, dan pseudo-element `:after` dengan `clear: both` dipakai sebagai **clearfix** agar tinggi `.row` tidak runtuh.

> **[Tempel screenshot di sini]**
>![gambar11.png](screenshots/gambar11.png)
> *Gambar 13. Tampilan content (tiga kolom box)*

**Analisis:** tiga kolom tampil sejajar dengan gambar lingkaran (`border-radius: 50%`). Pada modul, selector `box img` ditulis tanpa titik; pada laporan ini ditulis `.box img` agar cocok dengan class `box`.

#### 12 Hasil akhir halaman Home

Pada modul, class `btn`, `btn-large`, dan `btn-default` dipakai di HTML tetapi CSS-nya tidak disertakan, padahal gambar hasil akhir menampilkan tombol berwarna. Karena itu ditambahkan CSS tombol berikut agar tampilan sesuai Gambar 4.7 pada modul.

> **[Tempel screenshot di sini]**
>![gambar12.png](screenshots/gambar12.png)
> *Gambar 15. Hasil akhir halaman Home*

**Analisis:** seluruh bagian layout (header, navigasi, hero, konten tiga kolom, artikel, sidebar, dan footer) tersusun sesuai desain pada modul.

### Bagian C - Pertanyaan dan Tugas

#### 13 Tugas 1: Layout menu About

Halaman `about.html` dibuat dengan kerangka yang sama dengan `home.html` (header, navigasi, hero, wrapper, footer), dengan link **About** sebagai menu aktif. Konten utama berisi **deskripsi** diri (artikel dengan foto di kiri) dan **portfolio** (tiga box proyek memakai ulang class `.row` dan `.box`). Sidebar berisi widget **Data Diri** dan **Keahlian**. Kode CSS tambahan untuk halaman ini disimpan di akhir `style.css`.

> **[Tempel screenshot di sini]**
>![gambar13.png](screenshots/gambar13.png)
> *Gambar 16. Halaman About*

**Analisis:** dengan memakai ulang class yang sudah ada, halaman baru dapat dibuat cepat tanpa mengubah struktur layout. Data diri pada sidebar dapat diganti dengan data sebenarnya.

#### 14 Tugas 2: Layout menu Contact (Kontak)

Halaman `kontak.html` berisi **form isian** dengan kolom: nama lengkap, email, nomor telepon, subjek (dropdown), dan pesan (textarea), ditambah tombol *Kirim Pesan* dan *Reset*. Setiap input memiliki `<label for="...">` yang terhubung dengan `id`-nya agar aksesibel, dan atribut `required` serta `type="email"` memberi validasi bawaan browser. Sidebar berisi informasi kontak.

> **[Tempel screenshot di sini]**
>![gambar14.png](screenshots/gambar14.png)
> *Gambar 17. Halaman Kontak*

**Analisis:** input dibuat `width: 100%` dengan `box-sizing: border-box` agar tidak melebihi kolom `#main`. Form belum terhubung ke server (`action="#"`) karena praktikum ini berfokus pada layout.

## Kendala dan Catatan

- Float membuat tinggi elemen induk runtuh sehingga footer menimpa konten. Solusinya `clear: both` pada footer dan clearfix `:after` pada `.row` dan `.entry`.
- Lebar `#main` + `#sidebar` (termasuk padding) harus tepat 980px sesuai lebar container; jika lebih, sidebar turun ke bawah.
- Modul memakai class `btn` tanpa CSS-nya dan menulis selector `box img` tanpa titik. Keduanya diperbaiki pada laporan ini.
- Link menu **Artikel** (`artikel.html`) belum ada karena bukan bagian dari tugas.
- Google Fonts dan gambar `dummyimage.com` memerlukan koneksi internet; jika offline, font akan memakai `sans-serif` bawaan dan gambar tidak tampil.

## Kesimpulan

Dari praktikum ini dapat disimpulkan bahwa: (1) setiap elemen HTML merupakan *box* yang terdiri dari content, padding, border, dan margin; (2) properti `float` memudahkan penyusunan elemen secara horizontal, seperti kolom konten dan sidebar, tetapi menyebabkan tinggi elemen induk runtuh sehingga perlu ditangani dengan `clear` atau teknik clearfix; (3) elemen semantik HTML5 (`header`, `nav`, `section`, `article`, `aside`, `footer`) membuat struktur halaman lebih bermakna dan mudah dibaca; dan (4) kombinasi box model, float, dan elemen semantik dapat dipakai untuk membangun layout web sederhana yang lengkap, termasuk halaman About dan Kontak sebagai tugas praktikum.

