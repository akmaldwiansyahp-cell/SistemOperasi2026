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


Hasil Program:<br>
```markdown
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
```markdown
cd ~/praktikum-os/week07-bash/ruang-nama
ls -lah
```

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

## Tugas Praktikum 1

1. Tambahkan konfigurasi pada .bashrc

```markdown
A. export PATH="$HOME/bin:$PATH"
B. alias ll='ls -lh'
   alias dfh='df -hT'
C. topcpu() {
    echo "=== Top 5 proses dengan penggunaan CPU tertinggi ==="
    ps aux --sort=-%cpu | head -6
}
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ export PATH="$HOME/bin:$PATH"
pluto@Ubuntu-Server-Lab:~$ alias ll='ls -lh'
alias dfh='df -hT'
pluto@Ubuntu-Server-Lab:~$ topcpu() {
    echo "=== Top 5 proses dengan penggunaan CPU tertinggi ==="
    ps aux --sort=-%cpu | head -6
}
pluto@Ubuntu-Server-Lab:~$
```

2. Pastikan konfigurasi tersebut aktif kembali saat membuka shell login

```markdown
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
pluto@Ubuntu-Server-Lab:~$
```

3. Buat satu script sederhana di direktori bin pribadi, misalnya script untuk menampilkan ringkasan sistem.

```markdown
#!/bin/bash

echo "====================================="
echo "         RINGKASAN SISTEM            "
echo "====================================="
echo "Hostname    : $(hostname)"
echo "Uptime      : $(uptime -p)"
echo "Kernel      : $(uname -r)"
echo "Memory      : $(free -h | awk '/^Mem:/ {print $3 "/" $2}')"
echo "Disk usage /: $(df -h / | awk 'NR==2 {print $5}')"
echo "Load avg    : $(uptime | awk -F'load average:' '{print $2}')"
echo "====================================="
```

```markdown
pluto@Ubuntu-Server-Lab:~$ #!/bin/bash

echo "====================================="
echo "         RINGKASAN SISTEM            "
echo "====================================="
echo "Hostname    : $(hostname)"
echo "Uptime      : $(uptime -p)"
echo "Kernel      : $(uname -r)"
echo "Memory      : $(free -h | awk '/^Mem:/ {print $3 "/" $2}')"
echo "Disk usage /: $(df -h / | awk 'NR==2 {print $5}')"
echo "Load avg    : $(uptime | awk -F'load average:' '{print $2}')"
echo "====================================="
=====================================
         RINGKASAN SISTEM
=====================================
Hostname    : Ubuntu-Server-Lab
Uptime      : up 6 minutes
Kernel      : 6.8.0-101-generic
Memory      : 346Mi/2.9Gi
Disk usage /: 18%
Load avg    :  0.04, 0.11, 0.07
=====================================
pluto@Ubuntu-Server-Lab:~$
```

4. Uji dari direktori yang berbeda untuk memastikan script dapat dipanggil tanpa menuliskan path lengkap

```markdown
cd /tmp
sysinfo
ll
dfh
topcpu
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /tmp
sysinfo
ll
dfh
topcpu
=====================================
         RINGKASAN SISTEM
