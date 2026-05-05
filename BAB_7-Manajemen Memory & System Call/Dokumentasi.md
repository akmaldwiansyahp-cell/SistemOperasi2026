# Laporan Sistem Operasi Jobsheet 10

## Praktikum 10.1

1. Melihat penggunaan memori

Kode Program:<br>
```markdown
free -h
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ free -h
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       335Mi       2.4Gi       1.0Mi       306Mi       2.6Gi
Swap:             0B          0B          0B
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ 
```

2. Melihat detail memori kernel

Kode Program:<br>
```markdown
cat / proc / meminfo | head -n 20
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ cat /proc/meminfo | head -n 20
MemTotal:        3043724 kB
MemFree:         2540020 kB
MemAvailable:    2700096 kB
Buffers:           18936 kB
Cached:           277784 kB
SwapCached:            0 kB
Active:           280252 kB
Inactive:          49364 kB
Active(anon):      42700 kB
Inactive(anon):        0 kB
Active(file):     237552 kB
Inactive(file):    49364 kB
Unevictable:       27316 kB
Mlocked:           27316 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Zswap:                 0 kB
Zswapped:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis<br>
1. Hitung persentase memori tersedia: available / total × 100%. Jika hasilnya di bawah 10%, sistem mulai kekurangan memori.
**Jawab**<br>
2.6 / 2.9 x 100% = 89%. Ini di atas 10%, jadi kondisi normal.
2. Pada baris Swap, apakah kolom used bernilai 0? Jika lebih dari 0, kernel sudah pernah memindahkan data ke disk karena RAM tidak cukup.
**Jawab**<br>
Ya, kolom used adalah 0.0B. Ini berarti kernel tidak pernah memindahkan data ke disk karena RAM masih cukup.
3. Perhatikan field Cached dan Buffers di /proc/meminfo. Nilai ini sesuai dengan kolom buff/cache pada free -h.
**Jawab**<br>
Nilai Cached dan Buffers di /proc/meminfo jika dijumlahkan akan mendekati nilai buff/cache pada free -h.

## Studi Kasus 10.1

1. Pemeriksaan awal kondisi memori

Kode Program:<br>
```markdown
free -h
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ free -h
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       360Mi       2.4Gi       1.0Mi       350Mi       2.6Gi
Swap:             0B          0B          0B
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

2. Pemantauan real-time dengan top

Kode Program:<br>
```markdown
top
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ top
top - 11:01:33 up  1:43,  2 users,  load average: 0.01, 0.03, 0.00
Tasks: 124 total,   1 running, 123 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us, 50.0 sy,  0.0 ni, 50.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   2972.4 total,   2412.8 free,    360.3 used,    350.5 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   2612.1 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0   22116  13288   9560 S   0.0   0.4   0:02.75 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.11 kthreadd
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_g
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_p
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns
     11 root      20   0       0      0      0 I   0.0   0.0   0:00.06 kworker/u6:0-ext4-rsv-conversion
     12 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_pe
     13 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread
     15 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.42 ksoftirqd/0
     17 root      20   0       0      0      0 I   0.0   0.0   0:01.33 rcu_preempt
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.50 migration/0
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1
     23 root      rt   0       0      0      0 S   0.0   0.0   0:00.66 migration/1
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.06 ksoftirqd/1
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis:<br>
1. Apakah nilai available sangat kecil (misalnya di bawah 200 MB pada server dengan RAM 2 GB)? Jika ya, server kemungkinan kekurangan memori.
**Jawab**<br>
Tidak, nilai available masih termasuk banyak sekitar 89%
2. Apakah kolom used pada baris Swap lebih dari 0? Jika ya, kernel sedang menggunakan swap, yang berarti performa menurun.
**Jawab**<br>
Tidak, karena memory yang tersedia masih ada, jadi tidak perlu melakukan swap
3. Di tampilan top, proses apa yang memiliki %MEM terbesar? Proses tersebut menjadi kandidat utama penyebab lambatnya server.
**Jawab**<br>
Yang memiliki %MEM terbesar adalah Multipathd

## Praktikum 10.2

1. Melihat statistik memori virtual

Kode Program:<br>
```markdown
vmstat 1 5
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ vmstat 1 5
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 1  0      0 2472628  21672 337408    0    0    50     7  944    0  0  4 96  0  0  0
 0  0      0 2472628  21672 337432    0    0     0     0  949  125  0  3 97  0  0  0
 0  0      0 2472628  21672 337432    0    0     0     0  921  104  0  2 98  0  0  0
 0  0      0 2472628  21672 337432    0    0     0     0  814   59  0  3 97  0  0  0
 0  0      0 2472628  21672 337432    0    0     0     0  822   64  0  2 98  0  0  0
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis:<br>
1. Amati nilai si dan so pada kelima baris. Pada sistem normal dengan RAM cukup, kedua nilai ini selalu 0.
2. Jika nilai si atau so sesekali muncul lebih dari 0, artinya pernah ada aktivitas swap. Ini masih wajar jika tidak terus-menerus.
3. Jika si dan so terus-menerus lebih dari 0, sistem dalam kondisi memory pressure serius — performa turun drastis karena akses disk jauh lebih lambat dari RAM.
4. Perhatikan juga kolom free (RAM kosong) dan buff (buffer) untuk memahami kondisi keseluruhan RAM saat itu.

