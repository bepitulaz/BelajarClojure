Fungsi
======

* Apa itu fungsi?
* Memberi nama fungsi
* Fungsi-fungsi penting
    * Fungsi _collection_
* `map` dan `reduce` - Fungsi yang mengambil fungsi lain

## Apa itu fungsi?

Anda sudah melihat beberapa fungsi, seperti `count`, `conj`, `first`, dan `rest`. Semua operasi aritmetika yang kita lakukan juga memiliki fungsi, seperti `+`, `-`, `*`, dan `/`. Jadi apa maksudnya fungsi?

Sebuah _function_ adalah sekumpulan instruksi yang mengambil nilai (argumen), melakukan operasi terhadap nilai tersebut, dan mengembalikan nilai baru hasil operasi. Mari kita lihat contohnya:

```clojure
(defn jumlah-tagihan
  "Hitung jumlah tagihan setelah terkena pajak"
  [tagihan]
  (+ tagihan (* 0.15 tagihan)))
```

Pada kode di atas:

* `defn` sebuah fungsi yang menandai jika kita sedang mendefinisikan sebuah fungsi buatan kita sendiri
* `jumlah-tagihan` adalah nama fungsi yang sedang kita buat
* String di baris selanjutnya adalah dokumentasi yang menjelaskan kegunaan fungsi tersebut. Ini tidak harus ada, tapi sebaiknya ada karena berguna untuk memberi penjelasan pada kode kita
* `[tagihan]` daftar argumen yang harus dimasukkan, agar fungsi `jumlah-tagihan` bisa berjalan. Untuk fungsi `jumlah-tagihan` kita hanya butuh 1 argumen bernama `tagihan`
* `(+ tagihan (* 0.15 tagihan))` ini adalah _body_ dari fungsi tersebut. Baris ini lah yang akan dieksekusi saat kita menggunakan fungsi `jumlah-tagihan`

Untuk menggunakan `jumlah-tagihan`, kita bisa panggil fungsi tersebut seperti yang sudah kita lakukan di sesi sebelumnya.

```clojure
(jumlah-tagihan 100000) ;=> 115000
(jumlah-tagihan 55000) ;=> 62500
```

Fungsi juga bisa mengambil lebih dari 1 argumen. Mari kita buat fungsi `jumlah-tagihan-dengan-donasi` yang menghitung tagihan setelah pajak ditambah donasi seiklasnya.

```clojure
(defn jumlah-tagihan-dengan-donasi
  "Hitung tagihan setelah pajak ditambah donasi."
  [tagihan donasi]
  (+ tagihan donasi (* 0.15 tagihan)))

(jumlah-tagihan-dengan-donasi 100000 5000) ;=> 120000
(jumlah-tagihan-dengan-donasi 55000 2000) ;=> 65250
```

## Memberi Nama Fungsi

Nama fungsi adalah _symbol_. Sama seperti simbol yang kita gunakan pada `def` saat memberi nama pada nilai.

Simbol harus diawali dengan karakter non-numerik, tetapi di dalamnya bisa mengandung karakter alphanumeric bersama dengan *, +, !, -, _, dan ?. Fleksibilitas ini penting saat membuat nama fungsi, karena ada beberapa idiom yang kita gunakan saat memprogram.

Fungsi yang menghasilkan nilai `true` atau `false`--disebut _predicate_--seringnya diakhiri dengan `?`:

* `zero?`
* `vector?`
* `empty?`

## Fungsi-Fungsi Penting

Ada beberapa fungsi yang benar-benar penting saat menggunakan Clojure, seperti fungsi-fungsi aritmetik yang sudah kita bahas. Mari kita lihat beberapa yang lainnya.

### Fungsi-fungsi _collection_

Saat kita mempelajari struktur data, kita melihat banyak fungsi yang digunakan untuk beroperasi pada struktur-struktur data tersebut, termasuk:

* `count`
* `conj`
* `first`
* `rest`
* `nth`
* `assoc`
* `dissoc`
* `merge`

Beberapa fungsi yang memiliki kekuatan sangat besar untuk melakukan operasi pada _collection_ dapat menjadikan fungsi lain sebagai argumennya. Konsep fungsi sebagai argumen mungkin akan terdengar rumit, maka kita akan pelajari lebih lanjut.

## `map` and `reduce` - Fungsi yang menggunakan fungsi lain sebagai argumen

Salah satu sisi ajaib dari Clojure--dan ada beberapa bahasa lain yang punya fasilitas sama--adalah fungsi bisa menjadikan fungsi lain sebagai argumennya. Mungkin terdengar sangat rumit, jadi mari langsung kita lihat saja contohnya:

```clojure
(def harga [1500 2000 5400 4300])

(defn kali-dua
  "Jadikan harga dikali dua"
  [harga]
  (* 2 harga))

(map kali-dua harga) ;=> [3000 4000 10800 8600]
```

`map` adalah fungsi yang menjadikan fungsi lain sebagai argumennya, bersama-sama dengan _collection_. `map` akan menerapkan fungsi `kali-dua` ke setiap elemen yang ada pada vector `harga`, kemudian menghasilkan vector baru hasil operasinya. Konsep ini mungkin terdengar aneh, tapi fungsi yang bisa menggunakan fungsi lain sebagai argumennya adalah inti dari Clojure dan inti dari _functional programming_ pada umumnya.

Mari kita lihat fungsi lainnya yang juga mempunyai kemampuan sama untuk menggunakan fungsi sebagai argumennya. Yang satu ini bernama `reduce`, dan ini biasanya digunakan untuk mengubah _collection_ menjadi satu nilai sendiri (bukan _collection_).

```clojure
(defn tambah
  [x y]
  (+ x y))

(reduce tambah [1 2 4]) ;=> 7
```

`reduce` mengambil elemen 0 dan 1 dari _collection_, lalu menambahkannya `(+ 1 2)`. Setelah mendapat hasil akhir `3`, `reduce` akan memanggil lagi fungsi `tambah` dan memanggil elemen ke 2 (dalam _collection_ ini adalah 4), lalu menambahkannya kembali `(+ 3 4)` dan hasilnya `7`. `reduce` akan berhenti saat semua elemen pada _collection_ sudah dilakukan operasi.
