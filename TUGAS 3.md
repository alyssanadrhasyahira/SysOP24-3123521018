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

## Contoh penggunaan 
perintah dalam bahasa assembly sebagai berikut:

LOAD [10]

ADD [11]

STORE [12]

dapat diartikan sebagai berikut:

1. LOAD: Ambil instruksi dari memori 10 ke akumulator.

2. ADD: Tambahkan isi dari memori 11 dengan nilai yang ada di akumulator.

3. STORE: Simpan hasil penjumlahan yang ada di akumulator ke memori 12

## ilustrasi dalam CPU
* CPU terdiri dari Control Unit, Accumulator, dan Arithmetic Logic Unit (ALU).
* Register lain seperti Program Counter (PC), Current Instruction Register (CIR), Memory Address Register (MAR), dan Memory Data Register (MDR) juga ada.

## langkah-langkah dalam CPU
* Program Counter menyimpan alamat instruksi selanjutnya.
* Alamat memori disimpan di MAR, isi dari alamat memori dimuat di MDR, dan instruksi disimpan di CIR. Program Counter bertambah 1.
* Instruksi didekode dan proses dilanjutkan sesuai instruksi.
* Proses berlanjut hingga program selesai dieksekusi.






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

https://docs.google.com/spreadsheets/d/1CVZH3rk8T0rY-0BirmPdzeeieXzrKRjIVq6fb6Yu5GQ/edit#gid=0


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
  