## Praktikum 10.3

1. Membuat swap file 512MB

Kode Program:<br>
```markdown
sudo fallocate -l 512M/swapfile-week10
```

2. Mengamankan permission swap file

Kode Program:<br>
```markdown
sudo chmod 600 /swapfile-week10
```

3. Memformat dan mengaktifkan swap

Kode Program:<br>
```markdown
sudo mkswap /swapfile-week10
sudo swapon /swapfile-week10
```

4. Verifikasi swap aktif

Kode Program:<br>
```markdown
swapon --show
free -h
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ swapon --show
free -h
NAME             TYPE SIZE USED PRIO
/swapfile-week10 file 512M   0B   -2
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       392Mi       2.0Gi       1.1Mi       710Mi       2.5Gi
Swap:          511Mi          0B       511Mi
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

5. Melihat dan mengubah swappiness

Kode Program:<br>
```markdown
cat /proc/sys/vm/swappiness
sudo sysctl vm.swappiness=10
cat /proc/sys/vm/swappiness
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ cat /proc/sys/vm/swappiness
sudo sysctl vm.swappiness=10
cat /proc/sys/vm/swappiness
60
[sudo] password for pluto:
vm.swappiness = 10
10
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis:<br>
1. Berapa nilai swappiness default? Apa artinya bagi perilaku kernel dalammenggunakan swap?
**Jawab**<br>
Default biasanya 60. Nilai ini berarti kernel akan cukup agresif dalam menggunakan swap. Kernel akan mulai memindahkan data ke swap saat RAM mulai terisi, meskipun masih ada RAM bebas.
2. Setelah diubah ke 10, konfirmasi nilai berubah pada output cat kedua. Apa dampak nilai 10 terhadap penggunaan swap dibanding nilai 60?
**Jawab**<br>
Nilai 10 membuat kernel sangat tidak agresif menggunakan swap. Kernel akan menggunakan swap hanya jika RAM benar-benar sangat penuh (hampir habis). Ini lebih disarankan untuk server agar performa I/O tetap optimal.
3. Apakah entri /swapfile-week10 muncul di swapon –show? Jika tidak, pastikan Langkah 2 (chmod 600) sudah dijalankan sebelum Langkah 3.
**Jawab**<br>
Ya, harus muncul. Jika tidak, pastikan urutan chmod dijalankan sebelum mkswap.

## Praktikum 10.4

1. Proses dengan memori terbesar

Kode Program:<br>
```markdown
ps aux --sort=-%mem | head
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ ps aux --sort=-%mem | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root        1848  3.4  4.3 370844 130900 ?       Sl   11:37   3:07 /usr/bin/python3 /usr/bin/unattended-upgrade --download-only
root        1113  0.0  1.4 691532 43912 ?        Ssl  09:35   0:10 /usr/libexec/fwupd/fwupd
root         384  0.0  0.8 288988 27324 ?        SLsl 09:18   0:10 /sbin/multipathd -d -s
root         684  0.0  0.7 109640 23072 ?        Ssl  09:18   0:01 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
root        1314  0.0  0.5  50564 15576 ?        S<s  10:14   0:00 /usr/lib/systemd/systemd-journald
root         638  0.0  0.4 468968 13524 ?        Ssl  09:18   0:01 /usr/libexec/udisks2/udisksd
root           1  0.0  0.4  22116 13336 ?        Ss   09:17   0:07 /sbin/init splash noprompt noshell automatic-ubiquity
systemd+     463  0.0  0.4  21584 13064 ?        Ss   09:18   0:00 /usr/lib/systemd/systemd-resolved
root         706  0.0  0.4 392100 12896 ?        Ssl  09:18   0:00 /usr/sbin/ModemManager
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

2. Monitoring real-time

Kode Program:<br>
```markdown
top
```

Analisis:<br>
1. Proses apa yang berada di urutan pertama? Catat nilai %MEM dan RSS-nya.
**Jawab**<br>
Yang merupakan urutan pertama adalah root dengan penggunaan %MEM = 4.3 dan RSS = 130900
2. Konversikan RSS dari KB ke MB (bagi 1024). Misalnya, RSS=524288 berarti proses menggunakan 512 MB RAM Apakah wajar untuk jenis program tersebut?
**Jawab**<br>
RSS = 130900, maka yang digunakan sebesar 127 MB RAM
3. Mengapa VSZ selalu lebih besar dari RSS pada proses yang sama?
**Jawab**<br>
VSZ (Virtual Set Size) adalah total memori virtual yang dialokasikan untuk proses, termasuk memori yang di-swap, library yang di-share, dan memori yang dialokasikan tapi belum digunakan. RSS (Resident Set Size) hanya bagian dari memori virtual yang sedang berada di RAM. VSZ hampir selalu lebih besar karena sebuah proses bisa meminta memori lebih dulu daripada yang benar-benar dipakai.
4. Apakah urutan proses di ps konsisten dengan tampilan top saat diurutkan berdasarkan %MEM?
**Jawab**<br>
Ya sama

## Praktikum 10.5

1. Pindah ke direktori dan buka nano

Kode Program:<br>
```markdown
cd ~/praktikum-os/week10-memory
nano monitor-memori.sh
```

2. Isi file monitor-memori.sh

Kode Program:<br>
```markdown
#!/bin/bash
set -euo pipefail
THRESHOLD=20
echo "=== Monitor Memori ==="
date
echo
free -h
echo
AVAIL=$ (free | awk '/Mem/ {printf "%d", $7/$2*100}')
if [ "$AVAIL" -lt "$THRESHOLD" ]; then
echo "PERINGATAN: Memori tersedia hanya ${AVAIL}%!"
else
echo "Status: Memori tersedia ${AVAIL}% (normal)"
fi
echo
echo "--- 5 Proses Memori Tertinggi ---"
ps aux --sort=-%mem | head -n 6 | tail -n 5
```

3. Menjalankan script monitor

Kode Program:<br>
```markdown
chmod +x monitor-memori.sh
bash monitor-memori.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ chmod +x monitor-memori.sh
bash monitor-memori.sh
=== Monitor Memori ===
Tue May  5 01:03:09 PM UTC 2026

               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       350Mi       2.5Gi       1.0Mi       242Mi       2.6Gi
