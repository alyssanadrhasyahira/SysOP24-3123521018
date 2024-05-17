## Tugas Threads


**1 Berikan tiga contoh pemrograman di mana *multithreading* memberikan kinerja yang lebih baik daripada solusi dengan satu *thread*.**

Jawaban:

a. Sebuah *web server* yang melayani setiap permintaan dalam *thread* terpisah.

b. Aplikasi yang diparalelkan seperti perkalian matriks, di mana bagian-bagian berbeda dari matriks dapat dikerjakan secara paralel.

c. Program GUI interaktif seperti *debugger*, di mana satu *thread* digunakan untuk memantau masukan pengguna, *thread* lain mewakili aplikasi yang berjalan, dan *thread* ketiga memantau kinerja.

**2 Apa dua perbedaan antara *user-level threads* dan *kernel-level threads*? Dalam situasi apa salah satu jenis lebih baik daripada yang lain?**

Jawaban:

a. *User-level threads* tidak dikenal oleh kernel, sedangkan kernel mengetahui *kernel threads*.

b. Pada sistem yang menggunakan pemetaan M:1 atau M:N, *user threads* dijadwalkan oleh pustaka *thread*, sedangkan kernel menjadwalkan *kernel threads*.

c. *Kernel threads* tidak perlu terkait dengan proses, sedangkan setiap *user thread* terkait dengan proses. *Kernel threads* umumnya lebih mahal untuk dikelola daripada *user threads* karena harus direpresentasikan dengan struktur data kernel.

**3 Jelaskan tindakan yang diambil oleh kernel untuk beralih konteks antara *kernel-level threads*.**

Jawaban:

Beralih konteks antara *kernel threads* biasanya melibatkan menyimpan nilai register CPU dari *thread* yang akan digantikan dan mengembalikan nilai register CPU dari *thread* baru yang akan dijadwalkan.

**4 Sumber daya apa yang digunakan ketika sebuah *thread* dibuat? Bagaimana perbedaannya dengan sumber daya yang digunakan ketika sebuah proses dibuat?**

Jawaban:

Karena *thread* lebih kecil daripada proses, pembuatan *thread* biasanya menggunakan lebih sedikit sumber daya daripada pembuatan proses. Membuat proses memerlukan alokasi *process control block* (PCB), struktur data yang cukup besar. PCB mencakup peta memori, daftar file terbuka, dan variabel lingkungan. Membuat *user thread* atau *kernel thread* melibatkan alokasi struktur data kecil untuk menyimpan set register, *stack*, dan prioritas.

**5 Anggaplah sistem operasi memetakan *user-level threads* ke kernel menggunakan model banyak-ke-banyak dan pemetaan dilakukan melalui LWPs. Selain itu, sistem memungkinkan pengembang untuk membuat *real-time threads* untuk digunakan dalam sistem *real-time*. Apakah perlu mengikat *real-time thread* ke LWP? Jelaskan.**

Jawaban:

Ya. Waktu sangat penting untuk aplikasi *real-time*. Jika sebuah *thread* ditandai sebagai *real-time* tetapi tidak terikat ke LWP, *thread* tersebut mungkin harus menunggu untuk terhubung ke LWP sebelum berjalan. Pertimbangkan jika *real-time thread* sedang berjalan (terikat ke LWP) dan kemudian memblokir (misalnya harus melakukan I/O, telah dipreempti oleh *real-time thread* dengan prioritas lebih tinggi, menunggu *mutual exclusion lock*, dll.). Selama *real-time thread* diblokir, LWP yang terikat dengannya telah diberikan ke *thread* lain. Ketika *real-time thread* dijadwalkan untuk berjalan lagi, ia harus menunggu untuk terhubung ke LWP. Dengan mengikat LWP ke *real-time thread*, Anda memastikan *thread* tersebut dapat berjalan dengan penundaan minimal setelah dijadwalkan.
