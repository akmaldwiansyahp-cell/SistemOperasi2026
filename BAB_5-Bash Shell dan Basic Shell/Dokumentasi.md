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




