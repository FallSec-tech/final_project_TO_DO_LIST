
# FLOWCHART APLIKASI TO-DO LIST C++ (CLI)

Dokumen ini berisi **flowchart (alur program)** dari Aplikasi To-Do List berbasis CLI menggunakan bahasa C++.
Flowchart dituliskan dalam bentuk **alur langkah (teks)** agar mudah digambar ulang secara manual atau menggunakan tools seperti **draw.io**, **Visio**, atau **Lucidchart**.

---

## 1. Flowchart Program Utama (Main Program)

**Tujuan:**  
Mengatur alur login, register, dan perpindahan ke menu To-Do List.

**Alur Flowchart:**
1. Start
2. Tampilkan judul program
3. Tampilkan menu login
4. User memilih menu
5. Jika memilih Register → proses register → kembali ke menu login
6. Jika memilih Login:
   - Validasi username & password
   - Jika gagal → kembali ke menu login
   - Jika berhasil → masuk menu To-Do
7. Jika memilih Keluar → program selesai
8. End

**Alur Singkat:**
Start → Judul → Menu Login →  
Register / Login →  
Login berhasil → Menu To-Do → Logout → Menu Login → End

---

## 2. Flowchart Register User

**Tujuan:**  
Menambahkan akun user baru.

**Alur Flowchart:**
1. Start
2. Cek jumlah user
3. Jika user sudah penuh → tampil pesan “User penuh”
4. Jika belum penuh:
   - Input username
   - Input password
   - Simpan data ke array
   - Tambah jumlah user
5. Tampilkan pesan register berhasil
6. End

**Alur Singkat:**
Start → Cek kapasitas →  
Penuh? → Ya → End  
Tidak → Input data → Simpan → End

---

## 3. Flowchart Login User

**Tujuan:**  
Memverifikasi username dan password.

**Alur Flowchart:**
1. Start
2. Input username dan password
3. Bandingkan dengan data user
4. Jika cocok → login berhasil
5. Jika tidak cocok → login gagal
6. End

**Alur Singkat:**
Start → Input data → Validasi →  
Berhasil / Gagal → End

---

## 4. Flowchart Menu To-Do List

**Tujuan:**  
Menjalankan fitur pengelolaan tugas setelah login.

**Alur Flowchart:**
1. Start
2. Tampilkan menu To-Do
3. User memilih fitur
4. Jalankan fitur sesuai pilihan
5. Kembali ke menu To-Do
6. Jika pilih Logout → keluar dari menu
7. End

**Alur Singkat:**
Start → Menu To-Do → Pilih fitur → Proses →  
Kembali ke Menu → Logout → End

---

## 5. Flowchart Tambah Tugas

**Tujuan:**  
Menambahkan tugas baru ke dalam sistem.

**Alur Flowchart:**
1. Start
2. Cek kapasitas tugas
3. Jika penuh → tampil pesan “Tugas penuh” → End
4. Input nama tugas
5. Pilih kategori tugas
6. Pilih prioritas tugas
7. Set status = “Belum Selesai”
8. Simpan tugas ke array
9. Tambah jumlah tugas
10. End

**Alur Singkat:**
Start → Cek kapasitas →  
Penuh? → Ya → End  
Tidak → Input data → Simpan → End

---

## 6. Flowchart Lihat Tugas

**Tujuan:**  
Menampilkan daftar tugas.

**Alur Flowchart:**
1. Start
2. Cek apakah ada tugas
3. Jika tidak ada → tampil pesan “Belum ada tugas”
4. Jika ada → tampilkan semua tugas
5. End

---

## 7. Flowchart Tandai Tugas Selesai

**Tujuan:**  
Mengubah status tugas menjadi selesai.

**Alur Flowchart:**
1. Start
2. Tampilkan daftar tugas
3. Input nomor tugas
4. Validasi nomor
5. Jika tidak valid → tampil pesan error → End
6. Jika valid → ubah status menjadi “Selesai”
7. End

---

## 8. Flowchart Hapus Tugas

**Tujuan:**  
Menghapus tugas dari sistem.

**Alur Flowchart:**
1. Start
2. Tampilkan daftar tugas
3. Input nomor tugas
4. Validasi nomor
5. Konfirmasi hapus (y/n)
6. Jika y:
   - Geser data array
   - Kurangi jumlah tugas
7. Jika n → penghapusan dibatalkan
8. End

---

## 9. Flowchart Edit Tugas

**Tujuan:**  
Mengubah data tugas yang sudah ada.

**Alur Flowchart:**
1. Start
2. Tampilkan daftar tugas
3. Input nomor tugas
4. Validasi nomor
5. Input nama baru (opsional)
6. Konfirmasi ubah kategori
7. Jika ya → pilih kategori baru
8. Konfirmasi ubah prioritas
9. Jika ya → pilih prioritas baru
10. Simpan perubahan
11. End

---

## 10. Penutup
Flowchart ini menggambarkan alur kerja utama dari aplikasi To-Do List C++ berbasis CLI.
Flowchart dapat digunakan sebagai:
- Dokumentasi program
- Acuan pembuatan diagram visuala
- Penjelasan logika program saat presentasi atau ujian
