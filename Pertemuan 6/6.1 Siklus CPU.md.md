**JAWABAN NOMOR 1**
## pengertian
siklus CPU (fetch,decode,execute) cycle adalah proses berulang yang dilakukan oleh CPU untuk mengeksekusi instruksi dalam sebuah program. Setiap siklus melibatkan tiga tahap utama: Fetch, Decode, dan Execute.

## Tahap-tahap proses
Fetch:
* CPU mengambil instruksi program dari memori utama.
* Instruksi ini diambil berdasarkan alamat yang disimpan di Program Counter (PC).

Decode:
* CPU mendekode instruksi yang telah diambil untuk mengetahui operasi apa yang harus dilakukan.
* Instruksi dipecah menjadi operasi yang lebih kecil yang dapat dipahami oleh CPU.

Execute:
* CPU menjalankan instruksi yang telah didekode.
* Operasi-operasi matematika atau logika dilakukan sesuai dengan instruksi.

## Contoh fetch decode execute cycle ketika bekerja

Diberikan High level language source code yaitu

Z = X+Y

Untuk bahasa assemblynya bisa ditulis sebagai berikut

LOAD [10]

ADD [11]

STORE [12]

LOAD  X

ADD   Y

STORE Z

Assembled object code

100110     --       0000001010

110011     --       0000001011

111010     --       0000001100

dapat diartikan sebagai berikut:

1. LOAD: Ambil instruksi dari memori 10 ke akumulator.

2. ADD: Tambahkan isi dari memori 11 dengan nilai yang ada di akumulator.

3. STORE: Simpan hasil penjumlahan yang ada di akumulator ke memori 12

## ilustrasi dalam CPU

![Diagram Tanpa Judul (6)](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f0fe8c09-3043-4a69-88b2-ed9fb195eb8a)


* CPU terdiri dari Control Unit, Accumulator, dan Arithmetic Logic Unit (ALU).
* Register lain seperti Program Counter (PC), Current Instruction Register (CIR), Memory Address Register (MAR), dan Memory Data Register (MDR) juga ada.

## langkah-langkah dalam CPU

![Diagram Tanpa Judul (7)](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/4149ff67-b449-4272-96f3-385c980c7f0c)


* Program Counter menyimpan alamat untuk instruksI.
  
![Diagram Tanpa Judul (8)](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/ce8667d0-5127-4454-a976-56d0df33c95c)


* Alamat memori disimpan di MAR, isi dari alamat memori dimuat di MDR, dan instruksi disimpan di CIR. Program Counter bertambah 1.

 ![Diagram Tanpa Judul (9)](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/2af87eb7-4248-44cf-9700-ba064f3ad681)

fetch instruksi pertama dilakukan 

![KE 1](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/7d802cea-08d5-45ef-9252-7a13d4d62bc0)

1. Sekarang dapat melakukan decode kode instruksi, Masukan instruksi tersebut ke Control Unit
2. Setelah insturksi LOAD 10 dieksekusi maka selanjutnya CPU akan
melakukan fetch memori 10, Jadi Memory Address Register nya berubah menjadi 10
3. Lalu ambil isi dari memori 10 dan simpan di Memory Data Register
4. lalu dari MDR akan disimpan juga di Akumulator. 

Setelah instruksi pertama dilakukan maka selanjutnya adalah fetch
instruksi ke dua.

![KE 2](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/0af9bd1c-b5a6-481e-baa1-70f6216afcca)


1. Program Counter sudah menunjukkan alamat memori yang baru, sehingga langkah berikutnya adalah menyalin alamat memori tersebut ke Memory Address Register
2. Kemudian, konten dari alamat memori 101 diambil dan disimpan ke dalam Memory Data Register.
3. Instruksi yang terdapat di alamat memori 101 juga disimpan di Current Instruction Register
4. Setelah itu, Program Counter akan bertambah 1 untuk menunjukkan instruksi selanjutnya.

![KE 3](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/e237162c-e8d0-48e0-b722-06669ede2fa3)


1. Lakukan decode instruksi kedua dengan cara yang sama seperti instruksi pertama dengan diteruskan ke Control unit.
2. Setelah Control memahami bahwa instruksi ini adalah operasi add, maka instruksi add diteruskan ke Unit Logika Aritmetika (ALU).
3. Salin isi Akumulator ke ALU.
4. Salin alamat memori 11 ke Register Alamat Memori (MAR) karena akan mengambil data dari alamat tersebut.
5. Salin isi dari alamat memori 11 ke Register Data Memori (MDR).
6. Transfer data dari MDR ke Akumulator.
7. ALU akan menambahkan angka 3 dengan 2.
8. dan menampilan kembali hasilnya ke Akumulator sehingga bisa menjaga total running itu.

Setelah instruksi kedua dilakukan maka selanjutnya adalah fetch
instruksi ke tiga.

![KE 4](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/d967bc47-978c-4519-a8e2-9486d2504f27)


1. lokasi memori 102 di salin ke Memory Address Register.
2. Isi dari alamat memori 102 disalin ke Memory Data
3. Instruksi tersebut dipindahkan ke Current Instruction Register
4. selanjutnya Program Counter akan ditambah 1 menjadi 103, disini biasanya akan ada instruksi halt atau stop diakhir program.

<![KE 5](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/5408dd4b-b68a-451e-9260-839f7165ffda)


1. decode instruksi ketiga, dengan simpan instruksi tersebut kedalam Control
Unit.
2. Karena disini instruksinya adalah untuk STORE atau menyimpan hasil ke alamat memori 12 maka simpan lokasi 12 ke Memory Address Register
3. Lalu hasil dari Akumulator dipindahkan ke Memory Data Register
4. dan dari Memory Data Register
akan dilanjutkan ke lokasi memori 12. Begitu lah program ini terselesaikan







## Peran Bahasa Pemrograman
Bahasa pemrograman adalah suatu tools yang membantu programmer menulis serangkaian instruksi untuk dilakukan komputer dalam mengerjakan task tertentu.Fungsi bahasa dalam kehidupan manusia sehari-hari adalah sebagai alat komunikasi yang bisa dipahami. Begitu juga dengan bahasa pemrograman. Ini berfungsi sebagai penghubung komunikasi antara komputer dan manusia (programmer).

## Peran compiler
Compiler adalah software khusus untuk menerjemahkan bahasa pemrograman tingkat tinggi (kode sumber) menjadi kode mesin yang bisa dipahami dan dijalankan oleh komputer. Compiler memainkan peran penting dalam proses pengembangan software karena membantu mengetahui jika ada kesalahan sintaksis dan semantik dalam kode sebelum akhirnya programmer menjalankan kode tersebut. Adanya compiler bisa menghemat waktu, mencegah terjadinya crash, sampai akhirnya menghasilkan program yang lebih cepat dan ringkas.


## Peran Sistem Oprasi
1. Mengelola sumber daya terkait dengan pengendalian perangkat lunak
sistem/perangkat lunak aplikasi yang sedang dijalankan. Sebagai contoh
komponen perangkat keras pada komputer yaitu CPU, memori utama, alat
input/output.

2. Mempersiapkan agar program aplikasi dapat berinteraksi dengan
perangkat keras secara konsisten dan stabil tanpa harus mengetahui secara
detil perangkat keras.

3. melakukan pengelolaan proses mencakup penyiapan, penjadwalan, dan
pemantauan proses program yang sedang dijalankan.

4. melakukan pengelolaan data pengendalian terhadap data
masukan/keluaran






  
