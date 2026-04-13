# Laporan Sistem Operasi Jobsheet 7

## Praktikum 6.1

1. Melihat shell login dan shell aktif

Kode Program:<br>
```markdown
echo " Shell login : $SHELL "
echo " Shell aktif : $0"
bash --version | head -n 1
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo " Shell login : $SHELL "
Shell login : /bin/bash
pluto@Ubuntu-Server-Lab:~$ echo " Shell aktif : $0"
Shell aktif : -bash
pluto@Ubuntu-Server-Lab:~$ bash --version | head -n 1
GNU bash, version 5.2.21(1)-release (x86_64-pc-linux-gnu)
pluto@Ubuntu-Server-Lab:~$
```

2. Melihat proses shell aktif

Kode Program:<br>
```markdown
echo $$
ps -p $$ -o pid,ppid,args=
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo $$
1060
pluto@Ubuntu-Server-Lab:~$ ps -p $$ -o pid,ppid,args=
    PID    PPID
   1060    1059 -bash
pluto@Ubuntu-Server-Lab:~$
```

3. Membuat workspace Bash

Kode Program:<br>
```markdown
mkdir -p ~/praktikum-os/week07-bash/{bin,backup,logs,sampel,ruang-nama}
cd ~/praktikum-os/week04-bash
pwd
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir -p ~/praktikum-os/week07-bash/{bin,backup,logs,sampel,ruang-nama}
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$ pwd
/home/pluto/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$
```

4. Membuat file contoh untuk praktikum lanjutan

Kode Program:<br>
```markdown
touch sample-app.conf
touch logs/app-01.log logs/app-02.log logs/app-03.log
touch sampel/catatan -a.txt sampel/catatan-b.txt
touch sampel/backup-01.tar sampel/backup-02.tar
touch sampel/laporan-harian.log sampel/laporan-mingguan.log sampel/laporan-bulanan.log
touch "ruang-nama/laporan server april .txt"
touch "ruang-nama/backup [mingguan] server.conf "
ls -R
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash$ touch sample-app.conf
touch logs/app-01.log logs/app-02.log logs/app-03.log
touch sampel/catatan -a.txt sampel/catatan-b.txt
touch sampel/backup-01.tar sampel/backup-02.tar
touch sampel/laporan-harian.log sampel/laporan-mingguan.log sampel/laporan-bulanan.log
touch "ruang-nama/laporan server april .txt"
touch "ruang-nama/backup [mingguan] server.conf "
ls -R
touch: invalid option -- '.'
Try 'touch --help' for more information.
.:
backup  bin  logs  ruang-nama  sampel  sample-app.conf

./backup:

./bin:

./logs:
app-01.log  app-02.log  app-03.log

./ruang-nama:
'backup [mingguan] server.conf '  'laporan server april .txt'

./sampel:
backup-01.tar  laporan-bulanan.log  laporan-mingguan.log
backup-02.tar  laporan-harian.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash$
```

## Praktikum 6.2

1. Masuk ke workspace praktikum

Kode Program:<br>
```markdown
cd ~/ praktikum - os / week04 - bash
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$
```

2. Membuat ringkasan sesi terminal

Kode Program:<br>
```markdown
{
echo "=== RINGKASAN SESI BASH ==="
date
echo "User : $(whoami)"
echo "Hostname : $(hostname)"
echo "Shell login : $SHELL "
echo "Shell aktif : $0"
echo "PID shell : $$"
echo "Direktori : $(pwd)"
} | tee session-info.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$ {
echo "=== RINGKASAN SESI BASH ==="
date
echo "User : $(whoami)"
echo "Hostname : $(hostname)"
echo "Shell login : $SHELL "
echo "Shell aktif : $0"
echo "PID shell : $$"
echo "Direktori : $(pwd)"
} | tee session-info.txt
=== RINGKASAN SESI BASH ===
Sun Apr 12 01:40:45 PM UTC 2026
User : pluto
Hostname : Ubuntu-Server-Lab
Shell login : /bin/bash
Shell aktif : -bash
PID shell : 1060
Direktori : /home/pluto/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$
```

