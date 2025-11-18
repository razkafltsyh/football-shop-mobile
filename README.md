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

# TUGAS 9

### **1. Jelaskan mengapa kita perlu membuat model Dart saat mengambil/mengirim data JSON? Apa konsekuensinya jika langsung memetakan Map<String, dynamic> tanpa model (terkait validasi tipe, null-safety, maintainability)?**

Membuat model Dart diperlukan untuk menjamin keamanan tipe data dan struktur data yang konsisten. Dengan model, kita dapat memanfaatkan fitur autocomplete di IDE dan meminimalisir kesalahan penulisan key string.

Konsekuensi tanpa model:
- Validasi Tipe Lemah: Kompiler tidak bisa mendeteksi jika kita memasukkan String ke variabel yang seharusnya int.
- Rawan Error: Typo pada string key (misal: "price" ditulis "prie") baru akan ketahuan saat runtime, bukan saat kompilasi.
- Maintainability Buruk: Sulit melacak struktur data jika field bertambah banyak, karena tidak ada definisi kelas yang jelas.

---

### **2. Apa fungsi package http dan CookieRequest dalam tugas ini? Jelaskan perbedaan peran http vs CookieRequest.**

- package http: Pustaka dasar untuk melakukan permintaan HTTP (GET, POST, dll.) ke server. Sifatnya stateless (tidak menyimpan data sesi antar request).

- CookieRequest: Wrapper dari package pbp_django_auth yang dirancang khusus untuk menangani autentikasi Django. Ia menyimpan cookies (session ID dan CSRF token) secara otomatis setiap kali login berhasil.

- Perbedaan: http digunakan untuk request API umum yang tidak butuh persistensi sesi, sedangkan CookieRequest digunakan ketika berinteraksi dengan Django yang membutuhkan autentikasi user agar status login tetap terjaga antar halaman.

---

### **3.  Jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**

Agar status login (session cookies) konsisten di seluruh aplikasi. Jika kita membuat instance CookieRequest baru di setiap halaman, cookies dari proses login sebelumnya akan hilang, sehingga server akan menganggap pengguna belum login (logout otomatis) saat berpindah halaman.

---

### **4. Jelaskan konfigurasi konektivitas yang diperlukan agar Flutter dapat berkomunikasi dengan Django. Mengapa kita perlu menambahkan 10.0.2.2 pada ALLOWED_HOSTS, mengaktifkan CORS dan pengaturan SameSite/cookie, dan menambahkan izin akses internet di Android? Apa yang akan terjadi jika konfigurasi tersebut tidak dilakukan dengan benar?**

- 10.0.2.2: Alamat khusus pada emulator Android untuk mengakses localhost komputer host.

- ALLOWED_HOSTS: Agar Django mengizinkan request yang masuk melalui host header 10.0.2.2.

- CORS: Mengizinkan browser/klien dari origin berbeda untuk mengakses resource server.

- Izin Internet: Memberikan akses pada aplikasi Android untuk menggunakan radio jaringan.

Jika konfigurasi salah, aplikasi akan mengalami error seperti Connection Refused, 400 Bad Request, atau 403 Forbidden karena server menolak koneksi dari emulator.

---

### **5. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.**

1. Input: Pengguna mengisi form di Flutter, data ditangkap oleh TextEditingController.
2. Serialisasi: Data dikonversi menjadi format JSON.
3. Pengiriman: CookieRequest mengirim JSON via method POST ke endpoint Django.
4. Backend: Django menerima, memvalidasi, dan menyimpan data ke database.
5. Pengambilan (Fetch): Flutter melakukan request GET ke endpoint JSON Django.
6. Deserialisasi: JSON response diubah kembali menjadi objek Model Dart (fromJson).
7. Tampilan: Widget (seperti FutureBuilder dan ListView) merender data objek tersebut ke layar.

---

### **6. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**

- Register: Flutter mengirim data akun baru -> Django membuat User baru di database -> Return sukses.

- Login: Flutter mengirim username & password -> Django memverifikasi (authenticate) -> Jika valid, Django membuat session dan mengirimkan session cookie -> Flutter menyimpan cookie tersebut di instance CookieRequest -> Navigasi ke Menu Utama.

- Logout: Flutter mengirim request logout -> Django menghapus session di server -> Cookie di Flutter menjadi tidak valid -> Pengguna diarahkan kembali ke halaman Login.

---

### **7. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**

1. Setup Django: Menginstal django-cors-headers, menambahkan corsheaders ke INSTALLED_APPS, dan menambahkan 10.0.2.2 ke ALLOWED_HOSTS. Membuat view untuk login, register, dan logout di Django.

2. Setup Flutter Auth: Menginstal pbp_django_auth dan provider. Membungkus MaterialApp dengan Provider yang menyediakan CookieRequest.

3. Halaman Auth: Membuat LoginPage dan RegisterPage di Flutter yang menggunakan CookieRequest.login() dan postJson() untuk berkomunikasi dengan endpoint Django.

4. Model Custom: Mengambil contoh JSON dari endpoint produk Django, lalu menggunakan Quicktype untuk men-generate file product_entry.dart.

5. Daftar Item: Membuat halaman ProductEntryPage yang melakukan fetch data GET dari Django, lalu menampilkannya menggunakan FutureBuilder dan ListView.builder.

6. Detail Item: Membuat halaman ProductDetailPage. Menambahkan navigasi Navigator.push pada setiap item di list, dengan mengirimkan objek product sebagai parameter.

7. Integrasi & Filter: Memastikan endpoint Django memfilter produk berdasarkan request.user (Product.objects.filter(user=request.user)), sehingga data yang tampil di Flutter otomatis terfilter sesuai akun yang login.
