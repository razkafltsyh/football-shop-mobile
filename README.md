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

---
---

# TUGAS 8

### **1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?**

- Navigator.push()
Mendorong halaman baru di atas halaman saat ini dalam navigation stack. Halaman sebelumnya tetap ada di dalam stack. Pengguna dapat menggunakan tombol "Back" untuk kembali ke halaman tersebut.

Di project ini digunakan saat menekan kartu "Add Product". Ini memungkinkan navigasi dari Halaman Utama ke Halaman Form, dan pengguna dapat kembali ke Halaman Utama.

- Navigator.pushReplacement()
Mengganti halaman saat ini dengan halaman baru. Halaman yang sedang aktif akan dihapus dari navigation stack. Pengguna tidak bisa menekan "Back" untuk kembali ke halaman yang diganti tersebut.

Di project ini digunakan pada LeftDrawer, jika pengguna berada di Halaman Form dan memilih "Halaman Utama" dari drawer, halaman form akan diganti, pengguna tidak dapat kembali ke form dengan tombol "Back".

---

### **2. Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?**

Scaffold: Berfungsi sebagai dasar untuk setiap halaman. Scaffold menyediakan slot standar untuk appBar (area atas), body (konten utama), dan drawer (menu samping).

AppBar: Menempatkan AppBar yang sama di setiap Scaffold, header aplikasi akan selalu konsisten, memberikan visual yang seragam.

Drawer: Sebuah widget LeftDrawer dibuat satu kali dan digunakan kembali di beberapa Scaffold. Ini memastikan bahwa menu navigasi utama aplikasi selalu identik dan dapat diakses dari halaman halaman utama.

---

### **3. Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.**

- Padding
Kelebihan: Memberikan ruang visual antar elemen.
Contoh: Pada shop_form.dart, setiap TextFormField dibungkus Padding. Ini mencegah input field menempel di tepi layar atau menempel satu sama lain, sehingga antarmuka terlihat lebih rapi dan mudah dibaca.

- SingleChildScrollView
Kelebihan: Memungkinkan konten di dalamnya untuk di scroll.
Contoh: Di shop_form.dart, kolom yang berisi semua input field dibungkus dengan SingleChildScrollView. Ketika keyboard virtual muncul di layar kecil, form tidak akan terpotong atau mengalami overflow error. Pengguna dapat scroll untuk mengakses field yang tertutup keyboard.

- ListView
Kelebihan: Efisien untuk menampilkan daftar elemen yang bisa di scroll.
Contoh: Di left_drawer.dart, opsi-opsi menu ditempatkan di dalam ListView. Ini memastikan drawer tetap dapat di scroll jika nanti jumlah menunya bertambah banyak.

---

### **4. Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?**

Identitas visual aplikasi diatur di dalam file main.dart, tepatnya pada properti theme di widget MaterialApp

Dengan mendefinisikan primarySwatch: Colors.blue, secara otomatis akan:
1. Menggunakan palet warna biru sebagai warna dasar brand.
2. Menerapkan warna biru ke AppBar di semua halaman.
3. Menggunakan warna biru sebagai latar belakang widget utama seperti ElevatedButton.
4. Memberikan warna aksen (berbasis biru) pada elemen interaktif seperti form input saat aktif.

---
---