Swap:             0B          0B          0B

Status: Memori tersedia 88% (normal)

--- 5 Proses Memori Tertinggi ---
root         377  0.0  0.8 288988 27324 ?        SLsl 12:51   0:00 /sbin/multipathd -d -s
root         689  0.0  0.7 109640 23100 ?        Ssl  12:51   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
root         326  0.0  0.5  50456 16256 ?        S<s  12:51   0:00 /usr/lib/systemd/systemd-journald
root         646  0.0  0.4 468972 13500 ?        Ssl  12:51   0:00 /usr/libexec/udisks2/udisksd
root           1  0.1  0.4  22024 13200 ?        Ss   12:51   0:00 /sbin/init splash noprompt noshell automatic-ubiquity
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

1. Variabel THRESHOLD=20 menetapkan batas persentase. Perintah free | awk ’/Mem/ {printf "%d", $7/$2*100}’ mengambil kolom ke-7 (available) dibagi kolom ke-2 (total) dari baris Mem, lalu dikalikan 100 untuk menghasilkan persentase bilangan bulat.
**Jawab**<br>
- free: Mencetak penggunaan memori.
- |: Pipa, mengirim output free ke awk.
- awk '/Mem/ ...': awk mencari baris yang mengandung kata "Mem".
- $7/$2*100: Kolom ke-7 dari baris "Mem" adalah memori available, kolom ke-2 adalah total. Hasil bagi dikali 100.
- printf "%d": Mencetak hasil sebagai bilangan bulat.
2. Kondisi if [ "$AVAIL" -lt "$THRESHOLD" ] bernilai benar jika persentase memori tersedia di bawah 20.
**Jawab**<br>
Kondisi if [ "$AVAIL" -lt "$THRESHOLD" ] memeriksa apakah persentase memori tersedia kurang (-lt) dari batas (20).
3. Ubah THRESHOLD menjadi 90 dan jalankan ulang. Apa yang berubah pada output? Mengapa demikian?
**Jawab**<br>
Ubah THRESHOLD menjadi 90. Karena persentase memori tersedia (67.5%) akan kurang dari 90, maka kondisi if bernilai benar dan script akan mencetak peringatan meskipun sistem normal.

## Studi Kasus 10.2

1. Membuat file konfigurasi contoh

Kode Program:<br>
```markdown
mkdir -p ~/praktikum-os/week10-memory/syscall-case
cd ~/praktikum-os/week10-memory/syscall-case
echo "PORT=8080" > app.conf
ls -l app.conf
cat app.conf
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ mkdir -p ~/praktikum-os/week10-memory/syscall-case
cd ~/praktikum-os/week10-memory/syscall-case
echo "PORT=8080" > app.conf
ls -l app.conf
cat app.conf
-rw-rw-r-- 1 pluto pluto 10 May  5 13:12 app.conf
PORT=8080
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$
```

2. Menghapus semua izin akses

Kode Program:<br>
```markdown
chmod 000 app.conf
cat app.conf
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$ chmod 000 app.conf
cat app.conf
cat: app.conf: Permission denied
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$
```

3. Mengembalikan permission file

Kode Program:<br>
```markdown
chmod 644 app.conf
cat app.conf
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$ chmod 644 app.conf
cat app.conf
PORT=8080
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$
```

