Kontrol Program
===============

* `if`
* _boolean logic_
* `let`

_"Flow Control"_ atau kontrol program adalah istilah pemrograman untuk menentukan instruksi apa yang akan diberikan kepada komputer saat program bertemu pada kondisi tertentu. Kita membuat keputusan seperti ini setiap waktu. __Jika__ hari ini hujan, __maka__ kita akan membawa payung; __selain__ hujan bawa topi. __Jika__ jarak ke kantor lebih dari 2 km, __maka__ naik angkot; __selain__ itu jalan kaki.

Perangkat lunak juga penuh dengan pengambilan keputusan seperti itu. __Jika__ data dari user valid, __maka__ beri akses; __selain__ itu kembalikan mereka ke halaman home. Pola yang umum di sini menggunakan __boolean__ `true` atau `false` untuk mengecek apakah kondisi tertentu terjadi.

## `If`

Di Clojure, operator yang paling dasar untuk melakukan pengecekan ini adalah dengan menggunakan `if`. Di bawah ini adalah contoh skenario:

```clojure
(if (valid? data)
	(save! data)
	(error "Your data is invalid"))
```

Bentuk umum dari operator `if` adalah:

```clojure
(if kondisi-yang-akan-dicek
	ekspresi-yang-dijalankan-jika-true
  ekspresi-yang-dijalankan-jika-false)
```

Saat mengecek kebenaran sebuah ekspresi, Clojure mempertimbangkan `nil` dan `false` menjadi salah dan selain itu sebagai benar. Ini beberapa contohnya:

```clojure
(if (> 3 1)
	"3 lebih besar dari 1"
	"3 lebih kecil dari 1")
;=> "3 lebih besar dari 1"

(if (> 1 3)
	"1 lebih besar dari 3"
	"1 lebih kecil dari 3")
;=> "1 lebih kecil dari 3"

(if nil
	"nil berarti benar"
	"nil berarti salah")
;=> "nil berarti salah"

(if (get {:name "Asep"} :city)
	"Ini benar karena nil terpenuhi"
	"Ini salah karena kondisi nil selalu dianggap salah")
;=> "Ini salah karena kondisi nil selalu dianggap salah"
```

## _Boolean logic_ dengan menggunakan `and`, `or`, dan `not`

Pernyataan yang menggunakan `if` tidak terbatas hanya untuk mengecek satu hal. Anda dapat mengecek banyak kondisi menggunakan _boolean logic_. _Boolean logic_ digunakan untuk mengombinasikan dan mengubah hasil dari fungsi predikat menggunakan `and`, `or`, dan `not`.

Jika Anda belum pernah melihat konsep ini sebelumnya dalam pemrograman, ingatlah bahwa ini mengikuti pola pikir yang umum. Apakah ini __dan__ itu benar? Hanya jika keduanya benar. Apakah ini __atau__ itu yang benar? Hanya jika salah satu atau keduanya yang benar. Apakah ini __tidak__ benar? Ya, jika ini salah.

Lihat tabel kebenaran di bawah ini:

| x     | y     | (and x y) | (or x y) | (not x) | (not y) |
| ----- | ----- | --------- | -------- | ------- | ------- |
| false | false | false | false | true  | true  |
| true  | false | false | true  | false | true  |
| true  | true  | true  | true  | false | false |
| false | true  | false | true  | true  | false |

`and`, `or`, dan `not` bekerja seperti fungsi-fungsi lainnya (mereka tepatnya bukan fungsi). Mereka adalah _prefix notation_, seperti yang kita lihat pada aritmetik.

`and`, `or`, dan `not` dapat dikombinasikan. Kode di bawah ini bisa jadi sulit dibaca. Contohnya:

```clojure
(defn tahun-kabisat?
	"Setiap 4 tahun, kecuali tahun yang bisa dibagi 100, 
	tapi benar untuk tahun yang bisa dibagi oleh 400."
	[tahun]
	(and (zero? (mod tahun 4))
       (or (zero? (mod tahun 400))
	         (not (zero? (mod tahun 100))))))
```

## `let`

Saat Anda membuat fungsi, Anda mungkin ingin memberikan nama kepada nilai supaya nilai tersebut bisa digunakan kembali, atau supaya kode Anda ingin lebih mudah dibaca. Di dalam fungsi, bagaimanapun juga Anda tidak boleh menggunakan `def`, seperti yang Anda lakukan di luar fungsi.

Anda seharusnya menggunakan bentuk spesial, yaitu `let`. Mari kita lihat contohnya:

```clojure
(defn pemasukan-setelah-menikah
	"Menyatukan pemasukan Anda bersama pasangan yang Anda cintai."
	[asset-anda asset-pasangan]
	(let [pemasukan-anda (:pemasukan asset-anda)
        pemasukan-pasangan (:pemasukan asset-pasangan)
        total-pemasukan (+ pemasukan-anda pemasukan-pasangan)]
		(assoc {} :pemasukan-bersama total-pemasukan)))

; eksekusi fungsi di atas
(pemasukan-setelah-menikah {:pemasukan 5000000 :asset ["rumah"]} 
                           {:pemasukan 4500000 :asset ["mobil" "motor"]})
;=> {:pemasukan-bersama 9500000}
```

Mungkin fungsi di atas terlihat rumit. Mari kita bahas pelan-pelan.

Pertama, Anda membuat fungsi bernama `pemasukan-setelah-menikah`, lalu diikuti dengan teks dokumentasi fungsi, dan 2 buah argumen yang masing-masing menerima sebuah _map_.

Kemudian mari kita lihat `let`. `let` mengambil _keyword_ `:pemasukan` dari _map_ `asset-anda` dan hasilnya kita beri _symbol_ `pemasukan-anda`. Begitu juga dengan `pemasukan-pasangan`. Lalu `total-pemasukan` adalah _symbol_ dari operasi penjumlahan antara `pemasukan-anda` dan `pemasukan-pasangan`. Itu lah isi dari _vector_ `let`.

Setelah Anda memberi _symbol_ (nama) ke masing-masing ekspresi pemrograman, maka Anda bisa menggunakan _symbol_ tadi di dalam badan fungsi.

Cukup sekian saja materi dasar tentang Clojure, karena dengan modal pengetahuan dasar ini Anda sudah bisa membuat aplikasi menggunakan Clojure.  
