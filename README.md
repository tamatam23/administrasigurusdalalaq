# 🎓 Sistem Informasi Administrasi Guru & Sekolah

Aplikasi web responsif berbasis **Google Apps Script (GAS)** dan **Google Sheets** sebagai database. Dibangun dengan arsitektur *Single Page Application* (SPA) untuk mengelola administrasi guru, siswa, absensi, jurnal mengajar, dan arsip dokumen sekolah secara digital dan terpusat.

Diadaptasi khusus untuk kebutuhan administrasi (Studi Kasus: SD Islam Al Alaq), namun dapat dengan mudah dimodifikasi untuk sekolah atau instansi pendidikan lainnya.

---

## 🌟 Fitur Utama

Sistem ini memiliki dua hak akses utama: **Kepala Sekolah (Administrator)** dan **Guru Pengajar**.

### 👨‍🏫 Fitur Guru
* **Dashboard Interaktif:** Menampilkan statistik siswa, grafik kehadiran, kelas yang diampu, agenda terdekat, dan notifikasi *broadcast* secara *real-time*.
* **Manajemen Data Siswa:** Melihat data siswa khusus di kelas yang diampu (Wali Kelas/Asisten). Fitur *bulk upload* & *download* menggunakan Excel.
* **Absensi Cepat:** Fitur absensi harian dengan opsi "Hadir Semua" atau "Hadir Kecuali...". Mendukung fitur cetak (Print to PDF) rekap bulanan.
* **Jurnal Mengajar:** Pencatatan materi dan log mengajar harian.
* **Catatan Siswa:** Mencatat kejadian/perkembangan siswa. Dilengkapi fitur *Smart Autocomplete* (dropdown siswa akan terbuka dan difilter otomatis berdasarkan kelas yang dipilih).
* **Upload Modul/Berkas:** Mengunggah RPP/Modul Ajar (PDF, Word, MP4) langsung tersimpan ke Google Drive sekolah.
* **Kalender Pendidikan:** Melihat agenda dan hari libur sekolah.

### 🧑‍💼 Fitur Kepala Sekolah (Admin)
* **Super Monitoring:** Fitur *tracking* komprehensif untuk melihat riwayat jurnal, catatan, dan berkas yang diunggah oleh *guru tertentu* dalam satu layar.
* **Manajemen Data Guru:** Menambahkan, mengedit, dan mengatur pembagian tugas guru (Wali Kelas, Guru Mapel, Asisten).
* **Kepatuhan Jurnal:** Sistem pengecekan otomatis (1-klik) untuk melihat daftar guru yang sudah/belum mengisi jurnal hari ini, dengan fitur kirim peringatan massal.
* **Broadcast Pesan:** Mengirim pengumuman ke seluruh guru atau guru spesifik.
* **Bulk Download Berkas:** Mengunduh seluruh modul ajar yang diunggah guru dalam bentuk file **.ZIP**.
* **Manajemen Kalender:** Kalender interaktif (drag & drop) untuk mengatur agenda sekolah dan hari libur.

---

## 🛠️ Teknologi yang Digunakan

* **Backend:** [Google Apps Script (GAS)](https://developers.google.com/apps-script)
* **Database & Storage:** Google Sheets API & Google Drive API
* **Frontend:** Vanilla JavaScript, HTML5, CSS3
* **UI Framework:** [Bootstrap 5](https://getbootstrap.com/)
* **Icons:** Bootstrap Icons
* **Libraries:**
    * [SweetAlert2](https://sweetalert2.github.io/) (Pop-up modern & interaktif)
    * [FullCalendar.io](https://fullcalendar.io/) (Kalender interaktif)
    * [SheetJS / xlsx](https://sheetjs.com/) (Parsing file Excel di sisi klien)

---

## 📁 Struktur File (Google Apps Script)

Aplikasi ini dibagi menjadi beberapa file modular agar mudah di- *maintain*:

* `Code.gs` : Script backend utama (Logika server, CRUD Google Sheets, Auth, API integrasi).
* `Index.html` : Kerangka utama aplikasi web, *sidebar* navigasi, dan wadah SPA (`#dynamic-content`).
* `Login.html` : Tampilan antarmuka login 2-kolom dengan desain modern.
* `Style.html` : Kumpulan CSS kustom untuk memberikan styling pada UI.
* `Script.html` : Kumpulan logika *Vanilla JavaScript* (AJAX `google.script.run`, navigasi halaman, manipulasi DOM, logic Autocomplete).

---

## 🚀 Panduan Instalasi & Deployment

Karena aplikasi ini berjalan di atas ekosistem Google Workspace, Anda tidak perlu menyewa *hosting* atau *database*.

### Tahap 1: Persiapan Database
1. Buat sebuah **Google Sheets** baru.
2. Buat *sheet* (tab) dengan nama wajib berikut:
   - `Siswa` (ID, Nama Siswa, Tanggal Lahir, Gender, Kelas, Guru, Foto)
   - `Guru` (ID, Nama, Gender, Tugas, Mapel, Kelas, Foto)
   - `Absensi` (Tanggal, Nama Siswa, Status, Guru)
   - `Jurnal` (Tanggal, Kelas, Mapel, Materi, Ket, Guru)
   - `Catatan` (Tanggal, Nama Siswa, Tipe, Isi, Guru)
   - `Kalender` (Tanggal, Agenda)
   - `Broadcast` (Tanggal, Pesan, Target)
3. Salin **ID Spreadsheet** Anda (Kombinasi huruf & angka acak di URL).

### Tahap 2: Google Apps Script
1. Di dalam Spreadsheet Anda, klik menu **Ekstensi > Apps Script**.
2. Salin isi file `.gs` dan `.html` dari repositori ini ke editor Apps Script Anda. Pastikan nama file sesuai (terutama huruf besar/kecilnya).
3. Buka file `Code.gs`. Cari variabel penampung ID (misal: `var sheetId = "..."`) lalu masukkan **ID Spreadsheet** Anda.

### Tahap 3: Deployment
1. Di kanan atas editor Apps Script, klik tombol **Terapkan (Deploy) > Deployment baru**.
2. Pilih jenis **Aplikasi Web (Web App)**.
3. Setelan akses:
   - Jalankan sebagai: **Saya (Akun Anda)**
   - Siapa yang memiliki akses: **Siapa saja (Anyone)**
4. Klik **Terapkan**. Berikan izin otorisasi ke akun Google Anda saat diminta.
5. Salin URL Aplikasi Web yang diberikan. Aplikasi siap digunakan!

---

## 📸 Tampilan Layar (Screenshots)

*(Tambahkan gambar screenshot aplikasi Anda di sini)*
* `![Halaman Login](link_gambar)`
* `![Dashboard Guru](link_gambar)`
* `![Monitoring Kepsek](link_gambar)`

---

## 🔒 Lisensi
Didistribusikan di bawah Lisensi MIT. Bebas digunakan, dimodifikasi, dan dikembangkan untuk kebutuhan instansi pendidikan.