Analisis:<br>
1. Mengapa cat menghasilkan Permission denied setelah chmod 000? System call apa yang gagal?
**Jawab**<br>
Setelah chmod 000 app.conf, semua izin akses (baca, tulis, eksekusi) untuk owner, group, dan others dihapus Ketika perintah cat app.conf dijalankan, proses cat mencoba membuka file app.conf untuk dibaca.
<br>
Karena tidak ada bit izin baca (r) untuk user yang menjalankan cat (dalam kasus ini user biasa, bukan root), kernel menolak permintaan tersebut.

2. Apa perbedaan pesan error Permission denied vs No such file or directory? Coba rm app.conf lalu cat app.conf untuk melihat perbedaannya.
**Jawab**<br>
rm akan mendelete file tersebut sehingga tidak dapat diakses kembali, sedangkan dengan chmod 000 file masih ada tetapi tidak dapat diakses sementara karena tidak ada permission nya
3. Permission 644 berarti apa untuk owner, group, dan others?
**Jawab**<br>
6	= Owner (pemilik file)<br>
4	= Group (grup pemilik)<br>
4	= Others (pengguna lain)

## Praktikum 10.6

1. Detail system call ls

Kode Program:<br>
```markdown
strace ls 2>&1 | head -n 30
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$ strace ls 2>&1 | head -n 30
execve("/usr/bin/ls", ["ls"], 0x7ffe049d06c0 /* 25 vars */) = 0
brk(NULL)                               = 0x6181f7577000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7b4edbf4a000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=32555, ...}) = 0
mmap(NULL, 32555, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7b4edbf42000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=174472, ...}) = 0
mmap(NULL, 181960, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7b4edbf15000
mmap(0x7b4edbf1b000, 118784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7b4edbf1b000
mmap(0x7b4edbf38000, 24576, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23000) = 0x7b4edbf38000
mmap(0x7b4edbf3e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x29000) = 0x7b4edbf3e000
mmap(0x7b4edbf40000, 5832, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7b4edbf40000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\243\2\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
fstat(3, {st_mode=S_IFREG|0755, st_size=2125328, ...}) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2170256, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7b4edbc00000
mmap(0x7b4edbc28000, 1605632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7b4edbc28000
mmap(0x7b4edbdb0000, 323584, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b0000) = 0x7b4edbdb0000
mmap(0x7b4edbdff000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1fe000) = 0x7b4edbdff000
mmap(0x7b4edbe05000, 52624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7b4edbe05000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpcre2-8.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$
```

2. Ringkasan dan perbandingan system call

Kode Program:<br>
```markdown
strace -c ls
strace -c ls /etc 2>&1 | tail -5
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$ strace -c ls
strace -c ls /etc 2>&1 | tail -5
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 52.10    0.001641        1641         1           execve
 17.40    0.000548         274         2           getdents64
 16.70    0.000526          29        18           mmap
  2.76    0.000087          17         5           mprotect
  2.70    0.000085          12         7           openat
  1.75    0.000055           6         9           close
  1.30    0.000041           8         5           read
  1.17    0.000037          18         2         2 statfs
  1.02    0.000032          32         1           munmap
  0.79    0.000025           3         7           fstat
  0.76    0.000024           8         3           brk
  0.57    0.000018           9         2         2 access
  0.22    0.000007           7         1           getrandom
  0.19    0.000006           6         1           prlimit64
  0.16    0.000005           2         2           pread64
  0.13    0.000004           4         1           arch_prctl
  0.10    0.000003           3         1           set_tid_address
  0.10    0.000003           3         1           set_robust_list
  0.10    0.000003           3         1           rseq
  0.00    0.000000           0         2           ioctl
------ ----------- ----------- --------- --------- ----------------
100.00    0.003150          43        72         4 total
  0.07    0.000001           1         1           rseq
  0.00    0.000000           0         1           write
  0.00    0.000000           0         2           pread64
------ ----------- ----------- --------- --------- ----------------
100.00    0.001524          20        74         5 total
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory/syscall-case$
```

Analisis:<br>
1. Dari output Langkah 1, identifikasi minimal 4 system call berbeda. Jelaskan fungsi singkat masing-masing berdasarkan argumen yang terlihat.
**Jawab**<br>
execve = Menjalankan program baru, menggantikan proses yang sedang berjalan, access = Memeriksa apakah proses memiliki izin untuk mengakses file (baca, tulis, eksekusi, atau cek keberadaan), write = Menulis data dari buffer ke file descriptor (bisa file biasa, terminal, pipe, socket, dll), total = Dalam output strace -c, total adalah baris ringkasan yang menjumlahkan semua system call
2. Dari ringkasan strace -c, system call mana yang paling sering dipanggil? Mengapa?
**Jawab**<br>
mmap dengan 18 kali panggilan (di ls biasa), Program ls perlu memuat banyak library bersama (shared libraries) seperti libc.so.6, libselinux.so, dll.
3. Apakah ada system call dengan errors lebih dari 0? Apakah itu berarti program bermasalah, ataukah bagian normal dari logika program?
**Jawab**<br>
- Output ls pertama: 4 errors (total errors = 4)
- Output ls /etc: 5 errors (total errors = 5)
Error dalam konteks ini bukan berarti program crash atau bug. Error terjadi karena statfs("/etc/netplan/..", ...) mungkin gagal karena beberapa subdirektori tidak memiliki informasi filesystem yang diminta - ini bagian dari logika traversal direktori.
4. Apakah jumlah system call berbeda antara ls dan ls /etc? Faktor apa yang menyebabkan perbedaan tersebut?
**Jawab**<br>
- Jumlah file berbeda = Direktori /etc biasanya berisi ratusan file sedangkan direktori home biasa mungkin hanya sedikit
- Jumlah subdirektori = /etc memiliki banyak subdirektori yang perlu dibuka dan dibaca.
- Symlink dan file khusus = /etc banyak berisi symlink yang memerlukan pengecekan tambahan (statfs, access, dll).
- Locale dan konfigurasi = ls perlu membaca lebih banyak file konfigurasi saat berjalan di direktori yang lebih kompleks.

