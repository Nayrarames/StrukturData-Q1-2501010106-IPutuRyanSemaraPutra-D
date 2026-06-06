# StrukturData-Q1-2501010106-IPutuRyanSemaraPutra-D
Quis 1 Struktur Data: Array dan Linked List
Materi: Dasar Teori & Implementasi Konseptual
Instruksi
Jelaskan jawaban Anda dengan fokus pada konsep dasar struktur data dan analisis kompleksitas
waktu/ruang.
1. Karakteristik Memori dan Akses Data
Jelaskan mengapa operasi akses elemen pada Array dapat dilakukan dalam waktu konstan
O(1), sedangkan pada Singly Linked List membutuhkan waktu linear O(n). Hubungkan
jawaban Anda dengan konsep alamat memori (kontinu vs non-kontinu).
2. Analisis Efisiensi Operasi Manipulasi
Dalam kondisi apa sebuah Linked List lebih diunggulkan dibandingkan Array untuk operasi penyisipan (insertion) dan penghapusan (deletion) data? Berikan alasan teoritisnya.
3. Konsep Doubly Linked List
Jelaskan struktur anatomi dari sebuah node pada Doubly Linked List. Apa dampak keberadaan pointer tambahan tersebut terhadap penggunaan memori serta fleksibilitas penelusuran dibandingkan dengan Singly Linked List?
4. Mekanisme Circular Linked List
Apa yang membedakan Circular Linked List dari Linked List biasa secara teoritis? Sebutkan satu contoh skenario penggunaan (use case) di mana struktur melingkar ini lebih
efektif digunakan.
5. Array Dinamis di Python
Python list secara internal diimplementasikan sebagai Dynamic Array. Jelaskan mekanisme yang terjadi ”di balik layar” ketika sebuah Dynamic Array kehabisan kapasitas saat
melakukan operasi append.

Jawaban:

Quis 1 Struktur Data: Array dan Linked List

1. Karakteristik Memori dan Akses Data

Operasi akses elemen pada Array dapat dilakukan dalam waktu O(1) karena data disimpan secara kontinu (berurutan) di memori. Setiap elemen memiliki indeks, sehingga alamat memori suatu elemen dapat dihitung langsung menggunakan rumus:

[
Alamat = Alamat\ Awal + (Indeks \times Ukuran\ Data)
]

Karena alamat dapat dihitung secara langsung tanpa harus melewati elemen lain, waktu akses selalu konstan.

Sebaliknya, pada Singly Linked List, node-node disimpan secara non-kontinu (tidak berurutan) di memori. Setiap node hanya menyimpan data dan pointer ke node berikutnya. Untuk mengakses elemen ke-(n), program harus menelusuri node satu per satu dari head hingga mencapai node yang dicari.

Akibatnya:

Array → Akses elemen: O(1)
Singly Linked List → Akses elemen: O(n)

Kesimpulan: Keunggulan Array berasal dari penyimpanan memori yang berdekatan (kontinu), sedangkan Linked List memerlukan traversal karena lokasi node tersebar di memori.

---

2. Analisis Efisiensi Operasi Manipulasi

Linked List lebih unggul dibandingkan Array ketika sering dilakukan operasi penyisipan (insertion) dan penghapusan (deletion), terutama di awal atau tengah data.

Pada Array

Ketika menyisipkan atau menghapus elemen di posisi tertentu, elemen-elemen setelah posisi tersebut harus digeser.

Contoh:

```
Array: [A, B, C, D]

Sisipkan X di indeks 1

Menjadi:
[A, X, B, C, D]
```

Elemen B, C, dan D harus digeser sehingga kompleksitasnya:

[
O(n)
]

Pada Linked List

Jika posisi node sudah diketahui, penyisipan atau penghapusan cukup mengubah pointer antar node tanpa menggeser data.

Contoh:

```
A -> B -> C

Sisipkan X setelah A

A -> X -> B -> C
```

Hanya perlu memperbarui pointer:

[
O(1)
]

Kesimpulan

Linked List lebih efisien ketika:

Ukuran data sering berubah.
Banyak operasi insert/delete.
Posisi node sudah diketahui.

