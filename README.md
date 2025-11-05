# TUGAS 7

### **1. Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.**

Struktur hierarkis (pohon) yang digunakan Flutter untuk membangun UI dan memastikan fungsionalitas aplikasi, setiap elemen UI di Flutter seperti tata letak, teks dan tombol, adalah sebuah widget.

Hubungan Parent-Child: 
- Setiap widget memiliki satu parent, kecuali widget root dari aplikasi.
- Beberapa widget dapat memiliki satu atau lebih children.
- Widget parent bertanggung jawab untuk menentukan posisi dan ukuran widget child-nya.

---

### **2. Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.**

1. MaterialApp: Menyediakan struktur Material Design, tema, dan konfigurasi global aplikasi.
2. Scaffold: Sebagai struktur Halaman. Menyediakan tata letak dasar, termasuk tempat untuk AppBar dan body.
3. AppBar: Menampilkan judul di bagian atas (Header).
4. Column: Menyusun elemen utama halaman dari atas ke bawah.
5. Row: Menyusun InfoCard secara berdampingan.
6. GridView.count: Menampilkan daftar ItemCard dalam bentuk kotak kotak (grid 3 kolom).
7. Text & Icon: Menampilkan teks (judul, data) dan simbol gambar.
8. Card & Material: Memberikan tampilan seperti kartu dengan elevasi dan rounded corner.
9. InkWell: Membuat ItemCard dapat diklik dan menampilkan efek.
10. StatelessWidget: Mendefinisikan semua komponen UI yang tidak berubah (MyApp, MyHomePage, ItemCard, dll.).

---

### **3. Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.**

Mengimplementasikan Material Design secara global, menyediakan tema, dan mengelola navigasi. Digunakan sebagai root karena menyediakan Material Design agar widget lain dapat berfungsi dan terlihat dengan benar.

---

### **4. Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?**

StatelessWidget: Tidak memiliki state yang berubah, data-nya bersifat immutable setelah dibuat. Pilih ini kalau tampilan widget tidak akan berubah berdasarkan data di dalamnya atau interaksi pengguna.

StatefulWidget: Memiliki state yang dapat berubah, data-nya dapat berubah seiring waktu, biasanya karena interaksi pengguna. Pilih ini kalau tampilan widget perlu diperbarui secara dinamis sebagai respons terhadap perubahan data atau event.

---

### **5. Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?**

Merupakan lokasi atau "handle" unik dari sebuah widget di dalam Widget Tree. BuildContext Memungkinkan widget mengakses data, tema, atau layanan dari widget leluhur (ancestor) di atasnya. Penggunannya dengan cara diteruskan sebagai argumen ke metode build(), untuk menentukan dari lokasi mana pencarian data dimulai.

---

### **6. Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".**
Hot Reload adalah menyuntikkan kode baru ke aplikasi yang berjalan, memungkinkan untuk melihat perubahan UI secara instan tanpa me-reset state aplikasi. 

Hot Restart menghentikan dan memulai kembali seluruh aplikasi dari awal, sehingga semua state direset. Hot Reload digunakan untuk perubahan kecil pada UI, dan Hot Restart untuk perubahan kode yang lebih besar yang memengaruhi struktur atau state global.
