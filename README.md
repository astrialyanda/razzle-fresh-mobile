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

## Perbedaan Utama _Stateless_ dan _Stateful Widget_ di Flutter
_Stateless widget_ adalah widget yang tidak akan berubah atau immutable. _Stateless widget_ tidak akan mengalami perubahan selama runtime app. </br>
_Stateful widget_ adalah widget yang dinamis. Widget ini dapat berubah selama runtime app.

## Widget yang digunakan dalam tugas ini
Widget yang digunakan dalam tugas ini adalah _Stateless Widget_ yang digunakan untuk menampilkan widget-widget seperti button lihat item, tambah item, dan logout, dan icon-icon.

## Implementasi Checklist Tugas 7
1. Membuat sebuah program flutter dengan tema toko buah dan sayur bernama Razzle Fresh Mobile dengan cara memasukkan command `flutter create razzle_fresh_mobile`.</br>
Lalu membuat file baru di direktori lib dengan nama `menu.dart` dan memasukkan potongan code berisi class `MyHomePage` dan `_MyHomePageState` dari file `main.dart`.
2. Membuat tiga tombol sederhana dilakukan dengan menambahkan class baru yang akan mendefine text serta cardnya di dalam file `menu.dart` yang sebelumnya telah dibuat terlebih dahulu </br>
```
class ShopItem {
  final String name;
  final IconData icon;
  final Color color

  ShopItem(this.name, this.icon, this.color);
}
```
Masukkan potongan code berikut dibawah kode `MyHomePage({Key? key}) : super(key: key);`
```
final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.lightBlue),
    ShopItem("Tambah Item", Icons.add_shopping_cart,
        Color.fromARGB(255, 237, 158, 158)),
    ShopItem("Logout", Icons.logout, Color.fromARGB(255, 156, 240, 191)),
  ];
```
3. Memunculkan Snackbar dengan cara memasukkan potongan code berikut di dalam class `ShopCard` di dalam method `Widget`
```
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