## Tugas 10.1

Kode Program:<br>
```markdown
nano ~/praktikum-os/week10-memory/memory-audit.sh
#!/bin/bash
set -euo pipefail
LAPORAN="memory-report.txt"
{
echo "=== LAPORAN MEMORI SISTEM ==="
date
echo
echo " --- Ringkasan free -h ---"
free -h
echo
echo "--- /proc/meminfo ---"
cat /proc/meminfo | head -n 20
} > "$LAPORAN"
echo "Laporan disimpan ke : $LAPORAN"
cat "$LAPORAN"
chmod +x ~/praktikum-os/week10-memory/memory-audit.sh
cd ~/praktikum-os/week10-memory
bash memory-audit.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ chmod +x ~/praktikum-os/week10-memory/memory-audit.sh
cd ~/praktikum-os/week10-memory
bash memory-audit.sh
Laporan disimpan ke : memory-report.txt
=== LAPORAN MEMORI SISTEM ===
Tue May  5 02:01:48 PM UTC 2026

 --- Ringkasan free -h ---
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       378Mi       2.2Gi       1.0Mi       442Mi       2.5Gi
Swap:             0B          0B          0B

--- /proc/meminfo ---
MemTotal:        3043724 kB
MemFree:         2358524 kB
MemAvailable:    2655460 kB
Buffers:           23964 kB
Cached:           407420 kB
SwapCached:            0 kB
Active:           359636 kB
Inactive:         163136 kB
Active(anon):     101252 kB
Inactive(anon):        0 kB
Active(file):     258384 kB
Inactive(file):   163136 kB
Unevictable:       27316 kB
Mlocked:           27316 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Zswap:                 0 kB
Zswapped:              0 kB
Dirty:              1288 kB
Writeback:             0 kB
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis:<br>
1. Hitung persentase memori tersedia (available / total × 100%). Apakah sistem dalam kondisi normal?
**Jawab**<br>
Sistem dalam kondisi normal
```markdown
MemAvailable = 2.5 GiB = 2655460 kB
MemTotal = 2.9 GiB = 3043724 kB

Persentase = (2655460 / 3043724) × 100%
           = 0.8725 × 100%
           = 87.25%
```
2. Mengapa buff/cache tidak dihitung sebagai memori yang terpakai dari sudut pandang ketersediaan untuk aplikasi?
**Jawab**<br>
buff/cache tidak dihitung sebagai memori terpakai karena dapat langsung dibebaskan oleh kernel kapan saja ketika aplikasi membutuhkannya.
3. Dari /proc/meminfo, apakah SwapTotal lebih besar dari 0? Berapa nilai SwapFree?
**Jawab**<br>
Sistem TIDAK memiliki swap space sama sekali.

## Tugas 10.2

Kode Program:<br>
```markdown
ps aux --sort=-%mem | head -n 10 > top-memory-process.txt
cat top-memory-process.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ ps aux --sort=-%mem | head -n 10 > top-memory-process.txt
cat top-memory-process.txt
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root        1151  0.5  4.3 370832 130952 ?       Sl   13:25   0:49 /usr/bin/python3 /usr/bin/unattended-upgrade
root        1054  0.0  1.4 617760 43836 ?        Ssl  13:04   0:10 /usr/libexec/fwupd/fwupd
root         377  0.0  0.8 288988 27324 ?        SLsl 12:51   0:09 /sbin/multipathd -d -s
root         689  0.0  0.7 109640 23100 ?        Ssl  12:51   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
root         326  0.0  0.5  50456 16436 ?        S<s  12:51   0:01 /usr/lib/systemd/systemd-journald
root         646  0.0  0.4 468972 13500 ?        Ssl  12:51   0:00 /usr/libexec/udisks2/udisksd
root           1  0.0  0.4  22024 13240 ?        Ss   12:51   0:08 /sbin/init splash noprompt noshell automatic-ubiquity
systemd+     459  0.0  0.4  21588 13036 ?        Ss   12:51   0:00 /usr/lib/systemd/systemd-resolved
root         713  0.0  0.4 318368 13008 ?        Ssl  12:51   0:00 /usr/sbin/ModemManager
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis<br>
1. Proses apa di urutan pertama? Catat nilai %MEM dan RSS.
**Jawab**<br>
Proses	= /usr/bin/python3 /usr/bin/unattended-upgrade<br>
User	= root<br>
PID	= 1151<br>
%MEM	= 4.3%<br>
RSS	= 130952 KB<br>
2. Konversikan RSS ke MB (bagi 1024). Apakah wajar?
**Jawab**<br>
RSS = 130952 KB<br>
RSS dalam MB = 130952 / 1024 = 127.88 MB<br>
Sepertinya wajar
3. Jumlahkan %MEM dari 5 proses teratas. Berapa persen RAM yang mereka gunakan bersama?
**Jawab**<br>
Total memori yang digunakan 5 proses teratas = 7.7% dari RAM total

