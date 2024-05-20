## Perbedaan pararel concurrent dan pararel-concurrent

![WhatsApp Image 2024-05-14 at 09 03 30](https://github.com/PelangiKartikaChandraKirana/SysOP24-3123521003/assets/160555525/8212e08a-d7dd-4532-86ce-9c168b44ba28)


**Concurrent**
- Pengertian
  > Concurrent adalah sebuah proses yang dijalankan secara sekaligus atau sebuah proses yang dapat melakukan beberapa hal secara sekaligus. Dari pengertian diatas dapat diartikan bahwa concurrent tidak dijalankan secara bersamaan akan tetapi dilakukan secara sekaligus.

- Contoh
  > user melakukan click pada button kemudian aplikasi menjalankan background process pada thread yang berbeda, sehingga user-interface tetap responsive. Aplikasi menjalankan dua hal berbeda, yaitu background process dan user interface, secara bersamaan.
  
 **Parallel**
- Pengertian
  > Parallel adalah beberapa proses yang dilakukan secara bersamaan Parallel  dapat melakukan sebuah proses secara bersamaan
  
- Contoh
  > sebuah aplikasi melakukan pengolahan 1.000.000 data. Data tersebut dibagi menjadi empat bagian, masing-masing 250.000 data, kemudian tiap bagian tersebut dieksekusi secara bersamaan pada thread yang berbeda-beda.

 **pararel-concurrent**
- Pengertian
  > Kombinasi dari eksekusi tugas-tugas secara simultan (paralel) dan secara interleaved (konkuren).
  
- Contoh
  > Menangani Permintaan Klien:
  >
  >Paralel: Server web mampu melayani banyak permintaan dari klien secara bersamaan. Setiap permintaan klien yang diterima oleh server dapat ditangani dalam thread terpisah.
  >
  >Konkuren: Dalam setiap thread, beberapa langkah dapat dilakukan secara konkuren, seperti membaca permintaan, memprosesnya, dan mengirimkan respons kembali ke klien.


## Perbedaan Concurrent dan Serial

![WhatsApp Image 2024-05-14 at 09 01 08_59e26df8](https://github.com/Mardzyska/SysOP24-3123521008-/assets/139208195/6bb6e034-3646-4de1-9d8e-11e8c7325cd0)

 **concurrent**
- Pengertian
  > Concurrent adalah kemampuan untuk menjalankan beberapa tugas secara bersamaan, dengan tugas-tugas tersebut mungkin berlangsung secara bersamaan atau bergantian.
  
- Contoh
  > Multithreading, multiproses, dan asynchronous programming (pemrograman asinkron) adalah beberapa teknik yang digunakan dalam pemrosesan konkuren.

**Serial**
- Pengertian
  > Serial adalah menjalankan tugas secara berurutan, satu per satu, di mana setiap tugas harus menyelesaikan sebelum tugas berikutnya dapat dimulai.
  
- Contoh
  > Ketika kita membuat secangkir kopi di pagi hari, banyak langkah yang harus dilakukan secara berurutan. Setiap langkah bergantung pada langkah sebelumnya dan tidak dapat dilakukan secara konkuren











  

