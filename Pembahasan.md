
# LAPORAN FINAL PROJECT
## Aplikasi To-Do List Berbasis CLI Menggunakan Bahasa C++

---

## 1. Pendahuluan
Aplikasi To-Do List ini merupakan program berbasis **Command Line Interface (CLI)** yang dibuat menggunakan bahasa pemrograman **C++**. Program ini dirancang untuk membantu pengguna dalam mengelola daftar tugas sehari-hari dengan fitur **login dan register** sebagai sistem autentikasi.

Tujuan pembuatan program ini adalah untuk menerapkan konsep dasar pemrograman C++ seperti array, fungsi, percabangan, perulangan, validasi input, serta manipulasi string.

---

## 2. Landasan Teori Singkat
Beberapa konsep dasar C++ yang digunakan dalam program ini antara lain:
- Array statis
- Fungsi
- Percabangan (`if-else`)
- Perulangan (`for`, `do-while`)
- Input-output (`cin`, `cout`)
- Validasi input (`cin.fail()`)
- Manipulasi string (`string`, `getline()`)

---

## 3. Deskripsi Program
Program ini memungkinkan user untuk:
1. Mendaftarkan akun (Register)
2. Login ke sistem
3. Mengelola tugas setelah login

Setiap tugas memiliki:
- Nama tugas
- Status (Belum Selesai / Selesai)
- Kategori (Kuliah, Pekerjaan, Pribadi)
- Prioritas (Rendah, Sedang, Tinggi)

---

## 4. Struktur Data
### 4.1 Data User
Program menggunakan array statis untuk menyimpan data user:
- Username
- Password
- Jumlah user

### 4.2 Data Tugas
Program menyimpan data tugas menggunakan beberapa array terpisah:
- Nama tugas
- Status tugas
- Kategori tugas
- Prioritas tugas
- Jumlah tugas

---

## 5. Penjelasan Menu Program
### 5.1 Menu Login
Menu login terdiri dari:
- Register
- Login
- Keluar

### 5.2 Menu To-Do List
Menu ini muncul setelah login berhasil dan berisi:
- Tambah tugas
- Lihat semua tugas
- Tandai tugas selesai
- Hapus tugas
- Lihat tugas selesai/belum selesai
- Edit tugas
- Logout

---

## 6. Pembahasan Flowchart

### 6.1 Flowchart Program Utama
Alur program utama:
Start → Menu Login → Register/Login →
Jika login berhasil → Menu To-Do → Logout → End

### 6.2 Flowchart Register
Start → Cek kapasitas user → Input username & password → Simpan data → End

### 6.3 Flowchart Login
Start → Input username & password → Validasi data →
Login berhasil / Login gagal → End

### 6.4 Flowchart Tambah Tugas
Start → Cek kapasitas tugas → Input nama → Pilih kategori → Pilih prioritas → Simpan tugas → End

### 6.5 Flowchart Hapus Tugas
Start → Pilih tugas → Konfirmasi → Hapus & geser array → End

### 6.6 Flowchart Edit Tugas
Start → Pilih tugas → Edit data (opsional) → Simpan perubahan → End

---

## 7. Pengujian Program
Program diuji dengan:
- Input valid
- Input tidak valid
- Batas maksimal user dan tugas

Hasil pengujian menunjukkan program berjalan sesuai dengan yang diharapkan.

---

## 8. Kesimpulan
Program To-Do List berbasis CLI ini telah berhasil diimplementasikan menggunakan bahasa C++. Program mampu menjalankan fungsi login, register, dan manajemen tugas dengan baik serta menerapkan konsep dasar pemrograman secara tepat.

---

## 9. Saran Pengembangan
Beberapa saran pengembangan ke depan:
- Menggunakan `struct` atau `class`
- Menggunakan `vector`
- Menyimpan data ke file
- Membuat tampilan berbasis GUI

---