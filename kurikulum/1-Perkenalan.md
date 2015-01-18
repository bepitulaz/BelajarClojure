Perkenalan Pemrograman Menggunakan Clojure
==========================================

* Mengapa Clojure?
* Clojure bagusnya untuk apa?
* Seperti apakah Clojure?
* Apa itu REPL?
* Tipe data sederhana
* Memberi nama ke nilai

## Mengapa Clojure?

Jika Anda tidak pernah memprogram sebelumnya, Anda mungkin tidak tahu jika ada banyak bahasa pemrograman untuk dipilih. Beberapa bahasa pemrograman yang mungkin pernah Anda dengar atau akan dengar diantaranya C, Javascript, Python, PHP, dan Java.

Lalu mengapa kami mengajarkan Clojure? Bahasa yang tidak sepopuler bahasa-bahasa di atas (terutama di Indonesia). Kami menggunakan Clojure karena 3 kualitas yang bahasa ini miliki, sehingga membuatnya ideal untuk bahasa pemrograman pertama untuk dipelajari, dan juga sesuai untuk dipelajari oleh orang-orang yang sudah melakukan pemrograman menggunakan bahasa-bahasa pemrograman lain yang lebih populer:
* Clojure itu _mudah_. Bukan berarti tidak bagus. Konsep-konsep yang harus diketahui saat memprogram dengan Clojure sangat sedikit dan mudah dipahami. Pemahaman Anda akan Clojure akan semakin tumbuh, saat semakin sering menggunakannya, dan Anda pun tetap bisa lebih produktif dengan menggunakan sebagian kecil saja dari bahasa ini.
* Clojure bisa _digunakan untuk kebutuhan apa pun_. Beberapa bahasa memiliki kegunaan yang spesifik. Javascript, sebagai contoh, dulunya hanya digunakan pada halaman web (walaupun sekarang sudah banyak berubah). PHP hanya bisa digunakan untuk pembuatan aplikasi berbasis web. Sedangkan Clojure bisa digunakan untuk kebutuhan apa pun.
* Clojure itu _menyenangkan_. Ini mungkin hanya pendapat kami, tapi kami rasa ini benar.

## Clojure bagusnya untuk apa?

Tadi kami bilang Clojure bisa digunakan untuk kebutuhan apa pun, tapi itu bukan berarti Clojure tidak punya keunggulan sendiri.

Clojure dikenal bagus untuk melakukan pemrosesan data, karena Clojure memiliki struktur data yang tepat untuk melakukan itu. Clojure memiliki beberapa cara yang sangat bagus untuk menampilkan data, dan struktur datanya mudah digunakan.

Clojure dikenal akan konkurensinya. Ini bisa diilustrasikan ketika membangun rumah. Misal kita menyewa 4 tukang, tentunya kita memerlukan mereka untuk bekerja secara paralel  menurut bagiannya masing-masing, bukan satu tukang mengerjakan, sementara yang lain nganggur menunggu. Walaupun begitu, ada masanya mereka mereka harus berkoordinasi. Di bahasa lain, menulis cara mereka berkoordinasi adalah sangat kompleks, di Clojure, mengatur bagaimana tukang-tukang itu bekerja lebih mudah.

Clojure juga sesuai untuk digunakan membangun aplikasi berbasis web. Seperti yang akan kita lakukan bersama-sama.

## Seperti apakah Clojure?

Di bawah ini contoh beberapa bentuk baris kode Clojure:

```clojure
(+ 3 4)
(max 8 17 2)
(makan "pecel")
```

Tanda kurung `()` mungkin hal pertama yang langsung terlihat. Tanda kurung digunakan untuk menandai setiap instruksi untuk komputer pada bahasa Clojure. Setiap saat Anda melihat tanda kurung buka `(`, hal berikutnya yang akan Anda lihat adalah instruksi kepada komputer untuk melakukan sesuatu. Instruksi tersebut normalnya kita sebut _fungsi_. Fungsi digunakan untuk melakukan semua hal pada bahasa Clojure. Fungsi akan mengambil _argumen_--yang ada di sebelah kanan setelah nama fungsi dan masih ada di dalam tanda kurung--dan akan mengembalikan nilai baru. Untuk lebih jelas perhatikan kode di bawah ini:

```clojure
(makan "pecel" 2)
```

penjelasannya adalah `makan` adalah fungsi. `"pecel"` dan `2` adalah argumen yang akan diolah oleh fungsi `makan` yang hasilnya adalah `"kenyang"`. Satu contoh lagi:

```clojure
(+ 3 4 5)
```

penjelasannya adalah `+` adalah fungsi yang akan menjumlahkan argumen angka `3`, `4`, dan `5` dan menampilkan nilai baru berupa `12`.

## Komentar

Saat kita menulis kode, kita akan mencoba membuatnya sejelas mungkin agar pada saat orang lain membaca kode kita atau pada saat kita membaca kembali kode lama yang pernah kita tulis, kita akan langsung tau maksud dari kode tersebut. Salah satu cara untuk menjelaskan sebuah kode adalah dengan memberi komentar.