Sedangkan Array lebih cocok jika:

Akses data berdasarkan indeks lebih sering dilakukan.
Jumlah data relatif stabil.

---

3. Konsep Doubly Linked List

Pada Doubly Linked List, setiap node memiliki tiga bagian:

```
+--------+--------+--------+
| Prev   | Data   | Next   |
+--------+--------+--------+
```

Keterangan:

Prev → menunjuk ke node sebelumnya.
Data → menyimpan nilai data.
Next → menunjuk ke node berikutnya.

Dampak terhadap Memori

Karena terdapat satu pointer tambahan (Prev), kebutuhan memori menjadi lebih besar dibandingkan Singly Linked List.

Perbandingan:

Singly Linked List

```
Data + Next
```

Doubly Linked List

```
Prev + Data + Next
```

Sehingga penggunaan memori meningkat karena setiap node menyimpan dua pointer.

Dampak terhadap Fleksibilitas

Keuntungan:

Traversal dapat dilakukan maju dan mundur.
Penghapusan node lebih mudah karena dapat langsung mengakses node sebelumnya.
Navigasi lebih fleksibel.

Kompleksitas traversal:

Maju → O(n)
Mundur → O(n)

Kesimpulan: Doubly Linked List mengorbankan memori tambahan untuk memperoleh fleksibilitas penelusuran dua arah.

---

4. Mekanisme Circular Linked List

Perbedaan utama Circular Linked List dengan Linked List biasa adalah node terakhir tidak menunjuk ke `NULL`, melainkan kembali ke node pertama (head).

Linked List Biasa

```
A -> B -> C -> NULL
```

Circular Linked List

```
A -> B -> C
^         |
|_________|
```

Karakteristik

* Tidak memiliki node akhir yang bernilai NULL.
* Traversal dapat dilakukan terus-menerus dalam siklus.
* Semua node saling terhubung membentuk lingkaran.

Contoh Use Case

Round Robin Scheduling pada Sistem Operasi

Dalam penjadwalan CPU, setiap proses mendapatkan giliran eksekusi secara bergantian.

Contoh:

```
P1 -> P2 -> P3 -> P1 -> P2 -> ...
```

Setelah proses terakhir selesai mendapatkan jatah waktu, scheduler langsung kembali ke proses pertama tanpa perlu kembali ke awal struktur data.

Kesimpulan: Circular Linked List sangat efektif untuk sistem yang memerlukan pemrosesan berulang secara siklis.

---

5. Array Dinamis di Python

`list` pada Python diimplementasikan sebagai **Dynamic Array**.

Ketika melakukan:

```python
data.append(x)
```

Python akan menempatkan elemen baru pada ruang kosong yang masih tersedia.

Jika Kapasitas Masih Tersedia

Misalnya kapasitas array = 8 dan jumlah elemen = 5.

```
[1][2][3][4][5][_][_][_]
```

Operasi `append()` hanya menambahkan elemen baru:

```
[1][2][3][4][5][6][_][_]
```

Kompleksitas:

[
O(1)
]

Jika Kapasitas Penuh

Misalnya:

```
[1][2][3][4]
```

Kapasitas = 4 dan seluruh slot sudah terisi.

Saat `append(5)` dilakukan, Python akan:

1. Mengalokasikan blok memori baru yang lebih besar.
2. Menyalin seluruh elemen lama ke blok baru.
3. Menambahkan elemen baru.
4. Membebaskan memori lama.

Ilustrasi:

```
Memori Lama:
[1][2][3][4]

↓

Memori Baru:
[1][2][3][4][5][_][_][_]
```

Proses penyalinan memerlukan waktu:

[
O(n)
]

Namun, karena proses resize tidak terjadi setiap kali append, rata-rata kompleksitas operasi `append()` tetap:

[
O(1) \text{ (amortized)}
]

Kesimpulan

Dynamic Array pada Python menggabungkan:

Kecepatan akses Array (O(1))
Fleksibilitas ukuran yang dapat bertambah otomatis

dengan mekanisme resize dan copy ketika kapasitas memori yang tersedia telah habis.
