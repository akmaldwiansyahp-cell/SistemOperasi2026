# Laporan Sistem Operasi Jobsheet 9

## Praktikum 7.1

1. Menyiapkan workspace

Kode Program:<br>
```markdown
mkdir -p ~/praktikum-os/week09/{scripts,logs,data}
cd ~/praktikum-os/week09/scripts
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir -p ~/praktikum-os/week09/{scripts,logs,data}
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week09/scripts
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

2. Membuka nano

Kode Program:<br>
```markdown
nano laporan-sistem.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ nano laporan-sistem.sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

3. Isi laporan-sistem.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Script : laporan-sistem.sh
echo " ================================ "
echo " LAPORAN SISTEM "
echo " ================================ "
echo " Tanggal : $(date '+%A, %d %B %Y')"
echo "Jam : $(date '+%H:%M:%S')"
echo " Hostname : $(hostname)"
echo " User : $(whoami)"
echo "CPU core : $(nproc)"
echo "RAM bebas : $( free -h | awk '/^Mem/ {print $4}')"
echo " Disk / : $(df -h/ | awk 'NR==2 {print $5}')
terpakai "
echo " ================================ "
```

4. Menjalankan script

Kode Program:<br>
```markdown
chmod +x laporan-sistem.sh
./laporan-sistem.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x laporan-sistem.sh
./laporan-sistem.sh
 ================================
 LAPORAN SISTEM
 ================================
 Tanggal : Saturday, 25 April 2026
Jam : 17:09:05
 Hostname : Ubuntu-Server-Lab
 User : pluto
CPU core : 3
RAM bebas : 2.5Gi
 Disk / : 17% terpakai
 ================================
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Latihan 9.1
Modifikasi laporan-sistem.sh agar menyimpan output ke filelaporan-YYYY-MM-DD.txt sekaligus menampilkannya di terminal. Petunjuk: gunakan tee yang sudah dipelajari di bab sebelumnya.<br>

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week09/logs
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/logs$ FILE_LOG=~/praktikum-os/week09/logs/laporan-$(date '+%Y-%m-%d').txt

{
    echo "==========================================="
    echo "             LAPORAN SISTEM"
    echo "==========================================="
    echo "Tanggal    : $(date '+%A, %d %B %Y')"
    echo "Jam        : $(date '+%H:%M:%S')"
    echo "Hostname   : $(hostname)"
    echo "User       : $(whoami)"
    echo "CPU core   : $(nproc)"
    echo "RAM bebas  : $(free -h | awk '/^Mem/{print $4}')"
    echo "Disk /     : $(df -h / | awk 'NR==2 {print $5}') terpakai"
    echo "==========================================="
} | tee "$FILE_LOG"

echo ""
echo "Laporan disimpan ke: $FILE_LOG"
===========================================
             LAPORAN SISTEM
===========================================
Tanggal    : Saturday, 25 April 2026
Jam        : 17:16:48
Hostname   : Ubuntu-Server-Lab
User       : pluto
CPU core   : 3
RAM bebas  : 2.4Gi
Disk /     : 17% terpakai
===========================================

Laporan disimpan ke: /home/pluto/praktikum-os/week09/logs/laporan-2026-04-25.txt
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/logs$
```

## Praktikum 7.2

1. Membuat script info-sistem.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/info-sistem.sh
```

2. Isi info-sistem.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Penggunaan: ./info-sistem.sh [nama-admin] [batas-disk-persen]
ADMIN=${1:-"Tidak dikenal"}
BATAS=${2:-80}
TANGGAL=$(date '+%F %T')
DISK_PERSEN=$(df / | awk 'NR ==2 {print $5}' | tr -d '%')
echo "Admin : $ADMIN"
echo "Tanggal : $TANGGAL"
echo "Disk / : ${DISK_PERSEN}% terpakai"
echo "Batas : ${BATAS}%"
if [ "$DISK_PERSEN" -gt "$BATAS" ]; then
echo "STATUS : PERINGATAN - disk melebihi batas!"
else
SISA=$((BATAS-DISK_PERSEN))
echo "STATUS : Normal ( sisa toleransi ${SISA}%)"
fi
```

3. Menguji script

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/info-sistem.sh
./info-sistem.sh
./info-sistem.sh "Dian" 50
./info-sistem.sh "Dian" 10
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/info-sistem.sh
./info-sistem.sh
./info-sistem.sh "Dian" 50
./info-sistem.sh "Dian" 10
Admin : Tidak dikenal
Tanggal : 2026-04-25 17:32:19
Disk / : 17% terpakai
Batas : 80%
STATUS : Normal (sisa toleransi 63%)
Admin : Dian
Tanggal : 2026-04-25 17:32:19
Disk / : 17% terpakai
Batas : 50%
STATUS : Normal (sisa toleransi 33%)
Admin : Dian
Tanggal : 2026-04-25 17:32:19
Disk / : 17% terpakai
Batas : 10%
STATUS : PERINGATAN - disk melebihi batas!
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Latihan 9.2
Buat script kalkulator.sh yang menerima tiga argumen: **<angka1> <operator> <angka2>** dengan operator +, -, *, atau /. Contoh: ./kalkulator.sh 20 + 5 menghasilkan 25. Gunakan case untuk memilih operasi, dan validasi jika argumen tidak lengkap.<br>

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/kalkulator.sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ ./kalkulator.sh 1 + 1
1 + 1 = 2
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Praktikum 7.3

1. Membuat script grading-batch.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/grading-batch.sh
```