## Tugas 10.3

Kode Program:<br>
```markdown
sudo fallocate -l 256M /swapfile-tugas-week10
sudo chmod 600 /swapfile-tugas-week10
sudo mkswap /swapfile-tugas-week10
sudo swapon /swapfile-tugas-week10

{
    echo "=== VERIFIKASI SWAP ==="
    swapon --show
    echo
    free -h
} > swap-check.txt
cat swap-check.txt
```

Hasil Program:<br>
```markdown
  pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ sudo fallocate -l 256M /swapfile-tugas-week10
  sudo chmod 600 /swapfile-tugas-week10
  sudo mkswap /swapfile-tugas-week10
  sudo swapon /swapfile-tugas-week10
  [sudo] password for pluto:
  Setting up swapspace version 1, size = 256 MiB (268431360 bytes)
  no label, UUID=4e7baf66-d902-4693-a8e2-ea5f007ae519
  pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ {
      echo "=== VERIFIKASI SWAP ==="
      swapon --show
      echo
      free -h
  } > swap-check.txt
  cat swap-check.txt
  === VERIFIKASI SWAP ===
  NAME                   TYPE SIZE USED PRIO
  /swapfile-tugas-week10 file 256M   0B   -2

                total        used        free      shared  buff/cache   available
  Mem:           2.9Gi       401Mi       1.8Gi       1.1Mi       864Mi       2.5Gi
  Swap:          255Mi          0B       255Mi
  pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis<br>
1. Identifikasi kolom NAME, TYPE, SIZE, dan USED pada output swapon –show.
**Jawab**<br>
NAME	/swapfile-tugas-week10<br>
TYPE	file	<br>
SIZE	256M	<br>
USED	0B	<br>
PRIO	-2	<br>
2. Apakah nilai total pada baris Swap di free -h bertambah 256 MB?
**Jawab**<br>
ya, Baris Swap pada free -h sekarang menampilkan 255Mi total (dari sebelumnya 0B).
3. Mengapa permission 600 penting? Apa risiko jika diatur ke 644?
**Jawab**<br>
Permission 600 = rw-------<br>
Owner (root): Baca (r) + Tulis (w)<br>
Group: Tidak ada akses<br>
Others: Tidak ada akses<br>

## Tugas 10.4

Kode Program:<br>
```markdown
strace -c ls 2> strace-summary.txt
strace ls /etc 2> strace-ls-etc.txt
cat strace-summary.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ strace -c ls 2> strace-summary.txt
strace ls /etc 2> strace-ls-etc.txt
cat strace-summary.txt
memory-audit.sh    monitor-memori.sh   swap-check.txt  top-memory-process.txt
memory-report.txt  strace-summary.txt  syscall-case
adduser.conf            dhcpcd.conf      landscape       multipath.conf       rc3.d              sysctl.d
alternatives            dpkg             ldap            nanorc               rc4.d              sysstat
apparmor                e2scrub.conf     ld.so.cache     needrestart          rc5.d              systemd
apparmor.d              environment      ld.so.conf      netconfig            rc6.d              terminfo
apport                  ethertypes       ld.so.conf.d    netplan              rcS.d              thermald
apt                     fonts            legal           network              resolv.conf        timezone
bash.bashrc             fstab            libaudit.conf   networkd-dispatcher  rmt                tmpfiles.d
bash_completion         fuse.conf        libblockdev     networks             rpc                ubuntu-advantage
bash_completion.d       fwupd            libibverbs.d    newt                 rsyslog.conf       ucf.conf
bindresvport.blacklist  gai.conf         libnl-3         nftables.conf        rsyslog.d          udev
binfmt.d                ghostscript      libpaper.d      nsswitch.conf        screenrc           udisks2
byobu                   gnutls           locale.alias    opt                  security           ufw
ca-certificates         groff            locale.conf     os-release           selinux            updatedb.conf
ca-certificates.conf    group            locale.gen      overlayroot.conf     sensors3.conf      update-manager
cloud                   group-           localtime       PackageKit           sensors.d          update-motd.d
console-setup           grub.d           logcheck        pam.conf             services           update-notifier
credstore               gshadow          login.defs      pam.d                sgml               UPower
credstore.encrypted     gshadow-         logrotate.conf  papersize            shadow             usb_modeswitch.conf
cron.d                  gss              logrotate.d     passwd               shadow-            usb_modeswitch.d
cron.daily              hdparm.conf      lsb-release     passwd-              shells             vconsole.conf
cron.hourly             host.conf        lvm             perl                 skel               vim
cron.monthly            hostname         machine-id      pki                  sos                vmware-tools
crontab                 hosts            magic           plymouth             ssh                vtrgb
cron.weekly             hosts.allow      magic.mime      pm                   ssl                w3m
cron.yearly             hosts.deny       manpath.config  polkit-1             subgid             wgetrc
cryptsetup-initramfs    ImageMagick-6    mdadm           pollinate            subgid-            X11
crypttab                init.d           mime.types      profile              subuid             xattr.conf
dbus-1                  initramfs-tools  mke2fs.conf     profile.d            subuid-            xdg
debconf.conf            inputrc          ModemManager    protocols            sudo.conf          xml
debian_version          iproute2         modprobe.d      python3              sudoers            zsh_command_not_found
default                 iscsi            modules         python3.12           sudoers.d
deluser.conf            issue            modules-load.d  rc0.d                sudo_logsrvd.conf
depmod.d                issue.net        mtab            rc1.d                supercat
dhcp                    kernel           multipath       rc2.d                sysctl.conf
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 65.09    0.003979        3979         1           execve
  8.38    0.000512          56         9           close
  7.35    0.000449          24        18           mmap
  5.95    0.000364         182         2         2 access
  5.41    0.000331          66         5           read
  3.78    0.000231          33         7           openat
  2.37    0.000145          48         3           brk
  0.61    0.000037           4         8           fstat
  0.33    0.000020           4         5           mprotect
  0.26    0.000016           8         2           getdents64
  0.25    0.000015           7         2           ioctl
  0.10    0.000006           3         2           pread64
  0.05    0.000003           3         1           set_tid_address
  0.03    0.000002           2         1           arch_prctl
  0.03    0.000002           2         1           rseq
  0.02    0.000001           1         1           set_robust_list
  0.00    0.000000           0         2           write
  0.00    0.000000           0         1           munmap
  0.00    0.000000           0         2         2 statfs
  0.00    0.000000           0         1           prlimit64
  0.00    0.000000           0         1           getrandom
