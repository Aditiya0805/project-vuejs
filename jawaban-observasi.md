# Jawaban Observasi dan Refleksi Praktikum Pertemuan 3
**Mata Kuliah:** Pemrograman Web 2 (INF231102)  
**Materi:** Single File Component (SFC) & Struktur Project Vue  
**Nama Mahasiswa:** Aditiya Pratama  
**NIM:** 221051122  
**Program Studi:** Informatika  

---

## Soal 2 — Membuktikan `scoped` Style

### Hasil Eksperimen:
1. Pada `KartuProfil.vue`, style diubah dari `border: 2px solid #41B883` menjadi `border: 3px solid #FF0000`.
2. Pada browser, komponen `KotakInfo.vue` **TIDAK IKUT BERUBAH** dan tetap mempertahankan warna border aslinya (`#35495e`).

### Penjelasan:
Kartu `KotakInfo` tidak ikut berubah karena kedua komponen tersebut menggunakan atribut `<style scoped>`. Vue compiler secara otomatis menambahkan atribut data unik (seperti `data-v-xxxxxxx`) ke elemen HTML masing-masing komponen dan menyematkan atribut tersebut ke selector CSS yang dihasilkan (misalnya `.kartu[data-v-xxxxxxx]`). Oleh karena itu, meskipun kedua komponen menggunakan nama class yang sama (`.kartu`), aturan CSS terisolasi di dalam lingkup komponennya sendiri (CSS encapsulation/scoping) dan tidak akan terjadi bentrok style (*style leak/collision*).

---

## Soal 5c — Static Assets: `public/` vs `src/assets/`

### 1. Apa bedanya cara pakai gambar di `public/` dengan gambar di `src/assets/`?
- **Folder `public/`**: Gambar diakses menggunakan absolute URL path langsung dari root web server, contoh: `<img src="/logo.png">` (tanpa tanda titik dua `:` pada atribut `src`). File di `public/` tidak diproses melalui bundler/pipeline Vite dan disalin secara langsung apa adanya ke folder output `dist/`.
- **Folder `src/assets/`**: Gambar harus di-import di blok `<script setup>` terlebih dahulu (misal: `import logo from '@/assets/logo.png'`) lalu dipasang ke template menggunakan *attribute binding* `v-bind:src` atau shorthand `:src="logo"`. File ini diproses, dioptimasi, dan diberi *asset hashing* oleh Vite saat build.

### 2. Kenapa gambar di `src/assets/` harus di-`import`, sedangkan di `public/` cukup tulis path-nya saja?
- File di `src/assets/` merupakan bagian dari modul sistem aplikasi yang dikelola oleh Vite (bundler). Dengan melakukan `import`, Vite dapat melacak ketergantungan modul, melakukan kompresi/optimasi aset, menyertakan hash unik pada nama file untuk manajemen *browser cache-busting*, serta mendeteksi error jika file tidak ditemukan saat kompilasi.
- Sebaliknya, folder `public/` bertindak sebagai *static root server*, sehingga file di dalamnya diperlakukan sebagai URL statis murni yang langsung disediakan web server tanpa melalui pemrosesan modul JavaScript.

### 3. Kalau folder `src/assets/` tidak ada, apakah error muncul saat `import`? Jelaskan.
Ya, error akan muncul saat proses kompilasi/build maupun saat runtime di dev server Vite (`Failed to resolve import "@/assets/logo.png"`). Hal ini terjadi karena mekanisme `import` pada modul ECMAScript/Vite akan memvalidasi keberadaan target file pada sistem berkas secara statis. Jika path tidak ditemukan, bundler akan menghentikan proses kompilasi dan menampilkan pesan error resolusi modul.

---

## Soal 6 — Vue DevTools & Hot Module Replacement (HMR)

### 1. Apa yang terjadi di browser ketika kita menyimpan file `.vue`? (Jelaskan mekanismenya, sebut namanya.)
Proses ini dinamakan **Hot Module Replacement (HMR)**. Ketika file `.vue` disimpan di IDE, Vite mendeteksi perubahan file melalui *file watcher*, mengompilasi ulang hanya modul/komponen SFC yang berubah, dan mengirimkan notifikasi update ke browser melalui koneksi WebSocket. Browser kemudian menukar (*replace*) kode komponen tersebut di dalam DOM secara instan tanpa perlu memuat ulang (*full page reload*) seluruh halaman.

### 2. Kenapa HMR membuat halaman tidak perlu di-refresh manual?
Karena HMR hanya memperbarui dan mengganti modul/komponen yang mengalami perubahan secara dinamis (*in-memory module replacement*) ke dalam pohon aplikasi yang sedang berjalan. Dengan demikian, status aplikasi (*component state*, input form, scroll position) tetap terjaga tanpa harus menghancurkan (*destroy*) dan membuat ulang seluruh instance DOM halaman.

