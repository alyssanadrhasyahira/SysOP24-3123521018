## Readers and Writers Problem

Readers and Writers Problem adalah problem yang memodelkan proses yang mengakses database. Masalah ini timbul ketika ada dua proses atau lebih berbagi data yang sama. Data yang dimaksud disini bisa berbentuk buffer, file atau objek dari suatu program.
Terdapat dua variasi pada masalah ini, yaitu :

a. seorang reader tidak perlu menuggu reader lain untuk selesai hanya karena ada
writer menunggu (reader memiliki prioritas lebih tinggi disbanding dengan writer)

b. Jika ada writer yang sedang menunggu, maka tidak boleh ada reader lain yang
bekerja (writer memiliki prioritas yang lebih tinggi)
Jika terdapat writer dalam critical section dan terdapat n reader yang
menunggu, maka satu reader akan menunggu wrt dan n-1 reader akan antri di mutex.
Jika writer mengeksekusi signal(wrt), maka dapat disimpulkan bahwa eksekusi
adalah menunggu reader atau menunggu satu writer. 

![Screenshot 2024-06-04 094217](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/33e4b594-fe3a-4be5-b8b3-55aaf23dfa6f)



## producer-consumer problem 

producer-consumer problem  adalah contoh klasik dari masalah sinkronisasi multiproses yang melibatkan dua jenis proses, yaitu producer (produsen) dan consumer (konsumen), yang berbagi sebuah buffer dengan ukuran tetap yang digunakan sebagai antrean.
Tugas produsen adalah menghasilkan data dan memasukkannya ke dalam buffer, sedangkan tugas konsumen adalah mengambil data dari buffer. Sinkronisasi diperlukan untuk memastikan bahwa produsen tidak mencoba menambahkan data ke buffer ketika buffer penuh dan konsumen tidak mencoba mengeluarkan data dari buffer ketika buffer kosong.

![WhatsApp Image 2024-05-21 at 06 51 28_0623383a](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/fd462bc6-b048-49c2-90e1-b1e5d4a00670)


