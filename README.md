# razzle_fresh_mobile

A new Flutter project

## Getting Started
<details>
<summary>More</summary>
This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
</details>
</br>

# TUGAS 9

## Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?
Ya, kita bisa melakukan pengambilan data JSON tanpa membuat model terlebih dahulu dengan menggunakan suatu variabel yang nantinya akan digunakan untuk menyimpan dictionary berisi data tersebut. Melakukan pengambilan data dengan metode ini tidak lebih baik daripada menggunakan model. Menggunakan model lebih baik karena dapat mempermudah dalam mengambil data.

## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
CookieRequest adalah suatu class dari library pbp_django_auth.dart. CookieRequest berfungsi agar aplikasi dapat melacak status login, memberi informasi sesi login pengguna, serta request HTTP dengan metode GET dan POST. CookieRequest perlu dibagikan ke semu komponen di aplikasi Flutter agar status login serta informasi sesi login user terjaga.

## Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.
Terlebih dahulu menjalankan web app django untuk mengambil data JSON. Setelah mengambil data JSON dari proyek Django, gunakan website Quicktype untuk mentranslasikan JSON ke bahasa Dart. Lalu masukkan kode tersebut ke dalam file product.dart di dalam direktori models. Lalu tambahkan dependensi http `<uses-permission android:name="android.permission.INTERNET" />` pada android/app/src/main/AndroidManifest.xml agar aplikasi tersebut dapat mengakses internet.

## Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
User diminta memasukkan data login yaitu username dan password pada halaman login. Setelah tombol login ditekan, CookieRequest akan terpanggil dan mengirimkan HTTP request.

## Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.
1. TextField : digunakan untuk memasukkan input teks
2. FutureBuilder : mengelola status serta data secara asinkronus
3. Column : mengatur elemen yang berdampingan secara vertikal
4. ListView : menampilkan daftar widget.

# TUGAS 8

## Perbedaan antara Navigator.push() dan Navigator.pushReplacement()
Method `push()` pada `Navigator.push()` akan menambahkan suatu route ke dalam stack route yang dikelola oleh Navigator. route ini akan diletakkan di bagian paling atas stack route, sehingga dengan melakukan method `pop()` maka user dapat kembali ke route sebelumnya.</br>
Method `pushReplacement()` pada `Navigator.pushReplacement()` akan menghapus route yang sedang ditampilkan dan menggantinya dengan suatu route. Pada stack route, route paling atas akan diganti dengan suatu route.

## Layout Widget pada Flutter
1. Container </br>
Container adalah class widget yang memperbolehkan mengkustomisasi widget childnya. Properti dari container antara lain seperti padding, margin, borders, color.
2. Column </br>
Digunakan untuk mengatur elemen yang berdampingan secara vertikal.
3. Row </br>
Digunakan untuk mengatur elemen yang berdampingan secara horizontal.
4. ListView </br>
Untuk menampilkan daftar widget.
5. GridView </br>
Untuk menampilkan daftar widget dalam susunan grid.

## Elemen input pada form
1. name: digunakan untuk menyimpan nama stok barang. Tipe elemen berupa String.
2. amount: digunakan untuk menyimpan jumlah stok barang. Tipe elemen berupa integer.
3. description: digunakan untuk menyimpan penjelasan tentang stok barang. Tipe elemen berupa String.

## Penerapan clean architecture pada Flutter
Clean Architecture adalah suatu sistem desain yang mengikuti prinsip separation of concern. Arsitektur ini memusatkan pada membagi software ke dalam beberapa layer untuk mempermudah maintenance dan development dari sistem. </br>
Pada Flutter, Separation of Concerns dilakukan dengan membagi menjadi 3 layer arsitektur yaitu:
1. Presentation Layer: menyimpan kode yang terkait dengan user interface, termasuk widget dan screen.
2. Domain layer: menyimpan logika dan entitas atau variabel. 
3. Data layer: handle akses data

## Implementasi Checklist Tugas 8
1. Membuat halaman formulir tambah item baru dengan membuat file baru bernama `shoplist_form`. Terdapat 3 elemen input yaitu `name`, `amount`, dan `description`. Halaman formulir memiliki tombol save untuk menyimpan input data. Tombol save dibuat dengan wdiget `ElevatedButton`. Setiap input memiliki validasi.
2. Mengarahkan user ke halaman form tambah item ketika menekan tombol Tambah Item dengan fungsi `Navigator.push()` seperti berikut
```dart
if (item.name == "Tambah Item") {
            Navigator.push(context,
                MaterialPageRoute(builder: (context) => const ShopFormPage()));
          }
```
3. Membuat drawer dengan opsi Halaman Utama dan Tambah Item. Menggunakan `Navigator.pushReplacement()` untuk mengarahkan ke halaman lain.
```dart
return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(
              color: Colors.indigo,
            ),
            child: Column(
              children: [
                Text(
                  'Razzle Fresh Mobile',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 20,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(10)),
                Text("Catat seluruh keperluan belanjamu di sini!",
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 15,
                      fontWeight: FontWeight.normal,
                      color: Colors.white,
                    )),
              ],
            ),
          ),
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Halaman Utama'),
            // Bagian redirection ke MyHomePage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_shopping_cart),
            title: const Text('Tambah Produk'),
            // Bagian redirection ke MyHomePage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => ShopFormPage(),
                  ));
            },
          ),
        ],
      ),
    );
```

# TUGAS 7

## Perbedaan Utama _Stateless_ dan _Stateful Widget_ di Flutter
_Stateless widget_ adalah widget yang tidak akan berubah atau immutable. _Stateless widget_ tidak akan mengalami perubahan selama runtime app. </br>
_Stateful widget_ adalah widget yang dinamis. Widget ini dapat berubah selama runtime app.

## Widget yang digunakan dalam tugas ini
Widget yang digunakan dalam tugas ini adalah _Stateless Widget_ yang digunakan untuk menampilkan widget-widget seperti button lihat item, tambah item, dan logout, dan icon-icon.

## Implementasi Checklist Tugas 7
1. Membuat sebuah program flutter dengan tema toko buah dan sayur bernama Razzle Fresh Mobile dengan cara memasukkan command `flutter create razzle_fresh_mobile`.</br>
Lalu membuat file baru di direktori lib dengan nama `menu.dart` dan memasukkan potongan code berisi class `MyHomePage` dan `_MyHomePageState` dari file `main.dart`.
2. Membuat tiga tombol sederhana dilakukan dengan menambahkan class baru yang akan mendefine text serta cardnya di dalam file `menu.dart` yang sebelumnya telah dibuat terlebih dahulu </br>
```dart
class ShopItem {
  final String name;
  final IconData icon;
  final Color color

  ShopItem(this.name, this.icon, this.color);
}
```
Masukkan potongan code berikut dibawah kode `MyHomePage({Key? key}) : super(key: key);`
```dart
final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.lightBlue),
    ShopItem("Tambah Item", Icons.add_shopping_cart,
        Color.fromARGB(255, 237, 158, 158)),
    ShopItem("Logout", Icons.logout, Color.fromARGB(255, 156, 240, 191)),
  ];
```
3. Memunculkan Snackbar dengan cara memasukkan potongan code berikut di dalam class `ShopCard` di dalam method `Widget`
```dart
 return Material(
      color: Colors.indigo,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
```