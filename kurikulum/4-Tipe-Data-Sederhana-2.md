Lebih Lanjut dengan Tipe Data Sederhana
=======================================

* Tipe data sederhana
    - String
    - Boolean dan nil
    - Keyword

## Tipe Data Sederhana

Kita sudah mempelajari salah satu tipe data sederhana yaitu _number_. Sekarang kita akan lihat lebih dekat lagi tipe data sederhana lainnya yaitu _string_, _boolean_, dan _keyword_.

### String dan _character_

Apa itu _string_? _String_ hanyalah teks. Untuk membuat string, Anda hanya butuh mengapit karakter dengan tanda kutip dua `"`.

```clojure
"Hello World"
"Saya keren"
"Kata temannya, \"Clojure itu mudah\"."
```

Lihat contoh yang terakhir. Garis miring terbalik `\` digunakan jika kita hendak menulis tanda kutip sebagai teks di dalam tanda kutip penanda _string_. Jangan coba-coba membuat _string_ menggunakan tanda kutip satu `'`.

### Boolean dan nil

Boolean adalah tipe data yang nilainya hanya `true` dan `false`. Saat melakukan pemrograman kita sering bertanya kondisi dari hasil suatu fungsi, seperti "Apakah nilai yang dihasilkan lebih besar dari 10?" atau "Apakah pengguna yang aktif sekarang adalah wanita?". Saat kita melakukan pengecekan seperti itu jawabannya pasti boolean.

Ada satu tipe data yang penggunaannya mirip boolean, tapi sebenarnya berbeda pada konsepnya, yaitu `nil`. Artinya tidak memiliki nilai apapun. Anda mungkin akan jarang menggunakannya, tapi mungkin Anda akan menemukannya beberapa di kode-kode milik orang lain.

### Keyword

Akan kita bahas di bagian _collection_ lanjutan.