=====================================
Hostname    : Ubuntu-Server-Lab
Uptime      : up 13 minutes
Kernel      : 6.8.0-101-generic
Memory      : 353Mi/2.9Gi
Disk usage /: 18%
Load avg    :  0.16, 0.08, 0.06
=====================================
total 48K
drwxrwxrwt 12 root root 4.0K Apr 14 14:52 .
drwxr-xr-x 24 root root 4.0K Mar  1 17:30 ..
drwxrwxrwt  2 root root 4.0K Apr 14 14:52 .font-unix
drwxrwxrwt  2 root root 4.0K Apr 14 14:52 .ICE-unix
drwx------  2 root root 4.0K Apr 14 14:52 snap-private-tmp
drwx------  3 root root 4.0K Apr 14 14:52 systemd-private-5902fce286564049a857dfd834c2e433-ModemManager.service-90MHYz
drwx------  3 root root 4.0K Apr 14 14:52 systemd-private-5902fce286564049a857dfd834c2e433-polkit.service-LSryis
drwx------  3 root root 4.0K Apr 14 14:52 systemd-private-5902fce286564049a857dfd834c2e433-systemd-logind.service-fBwe2B
drwx------  3 root root 4.0K Apr 14 14:52 systemd-private-5902fce286564049a857dfd834c2e433-systemd-resolved.service-df0YHr
drwx------  3 root root 4.0K Apr 14 14:52 systemd-private-5902fce286564049a857dfd834c2e433-systemd-timesyncd.service-K7yd2J
drwxrwxrwt  2 root root 4.0K Apr 14 14:52 .X11-unix
drwxrwxrwt  2 root root 4.0K Apr 14 14:52 .XIM-unix
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  298M  1.1M  297M   1% /run
/dev/sda2      ext4    25G  4.0G   20G  18% /
tmpfs          tmpfs  1.5G     0  1.5G   0% /dev/shm
tmpfs          tmpfs  5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs  298M   12K  298M   1% /run/user/1000
=== Top 5 proses dengan penggunaan CPU tertinggi ===
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pluto       1143  100  0.1  10884  4580 pts/0    R+   15:05   0:00 ps aux --sort=-%cpu
root          97  0.6  0.0      0     0 ?        I    14:52   0:05 [kworker/0:2-events]
pluto       1030  0.2  0.2  15124  7136 ?        S    14:53   0:02 sshd: pluto@pts/0
root          96  0.1  0.0      0     0 ?        I    14:52   0:00 [kworker/2:2-events]
root         654  0.0  0.0      0     0 ?        I    14:52   0:00 [kworker/1:4-events]
pluto@Ubuntu-Server-Lab:/tmp$
```

5. Simpan bukti pengujian ke file toolkit-bash-report.txt.

```markdown
cat > ~/toolkit-bash-report.txt << 'EOF'
TOOLKIT BASH REPORT
===================
Tanggal uji: $(date)

1. KONFIGURASI .bashrc
-----------------------
Blok yang ditambahkan:
export PATH="$HOME/bin:$PATH"
alias ll='ls -lh'
alias dfh='df -hT'
topcpu() { ps aux --sort=-%cpu | head -6; }

2. OUTPUT echo $PATH
--------------------
$(echo $PATH)

3. OUTPUT TYPE UNTUK ALIAS, FUNGSI, SCRIPT
-------------------------------------------
$(type ll 2>/dev/null)
$(type dfh 2>/dev/null)
$(type topcpu 2>/dev/null)
$(type sysinfo 2>/dev/null)

4. PENGUJIAN FUNGSI
-------------------
$(topcpu)

5. KESIMPULAN
-------------
Toolkit berhasil dipasang dan berfungsi.
EOF
```

Hasil:<br>
pluto@Ubuntu-Server-Lab:~$ cat > ~/toolkit-bash-report.txt << 'EOF'
```markdown
> TOOLKIT BASH REPORT
===================
Tanggal uji: 2026-04-14

1. KONFIGURASI .bashrc
-----------------------
Blok yang ditambahkan:
export PATH="$HOME/bin:$PATH"
alias ll='ls -lh'
alias dfh='df -hT'
topcpu() { ps aux --sort=-%cpu | head -6; }

2. OUTPUT echo $PATH
--------------------
/home/administrator/bin:/usr/local/bin:/usr/bin:/bin

3. OUTPUT TYPE UNTUK ALIAS, FUNGSI, SCRIPT
-------------------------------------------
type ll
ll is aliased to `ls -lh'

type dfh
dfh is aliased to `df -hT'