3. Membaca ringkasan sesi

Kode Program:<br>
```markdown
cat session-info.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$ cat session-info.txt
=== RINGKASAN SESI BASH ===
Sun Apr 12 01:40:45 PM UTC 2026
User : pluto
Hostname : Ubuntu-Server-Lab
Shell login : /bin/bash
Shell aktif : -bash
PID shell : 1060
Direktori : /home/pluto/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$
```

## Praktikum 6.3

1. Melihat file konfigurasi Bash
Kode Program:<br>
```markdown
ls - la ~ | grep -E 'bashrc|bash_profile|profile'
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ls -la ~ | grep -E 'bashrc|bash_profi
le|profile'
-rw-r--r--  1 pluto pluto  3771 Mar 31  2024 .bashrc
-rw-r--r--  1 pluto pluto   807 Mar 31  2024 .profile
pluto@Ubuntu-Server-Lab:~$
```

2. Backup .bashrc

Kode Program:<br>
```markdown
cp ~/.bashrc ~/.bashrc.bak-praktikum
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cp ~/.bashrc ~/.bashrc.bak-praktikum
pluto@Ubuntu-Server-Lab:~$
```

3. Menambahkan konfigurasi ke .bashrc

Kode Program:<br>
```markdown
cat <<'EOF' >> ~/.bashrc
# --- Praktikum Bash Shell ---
export PRAKTIKUM_BASH_DIR="$HOME/praktikum-os/week04-bash"
export EDITOR=nano
# --- End Praktikum Bash Shell ---
EOF
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF'>> ~/.bashrc
# --- Praktikum Bash Shell ---
export PRAKTIKUM_BASH_DIR ="$HOME/praktikum-os/week04-bash"
export EDITOR = nano
# --- End Praktikum Bash Shell ---
EOF
pluto@Ubuntu-Server-Lab:~$
```

4. Memuat ulang .bashrc

Kode Program:<br>
```markdown
source ~/.bashrc
echo "$PRAKTIKUM_BASH_DIR"
echo "$EDITOR"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ source ~/.bashrc
echo "$PRAKTIKUM_BASH_DIR"
echo "$EDITOR"
-bash: export: `=/home/pluto/praktikum-os/week04-bash': not a valid identifier
-bash: export: `=': not a valid identifier
/home/pluto/praktikum-os/week04-bash
nano
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.4

1. Backup .bash_profile jika tersedia

Kode Program:<br>
```markdown
[ -f ~/.bash_profile ] && cp ~/.bash_profile ~/.bash_profile.bak-praktikum
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ [ -f ~/.bash_profile ] && cp ~/.bash_profile ~/.bash_profile.bak-praktikum
pluto@Ubuntu-Server-Lab:~$
```

2. Menambahkan konfigurasi ke .bash_profile

Kode Program:<br>
```markdown
cat <<'EOF' >> ~/.bash_profile
# --- Praktikum Bash Login Shell ---
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi
echo " Login Bash pada $(date '+%F %T')" >> "$HOME/praktikum-os/week07-bash/login-audit.log"
# --- End Praktikum Bash Login Shell ---
EOF
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF' >> ~/.bash_profile
# --- Praktikum Bash Login Shell ---
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi
echo " Login Bash pada $(date '+%F %T')" >> "$HOME/praktikum-os/week07-bash/login-audit.log"
# --- End Praktikum Bash Login Shell ---
EOF
pluto@Ubuntu-Server-Lab:~$
```

3. Menguji .bash_profile dengan login shell

Kode Program:<br>
```markdown
bash -l
tail -n 3 ~/praktikum-os/week07-bash/login-audit.log
exit
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ tail -n 3 ~/praktikum-os/week07-bash/login-audit.log
2024-10-01 09:15:30 user login failed
2024-10-01 10:30:45 user logout
 Login Bash pada 2026-04-13 04:02:14
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.5

