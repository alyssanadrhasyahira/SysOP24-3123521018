## TUGAS PENDAHULUAN:

## Jawablah pertanyaan-pertanyaan di bawah ini :

1. Apa yang dimaksud redirection?

Redirection adalah pembelokan yang dilakukan untuk standar input, output, dan error dan untuk mengalihkan file descriptor dari 0,1, dan 2

2. Apa yang dimaksud pipeline?

   Pipeline adalah suatu mekanisme pipa yang digunakan sebagai alat komunikasi antar proses.

3. Apa yang dimaksud perintah di bawah ini :
    echo, cat, more, sort, grep, wc, cut, uniq

- Echo digunakan untuk menampilkan output kelayar 
- Cat digunakan untuk menghasilkan output kelayar dan merupakan berasal dari 
  input sebuah keyboard 
- More Menurpakan perintah untuk mempaging halaman 
- Sort Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter
- Grep digunakan untuk menyaring masukannya dan menampilkan baris baris yang 
  hanya mengandung pola yang ditentukan, 
- WC digunakan untuk menghitung jumlah baris, kata dan karakter dari baris baris 
  masukan yang diberikan
- Cut digunakan untuk mengambil kolom tertentu dari baris baris masukannya yang ditentukan pada option -c
- Uniq digunakan untuk menghilangkan baris baris berurutan yang mengalami  
  duplokkasi, biasanya digabungkan dalam pipeline dengan sort 



## PERCOBAAN:

1. Login sebagai user.
2. Bukalah Console Terminal dan lakukan percobaan-percobaan di bawah ini. Perhatikan hasil setiap percobaan.
3. Selesaikan soal-soal latihan.


## Percobaan 1 : File descriptor

1. Output ke layar (standar output), input dari system (kernel)
    ```
    $ ps
    ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/d3175666-51ce-4fba-a62f-a2cc9e0a8fa5)

Analisis	: $ ps menampilkan informasi tentang proses yang berjalan pada sistem

2. Output ke layar (standar output), input dari keyboard (standard input)
   ```
    $ cat
    hallo, apa khabar
    hallo, apa khabar
    exit dengan ^d
    exit dengan ^d
    [Ctrl-d]
   ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/47d267bc-f669-43b7-8788-adcf039c75d9)

Analisis : $ cat menampilkan output kelayar sesuai inputan dari keybord

