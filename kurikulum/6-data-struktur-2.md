Lebih Lanjut Dengan Struktur Data _Collection_
==============================================

* _Keyword_ dan _Map_
* _Collection of collection_

## _Keyword_

```clojure
:pertama
:terakhir
```

_Keyword_ adalah tipe data yang paling dasar dan paling aneh, karena tidak ada padanannya di dunia nyata seperti _number_, _string_, dan _boolean_. Anda bisa membayangkan _keyword_ sebagai sebuah tipe _string_ khusus, yang digunakan sebagai label. _Keyword_ sering digunakan di dalam `map`.

## Map

_Map_ menampung satu set _key_ dan _value_ (nilai) yang saling berasosiasi. Anda bisa membayangkannya seperti membaca kamus: Anda mencari sebuah kata (_keyword_) dan melihat artinya (_value_). Jika Anda pernah melakukan pemrograman dengan bahasa lain, mungkin Anda pernah melihat sesuatu seperti _map_, mungkin namanya _dictionaries_, _hash_, atau _associative array_.

Kita menulis `map` dengan menutup _key_ dan _value_ menggunakan kurung kurawal `{ }`, seperti:

```clojure
{:firstname "Pete" :lastname "Green"}

{:a 1 :b "pete"}

{}
```

_Map_ berguna karena dapat menampung data secara normal seperti yang kita pikirkan. Kita ambil contoh, Pete Green. _Map_ dapat menampung nama depan, nama belakang, alamat, makanan favorit, atau apa pun. Menggunakan _map_ adalah salah satu cara termudah untuh mengumpulkan dan membaca data. Contoh di baris terakhir adalah _map_ kosong. Sebuah _map_ yang sudah siap menampung data, tapi belum ada apa-apa di dalamnya.

Mari kita melihat beberapa fungsi yang bisa kita gunakan bersama _map_. Kita tidak punya fungsi sebanyak _vector_ dan _list_.

```clojure
(map? {:firstname "Pete" :lastname "Green})
;=> true

(get {:firstname "Pete" :lastname "Green"} :lastname)
;=> "Green"

(get {:firstname "Pete" :lastname "Green"} :address :MISS)
;=> :MISS
```

`map?` menentukan apakah argumen yang dikirimkan adalah sebuah _map_. Nilai baliknya adalah `true` atau `false`.

`get` bekerja seperti `nth` pada _vector_, tapi yang diambil adalah _key_, bukan _number_. `get` menggunakan _key_ yang disuplai sebagai argumennya untuk mencari _value_ di dalam _map_. Apa yang terjadi pada contoh `get` yang terakhir? Kita bisa menyuplai _value_ untuk dikembalikan oleh `get` jika tidak bisa menemukan _key_ yang kita maksud, dalam hal ini `get` tidak bisa menemukan `:address` dari dalam _map_ sehingga mengembalikan _value_ yang sudah kita berikan sebelumnya, yaitu `:MISS`.

```clojure
(assoc {:firstname "Asep"} :address "Jakarta")
;=> {:firstname "Asep :address "Jakarta"}

(dissoc {:firstname "Asep" :address "Jakarta"} :address)
;=> {:firstname "Asep"}

(merge {:firstname "Asep"} {:address "Jakarta"})
;=> {:firstname "Asep" :address "Jakarta"}
```

`assoc` dan `dissoc` adalah sepasang fungsi yang gunanya untuk mengasosiasikan dan memisahkan sebuah _key_ dan _value_ pada sebuah _map_. Lihat bagaimana kita menambahkan `"Jakarta"` ke dalam sebuah _map_ menggunakan `assoc` kemudian mengeluarkannya lagi dari _map_ tersebut dengan menggunakan `dissoc`.

`merge` menyatukan 2 buah _map_ yang berbeda menjadi satu _map_ baru.

```clojure
(count {:firstname "Asep" :lastname "Bagja"})
;=> 2
```

`count`, setiap _collection_ memiliki fungsi ini. `count` mengembalikan jumlah asosiasi di dalam sebuah _map_.

```clojure
(keys {:firstname "Asep" :lastname "Bagja"})
;=> (:firstname :lastname)

(vals {:firstname "Asep" :lastname "Bagja"})
;=> ("Asep" "Bagja")
```

Lalu kita punya `keys` dan `vals`, yang fungsinya sangat sederhana: mengembalikan _keys_ dan _value_ dalam _map_. Urutannya tidak bisa dijamin, kita bisa saja mendapat `(:firstname :lastname)` atau `(:lastname :firstname)`.

Mari kita lihat satu lagi tentang _map_ sebelum melanjutkan ke materi selanjutnya.