type topcpu
topcpu is a function
topcpu ()
{
    ps aux --sort=-%cpu | head -6
Toolkit berfungsi dengan baik. Semua perintah dapat dijalankan tanpa path lengkap.
> EOF
pluto@Ubuntu-Server-Lab:~$
```

## Tugas Praktikum 2

```markdown
LAPORAN="audit-konfigurasi-$(date +%F).txt"
ERROR_LOG="audit-error.log"

find /etc -name "*.conf" 2> "$ERROR_LOG" | tee "$LAPORAN"

JUMLAH=$(find /etc -name "*.conf" 2> /dev/null | wc -l)

echo -e "\n=== RINGKASAN ===" | tee -a "$LAPORAN"
echo "Total file konfigurasi (*.conf) ditemukan: $JUMLAH" | tee -a "$LAPORAN"

cat << EOF | tee -a "$LAPORAN"

Mengapa pemisahan stdout dan stderr penting dalam audit sistem?
1. stdout berisi data normal (daftar file konfigurasi) untuk analisis lebih lanjut.
2. stderr menangkap error akses (permission denied, file not found) tanpa mengotori hasil utama.
3. Pemisahan memudahkan troubleshooting: error bisa diperiksa terpisah tanpa mengganggu inventarisasi.
4. Dalam pipeline, stderr tetap bisa direkam meskipun stdout diproses lebih lanjut.
5. Praktik ini memenuhi prinsip keamanan dan auditability: semua kejadian terekam sesuai jenisnya.
EOF
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ LAPORAN="audit-konfigurasi-$(date +%F).txt"
ERROR_LOG="audit-error.log"

find /etc -name "*.conf" 2> "$ERROR_LOG" | tee "$LAPORAN"

JUMLAH=$(find /etc -name "*.conf" 2> /dev/null | wc -l)

echo -e "\n=== RINGKASAN ===" | tee -a "$LAPORAN"
echo "Total file konfigurasi (*.conf) ditemukan: $JUMLAH" | tee -a "$LAPORAN"

cat << EOF | tee -a "$LAPORAN"

Mengapa pemisahan stdout dan stderr penting dalam audit sistem?
1. stdout berisi data normal (daftar file konfigurasi) untuk analisis lebih lanjut.
2. stderr menangkap error akses (permission denied, file not found) tanpa mengotori hasil utama.
3. Pemisahan memudahkan troubleshooting: error bisa diperiksa terpisah tanpa mengganggu inventarisasi.
4. Dalam pipeline, stderr tetap bisa direkam meskipun stdout diproses lebih lanjut.
5. Praktik ini memenuhi prinsip keamanan dan auditability: semua kejadian terekam sesuai jenisnya.
EOF
/etc/rsyslog.conf
/etc/resolv.conf
/etc/pam.conf
/etc/sysctl.d/10-zeropage.conf
/etc/sysctl.d/10-magic-sysrq.conf
/etc/sysctl.d/10-ipv6-privacy.conf
/etc/sysctl.d/10-ptrace.conf
/etc/sysctl.d/10-console-messages.conf
/etc/sysctl.d/10-kernel-hardening.conf
/etc/sysctl.d/10-map-count.conf
/etc/sysctl.d/99-sysctl.conf
/etc/sysctl.d/10-network-security.conf
/etc/sysctl.d/10-bufferbloat.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan2.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-gb1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-korea1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-cns1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan1.conf
/etc/ghostscript/fontmap.d/10fonts-urw-base35.conf
/etc/needrestart/needrestart.conf
/etc/needrestart/notify.conf
/etc/sudo.conf
/etc/hdparm.conf
/etc/initramfs-tools/update-initramfs.conf
/etc/initramfs-tools/initramfs.conf
/etc/xattr.conf
/etc/modules-load.d/modules.conf
/etc/modules-load.d/loop.conf
/etc/ldap/ldap.conf
/etc/nftables.conf
/etc/deluser.conf
/etc/ld.so.conf.d/x86_64-linux-gnu.conf
/etc/ld.so.conf.d/libc.conf
/etc/dhcpcd.conf
/etc/sos/sos.conf
/etc/overlayroot.conf
/etc/mke2fs.conf
/etc/multipath.conf
/etc/ca-certificates.conf
/etc/vconsole.conf
/etc/libaudit.conf
/etc/udisks2/udisks2.conf
/etc/nsswitch.conf
/etc/udev/iocost.conf
/etc/udev/udev.conf
/etc/ld.so.conf
/etc/UPower/UPower.conf
/etc/adduser.conf
/etc/apt/apt.conf.d/20apt-esm-hook.conf
/etc/apt/apt.conf.d/20snapd.conf
/etc/apparmor/parser.conf
/etc/xdg/user-dirs.conf
/etc/dbus-1/system.d/com.ubuntu.SoftwareProperties.conf
/etc/lvm/lvmlocal.conf
/etc/lvm/lvm.conf
/etc/rsyslog.d/20-ufw.conf
/etc/rsyslog.d/21-cloudinit.conf
/etc/rsyslog.d/50-default.conf
/etc/tmpfiles.d/screen-cleanup.conf
/etc/fuse.conf
/etc/sysctl.conf
/etc/sensors3.conf
/etc/ufw/sysctl.conf
/etc/ufw/ufw.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/mdadm.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/amd64-microcode-blacklist.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/intel-microcode-blacklist.conf
/etc/locale.conf
/etc/fwupd/fwupd.conf
/etc/fwupd/remotes.d/lvfs-testing.conf
/etc/fwupd/remotes.d/lvfs.conf
/etc/fwupd/remotes.d/vendor-directory.conf
/etc/updatedb.conf
/etc/fonts/conf.avail/57-dejavu-sans.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-serif.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.avail/57-dejavu-serif.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans-mono.conf
/etc/fonts/conf.avail/65-droid-sans-fallback.conf
/etc/fonts/conf.avail/57-dejavu-sans-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-serif.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.avail/30-droid-noto-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/58-dejavu-lgc-serif.conf
/etc/fonts/conf.d/20-unhint-small-vera.conf
/etc/fonts/conf.d/57-dejavu-sans.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-serif.conf
/etc/fonts/conf.d/58-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.d/90-synthetic.conf
/etc/fonts/conf.d/57-dejavu-serif.conf
/etc/fonts/conf.d/10-yes-antialias.conf
/etc/fonts/conf.d/61-urw-gothic.conf
/etc/fonts/conf.d/45-latin.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-sans.conf
/etc/fonts/conf.d/61-urw-z003.conf
/etc/fonts/conf.d/49-sansserif.conf
/etc/fonts/conf.d/10-hinting-slight.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-sans-mono.conf
/etc/fonts/conf.d/61-urw-nimbus-mono-ps.conf
/etc/fonts/conf.d/50-user.conf
/etc/fonts/conf.d/30-metric-aliases.conf
/etc/fonts/conf.d/65-droid-sans-fallback.conf
/etc/fonts/conf.d/70-no-bitmaps-except-emoji.conf
/etc/fonts/conf.d/60-latin.conf
/etc/fonts/conf.d/57-dejavu-sans-mono.conf
/etc/fonts/conf.d/60-generic.conf
/etc/fonts/conf.d/65-nonlatin.conf
/etc/fonts/conf.d/69-unifont.conf
/etc/fonts/conf.d/51-local.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-serif.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.d/11-lcdfilter-default.conf
/etc/fonts/conf.d/61-urw-nimbus-sans.conf
/etc/fonts/conf.d/61-urw-fallback-backwards.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans.conf
/etc/fonts/conf.d/61-urw-p052.conf
/etc/fonts/conf.d/65-fonts-persian.conf
/etc/fonts/conf.d/61-urw-fallback-generics.conf
/etc/fonts/conf.d/58-dejavu-lgc-sans.conf
/etc/fonts/conf.d/10-scale-bitmap-fonts.conf
/etc/fonts/conf.d/61-urw-standard-symbols-ps.conf
/etc/fonts/conf.d/80-delicious.conf
/etc/fonts/conf.d/61-urw-nimbus-roman.conf
/etc/fonts/conf.d/61-urw-c059.conf
/etc/fonts/conf.d/10-sub-pixel-rgb.conf
/etc/fonts/conf.d/61-urw-d050000l.conf
/etc/fonts/conf.d/40-nonlatin.conf
/etc/fonts/conf.d/45-generic.conf
/etc/fonts/conf.d/61-urw-bookman.conf
/etc/fonts/conf.d/48-spacing.conf
/etc/fonts/conf.d/58-dejavu-lgc-serif.conf
/etc/fonts/fonts.conf
/etc/logrotate.conf
/etc/ucf.conf
/etc/usb_modeswitch.conf
/etc/iscsi/iscsid.conf
/etc/ubuntu-advantage/uaclient.conf
/etc/vmware-tools/vgauth.conf
/etc/vmware-tools/tools.conf
/etc/debconf.conf
/etc/security/pam_env.conf
/etc/security/group.conf
/etc/security/limits.conf
/etc/security/time.conf
/etc/security/pwhistory.conf
/etc/security/capability.conf
/etc/security/sepermit.conf
/etc/security/access.conf
/etc/security/faillock.conf
/etc/security/namespace.conf
/etc/gai.conf
/etc/mdadm/mdadm.conf
/etc/PackageKit/Vendor.conf
/etc/PackageKit/PackageKit.conf
/etc/systemd/system.conf
/etc/systemd/timesyncd.conf.d/cloud-init.conf
/etc/systemd/resolved.conf
/etc/systemd/sleep.conf
/etc/systemd/timesyncd.conf
/etc/systemd/journald.conf
/etc/systemd/networkd.conf
/etc/systemd/pstore.conf
/etc/systemd/logind.conf
/etc/systemd/user.conf
/etc/host.conf
/etc/depmod.d/ubuntu.conf
/etc/selinux/semanage.conf
/etc/e2scrub.conf
/etc/sudo_logsrvd.conf
/etc/apport/crashdb.conf

=== RINGKASAN ===
Total file konfigurasi (*.conf) ditemukan: 179

Mengapa pemisahan stdout dan stderr penting dalam audit sistem?
1. stdout berisi data normal (daftar file konfigurasi) untuk analisis lebih lanjut.
2. stderr menangkap error akses (permission denied, file not found) tanpa mengotori hasil utama.
3. Pemisahan memudahkan troubleshooting: error bisa diperiksa terpisah tanpa mengganggu inventarisasi.
4. Dalam pipeline, stderr tetap bisa direkam meskipun stdout diproses lebih lanjut.
5. Praktik ini memenuhi prinsip keamanan dan auditability: semua kejadian terekam sesuai jenisnya.
pluto@Ubuntu-Server-Lab:~$
```

## Tugas Praktikum 3

```markdown
#!/bin/bash

export HEALTH_CHECK_USER=$(whoami)
export HEALTH_CHECK_DATE=$(date +%F)

export PATH="$HOME/bin:$PATH"

alias log_echo='echo "[$(date +%H:%M:%S)]"'

check_error() {
    if [ $? -ne 0 ]; then
        echo "ERROR: $1 gagal dieksekusi" >&2
        return 1
    fi
    return 0
}

get_last_history() {
    local hist_file="$HOME/.bash_history"
    if [ -f "$hist_file" ]; then
        echo "--- 10 baris terakhir history command (relevan dengan pengecekan) ---"
        tail -n 10 "$hist_file" | grep -E "systemctl|service|docker|ps|top|free|df|uptime|shutdown|reboot|maintenance" || \
        tail -n 10 "$hist_file"
    else
        echo "File history tidak ditemukan untuk user $USER"
    fi
}

LOG_FILE="$HOME/healthcheck-${HEALTH_CHECK_DATE}.log"

> "$LOG_FILE"

run_health_check() {
    echo "=========================================="
    echo "       DAILY HEALTH CHECK SERVER          "
    echo "=========================================="
    echo
    
    # 1. Tanggal dan waktu
    echo ">>> Tanggal dan Waktu"
    date "+%A, %d %B %Y - %H:%M:%S"
    echo
    
    # 2. Hostname
    echo ">>> Hostname"
    hostname
    echo
    
    # 3. User aktif
    echo ">>> User Aktif"
    echo "$HEALTH_CHECK_USER"
    echo
    
    # 4. Shell aktif
    echo ">>> Shell Aktif"
    echo "$SHELL"
    echo
    
    # 5. Uptime
    echo ">>> Uptime Server"
    uptime
    echo
    
    # 6. Penggunaan memori
    echo ">>> Penggunaan Memori"
    free -h
    echo
    
    # 7. Penggunaan filesystem root (/)
    echo ">>> Penggunaan Filesystem Root (/)"
    df -h /
    echo
    
    # 8. 10 baris terakhir history command yang relevan
    get_last_history
    echo
    
    echo "=========================================="
    echo "Health check selesai pada $(date)"
    echo "=========================================="
}

{
    run_health_check
} 2>&1 | tee -a "$LOG_FILE"

PIPESTATUS_EXIT=${PIPESTATUS[0]}
if [ $PIPESTATUS_EXIT -eq 0 ]; then
    echo " Health check berhasil disimpan ke $LOG_FILE" | tee -a "$LOG_FILE"
else
    echo " Terjadi kesalahan saat health check (exit code: $PIPESTATUS_EXIT)" | tee -a "$LOG_FILE"
    exit $PIPESTATUS_EXIT
fi

unalias log_echo 2>/dev/null
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ #!/bin/bash

export HEALTH_CHECK_USER=$(whoami)
export HEALTH_CHECK_DATE=$(date +%F)

export PATH="$HOME/bin:$PATH"

alias log_echo='echo "[$(date +%H:%M:%S)]"'

check_error() {
    if [ $? -ne 0 ]; then
        echo "ERROR: $1 gagal dieksekusi" >&2
        return 1
    fi
    return 0
}

get_last_history() {
    local hist_file="$HOME/.bash_history"
    if [ -f "$hist_file" ]; then
        echo "--- 10 baris terakhir history command (relevan dengan pengecekan) ---"
        tail -n 10 "$hist_file" | grep -E "systemctl|service|docker|ps|top|free|df|uptime|shutdown|reboot|maintenance" || \
        tail -n 10 "$hist_file"
    else
        echo "File history tidak ditemukan untuk user $USER"
    fi
}

unalias log_echo 2>/dev/null saat health check (exit code: $PIPESTATUS_EXIT)" | tee -a "$LOG_FILE"
==========================================
       DAILY HEALTH CHECK SERVER
==========================================

>>> Tanggal dan Waktu
Tuesday, 14 April 2026 - 15:42:19

>>> Hostname
Ubuntu-Server-Lab

>>> User Aktif
pluto

>>> Shell Aktif
/bin/bash

>>> Uptime Server
 15:42:19 up 50 min,  2 users,  load average: 0.00, 0.00, 0.00

>>> Penggunaan Memori
               total        used        free      shared  buff/cache   available
Mem:           2.9Gi       359Mi       2.4Gi       1.0Mi       283Mi       2.6Gi
Swap:             0B          0B          0B

>>> Penggunaan Filesystem Root (/)
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        25G  4.0G   20G  18% /

--- 10 baris terakhir history command (relevan dengan pengecekan) ---
ps aux --sort=-%mem
top
htop
ps aux --forest
ps aux -forest
ps aux --forest
ps -U root -u root u | wc -l
ps -U pluto -u pluto u | wc -l
ps -e -o pid,stat,cmd | grep '^ *[0-9] S'

==========================================
Health check selesai pada Tue Apr 14 03:42:19 PM UTC 2026
==========================================
 Health check berhasil disimpan ke /home/pluto/healthcheck-2026-04-14.log
pluto@Ubuntu-Server-Lab:~$
```

## Tugas Praktikum 4

```markdown
mkdir -p ~/praktikum-os/week07/{original,backup}
cd ~/praktikum-os/week07/original

touch "laporan keuangan 2024.txt"
touch "data[backup]01.log"
touch "hasil_export-2024-01-15.csv"
touch "program v1.2.3 (fix).sh"

rm laporan keuangan 2024.txt

rm 'laporan keuangan 2024.txt'

rm "data[backup]01.log"

rm program\ v1.2.3\ \(fix\).sh

echo *.txt
echo *[0-9]*.log
echo *backup*
echo *keuangan*

for f in *; do
    safe_name=$(echo "$f" | tr ' ()[]' '_____' | sed 's/__*/_/g')
    cp "$f" "../backup/$safe_name"
done

ls -l ../backup/

cd ~/praktikum-os/week07/
tar -czvf backup_arsip.tar.gz backup/
```

Hasil:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir -p ~/praktikum-os/week07/{original,backup}
cd ~/praktikum-os/week07/original
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ touch "laporan keuangan 2024.txt"
touch "data[backup]01.log"
touch "hasil_export-2024-01-15.csv"
touch "program v1.2.3 (fix).sh"
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ ls -l
total 0
-rw-rw-r-- 1 pluto pluto 0 Apr 14 15:51 'data[backup]01.log'
-rw-rw-r-- 1 pluto pluto 0 Apr 14 15:51  hasil_export-2024-01-15.csv
-rw-rw-r-- 1 pluto pluto 0 Apr 14 15:51 'laporan keuangan 2024.txt'
-rw-rw-r-- 1 pluto pluto 0 Apr 14 15:51 'program v1.2.3 (fix).sh'
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ rm laporan keuangan 2024.txt
rm: cannot remove 'laporan': No such file or directory
rm: cannot remove 'keuangan': No such file or directory
rm: cannot remove '2024.txt': No such file or directory
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ rm 'laporan keuangan 2024.txt'

rm "data[backup]01.log"

rm program\ v1.2.3\ \(fix\).sh
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ echo *.txt
echo *[0-9]*.log
echo *backup*
echo *keuangan*
*.txt
*[0-9]*.log
*backup*
*keuangan*
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ # Gunakan loop untuk rename aman saat copy
for f in *; do
    safe_name=$(echo "$f" | tr ' ()[]' '_____' | sed 's/__*/_/g')
    cp "$f" "../backup/$safe_name"
done

ls -l ../backup/
total 0
-rw-rw-r-- 1 pluto pluto 0 Apr 14 15:52 hasil_export-2024-01-15.csv
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07/original$ cd ~/praktikum-os/
tar -czvf backup_arsip.tar.gz backup/
tar: backup: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
pluto@Ubuntu-Server-Lab:~/praktikum-os$ cd ~/praktikum-os/week07
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07$ tar -czvf backup_arsip.tar.gz backup/
backup/
backup/hasil_export-2024-01-15.csv
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07$ # Simpan riwayat sesi ini ke file
history | tail -n 50 > ~/praktikum-os/week07/riwayat-arsip.txt
pluto@Ubuntu-Server-Lab:~/praktikum-os/week07$
```