3. Input nama direktori, output tidak ada (membuat direktori baru), bila terjadi error maka tampilan error pada layar (standard error)
   ```
   $ mkdir mydir
   $ mkdir mydir **(Terdapat pesan error)**
   ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/3136eea0-d580-4feb-8ef3-ec5dcdb60bdf)

Analisis  :
$ mkdir berfungsi untuk membuat folder baru, pada percobaan ini folder dinamakan sebagai mydir. Satu nama folder hanya dapat dibuat sekali, sehingga saat dibuat yang kedua kalinya muncul pesan error

## Percobaan 2 : Pembelokan (redirection)
1. Pembelokan standar output
   ```
    $ cat 1> myfile.txt
    Ini adalah teks yang saya simpan ke file myfile.txt
   ```
   <img width="313" alt="Screenshot 2024-03-18 115955" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/149427ca-7cd3-4bd4-badc-dd948f88fff1">

Analisa	:
$ cat 1> myfile.txt berfungsi untuk membuat sebuah file, perintah. File akan tersimpan dengan nama myfile.txt 

2. Pembelokan standar input, yaitu input dibelokkan dari keyboard menjadi dari file
   ```
    $ cat 0< myfile.txt
    $ cat myfile.txt
   ```
<img width="271" alt="Screenshot 2024-03-18 120105" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/61d024f0-d88c-404d-b841-fd5e5f83e619">

Analisa	:

•	$ cat 0< myfile.txt berfungsi untuk melihat atau menampilkan isi file

•	$ cat myfile.txt Berfungsi menampilkan isi file


3. Pembelokan standar error untuk disimpan di file
   ```
    $ mkdir mydir (Terdapat pesan error)
    $ mkdir mydir 2> myerror.txt
    $ cat myerror.txt
   ```
   ![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/34f5c9ca-0745-4e74-ab5d-56a508fea963)

Analisis	:

•	$ mkdir mydir berfungsi untuk membuat sebuah folder, namun pada pengetikan perintah mkdir mydir akan terdapat pesan error “mkdir: makdir tidak dapat membuat direktory: file exist”. Hal ini disebabkan karena direktori mydir sudah ada,dan tidak bisa membuat direktori baru dengan nama direktori yang sudah ada (tidak boleh sama).	(Terdapat pesan error)

•	$ mkdir mydir 2> myerror.txtberfungsi untuk membuat sebuah file yang berisikan pesan error karena membuat direktori dengan nama yang sama 

•	$ cat myerror.txtMenampilkan isi file myerror.txt
 

4. Notasi 2>&1 : pembelokan standar error (2>) adalah identik dengan file descriptor 1.
   ```
    $ ls filebaru (Terdapat pesan error)
    $ ls filebaru 2> out.txt
    $ cat out.txt
    $ ls filebaru 2> out.txt 2>&
    $ cat out.txt
   ```
   ![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f68c46a1-78a8-4bb4-8dcb-2e39861e54cc)

Analisa :

•	$ ls filebaru Pada perintah ini akan terdapat pesan error, “ls: cannot acces filebaru : no such file or directory “.  hal ini disebabkan karena direktori filebaru tidak ada.

•	$ ls filebaru 2> out.txt berfungsi untuk membuat sebuah file yang berisikan pesan error karena melihat direktori yang tidak tersedia

•	$ cat out.txt menampilkan isi file out.txt

•	$ ls filebaru 2> out.txt 2>&1Pada perintah ini akan lansung mendapatkan perintah error karena melihat direktori yang tidak tersedia, pada perintah ini juga tidak akan membuat file karena dilakukan pembelokan dan menyebabkan perintah sama sepreti perintah melihat file yang tidak tersedia.

•	$ cat out.txt menampilkan isi file out.txt .

6. Notasi 1>&2 (atau >&2) : pembelokan standar output adalah sama dengan file descriptor 2 yaitu standar error
   ```
   $ echo “mencoba menulis file” 1> baru
   $ cat filebaru 2> baru 1>&
   $ cat baru
   ```
   ![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/76dcb181-3b39-49a8-9894-12206ac42836)

Analisis :

•	$ echo “mencoba menulis file” 1> baruberfungsi untuk membuat sebuah file yang berisi teks yang di beri tanda petik setelah perintah echo, dan nama file setelah perintah pembelokan 1>. 

•	$ cat filebaru 2> baru 1>&2 Pembelokan yang berfungsi menyimpan pesan error ke file baru

•	$ cat baru untuk menampilkan file yang tidak ada


   
6. Notasi >> (append)
   ```
   $ echo “kata pertama” > surat
   $ echo “kata kedua” >> surat
   $ echo “kata ketiga” >> surat
   $ cat surat
   $ echo “kata keempat” > surat
   $ cat surat
   ```
<img width="258" alt="Screenshot 2024-03-18 095630" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/89cbf524-9ffe-4ce8-85a4-bc6479b1ba1c">

analisa :

•	$ echo “kata pertama” > surat : dengan adanya tanda > maka teks akan disimpan pada file dengan nama yang kita inginkan

•	$ echo “kata kedua” >> surat : Perintah ini berfungsi menambah isi file pada file surat 

•	$ echo “kata ketiga” >> surat : Perintah ini berfungsi menambah isi file pada file surat 

•	$ cat surat berfungsi untuk menampilkan isi file 

•	$ echo “kata keempat” > surat : dengan adanya tanda > maka teks akan disimpan pada file dengan nama yang kita inginkan

•	$ cat surat berfungsi untuk menampilkan isi file

7. Notasi here document (<<++ .... ++) digunakan sebagai pembatas input dari keyboard. Perhatikan bahwa tanda pembatas dapat digantikan dengan tanda apa saja, namun harus sama dan tanda penutup harus diberikan pada awal baris
   ```
   $ cat <<++
   Hallo, apa kabar?
   Baik-baik saja?
   Ok!
   ++
   $ cat <<%%%
   Hallo, apa kabar?
   Baik-baik saja?
   Ok!
   %%%
   ```
<img width="198" alt="Screenshot 2024-03-18 100018" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/86adb6ee-7d95-429c-b409-9c307613c95a">

Analisis	:

•	$ cat <<++Digunakan sebagai pembatas input dari keyboard. Tanda pembatas dapat diganti dengan apa saja namun harus sama dan tanda penutup harus diberikan pada awal baris. setelah diketikan tanda pembatas teks yang diketikkan akan dimunculkan setelah menekan enter. 

•	$ cat <<%%% untuk mencetak ulang inputan sebelumya


8. Notasi – (input keyboard) adalah representan input dari keyboard. Artinya menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Perhatikan bahwa notasi “-“ berarti menyelipkan input dari keyboard
  ```
  $ cat myfile.txt – surat
  ```
<img width="275" alt="Screenshot 2024-03-18 100310" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/497ca155-9905-44b1-9cab-5253226ef527">

Analisis	:
$ cat myfile.txt – surat berfungsi untuk menampilkan isi dari dua file sekaligus, pertama akan ditampilkan isi file pertama, tekan ^d maka akan ditampilkan isi dari file kedua 

## Percobaan 3 : Pipa (pipeline)

1. Operator pipa (|) digunakan untuk membuat eksekusi proses dengan melewati data langsung ke data lainnya.
   ```
   $ who
   $ who | sort
   $ who | sort –r
   $ who > tmp
   $ sort tmp
   $ rm tmp
   $ ls –l /etc | more
   $ ls –l /etc | sort | more
   ```
<img width="425" alt="Screenshot 2024-03-18 101956" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/afc5dd65-b668-4354-afec-3c3492d99bf0">

<img width="379" alt="Screenshot 2024-03-18 102128" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/76041cfc-4eb4-4123-8b40-32cbb339daa0">

Analisis	:

•	$ who digunakan untuk melihat nama user yang sedang login dan urutan waktu login berdasarkan kronologi

•	$ who | sort digunakan untuk melihat nama yang sedang aktif dan mengurutkan file teks

•	$ who | sort –r perintah ini menjalankan tugas sekaligus, pada perintah ini akan di tampilkan informasi tentang user login dan menampilkan isi file pada r

•	$ who > tmp Perintah ini berfungsi untuk menyimpan informasi who pada sebuah file yang diberi nama tmp

•	$ sort tmp Melihat isi file pada tmp

•	$ rm tmp Perintah ini berfumgsi untuk menghapus sebuah file

•	$ ls –l /etc | more Melihat isi direktory secara lengkap, untuk mengehentikan proses melihat isi file dengan kunci pintas ctrl+c

•	$ ls –l /etc | sort | more Melihat dan mengurutkan isi direktory


   
2. Untuk membelokkan standart output ke file, digunakan operator ">"
   ```
   $ echo hello
   $ echo hello > output
   $ cat output
   ```
   <img width="235" alt="Screenshot 2024-03-18 102237" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/8a1f845c-ec61-4b9b-8397-a5a601ebe907">

Analisa :  

• $ echo hello membuat teks yang akan lansung di output pada layar

•	$ echo hello > output berfungsi untuk membuat dan lansung menyimpan file

•	$ cat output berfungsi untukMenampilkan isi file 

3. Untuk menambahkan output ke file digunakan operator ">>"
   ```
   $ echo bye >> output
   $ cat output
   ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/752ddeb8-6a2a-43fd-b4e9-00948c60032c)