2. Isi grading-batch.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Script: grading - batch .sh
# Proses daftar nilai mahasiswa
MAHASISWA=("Andi:92" "Budi:73" "Citra:55" "Deni:80" "Eka:45")
echo "=== HASIL GRADING ==="
for ENTRI in "${MAHASISWA[@]}"; do
NAMA=$( echo "$ENTRI" | cut -d : -f1)
NILAI=$(echo "$ENTRI" | cut -d : -f2)
if [ "$NILAI" -ge 85 ]; then
GRADE="A"
elif [ "$NILAI" -ge 75 ]; then
GRADE="B"
elif [ "$NILAI" -ge 65 ]; then
GRADE="C"
elif [ "$NILAI" -ge 55 ]; then
GRADE="D"
else
GRADE ="E"
fi
printf "%-10s %3d %s\n" "$NAMA" "$NILAI" "$GRADE"
done
echo " ===================== "
```

3. Menjalankan script grading

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/grading-batch.sh
./grading-batch.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/grading-batch.sh
./grading-batch.sh
=== HASIL GRADING ===
Andi        92 A
Budi        73 C
Citra       55 D
Deni        80 B
Eka         45 E
 =====================
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

4. Membuat script menu-sistem.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/menu-sistem.sh
```

5. Isi menu-sistem.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Menu interaktif pemantauan sistem
while true ; do
echo ""
echo " ===== MENU MONITOR ===== "
echo "1) Info disk "
echo "2) Info memori "
echo "3) Proses teratas "
echo "4) Keluar "
echo -n "Pilih [1 -4]: "
read PILIHAN
case $PILIHAN in
1) df -h ;;
2) free -h ;;
3) ps aux --sort=-%cpu | head -6 ;;
4) echo "Sampai jumpa !"; exit 0 ;;
*) echo "Pilihan tidak valid ." ;;
esac
done
```

6. Menjalankan menu

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/menu-sistem.sh
./menu-sistem.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/menu-sistem.sh
./menu-sistem.sh

 ===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1 -4]: 1
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           298M  1.1M  297M   1% /run
/dev/sda2        25G  3.9G   20G  17% /
tmpfs           1.5G     0  1.5G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           298M   12K  298M   1% /run/user/1000

 ===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1 -4]: 2
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       355Mi       2.4Gi       1.0Mi       353Mi       2.6Gi
Swap:             0B          0B          0B

 ===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1 -4]: 3
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pluto       1482 28.5  0.1  10884  4596 pts/0    R+   18:00   0:00 ps aux --sort=-%cpu
pluto       1483 16.6  0.0   5696  2056 pts/0    S+   18:00   0:00 head -6
root        1232  0.9  0.0      0     0 ?        I    17:10   0:28 [kworker/1:1-events]
pluto       1027  0.5  0.2  15128  7112 ?        S    17:01   0:17 sshd: pluto@pts/0
pluto       1479  0.2  0.1   7340  3736 pts/0    S+   18:00   0:00 /bin/bash ./menu-sistem.sh

 ===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1 -4]: 4
Sampai jumpa !
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Latihan 9.3
Tambahkan ke script grading-batch.sh sebuah ringkasan di bagian bawahyang menampilkan: jumlah mahasiswa per grade (A, B, C, D, E) menggunakan perulangan for kedua yang mengiterasi array MAHASISWA.<br>

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/grading-batch.sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/menu-sistem.shchmod +x ~/praktikum-os/week09/scripts/grading-batch.sh
./grading-batch.sh
chmod: cannot access '/home/pluto/praktikum-os/week09/scripts/menu-sistem.shchmod': No such file or directory
chmod: cannot access '+x': No such file or directory
=== HASIL GRADING ===
Nama       Nilai Grade
------------------------
Andi        92 A
Budi        73 C
Citra       55 D
Deni        80 B
Eka         45 E
=====================

=== RINGKASAN PER GRADE ===
Grade A: 1 mahasiswa
Grade B: 1 mahasiswa
Grade C: 1 mahasiswa
Grade D: 1 mahasiswa
Grade E: 1 mahasiswa
===========================
Total  : 5 mahasiswa
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Praktikum 7.4

1. Membuat lib-validasi.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/lib-validasi.sh
```

