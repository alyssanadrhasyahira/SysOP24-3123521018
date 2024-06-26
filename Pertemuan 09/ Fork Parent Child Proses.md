
## FORK ORPHAN dan ZOMBIE

- clone ke repository https://github.com/ferryastika/operatingsystem.git

 ```
    $ git clone  https://github.com/ferryastika/operatingsystem.git
 ```

  
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/5020504c-e560-4927-bad6-71bedaca9e5d)

ket : mengclonning ke repository



- Melakukan instalasi g++ sebelum menjalan fork, orphan dan zombie.

 ```
    $ su root
    $ sudo apt update
    $ sudo apt upgrade
    $ sudo apt install g++
 ```

l![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/f2b3ef64-b700-4160-b2b8-776a83b6e71d)

Ket : Sebelum menjalankan frok kita perlu melakukan instalasi compailer dengan cara memasukkan perintah $ apt install gcc g++. Dimana gcc untuk compiler bahasa c dan g++ untuk compiler bahasa c++


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
  
- mengompilasi fork01.cpp menjadi fork01 menggunakan g++
  
  ```
  $ g++ fork01.cpp -o fork01
  ```
- kemudian menjalankan kode
  
```
$ ./[namafile]
 ```

- Hasil

  ![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/b2032548-ca22-4c48-900c-23fa013c7039)



Analisa :
program tersebut menampilkan informasi bahwa proses dengan ID 2245 memiliki parent process dengan ID 2209 dan dimiliki oleh pengguna dengan UID 1000 dan melakukan perulangan sebanyak 3 kali.
  


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
- mengompilasi fork01.cpp menjadi fork01 menggunakan g++
  
  ```
  $ g++ fork02.cpp -o fork02
  ```
- kemudian menjalankan kode
  
```
$ ./[namafile]
 ```
![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/43f81027-b0a8-42d3-9abb-536915577f65)




Analisa : terlihat bahwa ada dua proses yang berjalan secara bersamaan, yaitu proses dengan ID 2254 dan proses dengan ID 2255. Pada proses pertama dengan ID 2254, nilai dari variabel x diatur menjadi 5. Pada proses kedua dengan ID 2254, nilai dari variabel x diatur menjadi 6 begitu juga dengan proses ID 2255. Pada akhirnya, terdapat dua proses yang berjalan secara bersamaan (proses ID 2254dan proses ID 2255). Dalam kedua proses ini, nilai dari variabel x diatur menjadi 7 dst.


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
- mengompilasi fork01.cpp menjadi fork01 menggunakan g++
  
  ```
  $ g++ fork03.cpp -o fork03
  ```
- kemudian menjalankan kode
  
```
$ ./[namafile]
 ```

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/77c100e0-5e88-4f8a-83b4-098047daf659)


Analisa : terlihat bahwa ada dua proses yang berjalan secara bergantian, yaitu proses dengan ID 2264 dan proses dengan ID 2265






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

- Ubah orphan.c menjadi orphan menggunakan compiler gcc
  ```
  $ gcc orphan.c -o orphan
  ```
- Jalankan kode dengan menggunakan perintah ./orphan

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/fd032f57-1ebd-4cef-bcf5-31e7bb7daddc)


Analisa : terlihat bahwa proses dengan ID 2274 merupakan proses yang menjadi parents dari proses dengan ID 2173.

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
- Ubah zombie.c menjadi zombie menggunakan compiler gcc
  ```
  $ gcc zombie.c -o zombie
  ```
- Jalankan kode dengan menggunakan perintah ./zombie
  

![image](https://github.com/alyssanadrhasyahira/SysOP24-3123521018/assets/160555565/07639e22-31f8-4c28-9d36-1b95d97a3389)


ket : hasil dari perintah $ ./zombie



- untuk menghentikan proses tekan ctrl + c

  ## Producer-Consumer problem

- Bound buffer adalah struktur data dengan kapasitas tetap yang digunakan untuk mentransfer data antara produsen dan konsumen dalam pemrograman konkuren, memastikan pengelolaan sumber daya yang efisien dan menghindari masalah sinkronisasi.
  
- Producer-Consumer problem melibatkan dua entitas: produsen yang menghasilkan data dan mengisi buffer, serta konsumen yang mengambil data dari buffer. Tujuannya adalah mencegah produsen mengisi buffer saat penuh dan konsumen mengambil saat kosong. Solusi biasanya menggunakan sinkronisasi untuk mengatur akses ke buffer.







  



