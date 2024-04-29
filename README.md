## Perbedaan RISC dan CISC

>Reduced Instruction Set Computing (RISC) adalah arsitektur komputer yang mengutamakan kemudahan pengoperasian dan kecepatan dalam melakukan tugas-tugas tertentu.
Arsitektur RISC memiliki jumlah instruksi yang relatif sedikit dan setiap instruksi memiliki waktu eksekusi yang konstan.
Instruksi-instruksi pada arsitektur RISC terdiri dari operasi-operasi sederhana yang dapat dilakukan dengan cepat. Contoh arsitektur RISC yang populer adalah ARM dan MIPS.

>Complex Instruction Set Computing (CISC) adalah arsitektur komputer yang menggunakan instruksi-instruksi yang lebih kompleks dan beragam untuk melakukan tugas-tugas tertentu.
Instruksi-instruksi pada arsitektur CISC dapat melibatkan beberapa operasi yang lebih kompleks, seperti operasi matematika dan logika yang rumit. Contoh arsitektur CISC yang populer adalah x86 dan Intel Pentium.

**perbedaan**
1. Jumlah instruksi

    RISC memiliki jumlah instruksi yang lebih sedikit dibandingkan dengan        CISC.Ini membuat RISC lebih mudah diimplementasikan dan lebih cepat          dalampemrosesan instruksi.

2. Kompleksitas instruksi

   Instruksi dalam CISC lebih kompleks dibandingkan dengan RISC. Ini memungkinkan CISC untuk menyelesaikan tugas yang lebih kompleks dalam waktu yang lebih singkat. Namun,   kompleksitas instruksi ini juga membuat CISC membutuhkan waktu lebih lama untuk menjalankan setiap instruksi.

3. Sistem pipelining
   
    RISC menggunakan sistem pipelining, yang memungkinkan beberapa instruksi diproses secara bersamaan. Ini meningkatkan efisiensi pemrosesan instruksi dan meningkatkan kecepatan komputer secara keseluruhan. CISC juga dapat menggunakan sistem pipelining, tetapi tidak seefisien RISC.

5. Perangkat keras
   
    CISC membutuhkan lebih banyak perangkat keras dibandingkan dengan RISC karena kompleksitas instruksinya. Ini membuat CISC lebih mahal untuk diimplementasikan dan kurang efisien dalam hal penggunaan daya.

7. Aplikasi
   
    RISC lebih cocok untuk aplikasi yang membutuhkan pemrosesan data dalam jumlah besar dalam waktu yang singkat, seperti database dan server web. Sementara itu, CISC lebih cocok untuk aplikasi yang membutuhkan pemrosesan data kompleks, seperti pengolahan gambar dan video.

## Hubungan Arsitektur CPU dengan Arsitektur OS

>Arsitektur CPU dan arsitektur sistem operasi (OS) saling terkait dalam pengaturan dan penggunaan sumber daya komputer. CPU, sebagai otak dari sistem, menjalankan instruksi dan mengelola eksekusi program. Arsitektur CPU menentukan instruksi yang dapat dijalankan oleh CPU dan cara CPU berkomunikasi dengan perangkat keras lainnya.

>Sementara itu, arsitektur sistem operasi berperan dalam mengelola sumber daya komputer secara keseluruhan, termasuk memori, perangkat masukan/keluaran, dan proses. OS memfasilitasi interaksi antara perangkat keras dan perangkat lunak dengan menyediakan antarmuka yang mudah digunakan bagi pengguna dan aplikasi.

>Keduanya saling bergantung: arsitektur CPU mempengaruhi kemampuan OS dalam menjalankan instruksi dan mengelola sumber daya, sementara OS memanfaatkan fitur-fitur arsitektur CPU untuk mengoptimalkan kinerja sistem secara keseluruhan. Sebagai contoh, OS harus dapat memahami instruksi yang didukung oleh CPU untuk menjalankan program dengan benar, sementara CPU harus mendukung fitur-fitur yang dibutuhkan oleh OS untuk menjalankan fungsi manajemen sumber daya yang efisien.




## FORK ORPHAN dan ZOMBIE

- clone ke repository https://github.com/ferryastika/operatingsystem.git

 ```
    $ git clone  https://github.com/ferryastika/operatingsystem.git
 ```

  
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/5020504c-e560-4927-bad6-71bedaca9e5d)



- Melakukan instalasi g++ sebelum menjalan fork, orphan dan zombie.

 ```
    $ su root
    $ sudo apt update
    $ sudo apt upgrade
    $ sudo apt install g++
 ```

l![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f2b3ef64-b700-4160-b2b8-776a83b6e71d)


- Login kembali menjadi user

 ```
   $ login [username]
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/6e63a294-1876-4e98-b936-32f610ec6364)

- Masuk ke cd operatingsystem
  
 ```
   $ cd operatingsystem
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/6454ae23-b11a-459c-9e7c-5f519aaa457e)
  


> fork01.ccp