1. Membuat variabel shell lokal

Kode Program:<br>
```markdown
KELAS_OS="Sistem Operasi A"
echo "$KELAS_OS"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ KELAS_OS="Sistem Operasi A"
echo "$KELAS_OS"
Sistem Operasi A
pluto@Ubuntu-Server-Lab:~$
```

2. Menguji variabel lokal pada subshell

Kode Program:<br>
```markdown
bash
echo "$KELAS_OS"
exit
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ bash
echo "$KELAS_OS"
exit
pluto@Ubuntu-Server-Lab:~$
```

3. Membuat environment variable

Kode Program:<br>
```markdown
export KELAS_OS="Sistem Operasi A"
bash
echo "$KELAS_OS"
exit
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ export KELAS_OS="Sistem Operasi A"
bash
echo "$KELAS_OS"
exit
pluto@Ubuntu-Server-Lab:~$
```

4. Melihat PATH dan lokasi perintah

Kode Program:<br>
```markdown
echo "$PATH"
which bash
type ls
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo "$PATH"
which bash
type ls
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
/usr/bin/bash
ls is aliased to `ls --color=auto'
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.6

1. Menyiapkan direktori bin

Kode Program:<br>
```markdown
mkdir -p ~/praktikum-os/week07-bash/bin
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir -p ~/praktikum-os/week07-bash/bin
pluto@Ubuntu-Server-Lab:~$
```

2. Menambahkan direktori bin ke PATH

Kode Program:<br>
```markdown
cat <<'EOF' >> ~/.bashrc
# --- Praktikum PATH ---
export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH"
# --- End Praktikum PATH ---
EOF
source ~/.bashrc
echo "$PATH"
```

Kode Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF' >> ~/.bashrc
# --- Praktikum PATH ---
export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH"
# --- End Praktikum PATH ---
EOF
source ~/.bashrc
echo "$PATH"
/home/pluto/praktikum-os/week07-bash/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
pluto@Ubuntu-Server-Lab:~$
```

3. Membuat script ringkas-sistem

Kode Program:<br>
```markdown
cat <<'EOF' > ~/praktikum-os/week07-bash/bin/ringkas-sistem
#!/ usr/bin/env bash
echo "Hostname : $(hostname)"
echo "User : $(whoami)"
echo "Uptime : $(uptime -p)"
echo "Disk / :"
df -h /
EOF
chmod +x ~/praktikum-os/week07-bash/bin/ringkas-sistem
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF' > ~/praktikum-os/week07-bash/bin/ringkas-sistem
#!/ usr/bin/env bash
echo "Hostname : $(hostname)"
echo "User : $(whoami)"
echo "Uptime : $(uptime -p)"
echo "Disk / :"
df -h /
EOF
chmod +x ~/praktikum-os/week07-bash/bin/ringkas-sistem
pluto@Ubuntu-Server-Lab:~$
```

4. Menjalankan script dari sembarang lokasi

Kode Program:<br>
```markdown
cd ~
ringkas-sistem
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ringkas-sistem
Hostname : Ubuntu-Server-Lab
User : pluto
Uptime : up 2 hours, 11 minutes
Disk / :
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        25G  3.9G   20G  17% /
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.7

1. Menambahkan alias ke .bashrc

Kode Program:<br>
```markdown
cat <<'EOF' >> ~/.bashrc
# --- Praktikum Alias ---
alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'
alias cdbashlab='cd $HOME/praktikum-os/week04-bash'
# --- End Praktikum Alias ---
EOF
source ~/.bashrc
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF' >> ~/.bashrc
# --- Praktikum Alias ---
alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'
alias cdbashlab='cd $HOME/praktikum-os/week04-bash'
# --- End Praktikum Alias ---
EOF
source ~/.bashrc
pluto@Ubuntu-Server-Lab:~$
```

2. Menguji alias