------ ----------- ----------- --------- --------- ----------------
100.00    0.006113          81        75         4 total
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis<br>
1. Sebutkan minimal 5 system call dari strace-summary.txt beserta fungsi singkatnya.
**Jawab**<br>
execve = Menjalankan program ls (menggantikan proses shell)<br>
close = Menutup file descriptor yang sudah tidak digunakan<br>
mmap =	Memetakan file/library ke dalam memori proses<br>
access =	Memeriksa izin akses file (apakah bisa dibaca/ditulis)<br>
read =	Membaca data dari file descripto<br>
2. System call mana yang paling sering dipanggil? Mengapa?
**Jawab**<br>
mmap dengan 18 kali panggilan adalah yang paling sering, karena memuat library bersama (shared libraries)
3. Apakah ada errors lebih dari 0? Apakah program tetap berjalan normal meskipun ada kegagalan tersebut?
**Jawab**<br>
Ya, ada 4 errors pada output strace -c ls, Program ls tetap berjalan normal dan menampilkan output dengan benar.

## Tugas 10.5

Kode Program:<br>
```markdown
nano ~/praktikum-os/week10-memory/diagnosa-server.sh

#!/bin/bash
set -euo pipefail

LAPORAN="diagnosa-server-lambat.txt"
WARN_MEM=false
WARN_SWAP=0

cek_memori() {
    echo "--- Kondisi Memori ---"
    free -h
    echo
    AVAIL_PCT=$(free | awk '/Mem/ {printf "%d", $7/$2*100}')
    if [ "$AVAIL_PCT" -lt 20 ]; then
        echo "PERINGATAN: Memori tersedia hanya ${AVAIL_PCT}%"
        WARN_MEM=true
    fi
}

cek_swap() {
    echo "--- Penggunaan Swap ---"
    swapon --show 2>/dev/null || echo "Tidak ada swap aktif"
    echo
    WARN_SWAP=$(free | awk '/Swap/ {print $3}')
    if [ "$WARN_SWAP" -gt 0 ]; then
        echo "INFO: Swap digunakan (${WARN_SWAP} kB)"
    fi
}

cek_proses() {
    echo "--- 10 Proses Memori Tertinggi ---"
    ps aux --sort=-%mem | head -n 11
    echo
}

cek_paging() {
    echo "--- Aktivitas Paging (5 sampel) ---"
    vmstat 1 5
    echo
}

ringkasan() {
    echo "=== RINGKASAN ==="
    if [ "$WARN_MEM" = true ]; then
        echo "- Memori: KRITIS - perlu tindakan segera"
    else
        echo "- Memori: normal"
    fi
    if [ "$WARN_SWAP" -gt 0 ]; then
        echo "- Swap: aktif - pantau aktivitas paging"
    else
        echo "- Swap: tidak digunakan"
    fi
}

{
    echo "=== LAPORAN DIAGNOSA SERVER ==="
    date
    echo
    cek_memori
    cek_swap
    cek_proses
    cek_paging
    ringkasan
} | tee "$LAPORAN"

echo
echo "Laporan disimpan ke: $LAPORAN"

chmod +x ~/praktikum-os/week10-memory/diagnosa-server.sh
cd ~/praktikum-os/week10-memory
bash diagnosa-server.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$ chmod +x ~/praktikum-os/week10-memory/diagnosa-server.sh
cd ~/praktikum-os/week10-memory
bash diagnosa-server.sh
=== LAPORAN DIAGNOSA SERVER ===
Tue May  5 04:32:32 PM UTC 2026

--- Kondisi Memori ---
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       400Mi       1.7Gi       1.1Mi       952Mi       2.5Gi
Swap:          255Mi          0B       255Mi

--- Penggunaan Swap ---
NAME                   TYPE SIZE USED PRIO
/swapfile-tugas-week10 file 256M   0B   -2

--- 10 Proses Memori Tertinggi ---
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root        1151  0.4  4.3 370832 130952 ?       Sl   13:25   0:51 /usr/bin/python3 /usr/bin/unattended-upgrade
root        1054  0.0  1.4 617760 43836 ?        Ssl  13:04   0:10 /usr/libexec/fwupd/fwupd
root         377  0.0  0.8 288988 27324 ?        SLsl 12:51   0:11 /sbin/multipathd -d -s
root         689  0.0  0.7 109640 23100 ?        Ssl  12:51   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
root         326  0.0  0.5  50456 16528 ?        S<s  12:51   0:01 /usr/lib/systemd/systemd-journald
root         646  0.0  0.4 468972 13500 ?        Ssl  12:51   0:01 /usr/libexec/udisks2/udisksd
root           1  0.0  0.4  22024 13240 ?        Ss   12:51   0:10 /sbin/init splash noprompt noshell automatic-ubiquity
systemd+     459  0.0  0.4  21588 13036 ?        Ss   12:51   0:00 /usr/lib/systemd/systemd-resolved
root         713  0.0  0.4 318368 13008 ?        Ssl  12:51   0:00 /usr/sbin/ModemManager
pluto        921  0.0  0.3  20096 11248 ?        Ss   12:51   0:00 /usr/lib/systemd/systemd --user

--- Aktivitas Paging (5 sampel) ---
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 2  0      0 1831472  68416 907120    0    0    27    47 1032    0  0  6 93  0  0  0
 0  0      0 1831472  68416 907260    0    0     0     0 1113  246  0  9 91  0  0  0
 0  0      0 1831472  68424 907316    0    0     0    40 1036  188  0  6 92  2  0  0
 1  0      0 1831472  68424 907356    0    0     0     0  996  163  0  6 94  0  0  0
 0  0      0 1831472  68424 907388    0    0     0     0  999  170  0  6 94  0  0  0

=== RINGKASAN ===
- Memori: normal
- Swap: tidak digunakan

Laporan disimpan ke: diagnosa-server-lambat.txt
pluto@Ubuntu-Server-Lab:~/praktikum-os/week10-memory$
```