Analisis :

•	$ echo bye >> output pembelokan ini berfungsi untuk membuat dan lansung menyimpan file

•	$ cat output berfungsi menampilkan isi file 

4. Untuk membelokkan standart input digunakan operator "<"
   ```
   $ cat < output
   ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/78dad1f0-da54-4644-bf6a-811d8403737f)

Analisis :
$ cat < output yang berfungsi untuk menampilkan isi file

5. Pembelokan standart input dan standart output dapat dikombinasikan tetapi tidak boleh menggunakan nama file yang sama sebagai standart input dan output.
   ```
   $ cat < output > out
   $ cat out
   $ cat < output >> out
   $ cat out
   $ cat < output > output
   $ cat output
   $ cat < out >> out (Proses tidak berhenti)
   [Ctrl-c]
   $ cat out
   ```
<img width="203" alt="Screenshot 2024-03-18 103302" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/a98e85c6-b61a-4f3a-8573-39c907007085">

Analisa :

•	$ cat < output > out berfungsi untuk membuat sebuah file baru dengan isi file yang terdapat pada file yang sudah ada, dengan kata lain mengcopy file dan lansung me rename nama dari file tersebut. Pada pembelokan ini tidak dibenarkan membuat file baru dengan nama file yang sama dengan nama file yang akan di ambil isi filenya

•	$ cat out menampilkan isi file out 

•	$ cat < output >> out berfungsi untuk menambah kembali isi file out yang berasal dari isi file output

•	$ cat out menampilkan isi file out

•	$ cat < output > output berfungsi untuk membuat sebuah file baru dengan isi file yang terdapat pada file yang sudah ada, dengan kata lain mengcopy file dan lansung me rename nama dari file tersebut. Pada pembelokan ini tidak dibenarkan membuat file baru dengan nama file yang sama dengan nama file yang akan di ambil isi filenya

•	$ cat output menampilkan isi file 

•	$ cat < out >> out	(Proses tidak berhenti)
[Ctrl-c] Berfungsi untuk menduplikatkan isi file tanpa berhenti. Untuk menghentikan proses dengan kunci pintas ^c (ctrl+c) 

•	$ cat out menampilkan isi file

## Percobaan 4 : Filter
1. Pipa juga digunakan untuk mengkombinasikan utilitas sistem untuk membentuk fungsi yang lebih kompleks
   ```
    $ w –h | grep <user>
    $ grep <user> /etc/passwd
    $ ls /etc | wc
    $ ls /etc | wc –l
    $ cat > kelas1.txt
    Badu
    Zulkifli
    Yulizir
    Yudi
    Ade
    [Ctrl-d]
    $ cat > kelas2.txt
    Budi
    Gama
    Asep
    Muchlis
    [Ctrl-d]
    $ cat kelas1.txt kelas2.txt | sort
    $ cat kelas1.txt kelas2.txt > kelas.txt
    $ cat kelas.txt | sort | uniq
   ```
<img width="333" alt="Screenshot 2024-03-18 103914" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/773eb321-7dc0-471e-a1f3-a0cabf4e27f7">

Analisa : 

•	$ w –h | grep <user> Mencari kata pada user

•	$ grep <user> /etc/passwd Mencari kata yang sama dengan user pada direktori etc/passwd

•	$ ls /etc | wc Menghitung lansung jumlah kata jumlah baris yang terdapat pada direktory /etc

•	$ ls /etc | wc –l Melihat suatu jumlah

•	$ cat > kelas1.txt 

Badu
Zulkifli
Yulizir 
Yudi 
Ade 
[Ctrl-d]
Perintah ini berfungsi untuk membuat sebuah file.

## LATIHAN:

1. Lihat daftar secara lengkap pada direktori aktif, belokkan tampilan standard output   ke file baru.
<img width="270" alt="Screenshot 2024-03-18 104314" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/2645396f-2601-4df9-8bc7-ead67aff61a1">

analisis : 

* $ ls -l > file.txt digunakan untuk menyalurkan output dari perintah ls -l ke dalam sebuah file bernama file.txt

* $ cat file.txt digunakan untuk menampilkan isi dari file yang disebut file.txt

2. Lihat daftar secara lengkap pada direktori /etc/passwd, belokkan tampilan standard output ke file baru tanpa menghapus file baru sebelumnya.
<img width="284" alt="Screenshot 2024-03-18 104424" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/3b96fbf9-4cb5-4ad8-a9f8-c9e04300f141">

Analisis :

*$ cat /etc/passwd >> file.txt digunakan untuk menambahkan isi dari file /etc/passwd ke dalam file yang sudah ada bernama file.txt

*$ cat file.txt digunakan untuk menampilkan isi dari file yang disebut file.txt di terminal. 


3. Urutkan file baru dengan cara membelokkan standard input.
<img width="394" alt="Screenshot 2024-03-18 104538" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/185d6bec-8292-4c5a-bac0-f408fa31cb72">

Analisis :
$ sort < file.txt digunakan untuk mengurutkan baris-baris dalam file file.txt dan menampilkannya di terminal.

4. Urutkan file baru dengan cara membelokkan standard input dan standard output ke file baru.urut.
<img width="313" alt="Screenshot 2024-03-18 104603" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/91ffb149-1df7-4851-aa81-a65496cf60fe">

analisis : $ cat baru.urut dingunakan utuk melihat isi file baru.urut. dari hasil tersebut file tidak ditemukan.

5. Buatlah direktori latihan 2 sebanyak 2 kali dan belokkan standard error ke file rmdirerror.txt.
<img width="313" alt="Screenshot 2024-03-18 104603" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/731c125f-7906-4718-954d-a7f38d25ffaf">

analisa : 

* mkdir latihan2: Perintah ini membuat direktori bernama "latihan2".

*  mkdir latihan2 2> myerror.txt digunakan untuk membuat direktori baru bernama "latihan2" dan mengalihkan pesan kesalahan yang dihasilkan (jika ada) ke dalam file yang disebut "myerror.txt".

6. Urutkan kalimat berikut :
   ```
   Jakarta
   Bandung
   Surabaya
   Padang
   Palembang
   Lampung
   ```
  Dengan menggunakan notasi **here document (<@@@ ...@@@)** . [HINT](https://www.geeksforgeeks.org/how-to-use-here-document-in-bash-programming/)

<img width="219" alt="Screenshot 2024-03-18 104836" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/64170f4a-334b-4f97-8087-785486bb3fc9">

analisa : untuk mengurutkan kalimat kita bisa menggunakan notasi <<@@@...@@@

7. Hitung jumlah baris, kata dan karakter dari file baru.urut dengan menggunakan filter dan tambahkan data tersebut ke file baru.

<img width="343" alt="Screenshot 2024-03-18 105025" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/37c766d3-d66f-4ba3-8843-73b86473bef9">

analisa :

* $ cat baru.urut | wc digunakan untuk menghitung jumlah baris, kata, dan byte dalam file "baru.urut". 

* $ cat baru.urut | wc -l digunakan untuk menghitung jumlah baris dalam file "baru.urut".

* $ cat baru.urut | wc -c digunakan untuk menghitung jumlah byte dari isi file "baru.urut".

* $ cat baru.urut | wc -w digunakan untuk menghitung jumlah kata dalam file "baru.urut".

dalam latihan tersebut tidak ditemikan file baru.urut sehingga semua hasilnya 0

8. Gunakan perintah di bawah ini dan perhatikan hasilnya.
   ```
    $ cat > hello.txt
    dog cat
    cat duck
    dog chicken
    chicken duck
    chicken cat
    dog duck
    [Ctrl-d]
    $ cat hello.txt | sort | uniq
    $ cat hello.txt | grep “dog” | grep –v “cat”
   ```
<img width="309" alt="Screenshot 2024-03-18 105453" src="https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/b141c51e-7084-4c8a-a4d3-0d6d233c2eff">

Analisa : 
* $ cat > hallo.txt digunakan untuk membuat file "hello.txt"
  
* $ cat hello.txt | sort | uniq digunakan untuk memproses isi dari file "hello.txt" dengan melakukan tiga operasi
  
* $ cat hello.txt | grep "dog" | grep -v "cat" digunakan untuk mengambil baris-baris yang mengandung kata "dog" dan kemudian menghilangkan baris-baris yang juga mengandung kata "cat".
  
## LAPORAN RESMI:

1. Analisa hasil percobaan 1 sampai dengan 4, untuk setiap perintah jelaskan    tampilannya.
2. Kerjakan latihan diatas dan analisa hasilnya
3. Berikan kesimpulan dari praktikum ini.
Kesimpulan
Dari Latihan ini saya bisa mengenal fungsi-fungsi dari perintah-perintah dasar linux selain itu saya juga bisa mempraktekkan serta membuktikan secara langsung fungsi dari perintah dasar linux. Dan saya dapat mengetahui bahwa penggunaan Operasi Input dan Output proses dapat dipahami dengan mudah, sesuai dengan kebutuhan.

   