Kode Program:<br>
```markdown
ll
hist10
cdbashlab
pwd
type ll
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ll
hist10
cdbashlab
pwd
type ll
total 244K
-rw-rw-r--  1 pluto pluto   62 Mar 11 08:05 -
drwxr-x--- 11 pluto pluto 4.0K Apr 13 04:14 .
drwxr-xr-x  3 root  root  4.0K Feb 12 01:53 ..
drwxrwxr-x  4 pluto pluto 4.0K Mar  8 07:21 A
-rw-rw-r--  1 pluto pluto 5.4K Mar  1 17:23 backup-error.log
-rw-rw-r--  1 pluto pluto   62 Mar 11 08:05 backup-laporan.txt
-rwxrwxr-x  1 pluto pluto  974 Mar  1 17:29 backup.sh
-rw-rw-r--  1 pluto pluto   98 Mar  1 17:13 backup-success.log
-rw-------  1 pluto pluto  18K Apr  8 04:24 .bash_history
-rw-r--r--  1 pluto pluto  220 Mar 31  2024 .bash_logout
-rw-rw-r--  1 pluto pluto  212 Apr 13 03:53 .bash_profile
-rw-r--r--  1 pluto pluto 4.2K Apr 13 06:04 .bashrc
-rw-r--r--  1 pluto pluto 3.7K Apr 12 15:23 .bashrc.bak-praktikum
lrwxrwxrwx  1 pluto pluto    1 Mar  8 08:16 bye.txt -> z
drwxrwxr-x  2 pluto pluto 4.0K Mar  8 07:19 C
drwx------  2 pluto pluto 4.0K Feb 12 02:00 .cache
drwx------  5 pluto pluto 4.0K Feb 24 17:43 .config
-rw-rw-r--  1 pluto pluto  15K Mar  1 17:03 daftar_conf.txt
-rw-rw-r--  1 pluto pluto  206 Mar  1 14:38 error.log
-rw-rw-r--  1 pluto pluto  48K Mar 11 08:01 error.txt
-rw-rw-r--  2 pluto pluto   17 Mar  8 08:14 halo.txt
-rw-rw-r--  1 pluto pluto  17K Mar 11 08:01 hasil-pencarian.txt
-rw-rw-r--  1 pluto pluto   20 Feb 25 04:14 hello.txt
-rw-rw-r--  1 pluto pluto  549 Mar 11 08:05 laporan.txt
-rw-rw-r--  1 pluto pluto  763 Mar  1 14:38 large-logs.txt
-rw-------  1 pluto pluto   20 Feb 25 04:28 .lesshst
drwxrwxr-x  3 pluto pluto 4.0K Mar  1 15:34 .local
-rw-rw-r--  1 pluto pluto 1.5K Mar  1 15:43 monitor.log
-rwxrwxr-x  1 pluto pluto    1 Mar  1 16:49 monitor.sh
-rw-rw-r--  1 pluto pluto  256 Mar  8 08:21 myerror.txt
drwxrwxr-x  2 pluto pluto 4.0K Mar  8 10:10 play
drwxrwxr-x  5 pluto pluto 4.0K Apr 12 13:17 praktikum-os
-rw-r--r--  1 pluto pluto  807 Mar 31  2024 .profile
-rw-rw-r--  1 pluto pluto  419 Feb 24 13:34 server.log
drwxrwxr-x  2 pluto pluto 4.0K Mar  4 13:07 SistemOperasi
-rw-rw-r--  1 pluto pluto  248 Mar  1 14:49 sorted-users.txt
drwx------  2 pluto pluto 4.0K Feb 12 01:53 .ssh
-rw-r--r--  1 pluto pluto    0 Feb 12 02:01 .sudo_as_admin_successful
-rw-rw-r--  2 pluto pluto   17 Mar  8 08:14 z
alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'
alias cdbashlab='cd $HOME/praktikum-os/week04-bash'
# --- End Praktikum Alias ---
EOF

  452  source ~/.bashrc
  453  clear
  454  ll
  455  hist10
/home/pluto/praktikum-os/week04-bash
ll is aliased to `ls -lah --color=auto'
pluto@Ubuntu-Server-Lab:~/praktikum-os/week04-bash$
```

## Praktikum 6.8

1. Membuat file konfigurasi contoh

Kode Program:<br>
```markdown
echo "PORT =8080" > ~/praktikum-os/week07-bash/sample-app.conf
cat ~/praktikum-os/week07-bash/sample-app.conf
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo "PORT =8080" > ~/praktikum-os/week07-bash/sample-app.conf
cat ~/praktikum-os/week07-bash/sample-app.conf
PORT =8080
pluto@Ubuntu-Server-Lab:~$
```

2. Menambahkan fungsi backup_conf ke .bashrc

Kode Program:<br>
```markdown
cat <<'EOF' >> ~/.bashrc
# --- Praktikum Fungsi Shell ---
backup_conf () {
if [ $# -ne 1 ]; then
echo "Usage : backup_conf <file>"
return 1
fi
local src="$1"
local dst="$HOME/praktikum-os/week07-bash/backup "
if [ ! -f "$src" ]; then
echo "File tidak ditemukan : $src"
return 2
fi
mkdir -p "$dst"
cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak"
echo "Backup selesai di $dst"
}
# --- End Praktikum Fungsi Shell ---
EOF
source ~/.bashrc
```

Hasil Program:<>
```markdown
pluto@Ubuntu-Server-Lab:~$ cat <<'EOF' >> ~/.bashrc
# --- Praktikum Fungsi Shell ---
backup_conf () {
if [ $# -ne 1 ]; then
echo "Usage : backup_conf <file>"
return 1
fi
local src="$1"
local dst="$HOME/praktikum-os/week07-bash/backup "
if [ ! -f "$src" ]; then
echo "File tidak ditemukan : $src"
return 2
fi
mkdir -p "$dst"
cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak"
echo "Backup selesai di $dst"
}
# --- End Praktikum Fungsi Shell ---
EOF
source ~/.bashrc
pluto@Ubuntu-Server-Lab:~$
```

3. Menguji fungsi backup_conf

Kode Program:<br>
```markdown
backup_conf ~/praktikum-os/week07-bash/sample-app.conf
ls -lah ~/praktikum-os/week07-bash/backup
type backup_conf
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ backup_conf ~/praktikum-os/week07-bash/sample-app.conf
ls -lah ~/praktikum-os/week07-bash/backup
type backup_conf
Backup selesai di /home/pluto/praktikum-os/week07-bash/backup
total 8.0K
drwxrwxr-x 2 pluto pluto 4.0K Apr 12 13:17 .
drwxrwxr-x 8 pluto pluto 4.0K Apr 13 07:44 ..
backup_conf is a function
backup_conf ()
{
    if [ $# -ne 1 ]; then
        echo "Usage : backup_conf <file>";
        return 1;
    fi;
    local src="$1";
    local dst="$HOME/praktikum-os/week07-bash/backup ";
    if [ ! -f "$src" ]; then
        echo "File tidak ditemukan : $src";
        return 2;
    fi;
    mkdir -p "$dst";
    cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak";
    echo "Backup selesai di $dst"
}
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.9

1. Menyiapkan file untuk completion

Kode Program:<br>
```markdown
cd ~/praktikum-os/week07-bash/sampel
touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
ls
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week07-bash/sampel
touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
ls
backup-01.tar  backup-02.tar  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

2. Uji completion file:
a) Ketik cat lap lalu tekan Tab dua kali.<br>
b) Amati daftar file yang memiliki prefix lap.<br>
c) Ketik lebih spesifik, misalnya cat laporan-h lalu tekan Tab.<br>


Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ cat laporan-
cat: laporan-: No such file or directory
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ cat laporan-h
cat: laporan-h: No such file or directory
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ cat laporan-harian.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

3. Menjalankan beberapa perintah untuk history

Kode Program:<br>
```markdown
pwd
ls -lah
date
whoami
history | tail -n 10
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ pwd
ls -lah
date
whoami
history | tail -n 10
/home/pluto/praktikum-os/week07-bash/sampel
total 8.0K
drwxrwxr-x 2 pluto pluto 4.0K Apr 12 13:37 .
drwxrwxr-x 8 pluto pluto 4.0K Apr 13 07:44 ..
-rw-rw-r-- 1 pluto pluto    0 Apr 12 13:37 backup-01.tar
-rw-rw-r-- 1 pluto pluto    0 Apr 12 13:37 backup-02.tar
-rw-rw-r-- 1 pluto pluto    0 Apr 13 07:48 laporan-bulanan.log
-rw-rw-r-- 1 pluto pluto    0 Apr 13 07:48 laporan-harian.log
-rw-rw-r-- 1 pluto pluto    0 Apr 13 07:48 laporan-mingguan.log
Mon Apr 13 08:01:10 AM UTC 2026
pluto
  473  cat lap
  474  cd praktikum-os/week07-bash/sampel/
  475  cat laporan-
  476  cat laporan-h
  477  cat laporan-harian.log
  478  pwd
  479  ls -lah
  480  date
  481  whoami
  482  history | tail -n 10
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

## Praktikum 6.10

1. Menjalankan perintah diagnostik

Kode Program:<br>
```markdown
df -h
free -h
uptime
ps aux | head
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ df -h
free -h
uptime
ps aux | head
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           298M  1.1M  297M   1% /run
/dev/sda2        25G  3.9G   20G  17% /
tmpfs           1.5G     0  1.5G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           298M   12K  298M   1% /run/user/1000
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       387Mi       2.3Gi       1.0Mi       406Mi       2.5Gi
Swap:             0B          0B          0B
 08:04:52 up  4:21,  2 users,  load average: 0.17, 0.06, 0.01
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.4  22036 13236 ?        Ss   03:43   0:02 /sbin/init splash noprompt noshell automatic-ubiquity
root           2  0.0  0.0      0     0 ?        S    03:43   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    03:43   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   03:43   0:00 [kworker/R-rcu_g]
root           5  0.0  0.0      0     0 ?        I<   03:43   0:00 [kworker/R-rcu_p]
root           6  0.0  0.0      0     0 ?        I<   03:43   0:00 [kworker/R-slub_]
root           7  0.0  0.0      0     0 ?        I<   03:43   0:00 [kworker/R-netns]
root           9  0.0  0.0      0     0 ?        I    03:43   0:11 [kworker/0:1-events]
root          11  0.0  0.0      0     0 ?        I    03:43   0:00 [kworker/u6:0-ipv6_addrconf]
pluto@Ubuntu-Server-Lab:~$
```

2. Mencari perintah dari history

Kode Program:<br>
```markdown
history | grep -E 'df -h|free -h|uptime|ps aux'
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ history | grep -E 'df -h|free -h|uptime|ps aux'
  360  ps aux | grep sleep
  362  ps aux | grep sleep
  385  ps aux -- sort = -% cpu | head -10
  386  ps aux -- sort = -% mem | head -10
  387  ps aux --sort = -% cpu | head -10
  388  ps aux --sort = -% mem | head -10
  389  ps aux -- sort = -% cpu | head -10
  390  ps aux --sort = -% cpu | head -10
  392  ps aux --sort=-%cpu | head -10
  393  ps aux --sort=-%mem | head -10
  399  ps aux –sort=%mem
  400  ps aux –sort=-%mem | head -10
  402  ps aux –sort=%mem | tail -10
  407  ps aux
  408  ps aux -sort
  410  ps aux -sort%mem
  413  ps aux –sort=%mem | tail -10
  415  ps aux -–sort=%mem | tail -10
  416  ps aux --sort=-%mem | head -10
  417  ps aux --sort=-%mem
  421  ps aux --forest
  422  ps aux -forest
  423  ps aux --forest
echo "Uptime : $(uptime -p)"
df -h /
echo "Uptime : $(uptime -p)"
df -h /
  485  df -h
  486  free -h
  487  uptime
  488  ps aux | head
  489  history | grep -E 'df -h|free -h|uptime|ps aux'
pluto@Ubuntu-Server-Lab:~$
```

3. Menjalankan ulang perintah dari history

Kode Program:<br>
```markdown
!<NOMOR_HISTORY_ANDA>
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ !485
df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           298M  1.1M  297M   1% /run
/dev/sda2        25G  3.9G   20G  17% /
tmpfs           1.5G     0  1.5G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           298M   12K  298M   1% /run/user/1000
pluto@Ubuntu-Server-Lab:~$
```

4. Menyimpan history ke file

Kode Program:<br>
```markdown
history | tail -n 20 > ~/praktikum-os/week07-bash/diag-history.txt
cat ~/praktikum-os/week07-bash/diag-history.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ history | tail -n 20 > ~/praktikum-os/week07-bash/diag-history.txt
cat ~/praktikum-os/week07-bash/diag-history.txt
  477  cat laporan-harian.log
  478  pwd
  479  ls -lah
  480  date
  481  whoami
  482  history | tail -n 10
  483  cd
  484  clear
  485  df -h
  486  free -h
  487  uptime
  488  ps aux | head
  489  history | grep -E 'df -h|free -h|uptime|ps aux'
  490  ! <NOMOR_HISTORY_ANDA>
  491*
  492  ! <489>
  493  ! 489
  494  ! 485
  495  df -h
  496  history | tail -n 20 > ~/praktikum-os/week07-bash/diag-history.txt
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 6.11

1. Masuk ke direktori sampel

Kode Program:<br>
```markdown
cd ~/praktikum-os/week07-bash/sampel
ls
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week07-bash/sampel
ls
backup-01.tar  backup-02.tar  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

2. Mencoba wildcard dasar

Kode Program:<br>
```markdown
ls *.log
ls catatan-?.txt
ls backup-0[12].tar
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ ls *.log
ls catatan-?.txt
ls backup-0[12].tar
laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
ls: cannot access 'catatan-?.txt': No such file or directory
backup-01.tar  backup-02.tar
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

3. Mencoba brace dan tilde expansion

Kode Program:<br>
```markdown
echo log-{pagi,siang,malam}.txt
echo ~
echo ~/praktikum-os/week04-bash
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$ echo log-{pagi,siang,malam}.txt
echo ~
echo ~/praktikum-os/week04-bash
log-pagi.txt log-siang.txt log-malam.txt
/home/pluto
/home/pluto/praktikum-os/week04-bash
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/sampel$
```

## Praktikum 6.12

1. Menyiapkan file log tambahan

Kode Program:<br>
```markdown
cd ~/praktikum-os/week07-bash/logs
touch access-01.log access-02.log access-03.log
ls
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd ~/praktikum-os/week07-bash/logs
touch access-01.log access-02.log access-03.log
ls
access-01.log  access-02.log  access-03.log  app-01.log  app-02.log  app-03.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$
```

2. Preview hasil wildcard

Kode Program:<br>
```markdown
echo *.log
echo access-0?.log
```

```markdown
Hasil Program:<br>
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$ echo *.log
echo access-0?.log
access-01.log access-02.log access-03.log app-01.log app-02.log app-03.log
access-01.log access-02.log access-03.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$
```

3. Memindahkan file log ke folder arsip

Kode Program:<br>
```markdown
mkdir -p arsip-log
mv *.log arsip-log/
ls arsip-log
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$ mkdir -p arsip-log
mv *.log arsip-log/
ls arsip-log
access-01.log  access-02.log  access-03.log  app-01.log  app-02.log  app-03.log
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$
```

4. Membuat arsip terkompresi

Kode Program:<br>
```markdown
tar -czf arsip-log-$(date +%F).tar.gz arsip-log
ls -lah
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$ tar -czf arsip-log-$(date +%F).tar.gz arsip-log
ls -lah
total 16K
drwxrwxr-x 3 pluto pluto 4.0K Apr 13 08:59 .
drwxrwxr-x 8 pluto pluto 4.0K Apr 13 08:34 ..
drwxrwxr-x 2 pluto pluto 4.0K Apr 13 08:56 arsip-log
-rw-rw-r-- 1 pluto pluto  225 Apr 13 08:59 arsip-log-2026-04-13.tar.gz
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/logs$
```

## Praktikum 6.13

1. Menguji perbedaan jenis quote

Kode Program:<br>
```markdown
echo '$USER bekerja di $HOME'
echo "$USER bekerja di $HOME"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo '$USER bekerja di $HOME'
echo "$USER bekerja di $HOME"
$USER bekerja di $HOME
pluto bekerja di /home/pluto
pluto@Ubuntu-Server-Lab:~$
```

2. Menggunakan escape pada path

Kode Program:<br>
```markdown
cd ~/praktikum-os/week07-bash/ruang-nama
ls laporan\ server\ april.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ cd ~/praktikum-os/week07-bash/ruang-nama
ls laporan\ server\ april.txt
'laporan server april.txt'
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```

3. Menggunakan double quote pada path

Kode Program:<br>
```markdown
cat "laporan server april.txt"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ cat "laporan server april.txt"
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```

## Praktikum 6.14

1. Memastikan file target tersedia

Kode Program:<br>
cd ~/praktikum-os/week07-bash/ruang-nama
ls -lah

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ cd ~/praktikum-os/week07-bash/ruang-nama
ls -lah
total 8.0K
drwxrwxr-x 2 pluto pluto 4.0K Apr 13 09:19  .
drwxrwxr-x 8 pluto pluto 4.0K Apr 13 08:34  ..
-rw-rw-r-- 1 pluto pluto    0 Apr 12 13:37 'backup [mingguan] server.conf '
-rw-rw-r-- 1 pluto pluto    0 Apr 12 13:37 'laporan server april .txt'
-rw-rw-r-- 1 pluto pluto    0 Apr 13 09:19 'laporan server april.txt'
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```

2. Menyalin file dengan nama kompleks secara aman

Kode Program:<br>
```markdown
cp -- "backup [mingguan] server.conf" \ "$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server.conf"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ cp -- "backup [mingguan] server.conf" \"$HOME/praktikum-o
s/week07-bash/backup/backup-mingguan-server.conf"
> 
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```

3. Menggunakan variabel berisi path dengan aman

Kode Program:<br>
```markdown
file_asli="$HOME/praktikum-os/week07-bash/ruang-nama/backup [mingguan] server.conf"
file_salinan="$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server-v2.conf"
cp -- "$file_asli" "$file_salinan"
ls -lah "$HOME/praktikum-os/week07-bash/backup"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ file_asli="$HOME/praktikum-os/week07-bash/ruang-nama/backup [mingguan] server.conf"
file_salinan="$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server-v2.conf"
cp -- "$file_asli" "$file_salinan"
ls -lah "$HOME/praktikum-os/week07-bash/backup"
cp: cannot stat '/home/pluto/praktikum-os/week07-bash/ruang-nama/backup [mingguan] server.conf': No such file or directory
total 8.0K
drwxrwxr-x 2 pluto pluto 4.0K Apr 12 13:17 .
drwxrwxr-x 8 pluto pluto 4.0K Apr 13 08:34 ..
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```

4. Menampilkan file hasil backup dengan aman

Kode Program:<br>
```markdown
for file in "$HOME"/praktikum-os/week07-bash/backup/*;
do
printf 'Hasil backup : %s\n' "$file"
done
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$ for file in "$HOME"/praktikum-os/week07-bash/backup/*;
do
printf 'Hasil backup : %s\n' "$file"
done
Hasil backup : /home/pluto/praktikum-os/week07-bash/backup/*
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07-bash/ruang-nama$
```