Analisis:<br>
1. Jelaskan peran masing-masing fungsi: cek_memori, cek_swap, cek_proses, cek_paging, dan ringkasan. Mengapa diagnosa dipecah menjadi fungsi terpisah?
**Jawab**<br>
- cek_memori = Memeriksa kondisi RAM, menghitung persentase memori available, memberi peringatan jika di bawah 20%
- cek_swap = Menampilkan swap aktif dan mencatat jika swap sedang digunakan
- cek_proses = Menampilkan 10 proses dengan penggunaan memori terbesar
- cek_paging = Memantau aktivitas swap in/out dengan vmstat 1 5
- ringkasan = Menyimpulkan hasil diagnosa (normal vs kritis)
2. Berdasarkan bagian RINGKASAN, apakah kondisi sistem normal atau kritis? Jelaskan berdasarkan nilai threshold yang digunakan script.
**Jawab**<br>
Normal, Sistem dalam kondisi sangat sehat dengan memori available hampir 90%. Tidak ada indikasi server lambat karena memori.
3. Mengapa script menggunakan tee "$LAPORAN" bukan redirection biasa > "$LAPORAN"? Apa keuntungannya?
**Jawab**<br>
Keuntungan dari penggunaan tee adalah Real-time feedback, Dokumentasi otomatis, Monitoring interaktif dan lainnya
4. Dari output cek_paging, apakah ada aktivitas si atau so? Jika ada, apa implikasinya terhadap performa server?
**Jawab**<br>
Tidak terdapat aktivitas dari si maupun so