### 3. Dari komponen yang sudah dibuat, mana yang paling mudah di-debug lewat DevTools? Kenapa?
Komponen `KartuProfil` (dengan props) dan `IdentitasKampus` adalah yang paling mudah di-debug karena memiliki data yang jelas (baik melalui `props` maupun data yang di-import). Di Vue DevTools, kita dapat langsung melihat struktur hirarki komponen, menginspeksi nilai `props` atau `data` yang diterima, dan memverifikasi reaktivitas data secara visual secara realtime.

---

## Soal 7 — Refleksi Tertulis

### 1. Urutan file yang dimuat ketika pengguna membuka `http://localhost:5173`:
1. **`index.html`**: Browser meminta halaman utama dan menerima struktur dasar HTML yang memiliki container `<div id="app"></div>` serta tag `<script type="module" src="/src/main.js"></script>`.
2. **`src/main.js`**: Browser mengeksekusi file entry point JavaScript yang meng-import library Vue (`createApp`), instance `App.vue`, router, dan pinia.
3. **`src/App.vue`**: Instance root component dimuat dan di-render ke dalam `#app`.
4. **Child Components (`DaftarMahasiswa.vue`, `IdentitasKampus.vue`, `LogoKampus.vue`, `LogoKampusBesar.vue`)**: Komponen-komponen anak di-import dan di-render secara bertingkat.
5. **Grandchild Components (`KartuProfil.vue`, `KartuBiodata.vue`, `KotakInfo.vue`)**: Di-render di dalam `DaftarMahasiswa.vue`, sehingga seluruh elemen data mahasiswa dan kartu tampil sempurna di layar browser pengguna.

### 2. Efek baris `'@'` pada `vite.config.js`:
Konfigurasi alias `@` memetakan simbol `@` secara langsung ke path absolut folder `./src`. Efeknya:
- Kita tidak perlu menulis *relative path* bertingkat yang panjang dan rawan salah seperti `../../components/KartuProfil.vue`.
- Penulisan import menjadi konsisten dan bersih di semua level folder, misalnya: `@/components/KartuProfil.vue` atau `@/data/kampus.js`.
- Jika struktur folder diubah atau dipindahkan, import yang menggunakan alias tetap valid selama path relatif terhadap `src` tidak berubah.

### 3. Kenapa folder `node_modules/` tidak ikut di-commit ke Git? Apa dampaknya jika ikut?
- Folder `node_modules/` berukuran sangat besar (bisa ratusan megabyte hingga gigabyte) dan memuat puluhan ribu file kecil yang memperberat dan memperlambat operasi Git (*clone, push, pull*).
- Setiap developer dapat meregenerasi `node_modules/` secara identik hanya dengan menjalankan `npm install` berkat file `package.json` dan `package-lock.json`.
- Jika ikut di-commit, repositori Git akan menjadi membengkak, riwayat commit kotor, dan berpotensi menimbulkan konflik dependensi lintas sistem operasi (OS-specific binary builds).

### 4. Pengertian Single File Component (SFC) dan 3 bagian di dalamnya:
**Single File Component (SFC)** adalah file berekstensi `.vue` yang membungkus struktur, logika, dan gaya dari sebuah komponen UI dalam satu file tunggal. 3 bagian blok di dalamnya adalah:
1. **`<template>`**: Berisi struktur markup HTML dan sintaks interpolasi/direktif Vue untuk mendefinisikan tampilan antarmuka (UI).
2. **`<script setup>` / `<script>`**: Berisi logika JavaScript/TypeScript, deklarasi data reaktif, import modul/komponen lain, props, dan fungsi handler.
3. **`<style scoped>` / `<style>`**: Berisi kode CSS untuk mempercantik komponen. Atribut `scoped` memastikan aturan gaya hanya berlaku untuk elemen di dalam komponen tersebut.

### 5. Perbedaan penempatan file di `components/` vs `views/`:
- **`src/components/`**: Digunakan untuk komponen-komponen UI yang bersifat modular, kecil, dan dapat digunakan kembali (*reusable/shared components*), seperti tombol, kartu biodata, modal, header, atau kartu profil.
- **`src/views/` (atau `pages/`)**: Digunakan untuk komponen tingkat halaman (*page/view level components*) yang langsung terhubung ke rute tertentu pada **Vue Router** (contoh: `HomeView.vue`, `AboutView.vue`, `DashboardView.vue`). Komponen di `views` biasanya bertindak sebagai wadah yang merangkai beberapa komponen dari `components/`.