2. Isi lib-validasi.sh

Kode Program:<br>
```markdown
#!/bin/bash
# lib-validasi.sh - Library fungsi validasi
adalah_angka() {
[[ "$1" =~ ^[0-9]+$ ]]
}
file_bisa_dibaca() {
[ -f "$1" ] && [ -r "$1" ]
}
error_exit () {
echo "ERROR: $1" >&2
exit 1
}
info() { echo "[ INFO ] $1"; }
sukses() { echo "[OK] $1"; }
```

3. Membuat script pakai-library.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/pakai-library.sh
```

4. Isi pakai-library.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Muat library ( seperti import di Java )
source ~/praktikum-os/week09/scripts/lib-validasi.sh
ANGKA=$1
FILE=$2
[ -z "$ANGKA" ] || [ -z "$FILE" ] && \ error_exit "Penggunaan: $0 <angka> <path -file>"
if adalah_angka "$ANGKA"; then
sukses "Input '$ANGKA' adalah angka valid"
else
error_exit "'$ANGKA' bukan angka"
fi
if file_bisa_dibaca "$FILE"; then
sukses "File '$FILE' bisa dibaca"
info "Jumlah baris : $(wc -l < "$FILE")"
else
error_exit " File '$FILE' tidak ada atau tidak bisa dibaca"
fi
```

5. Menguji semua skenario

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/pakai-library.sh
./pakai-library.sh 42 /etc/hostname
./pakai-library.sh abc /etc/hostname
./pakai-library.sh 42 /tidak-ada.txt
./pakai-library.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ ./pakai-library.sh 42 /etc/hostname
./pakai-library.sh abc /etc/hostname
./pakai-library.sh 42 /tidak-ada.txt
./pakai-library.sh
[OK] Input '42' adalah angka valid
[OK] File '/etc/hostname' bisa dibaca
[INFO] Jumlah baris: 1
ERROR: 'abc' bukan angka
[OK] Input '42' adalah angka valid
ERROR: File '/tidak-ada.txt' tidak ada atau tidak bisa dibaca
ERROR: Penggunaan: ./pakai-library.sh <angka> <path-file>
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Latihan 9.4
Tambahkan fungsi konfirmasi() ke lib-validasi.sh. Fungsi ini menampilkan pertanyaan, membaca input Y/N dari user, mengembalikan 0 jika Y dan 1 jika N. Buat script demo yang memanggil fungsi ini sebelum menghapus sebuah file<br>

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ ./demo-konfirmasi.sh test.txt
[INFO] File target: test.txt
[INFO] Ukuran: 0
[INFO] Baris: 0
Apakah Anda yakin ingin menghapus file 'test.txt'? [y/N]: y
[OK] File 'test.txt' berhasil dihapus
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Praktikum 7.5