- Masuk ke compailer
  
 ```
   $ nano [namafile].cpp
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/fedf2a5b-413f-4ba7-a666-51454db6d8f7)


- memasukkan kode fork01.cpp
  
 ```
   using namespace std;

#include <iostream>
#include <sys/types.h>
#include <unistd.h>


/* getpid() adalah system call yg dideklarasikan pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t mypid;
	uid_t myuid;
	for (int i = 0; i < 3; i++) {
		mypid = getpid();
		cout << "I am process " << mypid << endl;
		cout << "My parent process ID is " << getppid() << endl;
		cout << "The owner of this process has uid " << getuid()
	<< endl;
/* sleep adalah system call atau fungsi library
yang menghentikan proses ini dalam detik
*/
	sleep(3);
	}
return 0;
}
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/17f2ea71-123f-4fb2-ac68-9ea843669864)

- kemudian simpan file dengan crlt + x

- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/345612fd-e454-4ba8-b870-9d6a426bbb00)


- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

- Hasil
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/b4e57378-6c6a-4493-94cc-60f43e1344a8)

  


> fork02.cpp
- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/6c57a340-c4fb-46fb-82af-bb8613ebabc6)


- memasukkan kode fork02.cpp
  
 ```
 #include <iostream>
#include <sys/types.h>
#include <unistd.h>
using namespace std;


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	int x = 5;
	childpid = fork();

	while (1) {
		cout << "This is process ID" << getpid() << endl;
		cout << "In this process the value of x becomes " << x << endl;	
		sleep(2);
		x++;
	}
	return 0;
}
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f9ecc84e-4e9f-4c95-a48d-2cbc19119c77)


- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/4a598364-e0df-4543-946b-7c3fd35a395e)


- untuk menghentikan proses tekan ctrl + c

  > fork03.cpp
- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
 ```

- memasukkan kode fork03.cpp
  
 ```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	childpid = fork();
	for (int i = 0; i < 5; i++) {
		cout << "This is process " << getpid() << endl;
		sleep(2);
	}
	return 0;
}
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/810acf5b-6c39-421e-8c01-4de755ed9ed6)

- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/6a618897-df13-4549-9e2d-ae8f1fc4749f)






> Orphan
- Masuk ke compiler
  
 ```
   $ nano [namafile].c
 ```

- memasukkan kode Orphan
  
 ```
 #include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
	// fork() Create a child process

	int pid = fork();
	if (pid > 0)
	{
		//getpid() returns process id
		// while getppid() will return parent process id
		printf("Parent process\n");
		printf("ID : %d\n\n",getpid());
	}
	else if (pid == 0)
	{
		printf("Child process\n");
		// getpid() will return process id of child process
		printf("ID: %d\n",getpid());
		// getppid() will return parent process id of child process
		printf("Parent -ID: %d\n\n",getppid());

		sleep(10);

		// At this time parent process has finished.
		// So if u will check parent process id 
		// it will show different process id
		printf("\nChild process \n");
		printf("ID: %d\n",getpid());
		printf("Parent -ID: %d\n",getppid());
	}
	else
	{
		printf("Failed to create child process");
	}
	
	return 0;
}

/* https://www.includehelp.com/c-programs/orphan-process.aspx */
 ```

![Screenshot 2024-04-29 194207](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/9353d5a8-bdb4-4825-8f9e-fa4e9e0b2be0)


- kemudian simpan file dengan crlt + x

- mengubah file.c menjadi .exe

```
   $ g++ [namafile].c -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

![Screenshot 2024-04-29 194408](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/09819c8b-03c0-4c19-9839-18a04bcd47e3)

- untuk menghentikan proses tekan ctrl + c

> Zombie

- Masuk ke compiler
  
 ```
   $ nano [namafile].c
 ```

- memasukkan kode zombie
  
 ```
 #include <iostream>
#include <sys/types.h>
#include <unistd.h>
using namespace std;


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	int x = 5;
	childpid = fork();

	while (1) {
		cout << "This is process ID" << getpid() << endl;
		cout << "In this process the value of x becomes " << x << endl;	
		sleep(2);
		x++;
	}
	return 0;
}
 ```

![Screenshot 2024-04-29 194838](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/e038c969-effb-4b52-a234-7d400ea0c204)



- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].c -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

![Screenshot 2024-04-29 200627](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/25dffe74-426e-47e7-b9d8-c2f1f807080a)



- untuk menghentikan proses tekan ctrl + c

  ## Producer-Consumer problem

- Bound buffer adalah struktur data dengan kapasitas tetap yang digunakan untuk mentransfer data antara produsen dan konsumen dalam pemrograman konkuren, memastikan pengelolaan sumber daya yang efisien dan menghindari masalah sinkronisasi.
  
- Producer-Consumer problem melibatkan dua entitas: produsen yang menghasilkan data dan mengisi buffer, serta konsumen yang mengambil data dari buffer. Tujuannya adalah mencegah produsen mengisi buffer saat penuh dan konsumen mengambil saat kosong. Solusi biasanya menggunakan sinkronisasi untuk mengatur akses ke buffer.







  



