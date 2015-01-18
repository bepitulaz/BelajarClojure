Struktur Data
=============

* Collection
    * Vector

## Collection

Sejauh ini, kita baru memprogram dengan data yang terpisah-pisah: satu angka, satu string, serta menghasilkan hanya satu nilai. Saat melakukan pemrograman, biasanya Anda akan lebih sering bekerja dengan satu grup data yang dikumpulkan. Clojure memiliki fasilitas yang bagus untuk bekerja dengan menggunakan satu grup data, kita akan sebut dengan _collection_. Sesuai namanya _collection_ adalah koleksi atau kumpulan data. Clojure memiliki 4 tipe _collection_, kita akan pelajari dulu salah satunya.

## Vector

Vector adalah sekumpulan data yang berurutan. Jika Anda pernah memprogram menggunakan bahasa pemrograman lain, vector mungkin akan disebut dengan _array_ di bahasa tersebut.

Untuk membayangkan bagaimana bentuk vector, bayangkan sebuah kotak dibagi menjadi beberapa ruang. Setiap ruang ditandai dengan nomor. Anda bisa meletakkan data apa pun ke dalam masing-masing ruangan, dan Anda akan mengetahui di mana posisi dari masing-masing data, karena setiap ruangan ada nomornya.

![Vector](../images/vector.png)

Perlu dicatat, penomoran ruangan tempat menyimpan data dimulai dari angka 0. Mungkin terlihat aneh, tapi di dunia pemrograman kita sering memulai hitungan dari angka 0.

Vector ditulis dengan menggunakan tanda kurung siku `[]`. Di dalam tanda kurung siku itu kita akan meletakkan setiap data yang akan kita jadikan satu grup. Setiap data dipisahkan dengan spasi. Bayangkan spasi ini sebagai pemisah antara ruang bernomor, seperti yang dijelaskan oleh gambar di atas. Ini adalah contoh vector:

```clojure
[1 4 7]
["lalapan" "ikan goreng" "sambal terasi" "tahu"]
[7 "lalapan" 9 "nasi"]
[]
```

Apa yang bisa kita lakukan dengan vector? Kita bisa menambahkan data baru ke dalam sebuah vector, menghapus unit data yang sudah ada di dalam vector, atau memanggil data yang kita butuhkan dari dalam vector. Di bawah ini beberapa contoh fungsi yang melakukan operasi terhadap vector:

```clojure
(vector? [5 10 15])
;=> true

(vector 5 10 15)
;=> [5 10 15]

(conj [5 10] 15)
;=> [5 10 15]

(count [5 10 15])
;=> 3

(nth [5 10 15] 1)
;=> 10

(first [5 10 15])
;=> 5

(rest [5 10 15])
;=> (10 15)

(last [5 10 15])
;=> 15
```

Mari kita bahas satu demi satu fungsi-fungsi tersebut. Yang pertama, Anda melihat fungsi `vector?`. Anda mungkin sudah bisa menebak untuk apa fungsi tersebut: fungsi tersebut memberi tahu kita apakah argumen yang diberikan vector atau bukan. Bisa Anda lihat ada tanda tanya `?` di akhir nama fungsi. Kita sering menyebut fungsi yang memiliki tanda `?` di belakang namanya sebagai _predicate function_. Nilai yang akan dikembalikan dari fungsi ini hanya jawaban `true` atau `false`.

Dua fungsi berikutnya digunakan untuk membuat vector baru. Fungsi `vector` akan meletakkan argumen-argumen yang diberikan ke fungsi tersebut ke dalam sebuah vector baru. Yang sangat menarik berikutnya adalah fungsi `conj`, karena Anda akan melihat fungsi ini sering digunakan oleh data struktur lainnya. Jika Anda menggunakannya bersama vector dan sebuah data lain, fungsi ini akan membentuk sebuah vector baru dengan tambahan data. Itu sebabnya fungsi ini bernama `conj` singkatan dari _conjugate_ yang dalam bahasa Inggris berarti "join together".

Jika Anda pernah memprogram di bahasa lain, Anda mungkin akan membayangkan `conj` itu memodifikasi vector. Pada kenyataannya tidak. Di Clojure semua _collection_ itu __immutable__--yang artinya data tidak bisa diubah. Saat kita berkata "tambahkan ke" atau "hilangkan dari" sebuah _collection_, yang kita maksud adalah menyuruh fungsi tersebut untuk membuat _collection_ baru dengan tambahan data atau dengan data yang sudah dihilangkan.

Mari kita bahas sisa fungsi lainnya. `count`, bisa Anda tebak fungsi ini memberi tahu kita ada berapa data di dalam sebuah vector. `nth` digunakan jika kita mau mengambil data ke berapa dari sebuah ruangan (masih ingat dengan konsep ruangan bernomor?) di dalam vector. Ingat kita menghitung ruangan dari angka 0. Jadi kalau kita memberi argumen angka 1 kepada fungsi `nth`, maka fungsi ini akan memberikan elemen data kedua dari vector. `first` digunakan untuk mengambil data pertama dari sebuah vector. `rest` mengembalikan sisa data sesudah data pertama. Lalu `last` mengembalikan hanya data yang terakhir dari sebuah vector. Jangan membayangkan `nth` berbarengan dengan `first`, `rest`, dan `last` secara bersama-sama, atau Anda akan merasa bingung.
