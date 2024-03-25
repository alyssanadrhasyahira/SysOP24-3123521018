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




**JAWABAN NOMOR 3**


## Melakukan clone 
https://github.com/ferryastika/flops-iops 

<img width="408" alt="Screenshot 2024-03-17 104618" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/e66bb465-4311-439e-a263-c3b8a6b1dbaa">

## Build Binaries

```sh
$ make
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/9f0182ab-9b4d-4a48-8da5-41ba28bf9c10)
 
Analisa $ make Perintah ini digunakan untuk mengompilasi program dari kode sumber. 

## Cleaning Old Build

```sh
$ make clean
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/ef904eec-16cd-4c1b-8d52-a347c14e5059)

Analisa : $ make clean Perintah ini digunakan untuk membersihkan file sementara dan objek yang dihasilkan oleh perintah make.

## Install Binaries 

```sh
$ sudo make install
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/d93f46a2-02ea-450c-9725-f8e03ea26bf5)

Analisa : $ sudo make install Perintah ini digunakan untuk menginstal program yang telah dikompilasi ke dalam sistem. 

## Uninstall Binaries 

```sh
$ sudo make uninstall
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/7f182e70-5ee7-4760-b991-eb5463732004)

Analisa : $ sudo make uninstall: Perintah ini digunakan untuk menghapus program yang telah diinstal menggunakan make install. 


## Usage
```sh
  $ iops64 $(nproc) 1
```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/61306b67-2fb6-4d04-97e6-7975ab123bac)

```sh
  $ flops64 $(nproc) 1
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/9a51df41-26e6-49a0-8fa1-36ba907a4a13)



```sh
  $ iops64 $(nproc) 2
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/84ab51b2-3d71-4eea-bcd8-b6fe339b572a)

```sh
  $ flops64 $(nproc) 2
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/0d5998c7-e6ad-4334-867d-a63c4de51bdb)


```sh
  $ iops64 $(nproc) 3
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/1dba4501-124d-4d2d-bdef-2b9f4ad481a8)

```sh
  $ flops64 $(nproc) 3
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/a583a496-ed36-490a-8f13-e5c674c7ef31)


  ```sh
  $ iops64 $(nproc) 4
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/6c825f26-5206-4330-a7a7-c038046b1628)

```sh
  $ flops64 $(nproc) 4
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f9b58ab6-b3dc-424e-9979-537275e892f1)



```sh
  $ iops64 $(nproc) 5
```
<img width="306" alt="Screenshot 2024-03-17 140839" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/79fcdd2c-5b7b-47f0-8c6a-f56b083ba5ac">

```sh
  $ flops64 $(nproc) 5
```
<img width="369" alt="Screenshot 2024-03-17 141047" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/91f7c473-5167-41f3-85f9-a630509c6e7a">

Analisis : IOPS digunakan untuk mengukur jumlah operasi masuk/keluar yang dapat dilakukan oleh sistem dalam satu detik. hasil dari setiap eksekusi yang dilakukan berbeda-beda hal ini dikarenkan perhitungan sistem dilakukan dalam hitungan detik saja dan hasil perhitungannya dipengaruhi oleh beberapa faktor yaitu jenis dan kecepatan media penyimpanan, sistem file, tingkat kerja (workload), dan arsitektur sistem. sedangkan FLOPS digunakan untuk mengukur jumlah operasi titik mengambang yang dapat dilakukan oleh sistem dalam satu detik. hasil dari setiap eksekusi yang dilakukan berbeda-beda hal ini dikarenkan perhitungan yang dilakukan sistem dilakukan dalam hitungan detik saja dan hasil perhitungannya dipengaruhi beberapa faktor yaitu arsitektur CPU, GPU, atau accelerator yang digunakan, serta algoritma yang diterapkan.

PERBANDINGAN EKSEKUSI DENGAN TEMAN

<img width="565" alt="Screenshot 2024-03-18 084806" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/59bf49a4-aec1-4617-9290-f59fb41115d3">

Analisa :
Dari plot perbandingan di atas, dapat dilihat bahwa Alyssa memiliki nilai rata-rata IOPS dan FLOPS yang lebih tinggi dibandingkan dengan Dyzka, Pelangi, dan Feby. Hal ini menunjukkan bahwa PC Alyssa cenderung memiliki performa yang lebih baik dalam menangani operasi input/output (IOPS) dan operasi floating point (FLOPS).

Kesimpulan yang bisa diambil adalah performa komputer dalam hal IOPS dan FLOPS sangat penting tergantung pada kebutuhan aplikasi atau tugas yang dijalankan. Semakin tinggi nilai IOPS dan FLOPS, semakin baik kemampuan komputer tersebut dalam menangani tugas-tugas yang memerlukan operasi input/output dan operasi floating point secara cepat dan efisien.


**JAWABAN NOMOR 4**

```sh
  $ su -l
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/01bcd7b1-0ade-4001-b632-ae4837cc9b4a)

ket : beralih ke akun pengguna root dan login

```sh
  $ apt update
```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/55f1ef6c-db92-4cde-a9ae-bf89518db9f3)

ket : mengupdate daftar paket dari repository yang terdaftar dalam sistem

```sh
  $ apt upgrade
```
<img width="356" alt="Screenshot 2024-03-16 151907" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/8fce6974-7277-40ce-9c9b-bb85982d2d24">

ket : mengupgrade paket yang sudah ter instal keversi terbaru

```sh
  $ apt install make
```
<img width="395" alt="Screenshot 2024-03-16 151959" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/9df1875f-94ae-4272-8fa9-582d4d99a5fc">

ket : menginstal make

```sh
  $ apt install git
```
<img width="420" alt="Screenshot 2024-03-16 152120" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/dab2afe0-5d68-4646-bba5-5cbc96ed91e6">

ket : menginstal git

```sh
  $ apt install gcc
```
<img width="421" alt="Screenshot 2024-03-16 152346" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/42b33095-753b-4fc1-a56e-5c21e1669375">

ket : menginstal gcc
  
