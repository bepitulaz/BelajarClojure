Lebih Lanjut dengan Fungsi
==========================

* Fungsi-fungsi penting
    - Fungsi perbandingan (boolean)
    - Fungsi string
* Fungsi Anonim

## Fungsi-fungsi penting

Ada beberapa fungsi yang sangat penting saat menggunaka Clojure. Fungsi aritmetik, membuat fungsi sendiri, dan fungsi yang menggunakan fungsi lain sebagai argumen sudah kita bahas. Mari kita lihat beberapa lagi:

### Fungsi perbandingan (boolean)

Anda bisa menggunakan fungsi `=` untuk melakukan tes persamaan pada dua data. Sebagai contoh, fungsi `meaning-of-life?` yang akan melakukan tes apakah input yang diberikan pada fungsi tersebut `42` atau bukan:

```clojure
(defn meaning-of-life
  [x]
  (= x 42))
```

Beberapa fungsi perbandingan lainnya adalah `>`, `>=`, `<`, `<=`, dan `not=`. Empat yang pertama digunakan secara eksklusif untuk tipe data _number_. Seperti semua fungsi Clojure lainnya, fungsi perbandingan dengan cara _prefix_. Beberapa contohnya:

```clojure
(> 4 3) ;=> true
(>= 4 5) ;=> false
(< -1 1) ;=> true
(<= -1 -2) ;=> false
(< 1 5 9) ;=> true
(< 1 5 3) ;=> false
```

### Fungsi string

Bagian terbesar dari kegiatan membuat program adalah manipulasi _string_. Fungsi _string_ yang paling penting di Clojure untuk diingat adalah `str`, yang akan menyatukan semua argumen menjadi satu _string_.

```clojure
(str "saya" "belajar" "clojure" ".")
;=> "saya belajar clojure."
```

### Fungsi pada _collection_

Saat kita belajar tentang struktur data _collection_, kita telah melihat banyak fungsi yang bisa dioperasikan pada _collection_, termasuk:

* `count`
* `conj`
* `first`
* `nth`
* `rest`
* `assoc`
* `dissoc`
* `merge`

Beberapa fungsi yang sangat penting  untuk digunakan bersama _collection_ dapat menerima fungsi lain sebagai argumennya. Terdengar sangat rumit memang, maka kita akan pelajari itu setelah ini.

### Fungsi _anonymous_

Sejauh ini, semua fungsi yang kita lihat pasti memiliki nama, seperti `+`, `str`, dan `reduce`. Akan tetapi, fungsi tidak selalu memerlukan nama. Sama seperti nilai, tidak selalu harus di-_binding_ ke dalam sebuah _**symbol**_

Fungsi dapat dinamai dengan nama **apapun**. Tidak ada yang salah dengan hal tersebut. Anda nanti akan banyak menjumpai kode Clojure yang tidak memiliki nama (_anonymous_), jadi mari kita pahami terlebih dahulu tentang fungsi tak bernama ini.

Sebuah fungsi _anonymous_ dibuat dengan menggunakan `fn`, seperti:

```clojure
(fn [string1 string2] (str string1 " " string2))
```

Fungsi _anonymous_ memiliki bentuk yang sama seperti pada fungsi yang dibuat dengan `defn`; kita tetap punya argumen yang disusun sebagai _vector_ dan sebuah isi dari fungsi.

Fungsi _anonymous_ akan sangat berguna saat kita berurusan dengan fungsi yang menggunakan fungsi lain sebagai argumennya. Mari kita lihat beberapa contohnya:

```clojure
(map (fn [x] (* 3 x)) [1 2 3]) ;=> [3 6 9]

(reduce (fn [x y] (+ x y)) [1 2 3]) ;=> 6

(reduce
  (fn [s1 s2] (str s1 " " s2))
  ["Belajar" "Clojure"])
;=> "Belajar Clojure"
```
         