Komentar pada Clojure diawali dengan menggunakan titik koma `;`. Apa pun yang ditulis dengan diawali `;` tidak akan dieksekusi oleh komputer. Hanya dibutuhkan satu tanda `;` untuk membuat komentar, tapi ada juga programmer yang menulis dengan `;;`. Itu cuma masalah gaya penulisan.

```clojure
;; teknik makan pecel
(makan "pecel" 2) ; enak enak
```

## Apa itu REPL?

"REPL" adalah singkatan dari "Read-Eval-Print-Loop". Banyak bahasa pemrograman, termasuk Clojure, memiliki fasilitas ini yang sangat memudahkan programmer dalam melakukan pengembangan aplikasi. Programmer dapat mengetik kode untuk dicoba-coba dan akan langsung mendapatkan hasil operasinya secara instan melalui terminal (konsol), sebelum mengetiknya langsung di kode sumber yang akan digunakan di dalam aplikasi. Kami akan jelaskan lebih lanjut nanti.

## Tipe data sederhana

Untuk melakukan apa pun pada sebuah bahasa pemrograman, Anda membutuhkan tipe data. Tipe data sederhana di Clojure adalah _numbers_, _strings_, _booleans_, dan _keywords_.

### Numbers

_Numbers_ sudah jelas artinya angka. Clojure punya beberapa perbedaan tipe angka.

Yang pertama adalah `Integer`. `Integer` meliputi 0 dan seluruh angka positif dan negatif. Anda akan menuliskan seperti yang biasa Anda tulis. Contohnya:

```clojure
0
12
-42
```

Lalu kita punya tipe angka `Decimal` dan juga `Float`. Contohnya:

```clojure
10.5
-99.9
0.0000072725
```

Kita juga punya tipe angka `Fraction` (pecahan), juga disebut `Ratio`. Komputer tidak bisa dengan sempurna menampilkan semua `float` dengan tepat, tapi pecahan sudah pasti akan tepat. Contohnya:

```clojure
1/2
-7/3
```

### Operasi Aritmetika

Anda bisa melakukan penjumlahan, pengurangan, perkalian, dan pembagian angka. Di Clojure, aritmetika akan terlihat sedikit berbeda daripada yang biasa Anda tulis. Lihat contoh berikut:

```clojure
(+ 1 1) ;=> 1 + 1 = 2
(- 12 4) ;=> 12 - 4 = 8
(* 13 2) ;=> 13 * 2 = 26
(/ 27 9) ;=> 27 / 9 = 3
```

Ini namanya _prefix notation_. Sedangkan yang biasa Anda lihat namanya _infix notation_, yaitu operator aritmetikanya diletakkan di antara angka yang mau diproses.

_Prefix notation_ berguna karena beberapa alasan. Misalnya jika Anda menggunakan operator aritmetika yang sama untuk sebuah operasi aritmetika yang panjang, Anda akan mengurangi penulisan yang berulang:

```
Infix: 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9
Prefix: (+ 1 2 3 4 5 6 7 8 9)
```

```
Infix: 1 + 2 * 2 + 3 / 3
Prefix: (+ (* 2 2) (/ 3 3) 1)
```

Contoh di atas menggunakan tipe data `Integer`. Anda juga bisa melakukan operasi aritmetika dengan menggunakan `float` dan `ratio`. Contohnya:

```clojure
(+ 4/3 7/8)   ;=> 53/24
(- 9 4.2 1/2) ;=> 4.3
(* 8 1/4)     ;=> 2
(/ 27/2 1.5)  ;=> 9.0
```

### String, Keyword, dan Boolean

Kita akan bahas tipe data ini lebih dalam nanti. Sekarang akan kami contohkan dulu cara penulisannya agar Anda mendapat gambaran.

```clojure
;;String
"Saya belajar Clojure"
"Halo!"

;;keyword
:surname
:birth-date
:r2

;;boolean
true
false
```

## Memberikan nama kepada nilai

Jika kita harus menulis nilai-nilai dengan tipe data tertentu berulang-ulang, tentu kita akan merasa kesulitan untuk menulis sebuah program atau aplikasi. Kita butuh memberi nama kepada nilai-nilai yang akan kita gunakan, sehingga kita bisa dengan mudah mengingatnya kembali saat kita butuhkan. Kita bisa melakukannya dengan fungsi `def`. Contohnya:

```clojure
(def pisang 3)
(def pete 4)
(+ pisang pete) ; akan menghasilkan nilai 7
```

Saat Anda memberi nama kepada sebuah nilai, nama tersebut kita sebut _symbol_. Anda bisa memberi _symbol_ tidak hanya kepada nilai atau data yang sederhana, tapi Anda juga bisa memberi _symbol_ kepada sebuah operasi. Contohnya melanjutkan dari kode di atas:

```clojure
(def gado-gado (+ pisang pete))
gado-gado ; saat Anda ketik ini maka nilai hasilnya berarti 7
```

Arti dari kode di atas yaitu `gado-gado` adalah _symbol_ dari nilai hasil operasi `(+ pisang pete)`.

Demikian bagian awal dari perkenalan terhadap bahasa Clojure.