1. Membuat backup-data.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/backup-data.sh
```

2. Isi backup-data.sh

Kode Program:<br>
```markdown
#!/bin/bash
# Penggunaan : ./backup-data.sh [-v] [-c] [-l logfile] <sumber> <tujuan>
VERBOSE=false
COMPRESS=false
LOG_FILE=""
while getopts "vcl:" OPSI ; do
case $OPSI in
v ) VERBOSE=true ;;
c ) COMPRESS=true ;;
l ) LOG_FILE="$OPTARG" ;;
*) echo " Penggunaan : $0 [-v] [-c] [-l logfile] <sumber> <tujuan>"
exit 1 ;;
esac
done
shift $(( OPTIND - 1))
SUMBER=$1
TUJUAN=$2
log () {
local MSG ="[$( date '+%T')] $1"
echo "$MSG"
[ -n "$LOG_FILE" ] && echo "$MSG" >> "$LOG_FILE"
}
[ -z "$SUMBER " ] || [ -z "$TUJUAN" ] && { echo "ERROR: sumber dan tujuan wajib diisi"; exit 1; }
[ ! -d "$SUMBER" ] && {log "ERROR: $SUMBER tidak ada"; exit 2;}
mkdir -p "$TUJUAN"
TANGGAL=$(date '+%F-%H%M%S')
[ "$VERBOSE" = true ] && log "Sumber: $SUMBER | Tujuan: $TUJUAN"
if [ "$COMPRESS" = true ]; then
ARSIP=" $TUJUAN/backup-$(basename "$SUMBER")-$TANGGAL.tar.gz"
tar -czf "$ARSIP" -C "$(dirname "$SUMBER")" "$(basename "$SUMBER")"
log "Arsip: $ARSIP ($(du -sh "$ARSIP" | cut -f1))"
else
cp -r "$SUMBER" "$TUJUAN/backup-$(basename "$SUMBER ")-$TANGGAL"
log "Backup selesai."
fi
```

3.  Menguji script backup

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/backup-data.sh
cd ~/praktikum-os/week09/scripts
# Tanpa opsi
./backup-data.sh ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
# Dengan verbose dan kompresi + log ke file
./backup-data.sh -v -c -l ../logs/backup.log \ ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
cat ../logs/backup.log
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ # Tanpa opsi
./backup-data.sh ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
# Dengan verbose dan kompresi + log ke file
./backup-data.sh -v -c -l ../logs/backup.log \ ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
cat ../logs/backup.log
[14:34:22] Backup selesai.
[14:34:22] ERROR:  ~/praktikum-os/week09/data tidak ada

[14:34:08] ERROR:  ~/praktikum-os/week09/data tidak ada
[14:34:22] ERROR:  ~/praktikum-os/week09/data tidak ada
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Praktikum 7.6

1. Membuat debug-latihan.sh

Kode Program:<br>
```markdown
nano ~/praktikum-os/week09/scripts/debug-latihan.sh
```

2. Isi debug-latihan.sh

Kode Program:<br>
```markdown
#!/ bin/ bash
# Script: debug-latihan.sh
# Penggunaan: ./debug-latihan.sh <direktori> <batas-MB>
DIREKTORI=$1
BATAS=$2
if [ $# -ne 2 ]; then
echo "Penggunaan: $0 <direktori> <batas-MB>"
exit 1
fi
UKURAN=$(du -sm "$DIREKTORI" | cut -f1 )
echo "Direktori: $DIREKTORI"
echo "Ukuran: ${UKURAN} MB"
echo "Batas: ${BATAS} MB"
if [ "$UKURAN" -gt "$BATAS" ]; then
echo "PERINGATAN: Ukuran melebihi batas!"
echo "Kelebihan: $((UKURAN - BATAS)) MB"
else
echo " Status: Normal (sisa: $((BATAS - UKURAN)) MB)"
fi
```

3. Menganalisis script dengan debugging

Kode Program:<br>
```markdown
chmod +x ~/praktikum-os/week09/scripts/debug-latihan.sh
bash -n debug-latihan.sh && echo "Sintaks OK"
bash -x debug-latihan.sh /etc 10
./debug-latihan.sh /var 50
./debug-latihan.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/debug-latihan.sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/debug-latihan.sh
bash -n debug-latihan.sh && echo "Sintaks OK"
bash -x debug-latihan.sh /etc 10
./debug-latihan.sh /var 50
./debug-latihan.sh
Sintaks OK
+ DIREKTORI=/etc
+ BATAS=10
+ '[' 2 -ne 2 ']'
++ du -sm /etc
++ cut -f1
du: cannot read directory '/etc/credstore.encrypted': Permission denied
du: cannot read directory '/etc/credstore': Permission denied
du: cannot read directory '/etc/polkit-1/rules.d': Permission denied
du: cannot read directory '/etc/multipath': Permission denied
du: cannot read directory '/etc/ssl/private': Permission denied
+ UKURAN=7
+ echo 'Direktori: /etc'
Direktori: /etc
+ echo 'Ukuran: 7 MB'
Ukuran: 7 MB
+ echo 'Batas: 10 MB'
Batas: 10 MB
+ '[' 7 -gt 10 ']'
+ echo ' Status: Normal (sisa: 3 MB)'
 Status: Normal (sisa: 3 MB)
-bash: ./debug-latihan.sh: /: bad interpreter: Permission denied
-bash: ./debug-latihan.sh: /: bad interpreter: Permission denied
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Latihan 9.5
Script debug-latihan.sh tidak menangani direktori yang tidak ada. Perbaiki
dengan menambahkan:<br>
- set -e di baris kedua
- Pengecekan -d "$DIREKTORI" sebelum memanggil du
- Pesan error yang informatif jika direktori tidak ditemukan
Uji dengan direktori yang tidak ada.<br>

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ bash -n debug-latihan.sh && echo "Sintaks OK"
bash -x debug-latihan.sh /etc 10
./debug-latihan.sh /var 50
./debug-latihan.sh
Sintaks OK
+ set -euo pipefail
+ trap cleanup EXIT
+ DEBUG=false
+ '[' 2 -ne 2 ']'
+ DIREKTORI=/etc
+ BATAS=10
+ [[ 10 =~ ^[0-9]+$ ]]
+ '[' '!' -d /etc ']'
+ '[' '!' -r /etc ']'
+ debug 'Memeriksa ukuran direktori: /etc'
+ '[' false = true ']'
+ cleanup
+ echo '[CLEANUP] Script selesai.'
[CLEANUP] Script selesai.
[CLEANUP] Script selesai.
ERROR: Jumlah argumen tidak tepat!
Penggunaan: ./debug-latihan.sh <direktori> <batas-MB>
[CLEANUP] Script selesai.
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

## Tugas Latihan
Kerjakan tugas di $HOME/praktikum-os/week09/. Script di scripts/, output di logs/.<br>

1. Tugas 1 Script Absensi Kelas

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/absensi.sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$ ./absensi.sh "Andi" hadir
./absensi.sh "Budi" hadir
./absensi.sh "Citra" izin
./absensi.sh "Dewi" hadir
./absensi.sh "Eka" alpha
./absensi.sh "Fajar" izin

./absensi.sh -r

./absensi.sh -h
✓ Kehadiran dicatat: Andi - HADIR
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt
✓ Kehadiran dicatat: Budi - HADIR
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt
✓ Kehadiran dicatat: Citra - IZIN
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt
✓ Kehadiran dicatat: Dewi - HADIR
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt
✓ Kehadiran dicatat: Eka - ALPHA
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt
✓ Kehadiran dicatat: Fajar - IZIN
  File: /home/pluto/praktikum-os/week09/logs/absensi-2026-04-26.txt

===========================================
     REKAPITULASI KEHADIRAN
     Tanggal: Sunday, 26 April 2026
===========================================

Waktu                Nama         Status
-------------------------------------------
[16:45:59] Andi - HADIR
Penggunaan: absensi.sh [-r] [-h] [nama status]

Opsi:
    -r          Tampilkan rekapitulasi kehadiran
    -h          Tampilkan bantuan ini

Daftar Status:
    hadir       Mahasiswa hadir
    izin        Mahasiswa izin
    alpha       Mahasiswa tidak hadir tanpa keterangan

Contoh:
    absensi.sh "Budi" hadir
    absensi.sh "Citra" izin
    absensi.sh -r

pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```

2. Tugas 2 Script Health Check Sistem

Hasil Program:<br>
```markdown

════════════════════════════════════════════════════════════
                    HEALTH CHECK SYSTEM
════════════════════════════════════════════════════════════

[2026-04-26 16:56:07] ========== HEALTH CHECK START ==========
[2026-04-26 16:56:07] Batas peringatan disk: 90%
Tanggal & Waktu
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sunday, 26 April 2026 - 16:56:07

nformasi Sistem
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Hostname             : Ubuntu-Server-Lab
Uptime               : up 4 hours, 46 minutes
Load Average         : 0.18, 0.07, 0.01

CPU Usage
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CPU Usage            : 6% RENDAH

Memory Usage
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Memory         : 2.9Gi
Used Memory          : 380Mi
Free Memory          : 2.3Gi
Memory Usage         : 13% NORMAL

--- Swap ---         :
Total                : 0B
Used                 : 0B
Free                 : 0B

Disk Usage (batas: 90%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Filesystem                 Used       Use% Status
----------                 ----       ---- ------
/run                       1.1M         1% NORMAL
/                          3.9G        17% NORMAL
/dev/shm                      0         0% NORMAL
/run/lock                     0         0% NORMAL
/run/user/1000              12K         1% NORMAL

[2026-04-26 16:56:08] Semua filesystem dalam batas normal (batas: 90%)

════════════════════════════════════════════════════════════
Log file: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
════════════════════════════════════════════════════════════

[2026-04-26 16:56:08] ========== HEALTH CHECK END ==========
[2026-04-26 16:56:08] Health check selesai. Log disimpan di: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
Penggunaan: healthcheck.sh [-t persen] [-h]

Opsi:
    -t <persen>   Ubah batas peringatan disk (default: 80%)
    -h            Tampilkan bantuan ini

Contoh:
    healthcheck.sh              # Cek dengan batas 80%
    healthcheck.sh -t 90        # Cek dengan batas 90%
    healthcheck.sh -h           # Tampilkan bantuan

[2026-04-26 16:56:08] Health check selesai. Log disimpan di: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
[2026-04-26 16:56:06] ========== HEALTH CHECK START ==========
[2026-04-26 16:56:06] Batas peringatan disk: 80%
Timestamp|2026-04-26 16:56:06
Threshold|80

=== SYSTEM INFORMATION ===
Hostname|Ubuntu-Server-Lab
Uptime|up 4 hours, 46 minutes
Load Average| 0.02, 0.04, 0.00

=== CPU USAGE ===
CPU Used|5%|RENDAH

=== MEMORY USAGE ===
Total|2.9Gi
Used|380Mi
Free|2.3Gi
Usage Percent|13%|NORMAL
--- Swap ---
Swap Total|0B
Swap Used|0B
Swap Free|0B

=== DISK USAGE ===
/run|1.1M|1|NORMAL
/|3.9G|17|NORMAL
/dev/shm|0|0|NORMAL
/run/lock|0|0|NORMAL
/run/user/1000|12K|1|NORMAL
[2026-04-26 16:56:07] Semua filesystem dalam batas normal (batas: 80%)
[2026-04-26 16:56:07] ========== HEALTH CHECK END ==========
[2026-04-26 16:56:07] Health check selesai. Log disimpan di: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
[2026-04-26 16:56:07] ========== HEALTH CHECK START ==========
[2026-04-26 16:56:07] Batas peringatan disk: 90%
Timestamp|2026-04-26 16:56:07
Threshold|90

=== SYSTEM INFORMATION ===
Hostname|Ubuntu-Server-Lab
Uptime|up 4 hours, 46 minutes
Load Average| 0.18, 0.07, 0.01

=== CPU USAGE ===
CPU Used|6%|RENDAH

=== MEMORY USAGE ===
Total|2.9Gi
Used|380Mi
Free|2.3Gi
Usage Percent|13%|NORMAL
--- Swap ---
Swap Total|0B
Swap Used|0B
Swap Free|0B

=== DISK USAGE ===
/run|1.1M|1|NORMAL
/|3.9G|17|NORMAL
/dev/shm|0|0|NORMAL
/run/lock|0|0|NORMAL
/run/user/1000|12K|1|NORMAL
[2026-04-26 16:56:08] Semua filesystem dalam batas normal (batas: 90%)
[2026-04-26 16:56:08] ========== HEALTH CHECK END ==========
[2026-04-26 16:56:08] Health check selesai. Log disimpan di: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
[2026-04-26 16:56:08] Health check selesai. Log disimpan di: /home/pluto/praktikum-os/week09/logs/healthcheck-2026-04-26.log
total 40
drwxrwxr-x 6 pluto pluto 4096 Apr 26 16:56 .
drwxrwxr-x 5 pluto pluto 4096 Apr 25 16:00 ..
-rw-rw-r-- 1 pluto pluto  429 Apr 26 16:49 absensi-2026-04-26.txt
drwxrwxr-x 2 pluto pluto 4096 Apr 26 14:32 backup-data-2026-04-26-143243
drwxrwxr-x 2 pluto pluto 4096 Apr 26 14:32 backup-data-2026-04-26-143259
drwxrwxr-x 2 pluto pluto 4096 Apr 26 14:34 backup-data-2026-04-26-143402
drwxrwxr-x 2 pluto pluto 4096 Apr 26 14:34 backup-data-2026-04-26-143422
-rw-rw-r-- 1 pluto pluto  113 Apr 26 14:34 backup.log
-rw-rw-r-- 1 pluto pluto 1775 Apr 26 16:56 healthcheck-2026-04-26.log
-rw-rw-r-- 1 pluto pluto    1 Apr 25 17:17 laporan-2026-04-25.txt
pluto@Ubuntu-Server-Lab:~/praktikum-os/week09/scripts$
```













