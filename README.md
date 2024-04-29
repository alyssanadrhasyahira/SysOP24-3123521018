## Perbedaan RISC dan CISC

>Reduced Instruction Set Computing (RISC) adalah arsitektur komputer yang mengutamakan kemudahan pengoperasian dan kecepatan dalam melakukan tugas-tugas tertentu.
Arsitektur RISC memiliki jumlah instruksi yang relatif sedikit dan setiap instruksi memiliki waktu eksekusi yang konstan.
Instruksi-instruksi pada arsitektur RISC terdiri dari operasi-operasi sederhana yang dapat dilakukan dengan cepat. Contoh arsitektur RISC yang populer adalah ARM dan MIPS.

>Complex Instruction Set Computing (CISC) adalah arsitektur komputer yang menggunakan instruksi-instruksi yang lebih kompleks dan beragam untuk melakukan tugas-tugas tertentu.
Instruksi-instruksi pada arsitektur CISC dapat melibatkan beberapa operasi yang lebih kompleks, seperti operasi matematika dan logika yang rumit. Contoh arsitektur CISC yang populer adalah x86 dan Intel Pentium.

## perbedaan
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

## FORK ORPHAN dan ZOMBIE

-clone ke repository https://github.com/ferryastika/operatingsystem.git

 ```
    $ su root
    $ sudo apt update
    $ sudo apt upgrade
    $ sudo apt install g++
 ```


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

  
> fork01.ccp

- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
 ```

- memasukkan kode fork.1
  
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

- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

> fork 2
- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
 ```

- memasukkan kode fork.2
  
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

- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

- untuk menghentikan proses tekan ctrl + c

> Orphan
- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
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

- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

- untuk menghentikan proses tekan ctrl + c

> Zombie

- Masuk ke compiler
  
 ```
   $ nano [namafile].cpp
 ```

- memasukkan kode fork.2
  
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

- kemudian simpan file dengan crlt + x
- mengubah file.cpp menjadi .exe

```
   $ g++ [namafile].cpp -o [namafile].exe
 ```

- kemudian menjalankan kode
  
```
$ ./[namafile].exe
 ```

- untuk menghentikan proses tekan ctrl + c







  



