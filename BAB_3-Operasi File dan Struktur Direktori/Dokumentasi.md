# Laporan Sistem Operasi Jobsheet 4

## Tugas Pendahuluan

1. Apa yang dimaksud perintah-perintah direktory: pwd, cd, mkdir, rmdir.

**Jawab**<br>
pwd = digunakan untuk mengetahui lokasi direktori saat ini<br>
cd = digunakan untuk pindah kesebuah direktori yang ingin ditujui<br>
mkdir = digunakan untuk membuat direktori baru<br>
rmdir = digunakan untuk menghapus sebuah direktori yang ingin dihapus

2. Apa yang dimaksud perintah-perintah manipulasi file: cp, mv dan rm (sertakan format yang digunakan).

**jawab**<br>
cp = digunakan untuk mengcopy sebuah file yang dipilih
mv = digunakan untuk memindahkan suatu file ke tujuan yang ingin di pindah
rm = digunakan untuk menghapus suatu file yang dipilih

3. Jelaskan perbedaan Symbolic link menggunakan hard link (direct) dan soft link (indirect).

**Jawab**<br>
Pada bentuk soft link, symbolic link dapat dilakukan pada file yang tidak ada, serta dapat dibentuk melalui media disk atau partisi yang berbeda. Sedangkan hard link tidak dapat/tidak mungkin melakukan symbolic link pada file yang tidak ada, serta terbatas pada partisi disk yang sama

4. Tuliskan maksud perintah-perintah: file, find, which, locate dan grep.

**Jawab**<br>
file = digunakan untuk mengetahui jenis dari file yang di panggil seperti ascii, html, dan lainnya<br>
find = digunakan untuk mencari lokasi dari file yang di sebutkan<br>
which = digunakan untuk mencari letak/lokasi dari suatu perintah/command<br>
locate = digunakan untuk mencari semua file yang memiliki nama yang dicari<br>

## Percobaan

1. Melihat direktori HOME
```markdown
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ echo $HOME
/home/pluto
pluto@Ubuntu-Server-Lab:~$
```

2. Melihat direktori aktual dan parent direktori
```markdown
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ cd .
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ cd ..
pluto@Ubuntu-Server-Lab:/home$ pwd
/home
pluto@Ubuntu-Server-Lab:/home$ cd
pluto@Ubuntu-Server-Lab:~$
```

3. Membuat satu direktori, lebih dari satu direktori atau sub direktori
```markdown
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ mkdir A B C A/D A/E B/F A/D/A
pluto@Ubuntu-Server-Lab:~$ ls -l
total 80
drwxrwxr-x 4 pluto pluto  4096 Mar  7 14:22 A
drwxrwxr-x 3 pluto pluto  4096 Mar  7 14:22 B
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  7 14:22 C
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ ls -l A
total 8
drwxrwxr-x 3 pluto pluto 4096 Mar  7 14:22 D
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 E
pluto@Ubuntu-Server-Lab:~$ ls -l A/D
total 4
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 A
pluto@Ubuntu-Server-Lab:~$
```

4. Menghapus satu atau lebih direktori
```markdown
pluto@Ubuntu-Server-Lab:~$ rdmir B
Command 'rdmir' not found, did you mean:
  command 'rdmsr' from deb msr-tools (1.3-5)
  command 'rmdir' from deb coreutils (9.4-3ubuntu6.1)
Try: sudo apt install <deb name>
pluto@Ubuntu-Server-Lab:~$ rmdir B
rmdir: failed to remove 'B': Directory not empty
pluto@Ubuntu-Server-Lab:~$ ls -l B
total 4
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 F
pluto@Ubuntu-Server-Lab:~$ rmdir B/F B
pluto@Ubuntu-Server-Lab:~$ ls -l B
ls: cannot access 'B': No such file or directory
pluto@Ubuntu-Server-Lab:~$
```
rmdir B tidak dapat dijalankan dikarenakan masih terdapat file/direktori didalamnya<br>
ls -l B tidak dapat diakses karena direktori telah dihapus

5. Navigasi direktori dengan instruksi cd
```markdown
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ ls -l
total 76
drwxrwxr-x 4 pluto pluto  4096 Mar  7 14:22 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  7 14:22 C
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ cd A
pluto@Ubuntu-Server-Lab:~/A$ pwd
/home/pluto/A
pluto@Ubuntu-Server-Lab:~/A$ cd ..
pluto@Ubuntu-Server-Lab:~$ cd /home/pluto/C
pluto@Ubuntu-Server-Lab:~/C$ pwd
/home/pluto/C
pluto@Ubuntu-Server-Lab:~/C$ cd /pluto/C
-bash: cd: /pluto/C: No such file or directory
pluto@Ubuntu-Server-Lab:~/C$ pwd
/home/pluto/C
pluto@Ubuntu-Server-Lab:~/C$ 
```
cd /<user>/C tidak dapat dijalankan karena sudah berada di direktori tersebut

## Percobaan 2

1. Perintah cp untuk mengkopi file atau seluruh direktori
```markdown
pluto@Ubuntu-Server-Lab:~$ cat > contoh
pluto@Ubuntu-Server-Lab:~$ cp contoh contoh1
pluto@Ubuntu-Server-Lab:~$ ls -l
total 76
drwxrwxr-x 4 pluto pluto  4096 Mar  7 14:22 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  8 07:19 C
-rw-rw-r-- 1 pluto pluto     0 Mar  8 07:20 contoh
-rw-rw-r-- 1 pluto pluto     0 Mar  8 07:20 contoh1
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ cp contoh A
pluto@Ubuntu-Server-Lab:~$ ls -l A
total 8
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:21 contoh
drwxrwxr-x 3 pluto pluto 4096 Mar  7 14:22 D
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 E
pluto@Ubuntu-Server-Lab:~$ cp contoh contoh1 A/D
pluto@Ubuntu-Server-Lab:~$ ls -l A/D
total 4
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 A
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:21 contoh
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:21 contoh1
pluto@Ubuntu-Server-Lab:~$
```

2. Perintah mv untuk memindah file
```markdown
pluto@Ubuntu-Server-Lab:~$ mv contoh contoh2
pluto@Ubuntu-Server-Lab:~$ ls -l
total 76
drwxrwxr-x 4 pluto pluto  4096 Mar  8 07:21 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  8 07:19 C
-rw-rw-r-- 1 pluto pluto     0 Mar  8 07:20 contoh1
-rw-rw-r-- 1 pluto pluto     0 Mar  8 07:20 contoh2
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ mv contoh1 contoh2 A/D
pluto@Ubuntu-Server-Lab:~$ ls -l A/D
total 4
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 A
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:21 contoh
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:20 contoh1
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:20 contoh2
pluto@Ubuntu-Server-Lab:~$ mv contoh contoh1 C
mv: cannot stat 'contoh': No such file or directory
mv: cannot stat 'contoh1': No such file or directory
pluto@Ubuntu-Server-Lab:~$ ls -l C
total 0
-rw-rw-r-- 1 pluto pluto 0 Mar  8 07:19 A
-rw-rw-r-- 1 pluto pluto 0 Mar  8 07:17 contoh
-rw-rw-r-- 1 pluto pluto 0 Mar  8 07:18 contoh1
pluto@Ubuntu-Server-Lab:~$ 
```

3. Perintah rm untuk menghapus file
```markdown
pluto@Ubuntu-Server-Lab:~/A/D$ rm contoh2
pluto@Ubuntu-Server-Lab:~/A/D$ ls -l
total 4
drwxrwxr-x 2 pluto pluto 4096 Mar  7 14:22 A
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:21 contoh
-rw-rw-r-- 1 pluto pluto    0 Mar  8 07:20 contoh1
pluto@Ubuntu-Server-Lab:~/A/D$ rm -i contoh
rm: remove regular empty file 'contoh'? yes
pluto@Ubuntu-Server-Lab:~/A/D$ rm -rf A C
pluto@Ubuntu-Server-Lab:~/A/D$ ls -l
total 0
-rw-rw-r-- 1 pluto pluto 0 Mar  8 07:20 contoh1
pluto@Ubuntu-Server-Lab:~/A/D$
```

## Percobaan 3
1. Membuat shortcut (file link)
```markdown
pluto@Ubuntu-Server-Lab:~$ echo "Hallo apa Khabar" > halo.txt
pluto@Ubuntu-Server-Lab:~$ ls -l
total 80
drwxrwxr-x 4 pluto pluto  4096 Mar  8 07:21 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  8 07:19 C
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    17 Mar  8 08:14 halo.txt
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ ln halo.txt z
pluto@Ubuntu-Server-Lab:~$ ls -l
total 84
drwxrwxr-x 4 pluto pluto  4096 Mar  8 07:21 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
drwxrwxr-x 2 pluto pluto  4096 Mar  8 07:19 C
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 2 pluto pluto    17 Mar  8 08:14 halo.txt
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
-rw-rw-r-- 2 pluto pluto    17 Mar  8 08:14 z
pluto@Ubuntu-Server-Lab:~$ cat z
Hallo apa Khabar
pluto@Ubuntu-Server-Lab:~$ ln z mydir/halo.juga
ln: failed to create hard link 'mydir/halo.juga' => 'z': No such file or directory
pluto@Ubuntu-Server-Lab:~$ cat mydir/halo.juga
cat: mydir/halo.juga: No such file or directory
pluto@Ubuntu-Server-Lab:~$ ln -s z bye.txt
pluto@Ubuntu-Server-Lab:~$ ls -l bye.txt
lrwxrwxrwx 1 pluto pluto 1 Mar  8 08:16 bye.txt -> z
pluto@Ubuntu-Server-Lab:~$ cat bye.txt
Hallo apa Khabar
pluto@Ubuntu-Server-Lab:~$
```

## Percobaan 4
1. Melihat Isi File
```markdown
pluto@Ubuntu-Server-Lab:~$ ls -l
total 84
drwxrwxr-x 4 pluto pluto  4096 Mar  8 07:21 A
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
lrwxrwxrwx 1 pluto pluto     1 Mar  8 08:16 bye.txt -> z
drwxrwxr-x 2 pluto pluto  4096 Mar  8 07:19 C
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 2 pluto pluto    17 Mar  8 08:14 halo.txt
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
-rw-rw-r-- 2 pluto pluto    17 Mar  8 08:14 z
pluto@Ubuntu-Server-Lab:~$ file halo.txt
halo.txt: ASCII text
pluto@Ubuntu-Server-Lab:~$ file bye.txt
bye.txt: symbolic link to z
pluto@Ubuntu-Server-Lab:~$
```

## Percobaan 5
1. Perintah find
```markdown
pluto@Ubuntu-Server-Lab:~$ find /home -name "*.txt" -print > myerror.txt
pluto@Ubuntu-Server-Lab:~$ cat myerror.txt
/home/pluto/daftar_conf.txt
/home/pluto/praktikum-os/week02/notes.txt
/home/pluto/praktikum-os/week02/config.txt
/home/pluto/myerror.txt
/home/pluto/halo.txt
/home/pluto/hello.txt
/home/pluto/large-logs.txt
/home/pluto/bye.txt
/home/pluto/sorted-users.txt
pluto@Ubuntu-Server-Lab:~$ find . -name "*.txt" -exec wc -l '{}' ';'
345 ./daftar_conf.txt
0 ./praktikum-os/week02/notes.txt
3 ./praktikum-os/week02/config.txt
9 ./myerror.txt
1 ./halo.txt
2 ./hello.txt
10 ./large-logs.txt
1 ./bye.txt
34 ./sorted-users.txt
pluto@Ubuntu-Server-Lab:~$
```

2. Perintah which
```markdown
pluto@Ubuntu-Server-Lab:~$ which ls
/usr/bin/ls
pluto@Ubuntu-Server-Lab:~$
```

3. Perintah locate
```markdown
pluto@Ubuntu-Server-Lab:~$ locate "*.txt"
/boot/grub/gfxblacklist.txt
/etc/X11/rgb.txt
/home/pluto/daftar_conf.txt
/home/pluto/hello.txt
/home/pluto/large-logs.txt
/home/pluto/sorted-users.txt
/home/pluto/praktikum-os/week02/config.txt
/home/pluto/praktikum-os/week02/notes.txt
/usr/lib/python3/dist-packages/Automat-22.10.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/Automat-22.10.0.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/Automat-22.10.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/Automat-22.10.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/requires.txt
/usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/top_level.txt
/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/requires.txt
/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/top_level.txt
/usr/lib/python3/dist-packages/PyJWT-2.7.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/PyYAML-6.0.1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/bcc-0.29.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/bcc-0.29.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/bcrypt-3.2.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/bcrypt-3.2.2.egg-info/requires.txt
/usr/lib/python3/dist-packages/bcrypt-3.2.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/boto3-1.34.46.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/boto3-1.34.46.egg-info/requires.txt
/usr/lib/python3/dist-packages/boto3-1.34.46.egg-info/top_level.txt
/usr/lib/python3/dist-packages/botocore-1.34.46.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/botocore-1.34.46.egg-info/requires.txt
/usr/lib/python3/dist-packages/botocore-1.34.46.egg-info/top_level.txt
/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/top_level.txt
/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/click-8.1.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/click-8.1.6.egg-info/requires.txt
/usr/lib/python3/dist-packages/click-8.1.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/requires.txt
/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/top_level.txt
/usr/lib/python3/dist-packages/configobj-5.0.8.dist-info/top_level.txt
/usr/lib/python3/dist-packages/constantly-23.10.4.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/constantly-23.10.4.egg-info/top_level.txt
/usr/lib/python3/dist-packages/cryptography-41.0.7.dist-info/top_level.txt
/usr/lib/python3/dist-packages/cryptography.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/cryptography.egg-info/requires.txt
/usr/lib/python3/dist-packages/cryptography.egg-info/top_level.txt
/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/distro-1.9.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/distro-1.9.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/distro_info-1.7+build1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/distro_info-1.7+build1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/httplib2-0.20.4.dist-info/top_level.txt
/usr/lib/python3/dist-packages/hyperlink-21.0.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/hyperlink-21.0.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/hyperlink-21.0.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/incremental-22.10.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/incremental-22.10.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/jmespath-1.0.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/jmespath-1.0.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/jsonschema-4.10.3.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/namespace_packages.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/requires.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/namespace_packages.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/requires.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/markdown_it_py-3.0.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/netaddr/eui/iab.txt
/usr/lib/python3/dist-packages/netaddr/eui/oui.txt
/usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/requires.txt
/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pyOpenSSL-23.2.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pyOpenSSL-23.2.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/pyOpenSSL-23.2.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pyasn1-0.4.8.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pyasn1-0.4.8.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pygments-2.17.2.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_apt-2.7.7+ubuntu5.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/python_apt-2.7.7+ubuntu5.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/requires.txt
/usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/requires.txt
/usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_magic-0.4.27.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/python_magic-0.4.27.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pytz-2024.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pytz-2024.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/s3transfer-0.10.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/s3transfer-0.10.1.egg-info/requires.txt
/usr/lib/python3/dist-packages/s3transfer-0.10.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/setuptools-68.1.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/setuptools-68.1.2.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/setuptools-68.1.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/sos-4.9.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/sos-4.9.2.egg-info/requires.txt
/usr/lib/python3/dist-packages/sos-4.9.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/ssh_import_id-5.11.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ssh_import_id-5.11.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/ssh_import_id-5.11.egg-info/requires.txt
/usr/lib/python3/dist-packages/ssh_import_id-5.11.egg-info/top_level.txt
/usr/lib/python3/dist-packages/systemd_python-235.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/systemd_python-235.egg-info/top_level.txt
/usr/lib/python3/dist-packages/twisted-24.3.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/requires.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/top_level.txt
/usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/requires.txt
/usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/zope.interface-6.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/zope.interface-6.1.egg-info/namespace_packages.txt
/usr/lib/python3/dist-packages/zope.interface-6.1.egg-info/requires.txt
/usr/lib/python3/dist-packages/zope.interface-6.1.egg-info/top_level.txt
/usr/lib/python3.12/LICENSE.txt
/usr/share/X11/rgb.txt
/usr/share/doc/bpfcc-tools/examples/doc/argdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bashreadline_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bindsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biolatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biolatpcts_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biopattern_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biosnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biotop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bitesize_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bpflist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/btrfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/btrfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cachestat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cachetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/capable_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/compactsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cpudist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cpuunclaimed_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/criticalstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cthreads_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dbslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dbstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dcsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dcstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/deadlock_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dirtop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/drsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/execsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/exitsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ext4dist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ext4slower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filegone_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filelife_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/fileslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funccount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funcinterval_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funclatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funcslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/gethostlatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/hardirqs_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/inject_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javacalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javaflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javagc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javaobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javastat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javathreads_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/killsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/klockstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/kvmexit_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/llcstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mdflush_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/memleak_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mountsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mysqld_qslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/netqtop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nodegc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nodestat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/offcputime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/offwaketime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/oomkill_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/opensnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pidpersec_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ppchcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/profile_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythoncalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythonflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythongc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythonstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rdmaucma_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/readahead_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/reset-trace_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubycalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubyflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubygc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubyobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubystat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqlat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqlen_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/shmsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/slabratetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/sofdsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/softirqs_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/solisten_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/sslsniff_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/stackcount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/statsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/swapin.txt
/usr/share/doc/bpfcc-tools/examples/doc/swapin_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/syncsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/syscount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpaccept_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpcong_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpconnect_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpconnlat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpdrop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcplife_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpretrans_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcprtt_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpstates_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpsubnet_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpsynbl_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcptop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcptracer_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/threadsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tplist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/trace_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ttysnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/vfscount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/vfsstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/virtiostat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/wakeuptime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/xfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/xfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/zfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/zfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ucalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ugc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ustat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uthreads_example.txt
/usr/share/doc/bpfcc-tools/examples/networking/neighbor_sharing/README.txt
/usr/share/doc/bpfcc-tools/examples/networking/vlan_learning/README.txt
/usr/share/doc/bpfcc-tools/examples/tracing/CMakeLists.txt
/usr/share/doc/bpfcc-tools/examples/tracing/biolatpcts_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/bitehist_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/dddos_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/disksnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/kvm_hypercall.txt
/usr/share/doc/bpfcc-tools/examples/tracing/mysqld_query_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/nodejs_http_server_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/stacksnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/tcpv4connect_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/undump_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/urandomread_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/vfsreadlat_example.txt
/usr/share/doc/bpftrace/examples/bashreadline_example.txt
/usr/share/doc/bpftrace/examples/biolatency_example.txt
/usr/share/doc/bpftrace/examples/biosnoop_example.txt
/usr/share/doc/bpftrace/examples/biostacks_example.txt
/usr/share/doc/bpftrace/examples/bitesize_example.txt
/usr/share/doc/bpftrace/examples/capable_example.txt
/usr/share/doc/bpftrace/examples/cpuwalk_example.txt
/usr/share/doc/bpftrace/examples/dcsnoop_example.txt
/usr/share/doc/bpftrace/examples/execsnoop_example.txt
/usr/share/doc/bpftrace/examples/gethostlatency_example.txt
/usr/share/doc/bpftrace/examples/killsnoop_example.txt
/usr/share/doc/bpftrace/examples/loads_example.txt
/usr/share/doc/bpftrace/examples/mdflush_example.txt
/usr/share/doc/bpftrace/examples/naptime_example.txt
/usr/share/doc/bpftrace/examples/oomkill_example.txt
/usr/share/doc/bpftrace/examples/opensnoop_example.txt
/usr/share/doc/bpftrace/examples/pidpersec_example.txt
/usr/share/doc/bpftrace/examples/runqlat_example.txt
/usr/share/doc/bpftrace/examples/runqlen_example.txt
/usr/share/doc/bpftrace/examples/setuids_example.txt
/usr/share/doc/bpftrace/examples/ssllatency_example.txt
/usr/share/doc/bpftrace/examples/sslsnoop_example.txt
/usr/share/doc/bpftrace/examples/statsnoop_example.txt
/usr/share/doc/bpftrace/examples/swapin_example.txt
/usr/share/doc/bpftrace/examples/syncsnoop_example.txt
/usr/share/doc/bpftrace/examples/syscount_example.txt
/usr/share/doc/bpftrace/examples/tcpaccept_example.txt
/usr/share/doc/bpftrace/examples/tcpconnect_example.txt
/usr/share/doc/bpftrace/examples/tcpdrop_example.txt
/usr/share/doc/bpftrace/examples/tcplife_example.txt
/usr/share/doc/bpftrace/examples/tcpretrans_example.txt
/usr/share/doc/bpftrace/examples/tcpsynbl_example.txt
/usr/share/doc/bpftrace/examples/threadsnoop_example.txt
/usr/share/doc/bpftrace/examples/undump_example.txt
/usr/share/doc/bpftrace/examples/vfscount_example.txt
/usr/share/doc/bpftrace/examples/vfsstat_example.txt
/usr/share/doc/bpftrace/examples/writeback_example.txt
/usr/share/doc/bpftrace/examples/xfsdist_example.txt
/usr/share/doc/byobu/help.screen.txt
/usr/share/doc/byobu/help.tmux.txt
/usr/share/doc/cloud-init/status.txt
/usr/share/doc/cloud-init/userdata.txt
/usr/share/doc/cloud-init/var-lib-cloud.txt
/usr/share/doc/cloud-init/examples/boothook.txt
/usr/share/doc/cloud-init/examples/cloud-config-add-apt-repos.txt
/usr/share/doc/cloud-init/examples/cloud-config-ansible-controller.txt
/usr/share/doc/cloud-init/examples/cloud-config-ansible-managed.txt
/usr/share/doc/cloud-init/examples/cloud-config-ansible-pull.txt
/usr/share/doc/cloud-init/examples/cloud-config-apt.txt
/usr/share/doc/cloud-init/examples/cloud-config-archive-launch-index.txt
/usr/share/doc/cloud-init/examples/cloud-config-archive.txt
/usr/share/doc/cloud-init/examples/cloud-config-boot-cmds.txt
/usr/share/doc/cloud-init/examples/cloud-config-ca-certs.txt
/usr/share/doc/cloud-init/examples/cloud-config-chef-oneiric.txt
/usr/share/doc/cloud-init/examples/cloud-config-chef.txt
/usr/share/doc/cloud-init/examples/cloud-config-datasources.txt
/usr/share/doc/cloud-init/examples/cloud-config-disk-setup.txt
/usr/share/doc/cloud-init/examples/cloud-config-gluster.txt
/usr/share/doc/cloud-init/examples/cloud-config-install-packages.txt
/usr/share/doc/cloud-init/examples/cloud-config-launch-index.txt
/usr/share/doc/cloud-init/examples/cloud-config-lxd.txt
/usr/share/doc/cloud-init/examples/cloud-config-mount-points.txt
/usr/share/doc/cloud-init/examples/cloud-config-ntp.txt
/usr/share/doc/cloud-init/examples/cloud-config-reporting.txt
/usr/share/doc/cloud-init/examples/cloud-config-run-cmds.txt
/usr/share/doc/cloud-init/examples/cloud-config-ssh-keys.txt
/usr/share/doc/cloud-init/examples/cloud-config-update-apt.txt
/usr/share/doc/cloud-init/examples/cloud-config-update-packages.txt
/usr/share/doc/cloud-init/examples/cloud-config-user-groups.txt
/usr/share/doc/cloud-init/examples/cloud-config-wireguard.txt
/usr/share/doc/cloud-init/examples/cloud-config-write-files.txt
/usr/share/doc/cloud-init/examples/cloud-config-yum-repo.txt
/usr/share/doc/cloud-init/examples/cloud-config.txt
/usr/share/doc/cloud-init/examples/include-once.txt
/usr/share/doc/cloud-init/examples/include.txt
/usr/share/doc/cloud-init/examples/kernel-command-line.txt
/usr/share/doc/cloud-init/examples/part-handler-v2.txt
/usr/share/doc/cloud-init/examples/part-handler.txt
/usr/share/doc/cloud-init/examples/plain-ignored.txt
/usr/share/doc/cloud-init/examples/user-script.txt
/usr/share/doc/cryptsetup/Keyring.txt
/usr/share/doc/cryptsetup/LUKS2-locking.txt
/usr/share/doc/gawk/examples/network/stoxdata.txt
/usr/share/doc/git/RelNotes/1.5.0.1.txt
/usr/share/doc/git/RelNotes/1.5.0.2.txt
/usr/share/doc/git/RelNotes/1.5.0.3.txt
/usr/share/doc/git/RelNotes/1.5.0.4.txt
/usr/share/doc/git/RelNotes/1.5.0.5.txt
/usr/share/doc/git/RelNotes/1.5.0.6.txt
/usr/share/doc/git/RelNotes/1.5.0.7.txt
/usr/share/doc/git/RelNotes/1.5.0.txt
/usr/share/doc/git/RelNotes/1.5.1.1.txt
/usr/share/doc/git/RelNotes/1.5.1.2.txt
/usr/share/doc/git/RelNotes/1.5.1.3.txt
/usr/share/doc/git/RelNotes/1.5.1.4.txt
/usr/share/doc/git/RelNotes/1.5.1.5.txt
/usr/share/doc/git/RelNotes/1.5.1.6.txt
/usr/share/doc/git/RelNotes/1.5.1.txt
/usr/share/doc/git/RelNotes/1.5.2.1.txt
/usr/share/doc/git/RelNotes/1.5.2.2.txt
/usr/share/doc/git/RelNotes/1.5.2.3.txt
/usr/share/doc/git/RelNotes/1.5.2.4.txt
/usr/share/doc/git/RelNotes/1.5.2.5.txt
/usr/share/doc/git/RelNotes/1.5.2.txt
/usr/share/doc/git/RelNotes/1.5.3.1.txt
/usr/share/doc/git/RelNotes/1.5.3.2.txt
/usr/share/doc/git/RelNotes/1.5.3.3.txt
/usr/share/doc/git/RelNotes/1.5.3.4.txt
/usr/share/doc/git/RelNotes/1.5.3.5.txt
/usr/share/doc/git/RelNotes/1.5.3.6.txt
/usr/share/doc/git/RelNotes/1.5.3.7.txt
/usr/share/doc/git/RelNotes/1.5.3.8.txt
/usr/share/doc/git/RelNotes/1.5.3.txt
/usr/share/doc/git/RelNotes/1.5.4.1.txt
/usr/share/doc/git/RelNotes/1.5.4.2.txt
/usr/share/doc/git/RelNotes/1.5.4.3.txt
/usr/share/doc/git/RelNotes/1.5.4.4.txt
/usr/share/doc/git/RelNotes/1.5.4.5.txt
/usr/share/doc/git/RelNotes/1.5.4.6.txt
/usr/share/doc/git/RelNotes/1.5.4.7.txt
/usr/share/doc/git/RelNotes/1.5.4.txt
/usr/share/doc/git/RelNotes/1.5.5.1.txt
/usr/share/doc/git/RelNotes/1.5.5.2.txt
/usr/share/doc/git/RelNotes/1.5.5.3.txt
/usr/share/doc/git/RelNotes/1.5.5.4.txt
/usr/share/doc/git/RelNotes/1.5.5.5.txt
/usr/share/doc/git/RelNotes/1.5.5.6.txt
/usr/share/doc/git/RelNotes/1.5.5.txt
/usr/share/doc/git/RelNotes/1.5.6.1.txt
/usr/share/doc/git/RelNotes/1.5.6.2.txt
/usr/share/doc/git/RelNotes/1.5.6.3.txt
/usr/share/doc/git/RelNotes/1.5.6.4.txt
/usr/share/doc/git/RelNotes/1.5.6.5.txt
/usr/share/doc/git/RelNotes/1.5.6.6.txt
/usr/share/doc/git/RelNotes/1.5.6.txt
/usr/share/doc/git/RelNotes/1.6.0.1.txt
/usr/share/doc/git/RelNotes/1.6.0.2.txt
/usr/share/doc/git/RelNotes/1.6.0.3.txt
/usr/share/doc/git/RelNotes/1.6.0.4.txt
/usr/share/doc/git/RelNotes/1.6.0.5.txt
/usr/share/doc/git/RelNotes/1.6.0.6.txt
/usr/share/doc/git/RelNotes/1.6.0.txt
/usr/share/doc/git/RelNotes/1.6.1.1.txt
/usr/share/doc/git/RelNotes/1.6.1.2.txt
/usr/share/doc/git/RelNotes/1.6.1.3.txt
/usr/share/doc/git/RelNotes/1.6.1.4.txt
/usr/share/doc/git/RelNotes/1.6.1.txt
/usr/share/doc/git/RelNotes/1.6.2.1.txt
/usr/share/doc/git/RelNotes/1.6.2.2.txt
/usr/share/doc/git/RelNotes/1.6.2.3.txt
/usr/share/doc/git/RelNotes/1.6.2.4.txt
/usr/share/doc/git/RelNotes/1.6.2.5.txt
/usr/share/doc/git/RelNotes/1.6.2.txt
/usr/share/doc/git/RelNotes/1.6.3.1.txt
/usr/share/doc/git/RelNotes/1.6.3.2.txt
/usr/share/doc/git/RelNotes/1.6.3.3.txt
/usr/share/doc/git/RelNotes/1.6.3.4.txt
/usr/share/doc/git/RelNotes/1.6.3.txt
/usr/share/doc/git/RelNotes/1.6.4.1.txt
/usr/share/doc/git/RelNotes/1.6.4.2.txt
/usr/share/doc/git/RelNotes/1.6.4.3.txt
/usr/share/doc/git/RelNotes/1.6.4.4.txt
/usr/share/doc/git/RelNotes/1.6.4.5.txt
/usr/share/doc/git/RelNotes/1.6.4.txt
/usr/share/doc/git/RelNotes/1.6.5.1.txt
/usr/share/doc/git/RelNotes/1.6.5.2.txt
/usr/share/doc/git/RelNotes/1.6.5.3.txt
/usr/share/doc/git/RelNotes/1.6.5.4.txt
/usr/share/doc/git/RelNotes/1.6.5.5.txt
/usr/share/doc/git/RelNotes/1.6.5.6.txt
/usr/share/doc/git/RelNotes/1.6.5.7.txt
/usr/share/doc/git/RelNotes/1.6.5.8.txt
/usr/share/doc/git/RelNotes/1.6.5.9.txt
/usr/share/doc/git/RelNotes/1.6.5.txt
/usr/share/doc/git/RelNotes/1.6.6.1.txt
/usr/share/doc/git/RelNotes/1.6.6.2.txt
/usr/share/doc/git/RelNotes/1.6.6.3.txt
/usr/share/doc/git/RelNotes/1.6.6.txt
/usr/share/doc/git/RelNotes/1.7.0.1.txt
/usr/share/doc/git/RelNotes/1.7.0.2.txt
/usr/share/doc/git/RelNotes/1.7.0.3.txt
/usr/share/doc/git/RelNotes/1.7.0.4.txt
/usr/share/doc/git/RelNotes/1.7.0.5.txt
/usr/share/doc/git/RelNotes/1.7.0.6.txt
/usr/share/doc/git/RelNotes/1.7.0.7.txt
/usr/share/doc/git/RelNotes/1.7.0.8.txt
/usr/share/doc/git/RelNotes/1.7.0.9.txt
/usr/share/doc/git/RelNotes/1.7.0.txt
/usr/share/doc/git/RelNotes/1.7.1.1.txt
/usr/share/doc/git/RelNotes/1.7.1.2.txt
/usr/share/doc/git/RelNotes/1.7.1.3.txt
/usr/share/doc/git/RelNotes/1.7.1.4.txt
/usr/share/doc/git/RelNotes/1.7.1.txt
/usr/share/doc/git/RelNotes/1.7.10.1.txt
/usr/share/doc/git/RelNotes/1.7.10.2.txt
/usr/share/doc/git/RelNotes/1.7.10.3.txt
/usr/share/doc/git/RelNotes/1.7.10.4.txt
/usr/share/doc/git/RelNotes/1.7.10.5.txt
/usr/share/doc/git/RelNotes/1.7.10.txt
/usr/share/doc/git/RelNotes/1.7.11.1.txt
/usr/share/doc/git/RelNotes/1.7.11.2.txt
/usr/share/doc/git/RelNotes/1.7.11.3.txt
/usr/share/doc/git/RelNotes/1.7.11.4.txt
/usr/share/doc/git/RelNotes/1.7.11.5.txt
/usr/share/doc/git/RelNotes/1.7.11.6.txt
/usr/share/doc/git/RelNotes/1.7.11.7.txt
/usr/share/doc/git/RelNotes/1.7.11.txt
/usr/share/doc/git/RelNotes/1.7.12.1.txt
/usr/share/doc/git/RelNotes/1.7.12.2.txt
/usr/share/doc/git/RelNotes/1.7.12.3.txt
/usr/share/doc/git/RelNotes/1.7.12.4.txt
/usr/share/doc/git/RelNotes/1.7.12.txt
/usr/share/doc/git/RelNotes/1.7.2.1.txt
/usr/share/doc/git/RelNotes/1.7.2.2.txt
/usr/share/doc/git/RelNotes/1.7.2.3.txt
/usr/share/doc/git/RelNotes/1.7.2.4.txt
/usr/share/doc/git/RelNotes/1.7.2.5.txt
/usr/share/doc/git/RelNotes/1.7.2.txt
/usr/share/doc/git/RelNotes/1.7.3.1.txt
/usr/share/doc/git/RelNotes/1.7.3.2.txt
/usr/share/doc/git/RelNotes/1.7.3.3.txt
/usr/share/doc/git/RelNotes/1.7.3.4.txt
/usr/share/doc/git/RelNotes/1.7.3.5.txt
/usr/share/doc/git/RelNotes/1.7.3.txt
/usr/share/doc/git/RelNotes/1.7.4.1.txt
/usr/share/doc/git/RelNotes/1.7.4.2.txt
/usr/share/doc/git/RelNotes/1.7.4.3.txt
/usr/share/doc/git/RelNotes/1.7.4.4.txt
/usr/share/doc/git/RelNotes/1.7.4.5.txt
/usr/share/doc/git/RelNotes/1.7.4.txt
/usr/share/doc/git/RelNotes/1.7.5.1.txt
/usr/share/doc/git/RelNotes/1.7.5.2.txt
/usr/share/doc/git/RelNotes/1.7.5.3.txt
/usr/share/doc/git/RelNotes/1.7.5.4.txt
/usr/share/doc/git/RelNotes/1.7.5.txt
/usr/share/doc/git/RelNotes/1.7.6.1.txt
/usr/share/doc/git/RelNotes/1.7.6.2.txt
/usr/share/doc/git/RelNotes/1.7.6.3.txt
/usr/share/doc/git/RelNotes/1.7.6.4.txt
/usr/share/doc/git/RelNotes/1.7.6.5.txt
/usr/share/doc/git/RelNotes/1.7.6.6.txt
/usr/share/doc/git/RelNotes/1.7.6.txt
/usr/share/doc/git/RelNotes/1.7.7.1.txt
/usr/share/doc/git/RelNotes/1.7.7.2.txt
/usr/share/doc/git/RelNotes/1.7.7.3.txt
/usr/share/doc/git/RelNotes/1.7.7.4.txt
/usr/share/doc/git/RelNotes/1.7.7.5.txt
/usr/share/doc/git/RelNotes/1.7.7.6.txt
/usr/share/doc/git/RelNotes/1.7.7.7.txt
/usr/share/doc/git/RelNotes/1.7.7.txt
/usr/share/doc/git/RelNotes/1.7.8.1.txt
/usr/share/doc/git/RelNotes/1.7.8.2.txt
/usr/share/doc/git/RelNotes/1.7.8.3.txt
/usr/share/doc/git/RelNotes/1.7.8.4.txt
/usr/share/doc/git/RelNotes/1.7.8.5.txt
/usr/share/doc/git/RelNotes/1.7.8.6.txt
/usr/share/doc/git/RelNotes/1.7.8.txt
/usr/share/doc/git/RelNotes/1.7.9.1.txt
/usr/share/doc/git/RelNotes/1.7.9.2.txt
/usr/share/doc/git/RelNotes/1.7.9.3.txt
/usr/share/doc/git/RelNotes/1.7.9.4.txt
/usr/share/doc/git/RelNotes/1.7.9.5.txt
/usr/share/doc/git/RelNotes/1.7.9.6.txt
/usr/share/doc/git/RelNotes/1.7.9.7.txt
/usr/share/doc/git/RelNotes/1.7.9.txt
/usr/share/doc/git/RelNotes/1.8.0.1.txt
/usr/share/doc/git/RelNotes/1.8.0.2.txt
/usr/share/doc/git/RelNotes/1.8.0.3.txt
/usr/share/doc/git/RelNotes/1.8.0.txt
/usr/share/doc/git/RelNotes/1.8.1.1.txt
/usr/share/doc/git/RelNotes/1.8.1.2.txt
/usr/share/doc/git/RelNotes/1.8.1.3.txt
/usr/share/doc/git/RelNotes/1.8.1.4.txt
/usr/share/doc/git/RelNotes/1.8.1.5.txt
/usr/share/doc/git/RelNotes/1.8.1.6.txt
/usr/share/doc/git/RelNotes/1.8.1.txt
/usr/share/doc/git/RelNotes/1.8.2.1.txt
/usr/share/doc/git/RelNotes/1.8.2.2.txt
/usr/share/doc/git/RelNotes/1.8.2.3.txt
/usr/share/doc/git/RelNotes/1.8.2.txt
/usr/share/doc/git/RelNotes/1.8.3.1.txt
/usr/share/doc/git/RelNotes/1.8.3.2.txt
/usr/share/doc/git/RelNotes/1.8.3.3.txt
/usr/share/doc/git/RelNotes/1.8.3.4.txt
/usr/share/doc/git/RelNotes/1.8.3.txt
/usr/share/doc/git/RelNotes/1.8.4.1.txt
/usr/share/doc/git/RelNotes/1.8.4.2.txt
/usr/share/doc/git/RelNotes/1.8.4.3.txt
/usr/share/doc/git/RelNotes/1.8.4.4.txt
/usr/share/doc/git/RelNotes/1.8.4.5.txt
/usr/share/doc/git/RelNotes/1.8.4.txt
/usr/share/doc/git/RelNotes/1.8.5.1.txt
/usr/share/doc/git/RelNotes/1.8.5.2.txt
/usr/share/doc/git/RelNotes/1.8.5.3.txt
/usr/share/doc/git/RelNotes/1.8.5.4.txt
/usr/share/doc/git/RelNotes/1.8.5.5.txt
/usr/share/doc/git/RelNotes/1.8.5.6.txt
/usr/share/doc/git/RelNotes/1.8.5.txt
/usr/share/doc/git/RelNotes/1.9.0.txt
/usr/share/doc/git/RelNotes/1.9.1.txt
/usr/share/doc/git/RelNotes/1.9.2.txt
/usr/share/doc/git/RelNotes/1.9.3.txt
/usr/share/doc/git/RelNotes/1.9.4.txt
/usr/share/doc/git/RelNotes/1.9.5.txt
/usr/share/doc/git/RelNotes/2.0.0.txt
/usr/share/doc/git/RelNotes/2.0.1.txt
/usr/share/doc/git/RelNotes/2.0.2.txt
/usr/share/doc/git/RelNotes/2.0.3.txt
/usr/share/doc/git/RelNotes/2.0.4.txt
/usr/share/doc/git/RelNotes/2.0.5.txt
/usr/share/doc/git/RelNotes/2.1.0.txt
/usr/share/doc/git/RelNotes/2.1.1.txt
/usr/share/doc/git/RelNotes/2.1.2.txt
/usr/share/doc/git/RelNotes/2.1.3.txt
/usr/share/doc/git/RelNotes/2.1.4.txt
/usr/share/doc/git/RelNotes/2.10.0.txt
/usr/share/doc/git/RelNotes/2.10.1.txt
/usr/share/doc/git/RelNotes/2.10.2.txt
/usr/share/doc/git/RelNotes/2.10.3.txt
/usr/share/doc/git/RelNotes/2.10.4.txt
/usr/share/doc/git/RelNotes/2.10.5.txt
/usr/share/doc/git/RelNotes/2.11.0.txt
/usr/share/doc/git/RelNotes/2.11.1.txt
/usr/share/doc/git/RelNotes/2.11.2.txt
/usr/share/doc/git/RelNotes/2.11.3.txt
/usr/share/doc/git/RelNotes/2.11.4.txt
/usr/share/doc/git/RelNotes/2.12.0.txt
/usr/share/doc/git/RelNotes/2.12.1.txt
/usr/share/doc/git/RelNotes/2.12.2.txt
/usr/share/doc/git/RelNotes/2.12.3.txt
/usr/share/doc/git/RelNotes/2.12.4.txt
/usr/share/doc/git/RelNotes/2.12.5.txt
/usr/share/doc/git/RelNotes/2.13.0.txt
/usr/share/doc/git/RelNotes/2.13.1.txt
/usr/share/doc/git/RelNotes/2.13.2.txt
/usr/share/doc/git/RelNotes/2.13.3.txt
/usr/share/doc/git/RelNotes/2.13.4.txt
/usr/share/doc/git/RelNotes/2.13.5.txt
/usr/share/doc/git/RelNotes/2.13.6.txt
/usr/share/doc/git/RelNotes/2.13.7.txt
/usr/share/doc/git/RelNotes/2.14.0.txt
/usr/share/doc/git/RelNotes/2.14.1.txt
/usr/share/doc/git/RelNotes/2.14.2.txt
/usr/share/doc/git/RelNotes/2.14.3.txt
/usr/share/doc/git/RelNotes/2.14.4.txt
/usr/share/doc/git/RelNotes/2.14.5.txt
/usr/share/doc/git/RelNotes/2.14.6.txt
/usr/share/doc/git/RelNotes/2.15.0.txt
/usr/share/doc/git/RelNotes/2.15.1.txt
/usr/share/doc/git/RelNotes/2.15.2.txt
/usr/share/doc/git/RelNotes/2.15.3.txt
/usr/share/doc/git/RelNotes/2.15.4.txt
/usr/share/doc/git/RelNotes/2.16.0.txt
/usr/share/doc/git/RelNotes/2.16.1.txt
/usr/share/doc/git/RelNotes/2.16.2.txt
/usr/share/doc/git/RelNotes/2.16.3.txt
/usr/share/doc/git/RelNotes/2.16.4.txt
/usr/share/doc/git/RelNotes/2.16.5.txt
/usr/share/doc/git/RelNotes/2.16.6.txt
/usr/share/doc/git/RelNotes/2.17.0.txt
/usr/share/doc/git/RelNotes/2.17.1.txt
/usr/share/doc/git/RelNotes/2.17.2.txt
/usr/share/doc/git/RelNotes/2.17.3.txt
/usr/share/doc/git/RelNotes/2.17.4.txt
/usr/share/doc/git/RelNotes/2.17.5.txt
/usr/share/doc/git/RelNotes/2.17.6.txt
/usr/share/doc/git/RelNotes/2.18.0.txt
/usr/share/doc/git/RelNotes/2.18.1.txt
/usr/share/doc/git/RelNotes/2.18.2.txt
/usr/share/doc/git/RelNotes/2.18.3.txt
/usr/share/doc/git/RelNotes/2.18.4.txt
/usr/share/doc/git/RelNotes/2.18.5.txt
/usr/share/doc/git/RelNotes/2.19.0.txt
/usr/share/doc/git/RelNotes/2.19.1.txt
/usr/share/doc/git/RelNotes/2.19.2.txt
/usr/share/doc/git/RelNotes/2.19.3.txt
/usr/share/doc/git/RelNotes/2.19.4.txt
/usr/share/doc/git/RelNotes/2.19.5.txt
/usr/share/doc/git/RelNotes/2.19.6.txt
/usr/share/doc/git/RelNotes/2.2.0.txt
/usr/share/doc/git/RelNotes/2.2.1.txt
/usr/share/doc/git/RelNotes/2.2.2.txt
/usr/share/doc/git/RelNotes/2.2.3.txt
/usr/share/doc/git/RelNotes/2.20.0.txt
/usr/share/doc/git/RelNotes/2.20.1.txt
/usr/share/doc/git/RelNotes/2.20.2.txt
/usr/share/doc/git/RelNotes/2.20.3.txt
/usr/share/doc/git/RelNotes/2.20.4.txt
/usr/share/doc/git/RelNotes/2.20.5.txt
/usr/share/doc/git/RelNotes/2.21.0.txt
/usr/share/doc/git/RelNotes/2.21.1.txt
/usr/share/doc/git/RelNotes/2.21.2.txt
/usr/share/doc/git/RelNotes/2.21.3.txt
/usr/share/doc/git/RelNotes/2.21.4.txt
/usr/share/doc/git/RelNotes/2.22.0.txt
/usr/share/doc/git/RelNotes/2.22.1.txt
/usr/share/doc/git/RelNotes/2.22.2.txt
/usr/share/doc/git/RelNotes/2.22.3.txt
/usr/share/doc/git/RelNotes/2.22.4.txt
/usr/share/doc/git/RelNotes/2.22.5.txt
/usr/share/doc/git/RelNotes/2.23.0.txt
/usr/share/doc/git/RelNotes/2.23.1.txt
/usr/share/doc/git/RelNotes/2.23.2.txt
/usr/share/doc/git/RelNotes/2.23.3.txt
/usr/share/doc/git/RelNotes/2.23.4.txt
/usr/share/doc/git/RelNotes/2.24.0.txt
/usr/share/doc/git/RelNotes/2.24.1.txt
/usr/share/doc/git/RelNotes/2.24.2.txt
/usr/share/doc/git/RelNotes/2.24.3.txt
/usr/share/doc/git/RelNotes/2.24.4.txt
/usr/share/doc/git/RelNotes/2.25.0.txt
/usr/share/doc/git/RelNotes/2.25.1.txt
/usr/share/doc/git/RelNotes/2.25.2.txt
/usr/share/doc/git/RelNotes/2.25.3.txt
/usr/share/doc/git/RelNotes/2.25.4.txt
/usr/share/doc/git/RelNotes/2.25.5.txt
/usr/share/doc/git/RelNotes/2.26.0.txt
/usr/share/doc/git/RelNotes/2.26.1.txt
/usr/share/doc/git/RelNotes/2.26.2.txt
/usr/share/doc/git/RelNotes/2.26.3.txt
/usr/share/doc/git/RelNotes/2.27.0.txt
/usr/share/doc/git/RelNotes/2.27.1.txt
/usr/share/doc/git/RelNotes/2.28.0.txt
/usr/share/doc/git/RelNotes/2.28.1.txt
/usr/share/doc/git/RelNotes/2.29.0.txt
/usr/share/doc/git/RelNotes/2.29.1.txt
/usr/share/doc/git/RelNotes/2.29.2.txt
/usr/share/doc/git/RelNotes/2.29.3.txt
/usr/share/doc/git/RelNotes/2.3.0.txt
/usr/share/doc/git/RelNotes/2.3.1.txt
/usr/share/doc/git/RelNotes/2.3.10.txt
/usr/share/doc/git/RelNotes/2.3.2.txt
/usr/share/doc/git/RelNotes/2.3.3.txt
/usr/share/doc/git/RelNotes/2.3.4.txt
/usr/share/doc/git/RelNotes/2.3.5.txt
/usr/share/doc/git/RelNotes/2.3.6.txt
/usr/share/doc/git/RelNotes/2.3.7.txt
/usr/share/doc/git/RelNotes/2.3.8.txt
/usr/share/doc/git/RelNotes/2.3.9.txt
/usr/share/doc/git/RelNotes/2.30.0.txt
/usr/share/doc/git/RelNotes/2.30.1.txt
/usr/share/doc/git/RelNotes/2.30.2.txt
/usr/share/doc/git/RelNotes/2.30.3.txt
/usr/share/doc/git/RelNotes/2.30.4.txt
/usr/share/doc/git/RelNotes/2.30.5.txt
/usr/share/doc/git/RelNotes/2.30.6.txt
/usr/share/doc/git/RelNotes/2.30.7.txt
/usr/share/doc/git/RelNotes/2.30.8.txt
/usr/share/doc/git/RelNotes/2.30.9.txt
/usr/share/doc/git/RelNotes/2.31.0.txt
/usr/share/doc/git/RelNotes/2.31.1.txt
/usr/share/doc/git/RelNotes/2.31.2.txt
/usr/share/doc/git/RelNotes/2.31.3.txt
/usr/share/doc/git/RelNotes/2.31.4.txt
/usr/share/doc/git/RelNotes/2.31.5.txt
/usr/share/doc/git/RelNotes/2.31.6.txt
/usr/share/doc/git/RelNotes/2.31.7.txt
/usr/share/doc/git/RelNotes/2.31.8.txt
/usr/share/doc/git/RelNotes/2.32.0.txt
/usr/share/doc/git/RelNotes/2.32.1.txt
/usr/share/doc/git/RelNotes/2.32.2.txt
/usr/share/doc/git/RelNotes/2.32.3.txt
/usr/share/doc/git/RelNotes/2.32.4.txt
/usr/share/doc/git/RelNotes/2.32.5.txt
/usr/share/doc/git/RelNotes/2.32.6.txt
/usr/share/doc/git/RelNotes/2.32.7.txt
/usr/share/doc/git/RelNotes/2.33.0.txt
/usr/share/doc/git/RelNotes/2.33.1.txt
/usr/share/doc/git/RelNotes/2.33.2.txt
/usr/share/doc/git/RelNotes/2.33.3.txt
/usr/share/doc/git/RelNotes/2.33.4.txt
/usr/share/doc/git/RelNotes/2.33.5.txt
/usr/share/doc/git/RelNotes/2.33.6.txt
/usr/share/doc/git/RelNotes/2.33.7.txt
/usr/share/doc/git/RelNotes/2.33.8.txt
/usr/share/doc/git/RelNotes/2.34.0.txt
/usr/share/doc/git/RelNotes/2.34.1.txt
/usr/share/doc/git/RelNotes/2.34.2.txt
/usr/share/doc/git/RelNotes/2.34.3.txt
/usr/share/doc/git/RelNotes/2.34.4.txt
/usr/share/doc/git/RelNotes/2.34.5.txt
/usr/share/doc/git/RelNotes/2.34.6.txt
/usr/share/doc/git/RelNotes/2.34.7.txt
/usr/share/doc/git/RelNotes/2.34.8.txt
/usr/share/doc/git/RelNotes/2.35.0.txt
/usr/share/doc/git/RelNotes/2.35.1.txt
/usr/share/doc/git/RelNotes/2.35.2.txt
/usr/share/doc/git/RelNotes/2.35.3.txt
/usr/share/doc/git/RelNotes/2.35.4.txt
/usr/share/doc/git/RelNotes/2.35.5.txt
/usr/share/doc/git/RelNotes/2.35.6.txt
/usr/share/doc/git/RelNotes/2.35.7.txt
/usr/share/doc/git/RelNotes/2.35.8.txt
/usr/share/doc/git/RelNotes/2.36.0.txt
/usr/share/doc/git/RelNotes/2.36.1.txt
/usr/share/doc/git/RelNotes/2.36.2.txt
/usr/share/doc/git/RelNotes/2.36.3.txt
/usr/share/doc/git/RelNotes/2.36.4.txt
/usr/share/doc/git/RelNotes/2.36.5.txt
/usr/share/doc/git/RelNotes/2.36.6.txt
/usr/share/doc/git/RelNotes/2.37.0.txt
/usr/share/doc/git/RelNotes/2.37.1.txt
/usr/share/doc/git/RelNotes/2.37.2.txt
/usr/share/doc/git/RelNotes/2.37.3.txt
/usr/share/doc/git/RelNotes/2.37.4.txt
/usr/share/doc/git/RelNotes/2.37.5.txt
/usr/share/doc/git/RelNotes/2.37.6.txt
/usr/share/doc/git/RelNotes/2.37.7.txt
/usr/share/doc/git/RelNotes/2.38.0.txt
/usr/share/doc/git/RelNotes/2.38.1.txt
/usr/share/doc/git/RelNotes/2.38.2.txt
/usr/share/doc/git/RelNotes/2.38.3.txt
/usr/share/doc/git/RelNotes/2.38.4.txt
/usr/share/doc/git/RelNotes/2.38.5.txt
/usr/share/doc/git/RelNotes/2.39.0.txt
/usr/share/doc/git/RelNotes/2.39.1.txt
/usr/share/doc/git/RelNotes/2.39.2.txt
/usr/share/doc/git/RelNotes/2.39.3.txt
/usr/share/doc/git/RelNotes/2.4.0.txt
/usr/share/doc/git/RelNotes/2.4.1.txt
/usr/share/doc/git/RelNotes/2.4.10.txt
/usr/share/doc/git/RelNotes/2.4.11.txt
/usr/share/doc/git/RelNotes/2.4.12.txt
/usr/share/doc/git/RelNotes/2.4.2.txt
/usr/share/doc/git/RelNotes/2.4.3.txt
/usr/share/doc/git/RelNotes/2.4.4.txt
/usr/share/doc/git/RelNotes/2.4.5.txt
/usr/share/doc/git/RelNotes/2.4.6.txt
/usr/share/doc/git/RelNotes/2.4.7.txt
/usr/share/doc/git/RelNotes/2.4.8.txt
/usr/share/doc/git/RelNotes/2.4.9.txt
/usr/share/doc/git/RelNotes/2.40.0.txt
/usr/share/doc/git/RelNotes/2.40.1.txt
/usr/share/doc/git/RelNotes/2.41.0.txt
/usr/share/doc/git/RelNotes/2.42.0.txt
/usr/share/doc/git/RelNotes/2.42.1.txt
/usr/share/doc/git/RelNotes/2.43.0.txt
/usr/share/doc/git/RelNotes/2.5.0.txt
/usr/share/doc/git/RelNotes/2.5.1.txt
/usr/share/doc/git/RelNotes/2.5.2.txt
/usr/share/doc/git/RelNotes/2.5.3.txt
/usr/share/doc/git/RelNotes/2.5.4.txt
/usr/share/doc/git/RelNotes/2.5.5.txt
/usr/share/doc/git/RelNotes/2.5.6.txt
/usr/share/doc/git/RelNotes/2.6.0.txt
/usr/share/doc/git/RelNotes/2.6.1.txt
/usr/share/doc/git/RelNotes/2.6.2.txt
/usr/share/doc/git/RelNotes/2.6.3.txt
/usr/share/doc/git/RelNotes/2.6.4.txt
/usr/share/doc/git/RelNotes/2.6.5.txt
/usr/share/doc/git/RelNotes/2.6.6.txt
/usr/share/doc/git/RelNotes/2.6.7.txt
/usr/share/doc/git/RelNotes/2.7.0.txt
/usr/share/doc/git/RelNotes/2.7.1.txt
/usr/share/doc/git/RelNotes/2.7.2.txt
/usr/share/doc/git/RelNotes/2.7.3.txt
/usr/share/doc/git/RelNotes/2.7.4.txt
/usr/share/doc/git/RelNotes/2.7.5.txt
/usr/share/doc/git/RelNotes/2.7.6.txt
/usr/share/doc/git/RelNotes/2.8.0.txt
/usr/share/doc/git/RelNotes/2.8.1.txt
/usr/share/doc/git/RelNotes/2.8.2.txt
/usr/share/doc/git/RelNotes/2.8.3.txt
/usr/share/doc/git/RelNotes/2.8.4.txt
/usr/share/doc/git/RelNotes/2.8.5.txt
/usr/share/doc/git/RelNotes/2.8.6.txt
/usr/share/doc/git/RelNotes/2.9.0.txt
/usr/share/doc/git/RelNotes/2.9.1.txt
/usr/share/doc/git/RelNotes/2.9.2.txt
/usr/share/doc/git/RelNotes/2.9.3.txt
/usr/share/doc/git/RelNotes/2.9.4.txt
/usr/share/doc/git/RelNotes/2.9.5.txt
/usr/share/doc/git/contrib/buildsystems/CMakeLists.txt
/usr/share/doc/git/contrib/contacts/git-contacts.txt
/usr/share/doc/git/contrib/hg-to-git/hg-to-git.txt
/usr/share/doc/git/contrib/subtree/git-subtree.txt
/usr/share/doc/gnupg/examples/qualified.txt
/usr/share/doc/gnupg/examples/trustlist.txt
/usr/share/doc/gpg-agent/examples/trustlist.txt
/usr/share/doc/libbpfcc/FAQ.txt
/usr/share/doc/libdb5.3t64/build_signature_amd64.txt
/usr/share/doc/lvm2/lvmpolld_overview.txt
/usr/share/doc/lvm2/pvmove_outline.txt
/usr/share/doc/lvm2/testing.txt
/usr/share/doc/lvm2/udev_assembly.txt
/usr/share/doc/mount/mount.txt
/usr/share/doc/openssl/fingerprints.txt
/usr/share/doc/openssl/HOWTO/keys.txt
/usr/share/doc/powermgmt-base/power_supply.txt
/usr/share/doc/publicsuffix/examples/test_psl.txt
/usr/share/doc/python3-botocore/requirements.txt
/usr/share/doc/sg3-utils/examples/forwarded_sense.txt
/usr/share/doc/sg3-utils/examples/reassign_addr.txt
/usr/share/doc/sg3-utils/examples/ref_sense.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p0_cjtpat.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p0_prbs9.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p1_cjtpat.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p1_idle.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p1_prbs15.txt
/usr/share/doc/sg3-utils/examples/sdiag_sas_p1_stop.txt
/usr/share/doc/sg3-utils/examples/sg_compare_and_write.txt
/usr/share/doc/sg3-utils/examples/sg_unmap_example.txt
/usr/share/doc/sg3-utils/examples/transport_ids.txt
/usr/share/doc/util-linux/00-about-docs.txt
/usr/share/doc/util-linux/PAM-configuration.txt
/usr/share/doc/util-linux/blkid.txt
/usr/share/doc/util-linux/cal.txt
/usr/share/doc/util-linux/col.txt
/usr/share/doc/util-linux/deprecated.txt
/usr/share/doc/util-linux/getopt.txt
/usr/share/doc/util-linux/getopt_changelog.txt
/usr/share/doc/util-linux/howto-build-sys.txt
/usr/share/doc/util-linux/howto-compilation.txt
/usr/share/doc/util-linux/howto-debug.txt
/usr/share/doc/util-linux/howto-man-page.txt
/usr/share/doc/util-linux/howto-tests.txt
/usr/share/doc/util-linux/hwclock.txt
/usr/share/doc/util-linux/modems-with-agetty.txt
/usr/share/doc/util-linux/mount.txt
/usr/share/doc/util-linux/pg.txt
/usr/share/doc/util-linux/release-schedule.txt
/usr/share/gnupg/help.be.txt
/usr/share/gnupg/help.ca.txt
/usr/share/gnupg/help.cs.txt
/usr/share/gnupg/help.da.txt
/usr/share/gnupg/help.de.txt
/usr/share/gnupg/help.el.txt
/usr/share/gnupg/help.eo.txt
/usr/share/gnupg/help.es.txt
/usr/share/gnupg/help.et.txt
/usr/share/gnupg/help.fi.txt
/usr/share/gnupg/help.fr.txt
/usr/share/gnupg/help.gl.txt
/usr/share/gnupg/help.hu.txt
/usr/share/gnupg/help.id.txt
/usr/share/gnupg/help.it.txt
/usr/share/gnupg/help.ja.txt
/usr/share/gnupg/help.nb.txt
/usr/share/gnupg/help.pl.txt
/usr/share/gnupg/help.pt.txt
/usr/share/gnupg/help.pt_BR.txt
/usr/share/gnupg/help.ro.txt
/usr/share/gnupg/help.ru.txt
/usr/share/gnupg/help.sk.txt
/usr/share/gnupg/help.sv.txt
/usr/share/gnupg/help.tr.txt
/usr/share/gnupg/help.txt
/usr/share/gnupg/help.zh_CN.txt
/usr/share/gnupg/help.zh_TW.txt
/usr/share/ieee-data/iab.txt
/usr/share/ieee-data/mam.txt
/usr/share/ieee-data/oui.txt
/usr/share/ieee-data/oui36.txt
/usr/share/libcaca/caca.txt
/usr/share/netpbm/rgb.txt
/usr/share/perl/5.38.2/Unicode/Collate/allkeys.txt
/usr/share/perl/5.38.2/Unicode/Collate/keys.txt
/usr/share/perl/5.38.2/unicore/Blocks.txt
/usr/share/perl/5.38.2/unicore/NamedSequences.txt
/usr/share/perl/5.38.2/unicore/SpecialCasing.txt
/usr/share/vim/vim91/doc/arabic.txt
/usr/share/vim/vim91/doc/autocmd.txt
/usr/share/vim/vim91/doc/builtin.txt
/usr/share/vim/vim91/doc/change.txt
/usr/share/vim/vim91/doc/channel.txt
/usr/share/vim/vim91/doc/cmdline.txt
/usr/share/vim/vim91/doc/debug.txt
/usr/share/vim/vim91/doc/debugger.txt
/usr/share/vim/vim91/doc/develop.txt
/usr/share/vim/vim91/doc/diff.txt
/usr/share/vim/vim91/doc/digraph.txt
/usr/share/vim/vim91/doc/editing.txt
/usr/share/vim/vim91/doc/eval.txt
/usr/share/vim/vim91/doc/farsi.txt
/usr/share/vim/vim91/doc/filetype.txt
/usr/share/vim/vim91/doc/fold.txt
/usr/share/vim/vim91/doc/ft_ada.txt
/usr/share/vim/vim91/doc/ft_context.txt
/usr/share/vim/vim91/doc/ft_mp.txt
/usr/share/vim/vim91/doc/ft_ps1.txt
/usr/share/vim/vim91/doc/ft_raku.txt
/usr/share/vim/vim91/doc/ft_rust.txt
/usr/share/vim/vim91/doc/ft_sql.txt
/usr/share/vim/vim91/doc/gui.txt
/usr/share/vim/vim91/doc/gui_w32.txt
/usr/share/vim/vim91/doc/gui_x11.txt
/usr/share/vim/vim91/doc/hangulin.txt
/usr/share/vim/vim91/doc/hebrew.txt
/usr/share/vim/vim91/doc/help.txt
/usr/share/vim/vim91/doc/helphelp.txt
/usr/share/vim/vim91/doc/howto.txt
/usr/share/vim/vim91/doc/if_cscop.txt
/usr/share/vim/vim91/doc/if_lua.txt
/usr/share/vim/vim91/doc/if_mzsch.txt
/usr/share/vim/vim91/doc/if_ole.txt
/usr/share/vim/vim91/doc/if_perl.txt
/usr/share/vim/vim91/doc/if_pyth.txt
/usr/share/vim/vim91/doc/if_ruby.txt
/usr/share/vim/vim91/doc/if_sniff.txt
/usr/share/vim/vim91/doc/if_tcl.txt
/usr/share/vim/vim91/doc/indent.txt
/usr/share/vim/vim91/doc/index.txt
/usr/share/vim/vim91/doc/insert.txt
/usr/share/vim/vim91/doc/intro.txt
/usr/share/vim/vim91/doc/map.txt
/usr/share/vim/vim91/doc/mbyte.txt
/usr/share/vim/vim91/doc/message.txt
/usr/share/vim/vim91/doc/mlang.txt
/usr/share/vim/vim91/doc/motion.txt
/usr/share/vim/vim91/doc/netbeans.txt
/usr/share/vim/vim91/doc/options.txt
/usr/share/vim/vim91/doc/os_390.txt
/usr/share/vim/vim91/doc/os_amiga.txt
/usr/share/vim/vim91/doc/os_beos.txt
/usr/share/vim/vim91/doc/os_dos.txt
/usr/share/vim/vim91/doc/os_haiku.txt
/usr/share/vim/vim91/doc/os_mac.txt
/usr/share/vim/vim91/doc/os_mint.txt
/usr/share/vim/vim91/doc/os_msdos.txt
/usr/share/vim/vim91/doc/os_os2.txt
/usr/share/vim/vim91/doc/os_qnx.txt
/usr/share/vim/vim91/doc/os_risc.txt
/usr/share/vim/vim91/doc/os_unix.txt
/usr/share/vim/vim91/doc/os_vms.txt
/usr/share/vim/vim91/doc/os_win32.txt
/usr/share/vim/vim91/doc/pattern.txt
/usr/share/vim/vim91/doc/pi_getscript.txt
/usr/share/vim/vim91/doc/pi_gzip.txt
/usr/share/vim/vim91/doc/pi_logipat.txt
/usr/share/vim/vim91/doc/pi_netrw.txt
/usr/share/vim/vim91/doc/pi_paren.txt
/usr/share/vim/vim91/doc/pi_spec.txt
/usr/share/vim/vim91/doc/pi_tar.txt
/usr/share/vim/vim91/doc/pi_vimball.txt
/usr/share/vim/vim91/doc/pi_zip.txt
/usr/share/vim/vim91/doc/popup.txt
/usr/share/vim/vim91/doc/print.txt
/usr/share/vim/vim91/doc/quickfix.txt
/usr/share/vim/vim91/doc/quickref.txt
/usr/share/vim/vim91/doc/quotes.txt
/usr/share/vim/vim91/doc/recover.txt
/usr/share/vim/vim91/doc/remote.txt
/usr/share/vim/vim91/doc/repeat.txt
/usr/share/vim/vim91/doc/rileft.txt
/usr/share/vim/vim91/doc/russian.txt
/usr/share/vim/vim91/doc/scroll.txt
/usr/share/vim/vim91/doc/sign.txt
/usr/share/vim/vim91/doc/spell.txt
/usr/share/vim/vim91/doc/sponsor.txt
/usr/share/vim/vim91/doc/starting.txt
/usr/share/vim/vim91/doc/syntax.txt
/usr/share/vim/vim91/doc/tabpage.txt
/usr/share/vim/vim91/doc/tagsrch.txt
/usr/share/vim/vim91/doc/term.txt
/usr/share/vim/vim91/doc/terminal.txt
/usr/share/vim/vim91/doc/testing.txt
/usr/share/vim/vim91/doc/textprop.txt
/usr/share/vim/vim91/doc/tips.txt
/usr/share/vim/vim91/doc/todo.txt
/usr/share/vim/vim91/doc/uganda.txt
/usr/share/vim/vim91/doc/undo.txt
/usr/share/vim/vim91/doc/userfunc.txt
/usr/share/vim/vim91/doc/usr_01.txt
/usr/share/vim/vim91/doc/usr_02.txt
/usr/share/vim/vim91/doc/usr_03.txt
/usr/share/vim/vim91/doc/usr_04.txt
/usr/share/vim/vim91/doc/usr_05.txt
/usr/share/vim/vim91/doc/usr_06.txt
/usr/share/vim/vim91/doc/usr_07.txt
/usr/share/vim/vim91/doc/usr_08.txt
/usr/share/vim/vim91/doc/usr_09.txt
/usr/share/vim/vim91/doc/usr_10.txt
/usr/share/vim/vim91/doc/usr_11.txt
/usr/share/vim/vim91/doc/usr_12.txt
/usr/share/vim/vim91/doc/usr_20.txt
/usr/share/vim/vim91/doc/usr_21.txt
/usr/share/vim/vim91/doc/usr_22.txt
/usr/share/vim/vim91/doc/usr_23.txt
/usr/share/vim/vim91/doc/usr_24.txt
/usr/share/vim/vim91/doc/usr_25.txt
/usr/share/vim/vim91/doc/usr_26.txt
/usr/share/vim/vim91/doc/usr_27.txt
/usr/share/vim/vim91/doc/usr_28.txt
/usr/share/vim/vim91/doc/usr_29.txt
/usr/share/vim/vim91/doc/usr_30.txt
/usr/share/vim/vim91/doc/usr_31.txt
/usr/share/vim/vim91/doc/usr_32.txt
/usr/share/vim/vim91/doc/usr_40.txt
/usr/share/vim/vim91/doc/usr_41.txt
/usr/share/vim/vim91/doc/usr_42.txt
/usr/share/vim/vim91/doc/usr_43.txt
/usr/share/vim/vim91/doc/usr_44.txt
/usr/share/vim/vim91/doc/usr_45.txt
/usr/share/vim/vim91/doc/usr_50.txt
/usr/share/vim/vim91/doc/usr_51.txt
/usr/share/vim/vim91/doc/usr_52.txt
/usr/share/vim/vim91/doc/usr_90.txt
/usr/share/vim/vim91/doc/usr_toc.txt
/usr/share/vim/vim91/doc/various.txt
/usr/share/vim/vim91/doc/version4.txt
/usr/share/vim/vim91/doc/version5.txt
/usr/share/vim/vim91/doc/version6.txt
/usr/share/vim/vim91/doc/version7.txt
/usr/share/vim/vim91/doc/version8.txt
/usr/share/vim/vim91/doc/version9.txt
/usr/share/vim/vim91/doc/vi_diff.txt
/usr/share/vim/vim91/doc/vim9.txt
/usr/share/vim/vim91/doc/vim9class.txt
/usr/share/vim/vim91/doc/visual.txt
/usr/share/vim/vim91/doc/windows.txt
/usr/share/vim/vim91/doc/workshop.txt
/usr/share/vim/vim91/pack/dist/opt/editorconfig/doc/editorconfig.txt
/usr/share/vim/vim91/pack/dist/opt/matchit/doc/matchit.txt
/usr/share/vim/vim91/tutor/README.ru.utf-8.txt
/usr/src/linux-headers-6.8.0-100/arch/sh/include/mach-ecovec24/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.8.0-100/arch/sh/include/mach-kfr2r09/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.8.0-100/scripts/head-object-list.txt
/usr/src/linux-headers-6.8.0-100/scripts/spelling.txt
/usr/src/linux-headers-6.8.0-100-generic/scripts/head-object-list.txt
/usr/src/linux-headers-6.8.0-100-generic/scripts/spelling.txt
/usr/src/linux-headers-6.8.0-101/arch/sh/include/mach-ecovec24/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.8.0-101/arch/sh/include/mach-kfr2r09/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.8.0-101/scripts/head-object-list.txt
/usr/src/linux-headers-6.8.0-101/scripts/spelling.txt
/usr/src/linux-headers-6.8.0-101-generic/scripts/head-object-list.txt
/usr/src/linux-headers-6.8.0-101-generic/scripts/spelling.txt
/var/lib/cloud/instances/iid-datasource-none/cloud-config.txt
/var/lib/cloud/instances/iid-datasource-none/user-data.txt
/var/lib/cloud/instances/iid-datasource-none/vendor-data.txt
/var/lib/cloud/instances/iid-datasource-none/vendor-data2.txt
/var/lib/ieee-data/iab.txt
/var/lib/ieee-data/mam.txt
/var/lib/ieee-data/oui.txt
/var/lib/ieee-data/oui36.txt
pluto@Ubuntu-Server-Lab:~$
```

## Latihan  
1. Cobalah urutan perintah berikut:

```markdown
pluto@Ubuntu-Server-Lab:~$ cd
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ ls -al
total 128
drwxr-x--- 8 pluto pluto  4096 Mar  4 13:07 .
drwxr-xr-x 3 root  root   4096 Feb 12 01:53 ..
-rw-rw-r-- 1 pluto pluto  5493 Mar  1 17:23 backup-error.log
-rwxrwxr-x 1 pluto pluto   974 Mar  1 17:29 backup.sh
-rw-rw-r-- 1 pluto pluto    98 Mar  1 17:13 backup-success.log
-rw------- 1 pluto pluto 16468 Mar  4 04:44 .bash_history
-rw-r--r-- 1 pluto pluto   220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 pluto pluto  3771 Mar 31  2024 .bashrc
drwx------ 2 pluto pluto  4096 Feb 12 02:00 .cache
drwx------ 5 pluto pluto  4096 Feb 24 17:43 .config
-rw-rw-r-- 1 pluto pluto 14494 Mar  1 17:03 daftar_conf.txt
-rw-rw-r-- 1 pluto pluto   206 Mar  1 14:38 error.log
-rw-rw-r-- 1 pluto pluto    20 Feb 25 04:14 hello.txt
-rw-rw-r-- 1 pluto pluto   763 Mar  1 14:38 large-logs.txt
-rw------- 1 pluto pluto    20 Feb 25 04:28 .lesshst
drwxrwxr-x 3 pluto pluto  4096 Mar  1 15:34 .local
-rw-rw-r-- 1 pluto pluto  1504 Mar  1 15:43 monitor.log
-rwxrwxr-x 1 pluto pluto     1 Mar  1 16:49 monitor.sh
drwxrwxr-x 3 pluto pluto  4096 Feb 24 08:43 praktikum-os
-rw-r--r-- 1 pluto pluto   807 Mar 31  2024 .profile
-rw-rw-r-- 1 pluto pluto   419 Feb 24 13:34 server.log
drwxrwxr-x 2 pluto pluto  4096 Mar  4 13:07 SistemOperasi
-rw-rw-r-- 1 pluto pluto   248 Mar  1 14:49 sorted-users.txt
drwx------ 2 pluto pluto  4096 Feb 12 01:53 .ssh
-rw-r--r-- 1 pluto pluto     0 Feb 12 02:01 .sudo_as_admin_successful
pluto@Ubuntu-Server-Lab:~$ cd .
pluto@Ubuntu-Server-Lab:~$ pwd
/home/pluto
pluto@Ubuntu-Server-Lab:~$ cd ..
pluto@Ubuntu-Server-Lab:/home$ pwd
/home
pluto@Ubuntu-Server-Lab:/home$ ls -al
total 12
drwxr-xr-x  3 root  root  4096 Feb 12 01:53 .
drwxr-xr-x 24 root  root  4096 Mar  1 17:30 ..
drwxr-x---  8 pluto pluto 4096 Mar  4 13:07 pluto
pluto@Ubuntu-Server-Lab:/home$ cd /etc
pluto@Ubuntu-Server-Lab:/etc$ ls -al | more
total 964
drwxr-xr-x 112 root root       4096 Mar  4 13:12 .
drwxr-xr-x  24 root root       4096 Mar  1 17:30 ..
-rw-r--r--   1 root root       3444 Jul  5  2023 adduser.conf
drwxr-xr-x   2 root root       4096 Mar  4 13:12 alternatives
drwxr-xr-x   2 root root       4096 Feb 12 02:09 apparmor
drwxr-xr-x   9 root root      12288 Feb 12 02:10 apparmor.d
drwxr-xr-x   3 root root       4096 Aug  5  2025 apport
drwxr-xr-x   9 root root       4096 Feb 12 01:43 apt
-rw-r--r--   1 root root       2319 Mar 31  2024 bash.bashrc
-rw-r--r--   1 root root         45 Aug  5  2025 bash_completion
drwxr-xr-x   2 root root       4096 Aug  5  2025 bash_completion.d
-rw-r--r--   1 root root        367 Aug  2  2022 bindresvport.blacklist
drwxr-xr-x   2 root root       4096 Jul  2  2025 binfmt.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 byobu
drwxr-xr-x   3 root root       4096 Aug  5  2025 ca-certificates
-rw-r--r--   1 root root       6288 Aug  5  2025 ca-certificates.conf
drwxr-xr-x   5 root root       4096 Feb 24 21:21 cloud
drwxr-xr-x   2 root root       4096 Feb 12 01:46 console-setup
drwx------   2 root root       4096 Jul  2  2025 credstore
drwx------   2 root root       4096 Jul  2  2025 credstore.encrypted
drwxr-xr-x   2 root root       4096 Aug  5  2025 cron.d
drwxr-xr-x   2 root root       4096 Mar  4 13:12 cron.daily
drwxr-xr-x   2 root root       4096 Aug  5  2025 cron.hourly
drwxr-xr-x   2 root root       4096 Aug  5  2025 cron.monthly
-rw-r--r--   1 root root       1136 Aug  5  2025 crontab
drwxr-xr-x   2 root root       4096 Aug  5  2025 cron.weekly
drwxr-xr-x   2 root root       4096 Aug  5  2025 cron.yearly
drwxr-xr-x   2 root root       4096 Aug  5  2025 cryptsetup-initramfs
-rw-r--r--   1 root root         54 Aug  5  2025 crypttab
drwxr-xr-x   4 root root       4096 Aug  5  2025 dbus-1
-rw-r--r--   1 root root       2967 Apr 12  2024 debconf.conf
-rw-r--r--   1 root root         11 Apr 22  2024 debian_version
drwxr-xr-x   3 root root       4096 Feb 12 02:13 default
-rw-r--r--   1 root root       1706 Jul  5  2023 deluser.conf
drwxr-xr-x   2 root root       4096 Aug  5  2025 depmod.d
drwxr-xr-x   3 root root       4096 Aug  5  2025 dhcp
-rw-r--r--   1 root root       1429 May  7  2024 dhcpcd.conf
drwxr-xr-x   4 root root       4096 Feb 12 02:07 dpkg
-rw-r--r--   1 root root        685 Apr  8  2024 e2scrub.conf
-rw-r--r--   1 root root        106 Aug  5  2025 environment
-rw-r--r--   1 root root       1853 Oct 17  2022 ethertypes
drwxr-xr-x   4 root root       4096 Feb 12 01:47 fonts
-rw-r--r--   1 root root        446 Feb 12 01:48 fstab
-rw-r--r--   1 root root        694 Apr  8  2024 fuse.conf
drwxr-xr-x   4 root root       4096 Feb 12 02:10 fwupd
-rw-r--r--   1 root root       2584 Jan 31  2024 gai.conf
drwxr-xr-x   4 root root       4096 Feb 24 16:01 ghostscript
drwxr-xr-x   2 root root       4096 Feb 24 21:21 gnutls
drwxr-xr-x   2 root root       4096 Aug  5  2025 groff
-rw-r--r--   1 root root        790 Mar  4 13:12 group
-rw-r--r--   1 root root        775 Feb 12 01:53 group-
drwxr-xr-x   2 root root       4096 Feb 12 02:10 grub.d
-rw-r-----   1 root shadow      664 Mar  4 13:12 gshadow
-rw-r-----   1 root shadow      652 Feb 12 01:53 gshadow-
drwxr-xr-x   3 root root       4096 Aug  5  2025 gss
-rw-r--r--   1 root root       4436 Aug  5  2025 hdparm.conf
-rw-r--r--   1 root root         92 Apr 22  2024 host.conf
-rw-r--r--   1 root root         18 Feb 12 01:53 hostname
-rw-r--r--   1 root root          0 Aug  5  2025 hosts
-rw-r--r--   1 root root        411 Feb 12 02:13 hosts.allow
-rw-r--r--   1 root root        711 Feb 12 02:13 hosts.deny
drwxr-xr-x   2 root root       4096 Feb 24 16:01 ImageMagick-6
drwxr-xr-x   2 root root       4096 Feb 24 16:01 init.d
drwxr-xr-x   5 root root       4096 Feb 24 21:22 initramfs-tools
-rw-r--r--   1 root root       1875 Mar 31  2024 inputrc
drwxr-xr-x   4 root root       4096 Aug  5  2025 iproute2
drwxr-xr-x   2 root root       4096 Aug  5  2025 iscsi
-rw-r--r--   1 root root         26 Feb  6 07:23 issue
-rw-r--r--   1 root root         19 Feb  6 07:23 issue.net
drwxr-xr-x   6 root root       4096 Feb 12 01:47 kernel
drwxrwxr-x   2 root landscape  4096 Aug  5  2025 landscape
drwxr-xr-x   2 root root       4096 Feb 12 02:09 ldap
-rw-r--r--   1 root root      32555 Mar  4 13:12 ld.so.cache
-rw-r--r--   1 root root         34 Aug  2  2022 ld.so.conf
drwxr-xr-x   2 root root       4096 Feb 12 02:07 ld.so.conf.d
-rw-r--r--   1 root root        267 Apr 22  2024 legal
-rw-r--r--   1 root root        191 Mar 31  2024 libaudit.conf
drwxr-xr-x   3 root root       4096 Aug  5  2025 libblockdev
drwxr-xr-x   2 root root       4096 Aug  5  2025 libibverbs.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 libnl-3
drwxr-xr-x   2 root root       4096 Apr  8  2024 libpaper.d
-rw-r--r--   1 root root       2996 Aug  5  2025 locale.alias
-rw-r--r--   1 root root         17 Feb 12 01:53 locale.conf
-rw-r--r--   1 root root       9563 Feb 12 02:09 locale.gen
lrwxrwxrwx   1 root root         27 Feb 12 01:53 localtime -> /usr/share/zoneinfo/Etc/UTC
drwxr-xr-x   4 root root       4096 Aug  5  2025 logcheck
-rw-r--r--   1 root root      12345 Feb 22  2024 login.defs
-rw-r--r--   1 root root        586 Aug  5  2025 logrotate.conf
drwxr-xr-x   2 root root       4096 Feb 24 21:21 logrotate.d
-rw-r--r--   1 root root        104 Feb  6 07:22 lsb-release
drwxr-xr-x   3 root root       4096 Aug  5  2025 lvm
-r--r--r--   1 root root         33 Feb 12 01:46 machine-id
-rw-r--r--   1 root root        111 Aug  5  2025 magic
-rw-r--r--   1 root root        111 Aug  5  2025 magic.mime
-rw-r--r--   1 root root       5230 Aug  5  2025 manpath.config
drwxr-xr-x   2 root root       4096 Aug  5  2025 mdadm
-rw-r--r--   1 root root      75113 Jul 12  2023 mime.types
-rw-r--r--   1 root root        744 Apr  8  2024 mke2fs.conf
drwxr-xr-x   4 root root       4096 Aug  5  2025 ModemManager
drwxr-xr-x   2 root root       4096 Feb 12 02:09 modprobe.d
-rw-r--r--   1 root root        212 Aug  5  2025 modules
drwxr-xr-x   2 root root       4096 Feb 24 01:16 modules-load.d
lrwxrwxrwx   1 root root         19 Aug  5  2025 mtab -> ../proc/self/mounts
drwx------   2 root root       4096 Feb 12 01:52 multipath
-rw-r--r--   1 root root         41 Apr  7  2024 multipath.conf
-rw-r--r--   1 root root      11424 Aug  5  2025 nanorc
drwxr-xr-x   6 root root       4096 Aug  5  2025 needrestart
-rw-r--r--   1 root root        767 Aug  5  2025 netconfig
drwxr-xr-x   2 root root       4096 Feb 12 01:53 netplan
drwxr-xr-x   4 root root       4096 Aug  5  2025 network
drwxr-xr-x   8 root root       4096 Aug  5  2025 networkd-dispatcher
-rw-r--r--   1 root root         91 Apr 22  2024 networks
drwxr-xr-x   2 root root       4096 Aug  5  2025 newt
-rwxr-xr-x   1 root root        243 Aug  5  2025 nftables.conf
-rw-r--r--   1 root root        526 Aug  5  2025 nsswitch.conf
drwxr-xr-x   2 root root       4096 Aug  5  2025 opt
lrwxrwxrwx   1 root root         21 Feb  6 07:23 os-release -> ../usr/lib/os-release
-rw-r--r--   1 root root       6920 Aug  5  2025 overlayroot.conf
drwxr-xr-x   2 root root       4096 Feb 12 02:10 PackageKit
-rw-r--r--   1 root root        552 Oct 13  2022 pam.conf
drwxr-xr-x   2 root root       4096 Feb 12 02:13 pam.d
-rw-r--r--   1 root root          7 Feb 24 16:01 papersize
-rw-r--r--   1 root root       1780 Feb 12 02:13 passwd
-rw-r--r--   1 root root       1734 Feb 12 01:53 passwd-
drwxr-xr-x   3 root root       4096 Aug  5  2025 perl
drwxr-xr-x   4 root root       4096 Aug  5  2025 pki
drwxr-xr-x   2 root root       4096 Feb 25  2025 plymouth
drwxr-xr-x   3 root root       4096 Aug  5  2025 pm
drwxr-xr-x   3 root root       4096 Aug  5  2025 polkit-1
drwxr-xr-x   2 root root       4096 Feb 12 01:48 pollinate
-rw-r--r--   1 root root        582 Apr 22  2024 profile
drwxr-xr-x   2 root root       4096 Feb 24 21:21 profile.d
-rw-r--r--   1 root root       3144 Oct 17  2022 protocols
-rw-------   1 root root          0 Aug  5  2025 .pwd.lock
drwxr-xr-x   2 root root       4096 Aug  5  2025 python3
drwxr-xr-x   2 root root       4096 Feb 12 02:09 python3.12
drwxr-xr-x   2 root root       4096 Aug  5  2025 rc0.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 rc1.d
drwxr-xr-x   2 root root       4096 Feb 12 02:13 rc2.d
drwxr-xr-x   2 root root       4096 Feb 12 02:13 rc3.d
drwxr-xr-x   2 root root       4096 Feb 12 02:13 rc4.d
drwxr-xr-x   2 root root       4096 Feb 12 02:13 rc5.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 rc6.d
drwxr-xr-x   2 root root       4096 Feb 24 16:01 rcS.d
lrwxrwxrwx   1 root root         39 Aug  5  2025 resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
-rw-r--r--   1 root root        862 Aug  5  2025 .resolv.conf.systemd-resolved.bak
lrwxrwxrwx   1 root root         13 Apr  8  2024 rmt -> /usr/sbin/rmt
-rw-r--r--   1 root root        911 Oct 17  2022 rpc
-rw-r--r--   1 root root       1213 Aug  5  2025 rsyslog.conf
drwxr-xr-x   2 root root       4096 Feb 24 21:21 rsyslog.d
-rw-r--r--   1 root root       3663 Aug  5  2025 screenrc
drwxr-xr-x   4 root root       4096 Feb 12 02:07 security
drwxr-xr-x   2 root root       4096 Aug  5  2025 selinux
-rw-r--r--   1 root root      10593 Aug  5  2025 sensors3.conf
drwxr-xr-x   2 root root       4096 Aug  5  2025 sensors.d
-rw-r--r--   1 root root      12813 Mar 27  2021 services
drwxr-xr-x   2 root root       4096 Aug  5  2025 sgml
-rw-r-----   1 root shadow      967 Feb 12 02:13 shadow
-rw-r-----   1 root shadow      948 Feb 12 01:53 shadow-
-rw-r--r--   1 root root        148 Feb 12 02:10 shells
drwxr-xr-x   2 root root       4096 Aug  5  2025 skel
drwxr-xr-x   6 root root       4096 Feb 12 02:10 sos
drwxr-xr-x   4 root root       4096 Feb 12 02:13 ssh
drwxr-xr-x   4 root root       4096 Feb 12 02:09 ssl
-rw-r--r--   1 root root         19 Feb 12 01:53 subgid
-rw-r--r--   1 root root          0 Aug  5  2025 subgid-
-rw-r--r--   1 root root         19 Feb 12 01:53 subuid
-rw-r--r--   1 root root          0 Aug  5  2025 subuid-
-rw-r--r--   1 root root       4343 Jun 25  2025 sudo.conf
-r--r-----   1 root root       1800 Jan 29  2024 sudoers
drwxr-xr-x   2 root root       4096 Aug  5  2025 sudoers.d
-rw-r--r--   1 root root       9804 Jun 25  2025 sudo_logsrvd.conf
drwxr-xr-x   2 root root       4096 Aug  5  2025 supercat
-rw-r--r--   1 root root       2209 Mar 24  2024 sysctl.conf
drwxr-xr-x   2 root root       4096 Feb 12 02:07 sysctl.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 sysstat
drwxr-xr-x   7 root root       4096 Feb 12 02:09 systemd
drwxr-xr-x   2 root root       4096 Aug  5  2025 terminfo
drwxr-xr-x   2 root root       4096 Feb 12 02:10 thermald
-rw-r--r--   1 root root          8 Feb 12 01:53 timezone
drwxr-xr-x   2 root root       4096 Aug  5  2025 tmpfiles.d
drwxr-xr-x   2 root root       4096 Feb 12 02:10 ubuntu-advantage
-rw-r--r--   1 root root       1260 Jan 27  2023 ucf.conf
drwxr-xr-x   4 root root       4096 Feb 12 02:09 udev
drwxr-xr-x   2 root root       4096 Feb 12 02:09 udisks2
drwxr-xr-x   3 root root       4096 Aug  5  2025 ufw
-rw-r--r--   1 root root        208 Aug  5  2025 .updated
-rw-r--r--   1 root root        583 Jul 31  2023 updatedb.conf
drwxr-xr-x   3 root root       4096 Feb 12 02:10 update-manager
drwxr-xr-x   2 root root       4096 Feb 12 02:10 update-motd.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 update-notifier
drwxr-xr-x   2 root root       4096 Feb 12 01:47 UPower
-rw-r--r--   1 root root       1523 Aug  5  2025 usb_modeswitch.conf
drwxr-xr-x   2 root root       4096 Aug  5  2025 usb_modeswitch.d
lrwxrwxrwx   1 root root         16 Aug  5  2025 vconsole.conf -> default/keyboard
drwxr-xr-x   2 root root       4096 Feb 12 02:10 vim
drwxr-xr-x   4 root root       4096 Feb 12 02:10 vmware-tools
lrwxrwxrwx   1 root root         23 Feb 26  2024 vtrgb -> /etc/alternatives/vtrgb
drwxr-xr-x   2 root root       4096 Feb 24 16:01 w3m
-rw-r--r--   1 root root       4942 Aug  5  2025 wgetrc
drwxr-xr-x   8 root root       4096 Feb 24 16:01 X11
-rw-r--r--   1 root root        681 Apr  8  2024 xattr.conf
drwxr-xr-x   4 root root       4096 Aug  5  2025 xdg
drwxr-xr-x   2 root root       4096 Aug  5  2025 xml
-rw-r--r--   1 root root        460 Aug  5  2025 zsh_command_not_found
pluto@Ubuntu-Server-Lab:/etc$ cat passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
_apt:x:42:65534::/nonexistent:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin
systemd-timesync:x:997:997:systemd Time Synchronization:/:/usr/sbin/nologin
dhcpcd:x:100:65534:DHCP Client Daemon,,,:/usr/lib/dhcpcd:/bin/false
messagebus:x:101:102::/nonexistent:/usr/sbin/nologin
systemd-resolve:x:992:992:systemd Resolver:/:/usr/sbin/nologin
pollinate:x:102:1::/var/cache/pollinate:/bin/false
polkitd:x:991:991:User for polkitd:/:/usr/sbin/nologin
syslog:x:103:104::/nonexistent:/usr/sbin/nologin
uuidd:x:104:105::/run/uuidd:/usr/sbin/nologin
tcpdump:x:105:107::/nonexistent:/usr/sbin/nologin
tss:x:106:108:TPM software stack,,,:/var/lib/tpm:/bin/false
landscape:x:107:109::/var/lib/landscape:/usr/sbin/nologin
fwupd-refresh:x:989:989:Firmware update daemon:/var/lib/fwupd:/usr/sbin/nologin
usbmux:x:108:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
pluto:x:1000:1000:pluto:/home/pluto:/bin/bash
sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
pluto@Ubuntu-Server-Lab:/etc$ cd -
/home
pluto@Ubuntu-Server-Lab:/home$ pwd
/home
pluto@Ubuntu-Server-Lab:/home$
```

2. Lanjutkan penelusuran pohon pada sistem file menggunakan cd, ls, pwd dan cat. Telusuri direktory /bin, /usr/bin, /sbin, /tmp dan /boot.<br>
**/bin**
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /bin
pluto@Ubuntu-Server-Lab:/bin$ ls
'['                                   lspgpot                            ps2pdf
 411toppm                             lspower                            ps2pdf12
 aa-enabled                           lsusb                              ps2pdf13
 aa-exec                              lzcat                              ps2pdf14
 aa-features-abi                      lzcmp                              ps2pdfwr
 acpidbg                              lzdiff                             ps2ps
 add-apt-repository                   lzegrep                            ps2ps2
 addpart                              lzfgrep                            ps2txt
 animate                              lzgrep                             psfaddtable
 animate-im6                          lzless                             psfgettable
 animate-im6.q16                      lzma                               psfstriptable
 anytopnm                             lzmainfo                           psfxtable
 apport-bug                           lzmore                             psidtopgm
 apport-cli                           macptopbm                          pslog
 apport-collect                       mailmail3                          pstopnm
 apport-unpack                        man                                pstree
 appstreamcli                         mandb                              pstree.x11
 apropos                              manifest                           ptar
 apt                                  manpath                            ptardiff
 apt-add-repository                   man-recode                         ptargrep
 apt-cache                            mapscrn                            ptx
 apt-cdrom                            markdown-it                        purge-old-kernels
 apt-config                           mawk                               pwd
 apt-extracttemplates                 mbimcli                            pwdx
 apt-ftparchive                       mbim-network                       py3clean
 apt-get                              mcookie                            py3compile
 apt-key                              md5sum                             py3versions
 apt-mark                             md5sum.textutils                   pybabel
 apt-sortpkgs                         mdatopbm                           pybabel-python3
 arch                                 mdig                               pydoc3
 asciitopgm                           memhog                             pydoc3.12
 atktopbm                             memusage                           pygettext3
 automat-visualize3                   memusagestat                       pygettext3.12
 avstopam                             mesg                               pygmentize
 awk                                  mgrtopbm                           pyhtmlizer3
 b2sum                                migratepages                       pyserial-miniterm
 base32                               migrate-pubring-from-classic-gpg   pyserial-ports
 base64                               migspeed                           python3
 basename                             mkdir                              python3.12
 basenc                               mkfifo                             pzstd
 bash                                 mkfontdir                          qmicli
 bashbug                              mkfontscale                        qmi-firmware-update
 bc                                   mk_modmap                          qmi-network
 bdftopcf                             mknod                              qoitopam
 bdftruncate                          mksquashfs                         qrttoppm
 bioradtopgm                          mktemp                             quirks-handler
 bmptopnm                             mmcli                              rasttopnm
 bmptoppm                             mogrify                            rawtopgm
 boltctl                              mogrify-im6                        rawtoppm
 bpftrace                             mogrify-im6.q16                    rbash
 bpftrace-aotrt                       montage                            rdma
 brushtopbm                           montage-im6                        readlink
 btrfs                                montage-im6.q16                    realpath
 btrfsck                              more                               red
 btrfs-convert                        mount                              rename.ul
 btrfs-find-root                      mountpoint                         renice
 btrfs-image                          mpstat                             rescan-scsi-bus.sh
 btrfs-map-logical                    mrftopbm                           reset
 btrfs-select-super                   mt                                 resizecons
 btrfstune                            mt-gnu                             resizepart
 busctl                               mtr                                resolvectl
 busybox                              mtrace                             rev
 byobu                                mtr-packet                         rgb3toppm
 byobu-config                         mtvtoppm                           rgrep
 byobu-ctrl-a                         mv                                 rlatopam
 byobu-disable                        namei                              rletopnm
 byobu-disable-prompt                 nano                               rm
 byobu-enable                         nawk                               rmdir
 byobu-enable-prompt                  nc                                 rnano
 byobu-export                         nc.openbsd                         routel
 byobu-janitor                        neofetch                           rpcgen
 byobu-keybindings                    neotoppm                           rrsync
 byobu-launch                         neqn                               rsync
 byobu-launcher                       netaddr                            rsync-ssl
 byobu-launcher-install               netcat                             rtla
 byobu-launcher-uninstall             networkctl                         rtstat
 byobu-layout                         networkd-dispatcher                runcon
 byobu-prompt                         newgrp                             run-one
 byobu-quiet                          NF                                 run-one-constantly
 byobu-reconnect-sockets              ngettext                           run-one-until-failure
 byobu-screen                         nice                               run-one-until-success
 byobu-select-backend                 nisdomainname                      run-parts
 byobu-select-profile                 nl                                 run-this-one
 byobu-select-session                 nohup                              rview
 byobu-shell                          nproc                              rvim
 byobu-silent                         nroff                              sadf
 byobu-status                         nsenter                            sar
 byobu-status-detail                  nslookup                           sar.sysstat
 byobu-tmux                           nstat                              savelog
 byobu-ugraph                         nsupdate                           sbattach
 byobu-ulevel                         ntfs-3g                            sbigtopgm
 cacaclock                            ntfs-3g.probe                      sbkeysync
 cacademo                             ntfscat                            sbsiglist
 cacafire                             ntfscluster                        sbsign
 cacaplay                             ntfscmp                            sbvarsign
 cacaserver                           ntfsdecrypt                        sbverify
 cacaview                             ntfsfallocate                      scalar
 cameratopam                          ntfsfix                            scandeps
 captoinfo                            ntfsinfo                           scp
 cat                                  ntfsls                             screen
 catman                               ntfsmove                           screendump
 cftp3                                ntfsrecover                        script
 chafa                                ntfssecaudit                       scriptlive
 chage                                ntfstruncate                       scriptreplay
 chardet                              ntfsusermap                        scsi_logging_level
 chardetect                           ntfswipe                           scsi_mandat
 chattr                               numactl                            scsi_readcap
 chcon                                numastat                           scsi_ready
 chfn                                 numfmt                             scsi_satl
 chgrp                                nvidia-detector                    scsi_start
 chmod                                od                                 scsi_stop
 choom                                oem-getlogs                        scsi_temperature
 chown                                on_ac_power                        sdiff
 chrt                                 openssl                            sed
 chsh                                 openvt                             select-editor
 chvt                                 os-prober                          sensible-browser
 cifsiostat                           pager                              sensible-editor
 cistopbm                             palmtopnm                          sensible-pager
 ckbcomp                              pamaddnoise                        sensible-terminal
 ckeygen3                             pamaltsat                          seq
 cksum                                pamarith                           setarch
 clear                                pambackground                      setfont
 clear_console                        pambayer                           setkeycodes
 cloud-id                             pambrighten                        setleds
 cloud-init                           pamcat                             setlogcons
 cloud-init-per                       pamchannel                         setmetamode
 cmp                                  pamcomp                            setpci
 cmuwmtopbm                           pamcrater                          setpriv
 codepage                             pamcut                             setsid
 col                                  pamdeinterlace                     setterm
 col1                                 pamdepth                           setupcon
 col2                                 pamdice                            sftp
 col3                                 pamditherbw                        sg
 col4                                 pamedge                            sg_bg_ctl
 col5                                 pamendian                          sg_compare_and_write
 col6                                 pamenlarge                         sg_copy_results
 col7                                 pamexec                            sg_dd
 col8                                 pamfile                            sg_decode_sense
 col9                                 pamfind                            sg_emc_trespass
 colcrt                               pamfix                             sg_format
 colrm                                pamfixtrunc                        sg_get_config
 column                               pamflip                            sg_get_elem_status
 comm                                 pamfunc                            sg_get_lba_status
 compare                              pamgauss                           sg_ident
 compare-im6                          pamgetcolor                        sginfo
 compare-im6.q16                      pamgradient                        sg_inq
 composite                            pamhomography                      sgitopnm
 composite-im6                        pamhue                             sg_logs
 composite-im6.q16                    pamlevels                          sg_luns
 conch3                               pamlookup                          sg_map
 conjure                              pammasksharpen                     sg_map26
 conjure-im6                          pammixinterlace                    sgm_dd
 conjure-im6.q16                      pammixmulti                        sg_modes
 convert                              pammosaicknit                      sg_opcodes
 convert-im6                          pamoil                             sgp_dd
 convert-im6.q16                      pampaintspill                      sg_persist
 corelist                             pamperspective                     sg_prevent
 cp                                   pampick                            sg_raw
 cpan                                 pampop9                            sg_rbuf
 cpan5.38-x86_64-linux-gnu            pamrecolor                         sg_rdac
 cpio                                 pamrestack                         sg_read
 cpupower                             pamrgbatopng                       sg_read_attr
 c_rehash                             pamrubber                          sg_read_block_limits
 crontab                              pamscale                           sg_read_buffer
 csplit                               pamseq                             sg_readcap
 ctail                                pamshadedrelief                    sg_read_long
 ctstat                               pamsharpmap                        sg_reassign
 curl                                 pamsharpness                       sg_referrals
 cut                                  pamshuffle                         sg_rep_pip
 cvtsudoers                           pamsistoaglyph                     sg_rep_zones
 dash                                 pamslice                           sg_requests
 date                                 pamsplit                           sg_reset
 dbus-cleanup-sockets                 pamstack                           sg_reset_wp
 dbus-daemon                          pamstereogram                      sg_rmsn
 dbus-monitor                         pamstretch                         sg_rtpg
 dbus-run-session                     pamstretch-gen                     sg_safte
 dbus-send                            pamsumm                            sg_sanitize
 dbus-update-activation-environment   pamsummcol                         sg_sat_identify
 dbus-uuidgen                         pamtable                           sg_sat_phy_event
 dbxtool                              pamthreshold                       sg_sat_read_gplog
 dd                                   pamtilt                            sg_sat_set_features
 ddbugtopbm                           pamtoavs                           sg_scan
 deallocvt                            pamtodjvurle                       sg_seek
 debconf                              pamtofits                          sg_senddiag
 debconf-apt-progress                 pamtogif                           sg_ses
 debconf-communicate                  pamtohdiff                         sg_ses_microcode
 debconf-copydb                       pamtohtmltbl                       sg_start
 debconf-escape                       pamtojpeg2k                        sg_stpg
 debconf-set-selections               pamtompfont                        sg_stream_ctl
 debconf-show                         pamtooctaveimg                     sg_sync
 debian-distro-info                   pamtopam                           sg_test_rwbuf
 deb-systemd-helper                   pamtopdbimg                        sg_timestamp
 deb-systemd-invoke                   pamtopfm                           sg_turs
 delpart                              pamtopng                           sg_unmap
 delv                                 pamtopnm                           sg_verify
 df                                   pamtoqoi                           sg_vpd
 dh_bash-completion                   pamtosrf                           sg_write_buffer
 dh_installxmlcatalogs                pamtosvg                           sg_write_long
 diff                                 pamtotga                           sg_write_same
 diff3                                pamtotiff                          sg_write_verify
 dig                                  pamtouil                           sg_write_x
 dir                                  pamtowinicon                       sg_wr_mode
 dircolors                            pamtoxvmini                        sg_xcopy
 dirmngr                              pamtris                            sg_zone
 dirmngr-client                       pamundice                          sh
 dirname                              pamunlookup                        sha1sum
 display                              pamvalidate                        sha224sum
 display-im6                          pamwipeout                         sha256sum
 display-im6.q16                      pamx                               sha384sum
 distro-info                          paperconf                          sha512sum
 dmesg                                partx                              shasum
 dnsdomainname                        passwd                             showconsolefont
 domainname                           paste                              showkey
 do-release-upgrade                   pastebinit                         shred
 dpkg                                 patch                              shuf
 dpkg-deb                             pathchk                            sirtopnm
 dpkg-divert                          pbget                              sixel2png
 dpkg-maintscript-helper              pbmclean                           skill
 dpkg-query                           pbmlife                            slabtop
 dpkg-realpath                        pbmmake                            sldtoppm
 dpkg-split                           pbmmask                            sleep
 dpkg-statoverride                    pbmminkowski                       slogin
 dpkg-trigger                         pbmnoise                           snap
 du                                   pbmpage                            snapctl
 dumpkeys                             pbmpscale                          snapfuse
 dvipdf                               pbmreduce                          snice
 eatmydata                            pbmtext                            soelim
 ec2metadata                          pbmtextps                          sort
 echo                                 pbmto10x                           sos
 ed                                   pbmto4425                          sos-collector
 editor                               pbmtoascii                         sosreport
 egrep                                pbmtoatk                           sotruss
 eject                                pbmtobbnbg                         spctoppm
 enc2xs                               pbmtocis                           splain
 encguess                             pbmtocmuwm                         split
 env                                  pbmtodjvurle                       splitfont
 envsubst                             pbmtoepsi                          spottopgm
 eps2eps                              pbmtoepson                         sprof
 eqn                                  pbmtoescp2                         sputoppm
 escp2topbm                           pbmtog3                            sqfscat
 ex                                   pbmtogem                           sqfstar
 expand                               pbmtogo                            srftopam
 expiry                               pbmtoibm23xx                       ss
 expr                                 pbmtoicon                          ssh
 eyuvtoppm                            pbmtolj                            ssh-add
 factor                               pbmtoln03                          ssh-agent
 faillog                              pbmtolps                           ssh-argv0
 fallocate                            pbmtomacp                          ssh-copy-id
 false                                pbmtomatrixorbital                 ssh-import-id
 fc-cache                             pbmtomda                           ssh-import-id-gh
 fc-cat                               pbmtomgr                           ssh-import-id-lp
 fc-conflist                          pbmtomrf                           ssh-keygen
 fc-list                              pbmtonokia                         ssh-keyscan
 fc-match                             pbmtopgm                           st4topgm
 fc-pattern                           pbmtopi3                           stat
 fc-query                             pbmtopk                            static-sh
 fc-scan                              pbmtoplot                          stdbuf
 fc-validate                          pbmtoppa                           strace
 fgconsole                            pbmtopsg3                          strace-log-merge
 fgrep                                pbmtoptx                           stream
 fiascotopnm                          pbmtosunicon                       stream-im6
 figlet                               pbmtowbmp                          stream-im6.q16
 figlet-toilet                        pbmtox10bm                         streamzip
 file                                 pbmtoxbm                           stty
 finalrd                              pbmtoybm                           su
 find                                 pbmtozinc                          sudo
 findmnt                              pbmupc                             sudoedit
 fitstopnm                            pbput                              sudoreplay
 flock                                pbputs                             sum
 fmt                                  pc1toppm                           sunicontopnm
 fold                                 pcdindex                           svgtopam
 fonttosfnt                           pcdovtoppm                         sync
 free                                 pcxtoppm                           systemctl
 fstopgm                              pdb3                               systemd
 ftp                                  pdb3.12                            systemd-ac-power
 fuser                                pdbimgtopam                        systemd-analyze
 fusermount                           pdf2dsc                            systemd-ask-password
 fusermount3                          pdf2ps                             systemd-cat
 fwupdmgr                             peekfd                             systemd-cgls
 fwupdtool                            perf                               systemd-cgtop
 g3topbm                              perl                               systemd-confext
 gapplication                         perl5.38.2                         systemd-creds
 gawk                                 perl5.38-x86_64-linux-gnu          systemd-cryptenroll
 gawkbug                              perlbug                            systemd-cryptsetup
 gdbus                                perldoc                            systemd-delta
 gdk-pixbuf-csource                   perlivp                            systemd-detect-virt
 gdk-pixbuf-pixdata                   perlthanks                         systemd-escape
 gdk-pixbuf-thumbnailer               pf2afm                             systemd-firstboot
 gemtopbm                             pfbtopfa                           systemd-hwdb
 gemtopnm                             pfmtopam                           systemd-id128
 gencat                               pgmabel                            systemd-inhibit
 geqn                                 pgmbentley                         systemd-machine-id-setup
 getconf                              pgmcrater                          systemd-mount
 getent                               pgmdeshadow                        systemd-notify
 getkeycodes                          pgmedge                            systemd-path
 getopt                               pgmenhance                         systemd-repart
 gettext                              pgmhist                            systemd-run
 gettext.sh                           pgmkernel                          systemd-socket-activate
 ghostscript                          pgmmake                            systemd-stdio-bridge
 giftopnm                             pgmmedian                          systemd-sysext
 ginstall-info                        pgmminkowski                       systemd-sysusers
 gio                                  pgmmorphconv                       systemd-tmpfiles
 gio-querymodules                     pgmnoise                           systemd-tty-ask-password-agent
 git                                  pgmnorm                            systemd-umount
 git-receive-pack                     pgmoil                             tabs
 git-shell                            pgmramp                            tac
 git-upload-archive                   pgmslice                           tail
 git-upload-pack                      pgmtexture                         tapestat
 glib-compile-schemas                 pgmtofs                            tar
 gouldtoppm                           pgmtolispm                         taskset
 gpasswd                              pgmtopbm                           tbl
 gpg                                  pgmtopgm                           tclsh
 gpg-agent                            pgmtoppm                           tclsh8.6
 gpgconf                              pgmtosbig                          tcpdump
 gpg-connect-agent                    pgmtost4                           tee
 gpgparsemail                         pgrep                              telnet
 gpgsm                                pi1toppm                           tempfile
 gpgsplit                             pi3topbm                           test
 gpgtar                               pic                                tgatoppm
 gpgv                                 pico                               thinkjettopbm
 gpg-wks-client                       piconv                             tic
 gpic                                 pidof                              tifftopnm
 gpu-manager                          pidstat                            time
 grep                                 pidwait                            timedatectl
 gresource                            pinentry                           timeout
 groff                                pinentry-curses                    tkconch3
 grog                                 ping                               tload
 grops                                ping4                              tmux
 grotty                               ping6                              tnftp
 groups                               pinky                              toe
 growpart                             pjtoppm                            toilet
 grub-editenv                         pkaction                           top
 grub-file                            pkcheck                            touch
 grub-fstest                          pkcon                              tput
 grub-glue-efi                        pkill                              tr
 grub-kbdcomp                         pkmon                              trace-cmd
 grub-menulst2cfg                     pktopbm                            tracepath
 grub-mkfont                          pkttyagent                         trial3
 grub-mkimage                         pl2pm                              troff
 grub-mklayout                        pldd                               true
 grub-mknetdir                        plocate                            truncate
 grub-mkpasswd-pbkdf2                 plymouth                           tset
 grub-mkrelpath                       pmap                               tsort
 grub-mkrescue                        pngtopam                           tty
 grub-mkstandalone                    pngtopnm                           turbostat
 grub-mount                           pnmalias                           twist3
 grub-ntldr-img                       pnmarith                           twistd3
 grub-render-label                    pnmcat                             tzselect
 grub-script-check                    pnmcolormap                        ua
 grub-syslinux2cfg                    pnmcomp                            ubuntu-advantage
 gs                                   pnmconvol                          ubuntu-bug
 gsbj                                 pnmcrop                            ubuntu-distro-info
 gsdj                                 pnmcut                             ubuntu-drivers
 gsdj500                              pnmdepth                           ubuntu-security-status
 gsettings                            pnmenlarge                         ucf
 gslj                                 pnmfile                            ucfq
 gslp                                 pnmflip                            ucfr
 gsnd                                 pnmgamma                           uclampset
 gtbl                                 pnmhisteq                          ucs2any
 gunzip                               pnmhistmap                         udevadm
 gzexe                                pnmindex                           udisksctl
 gzip                                 pnminterp                          ul
 h2ph                                 pnminterp-gen                      umount
 h2xs                                 pnminvert                          uname
 hardlink                             pnmmargin                          unattended-upgrade
 hd                                   pnmmercator                        unattended-upgrades
 hdifftopam                           pnmmontage                         uncompress
 head                                 pnmnlfilt                          unexpand
 helpztags                            pnmnoraw                           unicode_start
 hexdump                              pnmnorm                            unicode_stop
 hipstopgm                            pnmpad                             uniq
 host                                 pnmpaste                           unlink
 hostid                               pnmpsnr                            unlzma
 hostname                             pnmquant                           unminimize
 hostnamectl                          pnmquantall                        unmkinitramfs
 hpcdtoppm                            pnmremap                           unshare
 htop                                 pnmrotate                          unsquashfs
 hwe-support-status                   pnmscale                           unxz
 i386                                 pnmscalefixed                      unzstd
 icontopbm                            pnmshear                           update-alternatives
 iconv                                pnmsmooth                          updatedb
 id                                   pnmsplit                           update-mime-database
 identify                             pnmstitch                          upower
 identify-im6                         pnmtile                            uptime
 identify-im6.q16                     pnmtoddif                          usb-devices
 ilbmtoppm                            pnmtofiasco                        usbhid-dump
 imagetops                            pnmtofits                          usbip
 img2sixel                            pnmtojbig                          usbipd
 img2txt                              pnmtojpeg                          usbreset
 imgtoppm                             pnmtopalm                          users
 import                               pnmtopclxl                         utmpdump
 import-im6                           pnmtoplainpnm                      uuidgen
 import-im6.q16                       pnmtopng                           uuidparse
 inetutils-telnet                     pnmtopnm                           varlinkctl
 info                                 pnmtops                            vcs-run
 infobrowser                          pnmtorast                          vdir
 infocmp                              pnmtorle                           VGAuthService
 infotocap                            pnmtosgi                           vi
 infotopam                            pnmtosir                           view
 install                              pnmtotiff                          vigpg
 install-info                         pnmtotiffcmyk                      vim
 instmodsh                            pnmtoxwd                           vim.basic
 ionice                               pod2html                           vimdiff
 iostat                               pod2man                            vim.tiny
 ip                                   pod2text                           vimtutor
 ipcmk                                pod2usage                          vmhgfs-fuse
 ipcrm                                podchecker                         vmstat
 ipcs                                 pollinate                          vm-support
 iptables-xml                         pphs                               vmtoolsd
 ischroot                             ppm3d                              vmware-alias-import
 iscsiadm                             ppmbrighten                        vmware-checkvm
 jbigtopnm                            ppmchange                          vmware-hgfsclient
 join                                 ppmcie                             vmware-namespace-cmd
 journalctl                           ppmcolormask                       vmware-rpctool
 jp2a                                 ppmcolors                          vmware-toolbox-cmd
 jpeg2ktopam                          ppmdcfont                          vmware-vgauth-cmd
 jpegtopnm                            ppmddumpfont                       vmware-vmblock-fuse
 jq                                   ppmdim                             vmware-xferlogs
 jsondiff                             ppmdist                            w
 jsonpatch                            ppmdither                          w3m
 json-patch-jsondiff                  ppmdmkfont                         w3mman
 jsonpointer                          ppmdraw                            wall
 json_pp                              ppmfade                            watch
 jsonschema                           ppmflash                           watchgnupg
 JxrDecApp                            ppmforge                           wbmptopbm
 JxrEncApp                            ppmglobe                           wc
 kbdinfo                              ppmhist                            wdctl
 kbd_mode                             ppmlabel                           wget
 kbxutil                              ppmmake                            whatis
 keep-one-running                     ppmmix                             whereis
 kernel-install                       ppmnorm                            which
 kill                                 ppmntsc                            which.debianutils
 killall                              ppmpat                             whiptail
 kmod                                 ppmquant                           who
 kmodsign                             ppmquantall                        whoami
 landscape-sysinfo                    ppmrainbow                         wifi-status
 last                                 ppmrelief                          winicontopam
 lastb                                ppmrough                           winicontoppm
 lastlog                              ppmshadow                          write
 lcf                                  ppmshift                           www-browser
 ldd                                  ppmspread                          X11
 ld.so                                ppmtoacad                          x86_64
 leaftoppm                            ppmtoapplevol                      x86_energy_perf_policy
 less                                 ppmtoarbtxt                        xargs
 lessecho                             ppmtoascii                         xauth
 lessfile                             ppmtobmp                           xbmtopbm
 lesskey                              ppmtoeyuv                          xdg-user-dir
 lesspipe                             ppmtogif                           xdg-user-dirs-update
 lexgrog                              ppmtoicr                           ximtoppm
 libnetcfg                            ppmtoilbm                          xpmtoppm
 libsixel-config                      ppmtojpeg                          xsubpp
 link                                 ppmtoleaf                          xvminitoppm
 linux32                              ppmtolj                            xwdtopnm
 linux64                              ppmtomap                           xxd
 linux-boot-prober                    ppmtomitsu                         xz
 linux-check-removal                  ppmtompeg                          xzcat
 linux-update-symlinks                ppmtoneo                           xzcmp
 linux-version                        ppmtopcx                           xzdiff
 lispmtopgm                           ppmtopgm                           xzegrep
 ln                                   ppmtopi1                           xzfgrep
 lnstat                               ppmtopict                          xzgrep
 loadkeys                             ppmtopj                            xzless
 loadunimap                           ppmtopjxl                          xzmore
 locale                               ppmtoppm                           ybmtopbm
 locale-check                         ppmtopuzz                          yes
 localectl                            ppmtorgb3                          ypdomainname
 localedef                            ppmtosixel                         yuvsplittoppm
 locate                               ppmtospu                           yuvtoppm
 logger                               ppmtoterm                          yuy2topam
 login                                ppmtotga                           zcat
 loginctl                             ppmtouil                           zcmp
 logname                              ppmtowinicon                       zdiff
 look                                 ppmtoxpm                           zdump
 lowntfs-3g                           ppmtoyuv                           zegrep
 ls                                   ppmtoyuvsplit                      zeisstopnm
 lsattr                               ppmtv                              zfgrep
 lsblk                                ppmwheel                           zforce
 lsb_release                          pr                                 zgrep
 lscpu                                preconv                            zipdetails
 lshw                                 printafm                           zless
 lsinitramfs                          printenv                           zmore
 lsipc                                printf                             znew
 lslocks                              prlimit                            zstd
 lslogins                             pro                                zstdcat
 lsmem                                prove                              zstdgrep
 lsmod                                prtstat                            zstdless
 lsns                                 ps                                 zstdmt
 lsof                                 ps2ascii
 lspci                                ps2epsi
pluto@Ubuntu-Server-Lab:/bin$ pwd
/bin
pluto@Ubuntu-Server-Lab:/bin$ cat
pluto@Ubuntu-Server-Lab:/bin$
```
**usr/bin**
```markdown
pluto@Ubuntu-Server-Lab:/bin$ cd
pluto@Ubuntu-Server-Lab:~$ cd usr/bin
-bash: cd: usr/bin: No such file or directory
pluto@Ubuntu-Server-Lab:~$ cd pluto/bin
-bash: cd: pluto/bin: No such file or directory
pluto@Ubuntu-Server-Lab:~$ cd /usr/bin
pluto@Ubuntu-Server-Lab:/usr/bin$ ls
'['                                   lspgpot                            ps2pdf
 411toppm                             lspower                            ps2pdf12
 aa-enabled                           lsusb                              ps2pdf13
 aa-exec                              lzcat                              ps2pdf14
 aa-features-abi                      lzcmp                              ps2pdfwr
 acpidbg                              lzdiff                             ps2ps
 add-apt-repository                   lzegrep                            ps2ps2
 addpart                              lzfgrep                            ps2txt
 animate                              lzgrep                             psfaddtable
 animate-im6                          lzless                             psfgettable
 animate-im6.q16                      lzma                               psfstriptable
 anytopnm                             lzmainfo                           psfxtable
 apport-bug                           lzmore                             psidtopgm
 apport-cli                           macptopbm                          pslog
 apport-collect                       mailmail3                          pstopnm
 apport-unpack                        man                                pstree
 appstreamcli                         mandb                              pstree.x11
 apropos                              manifest                           ptar
 apt                                  manpath                            ptardiff
 apt-add-repository                   man-recode                         ptargrep
 apt-cache                            mapscrn                            ptx
 apt-cdrom                            markdown-it                        purge-old-kernels
 apt-config                           mawk                               pwd
 apt-extracttemplates                 mbimcli                            pwdx
 apt-ftparchive                       mbim-network                       py3clean
 apt-get                              mcookie                            py3compile
 apt-key                              md5sum                             py3versions
 apt-mark                             md5sum.textutils                   pybabel
 apt-sortpkgs                         mdatopbm                           pybabel-python3
 arch                                 mdig                               pydoc3
 asciitopgm                           memhog                             pydoc3.12
 atktopbm                             memusage                           pygettext3
 automat-visualize3                   memusagestat                       pygettext3.12
 avstopam                             mesg                               pygmentize
 awk                                  mgrtopbm                           pyhtmlizer3
 b2sum                                migratepages                       pyserial-miniterm
 base32                               migrate-pubring-from-classic-gpg   pyserial-ports
 base64                               migspeed                           python3
 basename                             mkdir                              python3.12
 basenc                               mkfifo                             pzstd
 bash                                 mkfontdir                          qmicli
 bashbug                              mkfontscale                        qmi-firmware-update
 bc                                   mk_modmap                          qmi-network
 bdftopcf                             mknod                              qoitopam
 bdftruncate                          mksquashfs                         qrttoppm
 bioradtopgm                          mktemp                             quirks-handler
 bmptopnm                             mmcli                              rasttopnm
 bmptoppm                             mogrify                            rawtopgm
 boltctl                              mogrify-im6                        rawtoppm
 bpftrace                             mogrify-im6.q16                    rbash
 bpftrace-aotrt                       montage                            rdma
 brushtopbm                           montage-im6                        readlink
 btrfs                                montage-im6.q16                    realpath
 btrfsck                              more                               red
 btrfs-convert                        mount                              rename.ul
 btrfs-find-root                      mountpoint                         renice
 btrfs-image                          mpstat                             rescan-scsi-bus.sh
 btrfs-map-logical                    mrftopbm                           reset
 btrfs-select-super                   mt                                 resizecons
 btrfstune                            mt-gnu                             resizepart
 busctl                               mtr                                resolvectl
 busybox                              mtrace                             rev
 byobu                                mtr-packet                         rgb3toppm
 byobu-config                         mtvtoppm                           rgrep
 byobu-ctrl-a                         mv                                 rlatopam
 byobu-disable                        namei                              rletopnm
 byobu-disable-prompt                 nano                               rm
 byobu-enable                         nawk                               rmdir
 byobu-enable-prompt                  nc                                 rnano
 byobu-export                         nc.openbsd                         routel
 byobu-janitor                        neofetch                           rpcgen
 byobu-keybindings                    neotoppm                           rrsync
 byobu-launch                         neqn                               rsync
 byobu-launcher                       netaddr                            rsync-ssl
 byobu-launcher-install               netcat                             rtla
 byobu-launcher-uninstall             networkctl                         rtstat
 byobu-layout                         networkd-dispatcher                runcon
 byobu-prompt                         newgrp                             run-one
 byobu-quiet                          NF                                 run-one-constantly
 byobu-reconnect-sockets              ngettext                           run-one-until-failure
 byobu-screen                         nice                               run-one-until-success
 byobu-select-backend                 nisdomainname                      run-parts
 byobu-select-profile                 nl                                 run-this-one
 byobu-select-session                 nohup                              rview
 byobu-shell                          nproc                              rvim
 byobu-silent                         nroff                              sadf
 byobu-status                         nsenter                            sar
 byobu-status-detail                  nslookup                           sar.sysstat
 byobu-tmux                           nstat                              savelog
 byobu-ugraph                         nsupdate                           sbattach
 byobu-ulevel                         ntfs-3g                            sbigtopgm
 cacaclock                            ntfs-3g.probe                      sbkeysync
 cacademo                             ntfscat                            sbsiglist
 cacafire                             ntfscluster                        sbsign
 cacaplay                             ntfscmp                            sbvarsign
 cacaserver                           ntfsdecrypt                        sbverify
 cacaview                             ntfsfallocate                      scalar
 cameratopam                          ntfsfix                            scandeps
 captoinfo                            ntfsinfo                           scp
 cat                                  ntfsls                             screen
 catman                               ntfsmove                           screendump
 cftp3                                ntfsrecover                        script
 chafa                                ntfssecaudit                       scriptlive
 chage                                ntfstruncate                       scriptreplay
 chardet                              ntfsusermap                        scsi_logging_level
 chardetect                           ntfswipe                           scsi_mandat
 chattr                               numactl                            scsi_readcap
 chcon                                numastat                           scsi_ready
 chfn                                 numfmt                             scsi_satl
 chgrp                                nvidia-detector                    scsi_start
 chmod                                od                                 scsi_stop
 choom                                oem-getlogs                        scsi_temperature
 chown                                on_ac_power                        sdiff
 chrt                                 openssl                            sed
 chsh                                 openvt                             select-editor
 chvt                                 os-prober                          sensible-browser
 cifsiostat                           pager                              sensible-editor
 cistopbm                             palmtopnm                          sensible-pager
 ckbcomp                              pamaddnoise                        sensible-terminal
 ckeygen3                             pamaltsat                          seq
 cksum                                pamarith                           setarch
 clear                                pambackground                      setfont
 clear_console                        pambayer                           setkeycodes
 cloud-id                             pambrighten                        setleds
 cloud-init                           pamcat                             setlogcons
 cloud-init-per                       pamchannel                         setmetamode
 cmp                                  pamcomp                            setpci
 cmuwmtopbm                           pamcrater                          setpriv
 codepage                             pamcut                             setsid
 col                                  pamdeinterlace                     setterm
 col1                                 pamdepth                           setupcon
 col2                                 pamdice                            sftp
 col3                                 pamditherbw                        sg
 col4                                 pamedge                            sg_bg_ctl
 col5                                 pamendian                          sg_compare_and_write
 col6                                 pamenlarge                         sg_copy_results
 col7                                 pamexec                            sg_dd
 col8                                 pamfile                            sg_decode_sense
 col9                                 pamfind                            sg_emc_trespass
 colcrt                               pamfix                             sg_format
 colrm                                pamfixtrunc                        sg_get_config
 column                               pamflip                            sg_get_elem_status
 comm                                 pamfunc                            sg_get_lba_status
 compare                              pamgauss                           sg_ident
 compare-im6                          pamgetcolor                        sginfo
 compare-im6.q16                      pamgradient                        sg_inq
 composite                            pamhomography                      sgitopnm
 composite-im6                        pamhue                             sg_logs
 composite-im6.q16                    pamlevels                          sg_luns
 conch3                               pamlookup                          sg_map
 conjure                              pammasksharpen                     sg_map26
 conjure-im6                          pammixinterlace                    sgm_dd
 conjure-im6.q16                      pammixmulti                        sg_modes
 convert                              pammosaicknit                      sg_opcodes
 convert-im6                          pamoil                             sgp_dd
 convert-im6.q16                      pampaintspill                      sg_persist
 corelist                             pamperspective                     sg_prevent
 cp                                   pampick                            sg_raw
 cpan                                 pampop9                            sg_rbuf
 cpan5.38-x86_64-linux-gnu            pamrecolor                         sg_rdac
 cpio                                 pamrestack                         sg_read
 cpupower                             pamrgbatopng                       sg_read_attr
 c_rehash                             pamrubber                          sg_read_block_limits
 crontab                              pamscale                           sg_read_buffer
 csplit                               pamseq                             sg_readcap
 ctail                                pamshadedrelief                    sg_read_long
 ctstat                               pamsharpmap                        sg_reassign
 curl                                 pamsharpness                       sg_referrals
 cut                                  pamshuffle                         sg_rep_pip
 cvtsudoers                           pamsistoaglyph                     sg_rep_zones
 dash                                 pamslice                           sg_requests
 date                                 pamsplit                           sg_reset
 dbus-cleanup-sockets                 pamstack                           sg_reset_wp
 dbus-daemon                          pamstereogram                      sg_rmsn
 dbus-monitor                         pamstretch                         sg_rtpg
 dbus-run-session                     pamstretch-gen                     sg_safte
 dbus-send                            pamsumm                            sg_sanitize
 dbus-update-activation-environment   pamsummcol                         sg_sat_identify
 dbus-uuidgen                         pamtable                           sg_sat_phy_event
 dbxtool                              pamthreshold                       sg_sat_read_gplog
 dd                                   pamtilt                            sg_sat_set_features
 ddbugtopbm                           pamtoavs                           sg_scan
 deallocvt                            pamtodjvurle                       sg_seek
 debconf                              pamtofits                          sg_senddiag
 debconf-apt-progress                 pamtogif                           sg_ses
 debconf-communicate                  pamtohdiff                         sg_ses_microcode
 debconf-copydb                       pamtohtmltbl                       sg_start
 debconf-escape                       pamtojpeg2k                        sg_stpg
 debconf-set-selections               pamtompfont                        sg_stream_ctl
 debconf-show                         pamtooctaveimg                     sg_sync
 debian-distro-info                   pamtopam                           sg_test_rwbuf
 deb-systemd-helper                   pamtopdbimg                        sg_timestamp
 deb-systemd-invoke                   pamtopfm                           sg_turs
 delpart                              pamtopng                           sg_unmap
 delv                                 pamtopnm                           sg_verify
 df                                   pamtoqoi                           sg_vpd
 dh_bash-completion                   pamtosrf                           sg_write_buffer
 dh_installxmlcatalogs                pamtosvg                           sg_write_long
 diff                                 pamtotga                           sg_write_same
 diff3                                pamtotiff                          sg_write_verify
 dig                                  pamtouil                           sg_write_x
 dir                                  pamtowinicon                       sg_wr_mode
 dircolors                            pamtoxvmini                        sg_xcopy
 dirmngr                              pamtris                            sg_zone
 dirmngr-client                       pamundice                          sh
 dirname                              pamunlookup                        sha1sum
 display                              pamvalidate                        sha224sum
 display-im6                          pamwipeout                         sha256sum
 display-im6.q16                      pamx                               sha384sum
 distro-info                          paperconf                          sha512sum
 dmesg                                partx                              shasum
 dnsdomainname                        passwd                             showconsolefont
 domainname                           paste                              showkey
 do-release-upgrade                   pastebinit                         shred
 dpkg                                 patch                              shuf
 dpkg-deb                             pathchk                            sirtopnm
 dpkg-divert                          pbget                              sixel2png
 dpkg-maintscript-helper              pbmclean                           skill
 dpkg-query                           pbmlife                            slabtop
 dpkg-realpath                        pbmmake                            sldtoppm
 dpkg-split                           pbmmask                            sleep
 dpkg-statoverride                    pbmminkowski                       slogin
 dpkg-trigger                         pbmnoise                           snap
 du                                   pbmpage                            snapctl
 dumpkeys                             pbmpscale                          snapfuse
 dvipdf                               pbmreduce                          snice
 eatmydata                            pbmtext                            soelim
 ec2metadata                          pbmtextps                          sort
 echo                                 pbmto10x                           sos
 ed                                   pbmto4425                          sos-collector
 editor                               pbmtoascii                         sosreport
 egrep                                pbmtoatk                           sotruss
 eject                                pbmtobbnbg                         spctoppm
 enc2xs                               pbmtocis                           splain
 encguess                             pbmtocmuwm                         split
 env                                  pbmtodjvurle                       splitfont
 envsubst                             pbmtoepsi                          spottopgm
 eps2eps                              pbmtoepson                         sprof
 eqn                                  pbmtoescp2                         sputoppm
 escp2topbm                           pbmtog3                            sqfscat
 ex                                   pbmtogem                           sqfstar
 expand                               pbmtogo                            srftopam
 expiry                               pbmtoibm23xx                       ss
 expr                                 pbmtoicon                          ssh
 eyuvtoppm                            pbmtolj                            ssh-add
 factor                               pbmtoln03                          ssh-agent
 faillog                              pbmtolps                           ssh-argv0
 fallocate                            pbmtomacp                          ssh-copy-id
 false                                pbmtomatrixorbital                 ssh-import-id
 fc-cache                             pbmtomda                           ssh-import-id-gh
 fc-cat                               pbmtomgr                           ssh-import-id-lp
 fc-conflist                          pbmtomrf                           ssh-keygen
 fc-list                              pbmtonokia                         ssh-keyscan
 fc-match                             pbmtopgm                           st4topgm
 fc-pattern                           pbmtopi3                           stat
 fc-query                             pbmtopk                            static-sh
 fc-scan                              pbmtoplot                          stdbuf
 fc-validate                          pbmtoppa                           strace
 fgconsole                            pbmtopsg3                          strace-log-merge
 fgrep                                pbmtoptx                           stream
 fiascotopnm                          pbmtosunicon                       stream-im6
 figlet                               pbmtowbmp                          stream-im6.q16
 figlet-toilet                        pbmtox10bm                         streamzip
 file                                 pbmtoxbm                           stty
 finalrd                              pbmtoybm                           su
 find                                 pbmtozinc                          sudo
 findmnt                              pbmupc                             sudoedit
 fitstopnm                            pbput                              sudoreplay
 flock                                pbputs                             sum
 fmt                                  pc1toppm                           sunicontopnm
 fold                                 pcdindex                           svgtopam
 fonttosfnt                           pcdovtoppm                         sync
 free                                 pcxtoppm                           systemctl
 fstopgm                              pdb3                               systemd
 ftp                                  pdb3.12                            systemd-ac-power
 fuser                                pdbimgtopam                        systemd-analyze
 fusermount                           pdf2dsc                            systemd-ask-password
 fusermount3                          pdf2ps                             systemd-cat
 fwupdmgr                             peekfd                             systemd-cgls
 fwupdtool                            perf                               systemd-cgtop
 g3topbm                              perl                               systemd-confext
 gapplication                         perl5.38.2                         systemd-creds
 gawk                                 perl5.38-x86_64-linux-gnu          systemd-cryptenroll
 gawkbug                              perlbug                            systemd-cryptsetup
 gdbus                                perldoc                            systemd-delta
 gdk-pixbuf-csource                   perlivp                            systemd-detect-virt
 gdk-pixbuf-pixdata                   perlthanks                         systemd-escape
 gdk-pixbuf-thumbnailer               pf2afm                             systemd-firstboot
 gemtopbm                             pfbtopfa                           systemd-hwdb
 gemtopnm                             pfmtopam                           systemd-id128
 gencat                               pgmabel                            systemd-inhibit
 geqn                                 pgmbentley                         systemd-machine-id-setup
 getconf                              pgmcrater                          systemd-mount
 getent                               pgmdeshadow                        systemd-notify
 getkeycodes                          pgmedge                            systemd-path
 getopt                               pgmenhance                         systemd-repart
 gettext                              pgmhist                            systemd-run
 gettext.sh                           pgmkernel                          systemd-socket-activate
 ghostscript                          pgmmake                            systemd-stdio-bridge
 giftopnm                             pgmmedian                          systemd-sysext
 ginstall-info                        pgmminkowski                       systemd-sysusers
 gio                                  pgmmorphconv                       systemd-tmpfiles
 gio-querymodules                     pgmnoise                           systemd-tty-ask-password-agent
 git                                  pgmnorm                            systemd-umount
 git-receive-pack                     pgmoil                             tabs
 git-shell                            pgmramp                            tac
 git-upload-archive                   pgmslice                           tail
 git-upload-pack                      pgmtexture                         tapestat
 glib-compile-schemas                 pgmtofs                            tar
 gouldtoppm                           pgmtolispm                         taskset
 gpasswd                              pgmtopbm                           tbl
 gpg                                  pgmtopgm                           tclsh
 gpg-agent                            pgmtoppm                           tclsh8.6
 gpgconf                              pgmtosbig                          tcpdump
 gpg-connect-agent                    pgmtost4                           tee
 gpgparsemail                         pgrep                              telnet
 gpgsm                                pi1toppm                           tempfile
 gpgsplit                             pi3topbm                           test
 gpgtar                               pic                                tgatoppm
 gpgv                                 pico                               thinkjettopbm
 gpg-wks-client                       piconv                             tic
 gpic                                 pidof                              tifftopnm
 gpu-manager                          pidstat                            time
 grep                                 pidwait                            timedatectl
 gresource                            pinentry                           timeout
 groff                                pinentry-curses                    tkconch3
 grog                                 ping                               tload
 grops                                ping4                              tmux
 grotty                               ping6                              tnftp
 groups                               pinky                              toe
 growpart                             pjtoppm                            toilet
 grub-editenv                         pkaction                           top
 grub-file                            pkcheck                            touch
 grub-fstest                          pkcon                              tput
 grub-glue-efi                        pkill                              tr
 grub-kbdcomp                         pkmon                              trace-cmd
 grub-menulst2cfg                     pktopbm                            tracepath
 grub-mkfont                          pkttyagent                         trial3
 grub-mkimage                         pl2pm                              troff
 grub-mklayout                        pldd                               true
 grub-mknetdir                        plocate                            truncate
 grub-mkpasswd-pbkdf2                 plymouth                           tset
 grub-mkrelpath                       pmap                               tsort
 grub-mkrescue                        pngtopam                           tty
 grub-mkstandalone                    pngtopnm                           turbostat
 grub-mount                           pnmalias                           twist3
 grub-ntldr-img                       pnmarith                           twistd3
 grub-render-label                    pnmcat                             tzselect
 grub-script-check                    pnmcolormap                        ua
 grub-syslinux2cfg                    pnmcomp                            ubuntu-advantage
 gs                                   pnmconvol                          ubuntu-bug
 gsbj                                 pnmcrop                            ubuntu-distro-info
 gsdj                                 pnmcut                             ubuntu-drivers
 gsdj500                              pnmdepth                           ubuntu-security-status
 gsettings                            pnmenlarge                         ucf
 gslj                                 pnmfile                            ucfq
 gslp                                 pnmflip                            ucfr
 gsnd                                 pnmgamma                           uclampset
 gtbl                                 pnmhisteq                          ucs2any
 gunzip                               pnmhistmap                         udevadm
 gzexe                                pnmindex                           udisksctl
 gzip                                 pnminterp                          ul
 h2ph                                 pnminterp-gen                      umount
 h2xs                                 pnminvert                          uname
 hardlink                             pnmmargin                          unattended-upgrade
 hd                                   pnmmercator                        unattended-upgrades
 hdifftopam                           pnmmontage                         uncompress
 head                                 pnmnlfilt                          unexpand
 helpztags                            pnmnoraw                           unicode_start
 hexdump                              pnmnorm                            unicode_stop
 hipstopgm                            pnmpad                             uniq
 host                                 pnmpaste                           unlink
 hostid                               pnmpsnr                            unlzma
 hostname                             pnmquant                           unminimize
 hostnamectl                          pnmquantall                        unmkinitramfs
 hpcdtoppm                            pnmremap                           unshare
 htop                                 pnmrotate                          unsquashfs
 hwe-support-status                   pnmscale                           unxz
 i386                                 pnmscalefixed                      unzstd
 icontopbm                            pnmshear                           update-alternatives
 iconv                                pnmsmooth                          updatedb
 id                                   pnmsplit                           update-mime-database
 identify                             pnmstitch                          upower
 identify-im6                         pnmtile                            uptime
 identify-im6.q16                     pnmtoddif                          usb-devices
 ilbmtoppm                            pnmtofiasco                        usbhid-dump
 imagetops                            pnmtofits                          usbip
 img2sixel                            pnmtojbig                          usbipd
 img2txt                              pnmtojpeg                          usbreset
 imgtoppm                             pnmtopalm                          users
 import                               pnmtopclxl                         utmpdump
 import-im6                           pnmtoplainpnm                      uuidgen
 import-im6.q16                       pnmtopng                           uuidparse
 inetutils-telnet                     pnmtopnm                           varlinkctl
 info                                 pnmtops                            vcs-run
 infobrowser                          pnmtorast                          vdir
 infocmp                              pnmtorle                           VGAuthService
 infotocap                            pnmtosgi                           vi
 infotopam                            pnmtosir                           view
 install                              pnmtotiff                          vigpg
 install-info                         pnmtotiffcmyk                      vim
 instmodsh                            pnmtoxwd                           vim.basic
 ionice                               pod2html                           vimdiff
 iostat                               pod2man                            vim.tiny
 ip                                   pod2text                           vimtutor
 ipcmk                                pod2usage                          vmhgfs-fuse
 ipcrm                                podchecker                         vmstat
 ipcs                                 pollinate                          vm-support
 iptables-xml                         pphs                               vmtoolsd
 ischroot                             ppm3d                              vmware-alias-import
 iscsiadm                             ppmbrighten                        vmware-checkvm
 jbigtopnm                            ppmchange                          vmware-hgfsclient
 join                                 ppmcie                             vmware-namespace-cmd
 journalctl                           ppmcolormask                       vmware-rpctool
 jp2a                                 ppmcolors                          vmware-toolbox-cmd
 jpeg2ktopam                          ppmdcfont                          vmware-vgauth-cmd
 jpegtopnm                            ppmddumpfont                       vmware-vmblock-fuse
 jq                                   ppmdim                             vmware-xferlogs
 jsondiff                             ppmdist                            w
 jsonpatch                            ppmdither                          w3m
 json-patch-jsondiff                  ppmdmkfont                         w3mman
 jsonpointer                          ppmdraw                            wall
 json_pp                              ppmfade                            watch
 jsonschema                           ppmflash                           watchgnupg
 JxrDecApp                            ppmforge                           wbmptopbm
 JxrEncApp                            ppmglobe                           wc
 kbdinfo                              ppmhist                            wdctl
 kbd_mode                             ppmlabel                           wget
 kbxutil                              ppmmake                            whatis
 keep-one-running                     ppmmix                             whereis
 kernel-install                       ppmnorm                            which
 kill                                 ppmntsc                            which.debianutils
 killall                              ppmpat                             whiptail
 kmod                                 ppmquant                           who
 kmodsign                             ppmquantall                        whoami
 landscape-sysinfo                    ppmrainbow                         wifi-status
 last                                 ppmrelief                          winicontopam
 lastb                                ppmrough                           winicontoppm
 lastlog                              ppmshadow                          write
 lcf                                  ppmshift                           www-browser
 ldd                                  ppmspread                          X11
 ld.so                                ppmtoacad                          x86_64
 leaftoppm                            ppmtoapplevol                      x86_energy_perf_policy
 less                                 ppmtoarbtxt                        xargs
 lessecho                             ppmtoascii                         xauth
 lessfile                             ppmtobmp                           xbmtopbm
 lesskey                              ppmtoeyuv                          xdg-user-dir
 lesspipe                             ppmtogif                           xdg-user-dirs-update
 lexgrog                              ppmtoicr                           ximtoppm
 libnetcfg                            ppmtoilbm                          xpmtoppm
 libsixel-config                      ppmtojpeg                          xsubpp
 link                                 ppmtoleaf                          xvminitoppm
 linux32                              ppmtolj                            xwdtopnm
 linux64                              ppmtomap                           xxd
 linux-boot-prober                    ppmtomitsu                         xz
 linux-check-removal                  ppmtompeg                          xzcat
 linux-update-symlinks                ppmtoneo                           xzcmp
 linux-version                        ppmtopcx                           xzdiff
 lispmtopgm                           ppmtopgm                           xzegrep
 ln                                   ppmtopi1                           xzfgrep
 lnstat                               ppmtopict                          xzgrep
 loadkeys                             ppmtopj                            xzless
 loadunimap                           ppmtopjxl                          xzmore
 locale                               ppmtoppm                           ybmtopbm
 locale-check                         ppmtopuzz                          yes
 localectl                            ppmtorgb3                          ypdomainname
 localedef                            ppmtosixel                         yuvsplittoppm
 locate                               ppmtospu                           yuvtoppm
 logger                               ppmtoterm                          yuy2topam
 login                                ppmtotga                           zcat
 loginctl                             ppmtouil                           zcmp
 logname                              ppmtowinicon                       zdiff
 look                                 ppmtoxpm                           zdump
 lowntfs-3g                           ppmtoyuv                           zegrep
 ls                                   ppmtoyuvsplit                      zeisstopnm
 lsattr                               ppmtv                              zfgrep
 lsblk                                ppmwheel                           zforce
 lsb_release                          pr                                 zgrep
 lscpu                                preconv                            zipdetails
 lshw                                 printafm                           zless
 lsinitramfs                          printenv                           zmore
 lsipc                                printf                             znew
 lslocks                              prlimit                            zstd
 lslogins                             pro                                zstdcat
 lsmem                                prove                              zstdgrep
 lsmod                                prtstat                            zstdless
 lsns                                 ps                                 zstdmt
 lsof                                 ps2ascii
 lspci                                ps2epsi
pluto@Ubuntu-Server-Lab:/usr/bin$ pwd
/usr/bin
pluto@Ubuntu-Server-Lab:/usr/bin$ cat
pluto@Ubuntu-Server-Lab:/usr/bin$
```
**/sbin**
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /sbin
pluto@Ubuntu-Server-Lab:/sbin$ ls
aa-load                fsck.fat                     mkswap                 tclflow-bpfcc
aa-remove-unknown      fsck.minix                   ModemManager           tclobjnew-bpfcc
aa-status              fsck.msdos                   modinfo                tclstat-bpfcc
aa-teardown            fsck.vfat                    modprobe               tcpaccept-bpfcc
accessdb               fsck.xfs                     mount.fuse             tcpaccept.bt
addgnupghome           fsfreeze                     mount.fuse3            tcpcong-bpfcc
addgroup               fstab-decode                 mount.lowntfs-3g       tcpconnect-bpfcc
add-shell              fstrim                       mount.ntfs             tcpconnect.bt
adduser                funccount-bpfcc              mount.ntfs-3g          tcpconnlat-bpfcc
agetty                 funcinterval-bpfcc           mountsnoop-bpfcc       tcpdrop-bpfcc
apparmor_parser        funclatency-bpfcc            mpathpersist           tcpdrop.bt
apparmor_status        funcslower-bpfcc             multipath              tcplife-bpfcc
applygnupgdefaults     gdisk                        multipathc             tcplife.bt
argdist-bpfcc          genl                         multipathd             tcpretrans-bpfcc
arpd                   getcap                       mysqld_qslower-bpfcc   tcpretrans.bt
arptables              gethostlatency-bpfcc         naptime.bt             tcprtt-bpfcc
arptables-nft          gethostlatency.bt            needrestart            tcpstates-bpfcc
arptables-nft-restore  getpcaps                     netplan                tcpsubnet-bpfcc
arptables-nft-save     getty                        netqtop-bpfcc          tcpsynbl-bpfcc
arptables-restore      groupadd                     newusers               tcpsynbl.bt
arptables-save         groupdel                     nfnl_osf               tcptop-bpfcc
badblocks              groupmems                    nfsdist-bpfcc          tcptracer-bpfcc
bashreadline-bpfcc     groupmod                     nfsslower-bpfcc        telinit
bashreadline.bt        grpck                        nft                    thermald
bcache-super-show      grpconv                      nodegc-bpfcc           thin_check
bindsnoop-bpfcc        grpunconv                    nodestat-bpfcc         thin_delta
biolatency-bpfcc       grub-bios-setup              nologin                thin_dump
biolatency.bt          grub-install                 ntfsclone              thin_ls
biolatency-kp.bt       grub-macbless                ntfscp                 thin_metadata_size
biolatpcts-bpfcc       grub-mkconfig                ntfslabel              thin_repair
biopattern-bpfcc       grub-mkdevicemap             ntfsresize             thin_restore
biosdecode             grub-probe                   ntfsundelete           thin_rmap
biosnoop-bpfcc         grub-reboot                  offcputime-bpfcc       thin_trim
biosnoop.bt            grub-set-default             offwaketime-bpfcc      threadsnoop-bpfcc
biostacks.bt           halt                         on_ac_power            threadsnoop.bt
biotop-bpfcc           hardirqs-bpfcc               oomkill-bpfcc          tipc
bitesize-bpfcc         hdparm                       oomkill.bt             tplist-bpfcc
bitesize.bt            iconvconfig                  opensnoop-bpfcc        trace-bpfcc
blkdeactivate          init                         opensnoop.bt           ttysnoop-bpfcc
blkdiscard             inject-bpfcc                 overlayroot-chroot     tune2fs
blkid                  insmod                       ownership              ucalls
blkzone                installkernel                pam-auth-update        u-d-c-print-pci-ids
blockdev               install-sgmlcatalog          pam_extrausers_chkpwd  uflow
bpflist-bpfcc          integritysetup               pam_extrausers_update  ufw
bpftool                invoke-rc.d                  pam_getenv             ugc
bridge                 ip                           pam_namespace_helper   umount.udisks2
btrfsdist-bpfcc        ip6tables                    pam_timestamp_check    undump.bt
btrfsslower-bpfcc      ip6tables-apply              paperconfig            unix_chkpwd
cache_check            ip6tables-legacy             parted                 unix_update
cache_dump             ip6tables-legacy-restore     partprobe              uobjnew
cache_metadata_size    ip6tables-legacy-save        pdata_tools            update-ca-certificates
cache_repair           ip6tables-nft                perlcalls-bpfcc        update-catalog
cache_restore          ip6tables-nft-restore        perlflow-bpfcc         updatedb.plocate
cachestat-bpfcc        ip6tables-nft-save           perlstat-bpfcc         update-fonts-alias
cachetop-bpfcc         ip6tables-restore            phpcalls-bpfcc         update-fonts-dir
cache_writeback        ip6tables-restore-translate  phpflow-bpfcc          update-fonts-scale
capable-bpfcc          ip6tables-save               phpstat-bpfcc          update-grub
capable.bt             ip6tables-translate          pidpersec-bpfcc        update-grub2
capsh                  iptables                     pidpersec.bt           update-grub-gfxpayload
cfdisk                 iptables-apply               pivot_root             update-gsfontmap
cgdisk                 iptables-legacy              plocate-build          update-ieee-data
chcpu                  iptables-legacy-restore      plymouthd              update-info-dir
chgpasswd              iptables-legacy-save         poweroff               update-initramfs
chmem                  iptables-nft                 ppchcalls-bpfcc        update-locale
chpasswd               iptables-nft-restore         profile-bpfcc          update-passwd
chroot                 iptables-nft-save            pvchange               update-pciids
cobjnew-bpfcc          iptables-restore             pvck                   update-rc.d
compactsnoop-bpfcc     iptables-restore-translate   pvcreate               update-shells
cpgr                   iptables-save                pvdisplay              update-xmlcatalog
cppw                   iptables-translate           pvmove                 upgrade-from-grub-legacy
cpudist-bpfcc          iscsiadm                     pvremove               usb_modeswitch
cpuunclaimed-bpfcc     iscsid                       pvresize               usb_modeswitch_dispatcher
cpuwalk.bt             iscsi_discovery              pvs                    usbmuxd
criticalstat-bpfcc     iscsi-iname                  pvscan                 useradd
cron                   iscsistart                   pwck                   userdel
cryptdisks_start       isosize                      pwconv                 usermod
cryptdisks_stop        iucode-tool                  pwhistory_helper       ustat
cryptsetup             iucode_tool                  pwunconv               uthreads
ctrlaltdel             javacalls-bpfcc              pythoncalls-bpfcc      uuidd
dbslower-bpfcc         javaflow-bpfcc               pythonflow-bpfcc       validlocale
dbstat-bpfcc           javagc-bpfcc                 pythongc-bpfcc         vcstime
dcb                    javaobjnew-bpfcc             pythonstat-bpfcc       vdpa
dcsnoop-bpfcc          javastat-bpfcc               rdmaucma-bpfcc         veritysetup
dcsnoop.bt             javathreads-bpfcc            readahead-bpfcc        vfscount-bpfcc
dcstat-bpfcc           kbdrate                      readprofile            vfscount.bt
deadlock-bpfcc         killall5                     reboot                 vfsstat-bpfcc
debugfs                killsnoop-bpfcc              remove-shell           vfsstat.bt
delgroup               killsnoop.bt                 reset-trace-bpfcc      vgcfgbackup
deluser                klockstat-bpfcc              resize2fs              vgcfgrestore
depmod                 kpartx                       resolvconf             vgchange
devlink                kvmexit-bpfcc                rmmod                  vgck
dhcpcd                 ldattach                     rmt                    vgconvert
dirtop-bpfcc           ldconfig                     rmt-tar                vgcreate
dmeventd               ldconfig.real                rsyslogd               vgdisplay
dmidecode              llcstat-bpfcc                rtacct                 vgexport
dmsetup                loads.bt                     rtcwake                vgextend
dmstats                locale-gen                   rtmon                  vgimport
dosfsck                logrotate                    rubycalls-bpfcc        vgimportclone
dosfslabel             logsave                      rubyflow-bpfcc         vgmerge
dpkg-preconfigure      losetup                      rubygc-bpfcc           vgmknodes
dpkg-reconfigure       lsmod                        rubyobjnew-bpfcc       vgreduce
drsnoop-bpfcc          luksformat                   rubystat-bpfcc         vgremove
dumpe2fs               lvchange                     runlevel               vgrename
e2freefrag             lvconvert                    runqlat-bpfcc          vgs
e2fsck                 lvcreate                     runqlat.bt             vgscan
e2image                lvdisplay                    runqlen-bpfcc          vgsplit
e2label                lvextend                     runqlen.bt             vigr
e2mmpstatus            lvm                          runqslower-bpfcc       vipw
e2scrub                lvmconfig                    runuser                virtiostat-bpfcc
e2scrub_all            lvmdiskscan                  service                visudo
e2undo                 lvmdump                      setcap                 vpddecode
e4crypt                lvmpolld                     setuids.bt             wakeuptime-bpfcc
e4defrag               lvmsadc                      setvesablank           wipefs
ebtables               lvmsar                       setvtrgb               writeback.bt
ebtables-nft           lvreduce                     sfdisk                 xfs_admin
ebtables-nft-restore   lvremove                     sgdisk                 xfs_bmap
ebtables-nft-save      lvrename                     shadowconfig           xfs_copy
ebtables-restore       lvresize                     shmsnoop-bpfcc         xfs_db
ebtables-save          lvs                          shutdown               xfsdist-bpfcc
ebtables-translate     lvscan                       slabratetop-bpfcc      xfsdist.bt
era_check              lxc                          sofdsnoop-bpfcc        xfs_estimate
era_dump               lxd                          softirqs-bpfcc         xfs_freeze
era_invalidate         make-bcache                  solisten-bpfcc         xfs_fsr
era_restore            mdadm                        sshd                   xfs_growfs
ethtool                mdflush-bpfcc                ssllatency.bt          xfs_info
execsnoop-bpfcc        mdflush.bt                   sslsniff-bpfcc         xfs_io
execsnoop.bt           mdmon                        sslsnoop.bt            xfs_logprint
exitsnoop-bpfcc        memleak-bpfcc                stackcount-bpfcc       xfs_mdrestore
ext4dist-bpfcc         mkdosfs                      start-stop-daemon      xfs_metadump
ext4slower-bpfcc       mke2fs                       statsnoop-bpfcc        xfs_mkfile
faillock               mkfs                         statsnoop.bt           xfs_ncheck
fatlabel               mkfs.bfs                     sudo_logsrvd           xfs_quota
fdisk                  mkfs.btrfs                   sudo_sendlog           xfs_repair
filefrag               mkfs.cramfs                  sulogin                xfs_rtcp
filegone-bpfcc         mkfs.ext2                    swapin.bt              xfs_scrub
filelife-bpfcc         mkfs.ext3                    swaplabel              xfs_scrub_all
fileslower-bpfcc       mkfs.ext4                    swapoff                xfsslower-bpfcc
filetop-bpfcc          mkfs.fat                     swapon                 xfs_spaceman
findfs                 mkfs.minix                   switch_root            xtables-legacy-multi
fixparts               mkfs.msdos                   syncsnoop-bpfcc        xtables-monitor
fsadm                  mkfs.ntfs                    syncsnoop.bt           xtables-nft-multi
fsck                   mkfs.vfat                    syscount-bpfcc         zerofree
fsck.btrfs             mkfs.xfs                     syscount.bt            zfsdist-bpfcc
fsck.cramfs            mkhomedir_helper             sysctl                 zfsslower-bpfcc
fsck.ext2              mkinitramfs                  tarcat                 zic
fsck.ext3              mklost+found                 tc                     zramctl
fsck.ext4              mkntfs                       tclcalls-bpfcc
pluto@Ubuntu-Server-Lab:/sbin$ pwd
/sbin
pluto@Ubuntu-Server-Lab:/sbin$ cat
pluto@Ubuntu-Server-Lab:/sbin$
```

**/tmp**
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /tmp
pluto@Ubuntu-Server-Lab:/tmp$ ls
snap-private-tmp
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-ModemManager.service-zgVZTp
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-polkit.service-B63PWD
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-systemd-logind.service-fV4Pho
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-systemd-resolved.service-mySaLE
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-systemd-timesyncd.service-DP7jRY
systemd-private-e2ad428e08b84eb4802ad2ba11e68670-upower.service-eB8u2v
pluto@Ubuntu-Server-Lab:/tmp$ pwd
/tmp
pluto@Ubuntu-Server-Lab:/tmp$ cat 
```

**/boot**
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /boot
pluto@Ubuntu-Server-Lab:/boot$ ls
config-6.8.0-100-generic  initrd.img-6.8.0-100-generic  System.map-6.8.0-101-generic  vmlinuz.old
config-6.8.0-101-generic  initrd.img-6.8.0-101-generic  vmlinuz
grub                      initrd.img.old                vmlinuz-6.8.0-100-generic
initrd.img                System.map-6.8.0-100-generic  vmlinuz-6.8.0-101-generic
pluto@Ubuntu-Server-Lab:/boot$ pwd
/boot
pluto@Ubuntu-Server-Lab:/boot$ cat 
```

3. Telusuri direktory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty (terminal) Anda (ketik who am i); siapa pemilik tty Anda (gunakan ls -l).
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /dev
pluto@Ubuntu-Server-Lab:/dev$ who am i
pluto    pts/0        2026-03-08 05:54 (192.168.1.10)
pluto@Ubuntu-Server-Lab:/dev$ ls -l
total 0
crw-r--r--  1 root  root     10, 235 Mar  8 05:53 autofs
drwxr-xr-x  2 root  root         280 Mar  8 05:53 block
drwxr-xr-x  2 root  root          80 Mar  8 05:53 bsg
crw-rw----  1 root  disk     10, 234 Mar  8 05:53 btrfs-control
drwxr-xr-x  3 root  root          60 Mar  8 05:53 bus
lrwxrwxrwx  1 root  root           3 Mar  8 05:53 cdrom -> sr0
drwxr-xr-x  2 root  root        3740 Mar  8 05:53 char
crw-------  1 root  root      5,   1 Mar  8 05:53 console
lrwxrwxrwx  1 root  root          11 Mar  8 05:53 core -> /proc/kcore
drwxr-xr-x  5 root  root         100 Mar  8 05:53 cpu
crw-------  1 root  root     10, 123 Mar  8 05:53 cpu_dma_latency
crw-------  1 root  root     10, 203 Mar  8 05:53 cuse
drwxr-xr-x  7 root  root         140 Mar  8 05:53 disk
drwxr-xr-x  2 root  root          60 Mar  8 05:53 dma_heap
drwxr-xr-x  3 root  root         100 Mar  8 05:53 dri
crw-------  1 root  root     10, 125 Mar  8 05:53 ecryptfs
crw-rw----  1 root  video    29,   0 Mar  8 05:53 fb0
lrwxrwxrwx  1 root  root          13 Mar  8 05:53 fd -> /proc/self/fd
crw-rw-rw-  1 root  root      1,   7 Mar  8 05:53 full
crw-rw-rw-  1 root  root     10, 229 Mar  8 05:53 fuse
crw-------  1 root  root    241,   0 Mar  8 05:53 hidraw0
crw-------  1 root  root     10, 228 Mar  8 05:53 hpet
drwxr-xr-x  2 root  root           0 Mar  8 05:53 hugepages
crw-------  1 root  root     10, 183 Mar  8 05:53 hwrng
crw-------  1 root  root     89,   0 Mar  8 05:53 i2c-0
lrwxrwxrwx  1 root  root          12 Mar  8 05:53 initctl -> /run/initctl
drwxr-xr-x  4 root  root         340 Mar  8 05:53 input
crw-r--r--  1 root  root      1,  11 Mar  8 05:53 kmsg
lrwxrwxrwx  1 root  root          28 Mar  8 05:53 log -> /run/systemd/journal/dev-log
brw-rw----  1 root  disk      7,   0 Mar  8 05:53 loop0
brw-rw----  1 root  disk      7,   1 Mar  8 05:53 loop1
brw-rw----  1 root  disk      7,   2 Mar  8 05:53 loop2
brw-rw----  1 root  disk      7,   3 Mar  8 05:53 loop3
brw-rw----  1 root  disk      7,   4 Mar  8 05:53 loop4
brw-rw----  1 root  disk      7,   5 Mar  8 05:53 loop5
brw-rw----  1 root  disk      7,   6 Mar  8 05:53 loop6
brw-rw----  1 root  disk      7,   7 Mar  8 05:53 loop7
crw-rw----  1 root  disk     10, 237 Mar  8 05:53 loop-control
drwxr-xr-x  2 root  root          60 Mar  8 05:53 mapper
crw-------  1 root  root     10, 227 Mar  8 05:53 mcelog
crw-r-----  1 root  kmem      1,   1 Mar  8 05:53 mem
drwxrwxrwt  2 root  root          40 Mar  8 05:53 mqueue
drwxr-xr-x  2 root  root          60 Mar  8 05:53 net
crw-rw-rw-  1 root  root      1,   3 Mar  8 05:53 null
crw-------  1 root  root     10, 144 Mar  8 05:53 nvram
crw-r-----  1 root  kmem      1,   4 Mar  8 05:53 port
crw-------  1 root  root    108,   0 Mar  8 05:53 ppp
crw-------  1 root  root     10,   1 Mar  8 05:53 psaux
crw-rw-rw-  1 root  tty       5,   2 Mar  8 08:44 ptmx
drwxr-xr-x  2 root  root           0 Mar  8 05:53 pts
crw-rw-rw-  1 root  root      1,   8 Mar  8 05:53 random
crw-rw-r--+ 1 root  root     10, 242 Mar  8 05:53 rfkill
lrwxrwxrwx  1 root  root           4 Mar  8 05:53 rtc -> rtc0
crw-------  1 root  root    248,   0 Mar  8 05:53 rtc0
brw-rw----  1 root  disk      8,   0 Mar  8 05:53 sda
brw-rw----  1 root  disk      8,   1 Mar  8 05:53 sda1
brw-rw----  1 root  disk      8,   2 Mar  8 05:53 sda2
crw-rw----+ 1 root  cdrom    21,   0 Mar  8 05:53 sg0
crw-rw----  1 root  disk     21,   1 Mar  8 05:53 sg1
drwxrwxrwt  2 root  root          40 Mar  8 05:53 shm
crw-------  1 root  root     10, 231 Mar  8 05:53 snapshot
drwxr-xr-x  3 root  root         180 Mar  8 05:53 snd
brw-rw----+ 1 root  cdrom    11,   0 Mar  8 05:53 sr0
lrwxrwxrwx  1 root  root          15 Mar  8 05:53 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root  root          15 Mar  8 05:53 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root  root          15 Mar  8 05:53 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root  tty       5,   0 Mar  8 05:53 tty
crw--w----  1 root  tty       4,   0 Mar  8 05:53 tty0
crw-------  1 pluto tty       4,   1 Mar  8 05:54 tty1
crw--w----  1 root  tty       4,  10 Mar  8 05:53 tty10
crw--w----  1 root  tty       4,  11 Mar  8 05:53 tty11
crw--w----  1 root  tty       4,  12 Mar  8 05:53 tty12
crw--w----  1 root  tty       4,  13 Mar  8 05:53 tty13
crw--w----  1 root  tty       4,  14 Mar  8 05:53 tty14
crw--w----  1 root  tty       4,  15 Mar  8 05:53 tty15
crw--w----  1 root  tty       4,  16 Mar  8 05:53 tty16
crw--w----  1 root  tty       4,  17 Mar  8 05:53 tty17
crw--w----  1 root  tty       4,  18 Mar  8 05:53 tty18
crw--w----  1 root  tty       4,  19 Mar  8 05:53 tty19
crw--w----  1 root  tty       4,   2 Mar  8 05:53 tty2
crw--w----  1 root  tty       4,  20 Mar  8 05:53 tty20
crw--w----  1 root  tty       4,  21 Mar  8 05:53 tty21
crw--w----  1 root  tty       4,  22 Mar  8 05:53 tty22
crw--w----  1 root  tty       4,  23 Mar  8 05:53 tty23
crw--w----  1 root  tty       4,  24 Mar  8 05:53 tty24
crw--w----  1 root  tty       4,  25 Mar  8 05:53 tty25
crw--w----  1 root  tty       4,  26 Mar  8 05:53 tty26
crw--w----  1 root  tty       4,  27 Mar  8 05:53 tty27
crw--w----  1 root  tty       4,  28 Mar  8 05:53 tty28
crw--w----  1 root  tty       4,  29 Mar  8 05:53 tty29
crw--w----  1 root  tty       4,   3 Mar  8 05:53 tty3
crw--w----  1 root  tty       4,  30 Mar  8 05:53 tty30
crw--w----  1 root  tty       4,  31 Mar  8 05:53 tty31
crw--w----  1 root  tty       4,  32 Mar  8 05:53 tty32
crw--w----  1 root  tty       4,  33 Mar  8 05:53 tty33
crw--w----  1 root  tty       4,  34 Mar  8 05:53 tty34
crw--w----  1 root  tty       4,  35 Mar  8 05:53 tty35
crw--w----  1 root  tty       4,  36 Mar  8 05:53 tty36
crw--w----  1 root  tty       4,  37 Mar  8 05:53 tty37
crw--w----  1 root  tty       4,  38 Mar  8 05:53 tty38
crw--w----  1 root  tty       4,  39 Mar  8 05:53 tty39
crw--w----  1 root  tty       4,   4 Mar  8 05:53 tty4
crw--w----  1 root  tty       4,  40 Mar  8 05:53 tty40
crw--w----  1 root  tty       4,  41 Mar  8 05:53 tty41
crw--w----  1 root  tty       4,  42 Mar  8 05:53 tty42
crw--w----  1 root  tty       4,  43 Mar  8 05:53 tty43
crw--w----  1 root  tty       4,  44 Mar  8 05:53 tty44
crw--w----  1 root  tty       4,  45 Mar  8 05:53 tty45
crw--w----  1 root  tty       4,  46 Mar  8 05:53 tty46
crw--w----  1 root  tty       4,  47 Mar  8 05:53 tty47
crw--w----  1 root  tty       4,  48 Mar  8 05:53 tty48
crw--w----  1 root  tty       4,  49 Mar  8 05:53 tty49
crw--w----  1 root  tty       4,   5 Mar  8 05:53 tty5
crw--w----  1 root  tty       4,  50 Mar  8 05:53 tty50
crw--w----  1 root  tty       4,  51 Mar  8 05:53 tty51
crw--w----  1 root  tty       4,  52 Mar  8 05:53 tty52
crw--w----  1 root  tty       4,  53 Mar  8 05:53 tty53
crw--w----  1 root  tty       4,  54 Mar  8 05:53 tty54
crw--w----  1 root  tty       4,  55 Mar  8 05:53 tty55
crw--w----  1 root  tty       4,  56 Mar  8 05:53 tty56
crw--w----  1 root  tty       4,  57 Mar  8 05:53 tty57
crw--w----  1 root  tty       4,  58 Mar  8 05:53 tty58
crw--w----  1 root  tty       4,  59 Mar  8 05:53 tty59
crw--w----  1 root  tty       4,   6 Mar  8 05:53 tty6
crw--w----  1 root  tty       4,  60 Mar  8 05:53 tty60
crw--w----  1 root  tty       4,  61 Mar  8 05:53 tty61
crw--w----  1 root  tty       4,  62 Mar  8 05:53 tty62
crw--w----  1 root  tty       4,  63 Mar  8 05:53 tty63
crw--w----  1 root  tty       4,   7 Mar  8 05:53 tty7
crw--w----  1 root  tty       4,   8 Mar  8 05:53 tty8
crw--w----  1 root  tty       4,   9 Mar  8 05:53 tty9
crw-------  1 root  root      5,   3 Mar  8 05:53 ttyprintk
crw-rw----  1 root  dialout   4,  64 Mar  8 05:53 ttyS0
crw-rw----  1 root  dialout   4,  65 Mar  8 05:53 ttyS1
crw-rw----  1 root  dialout   4,  74 Mar  8 05:53 ttyS10
crw-rw----  1 root  dialout   4,  75 Mar  8 05:53 ttyS11
crw-rw----  1 root  dialout   4,  76 Mar  8 05:53 ttyS12
crw-rw----  1 root  dialout   4,  77 Mar  8 05:53 ttyS13
crw-rw----  1 root  dialout   4,  78 Mar  8 05:53 ttyS14
crw-rw----  1 root  dialout   4,  79 Mar  8 05:53 ttyS15
crw-rw----  1 root  dialout   4,  80 Mar  8 05:53 ttyS16
crw-rw----  1 root  dialout   4,  81 Mar  8 05:53 ttyS17
crw-rw----  1 root  dialout   4,  82 Mar  8 05:53 ttyS18
crw-rw----  1 root  dialout   4,  83 Mar  8 05:53 ttyS19
crw-rw----  1 root  dialout   4,  66 Mar  8 05:53 ttyS2
crw-rw----  1 root  dialout   4,  84 Mar  8 05:53 ttyS20
crw-rw----  1 root  dialout   4,  85 Mar  8 05:53 ttyS21
crw-rw----  1 root  dialout   4,  86 Mar  8 05:53 ttyS22
crw-rw----  1 root  dialout   4,  87 Mar  8 05:53 ttyS23
crw-rw----  1 root  dialout   4,  88 Mar  8 05:53 ttyS24
crw-rw----  1 root  dialout   4,  89 Mar  8 05:53 ttyS25
crw-rw----  1 root  dialout   4,  90 Mar  8 05:53 ttyS26
crw-rw----  1 root  dialout   4,  91 Mar  8 05:53 ttyS27
crw-rw----  1 root  dialout   4,  92 Mar  8 05:53 ttyS28
crw-rw----  1 root  dialout   4,  93 Mar  8 05:53 ttyS29
crw-rw----  1 root  dialout   4,  67 Mar  8 05:53 ttyS3
crw-rw----  1 root  dialout   4,  94 Mar  8 05:53 ttyS30
crw-rw----  1 root  dialout   4,  95 Mar  8 05:53 ttyS31
crw-rw----  1 root  dialout   4,  68 Mar  8 05:53 ttyS4
crw-rw----  1 root  dialout   4,  69 Mar  8 05:53 ttyS5
crw-rw----  1 root  dialout   4,  70 Mar  8 05:53 ttyS6
crw-rw----  1 root  dialout   4,  71 Mar  8 05:53 ttyS7
crw-rw----  1 root  dialout   4,  72 Mar  8 05:53 ttyS8
crw-rw----  1 root  dialout   4,  73 Mar  8 05:53 ttyS9
crw-rw----  1 root  kvm      10, 124 Mar  8 05:53 udmabuf
crw-------  1 root  root     10, 239 Mar  8 05:53 uhid
crw-------  1 root  root     10, 223 Mar  8 05:53 uinput
crw-rw-rw-  1 root  root      1,   9 Mar  8 05:53 urandom
crw-------  1 root  root     10, 126 Mar  8 05:53 userfaultfd
crw-------  1 root  root     10, 240 Mar  8 05:53 userio
crw-------  1 root  root     10, 122 Mar  8 05:53 vboxguest
crw-------  1 root  root     10, 121 Mar  8 05:53 vboxuser
crw-rw----  1 root  tty       7,   0 Mar  8 05:53 vcs
crw-rw----  1 root  tty       7,   1 Mar  8 05:53 vcs1
crw-rw----  1 root  tty       7,   2 Mar  8 05:53 vcs2
crw-rw----  1 root  tty       7,   3 Mar  8 05:53 vcs3
crw-rw----  1 root  tty       7,   4 Mar  8 05:53 vcs4
crw-rw----  1 root  tty       7,   5 Mar  8 05:53 vcs5
crw-rw----  1 root  tty       7,   6 Mar  8 05:53 vcs6
crw-rw----  1 root  tty       7, 128 Mar  8 05:53 vcsa
crw-rw----  1 root  tty       7, 129 Mar  8 05:53 vcsa1
crw-rw----  1 root  tty       7, 130 Mar  8 05:53 vcsa2
crw-rw----  1 root  tty       7, 131 Mar  8 05:53 vcsa3
crw-rw----  1 root  tty       7, 132 Mar  8 05:53 vcsa4
crw-rw----  1 root  tty       7, 133 Mar  8 05:53 vcsa5
crw-rw----  1 root  tty       7, 134 Mar  8 05:53 vcsa6
crw-rw----  1 root  tty       7,  64 Mar  8 05:53 vcsu
crw-rw----  1 root  tty       7,  65 Mar  8 05:53 vcsu1
crw-rw----  1 root  tty       7,  66 Mar  8 05:53 vcsu2
crw-rw----  1 root  tty       7,  67 Mar  8 05:53 vcsu3
crw-rw----  1 root  tty       7,  68 Mar  8 05:53 vcsu4
crw-rw----  1 root  tty       7,  69 Mar  8 05:53 vcsu5
crw-rw----  1 root  tty       7,  70 Mar  8 05:53 vcsu6
drwxr-xr-x  2 root  root          60 Mar  8 05:53 vfio
crw-------  1 root  root     10, 127 Mar  8 05:53 vga_arbiter
crw-------  1 root  root     10, 137 Mar  8 05:53 vhci
crw-rw----  1 root  kvm      10, 238 Mar  8 05:53 vhost-net
crw-rw----  1 root  kvm      10, 241 Mar  8 05:53 vhost-vsock
crw-rw-rw-  1 root  root      1,   5 Mar  8 05:53 zero
crw-------  1 root  root     10, 249 Mar  8 05:53 zfs
pluto@Ubuntu-Server-Lab:/dev$
```

4. Telusuri direktory /proc. Tampilkan isi file interrupts, devices, cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda melihat mengapa direktory /proc disebut pseudo-filesystem yang memungkinkan akses ke struktur data kernel?
**interrupts**
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /proc
pluto@Ubuntu-Server-Lab:/proc$ cat interrupts
           CPU0       CPU1       CPU2
  0:        122          0          0   IO-APIC   2-edge      timer
  1:         55          0          0   IO-APIC   1-edge      i8042
  8:          0          0          0   IO-APIC   8-edge      rtc0
  9:          0          0          0   IO-APIC   9-fasteoi   acpi
 12:          0          0        158   IO-APIC  12-edge      i8042
 14:          0          0       9154   IO-APIC  14-edge      ata_piix
 15:          0          0          0   IO-APIC  15-edge      ata_piix
 18:          0          0          0   IO-APIC  18-fasteoi   vmwgfx
 19:          0      48802          0   IO-APIC  19-fasteoi   ehci_hcd:usb2, enp0s3
 20:          0          0          0   IO-APIC  20-fasteoi   vboxguest
 21:      10072          0          0   IO-APIC  21-fasteoi   ahci[0000:00:0d.0], snd_intel8x0
 22:          0         25          0   IO-APIC  22-fasteoi   ohci_hcd:usb1
NMI:          0          0          0   Non-maskable interrupts
LOC:    1085074      60436      62916   Local timer interrupts
SPU:          0          0          0   Spurious interrupts
PMI:          0          0          0   Performance monitoring interrupts
IWI:          5         29        350   IRQ work interrupts
RTR:          0          0          0   APIC ICR read retries
RES:        537       1618       2555   Rescheduling interrupts
CAL:      13116      27022      33834   Function call interrupts
TLB:        108         72         62   TLB shootdowns
TRM:          0          0          0   Thermal event interrupts
THR:          0          0          0   Threshold APIC interrupts
DFR:          0          0          0   Deferred Error APIC interrupts
MCE:          0          0          0   Machine check exceptions
MCP:         32         32         32   Machine check polls
ERR:          0
MIS:         55
PIN:          0          0          0   Posted-interrupt notification event
NPI:          0          0          0   Nested posted-interrupt event
PIW:          0          0          0   Posted-interrupt wakeup event
```

**devices**
```markdown
pluto@Ubuntu-Server-Lab:/proc$ cat devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  5 ttyprintk
  7 vcs
 10 misc
 13 input
 21 sg
 29 fb
 89 i2c
108 ppp
116 alsa
128 ptm
136 pts
180 usb
189 usb_device
202 cpu/msr
204 ttyMAX
226 drm
241 hidraw
242 ttyDBC
243 bsg
244 watchdog
245 remoteproc
246 ptp
247 pps
248 rtc
249 dma_heap
250 dax
251 dimmctl
252 ndctl
253 tpm
254 gpiochip
261 accel

Block devices:
  7 loop
  8 sd
  9 md
 11 sr
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
252 device-mapper
253 virtblk
254 mdp
259 blkext
```

**cpuinfo**
```markdown
pluto@Ubuntu-Server-Lab:/proc$ cat cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family     : 6
model   : 186
model name     : 13th Gen Intel(R) Core(TM) i5-1334U
stepping : 3
microcode : 0xffffffff
cpu MHz  : 2496.010
cache size     : 12288 KB
physical id    : 0
siblings : 3
core id  : 0
cpu cores : 3
apicid  : 0
initial apicid : 0
fpu  : yes
fpu_exception  : yes
cpuid level    : 22
wp   : yes
flags   : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs   : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi its
bogomips : 4992.02
clflush size   : 64
cache_alignment : 64
address sizes  : 39 bits physical, 48 bits virtual
power management:

processor : 1
vendor_id : GenuineIntel
cpu family     : 6
model   : 186
model name     : 13th Gen Intel(R) Core(TM) i5-1334U
stepping : 3
microcode : 0xffffffff
cpu MHz  : 2496.010
cache size     : 12288 KB
physical id    : 0
siblings : 3
core id  : 1
cpu cores : 3
apicid  : 1
initial apicid : 1
fpu  : yes
fpu_exception  : yes
cpuid level    : 22
wp   : yes
flags   : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs   : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi its
bogomips : 4992.02
clflush size   : 64
cache_alignment : 64
address sizes  : 39 bits physical, 48 bits virtual
power management:

processor : 2
vendor_id : GenuineIntel
cpu family     : 6
model   : 186
model name     : 13th Gen Intel(R) Core(TM) i5-1334U
stepping : 3
microcode : 0xffffffff
cpu MHz  : 2496.010
cache size     : 12288 KB
physical id    : 0
siblings : 3
core id  : 2
cpu cores : 3
apicid  : 2
initial apicid : 2
fpu  : yes
fpu_exception  : yes
cpuid level    : 22
wp   : yes
flags   : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs   : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi its
bogomips : 4992.02
clflush size   : 64
cache_alignment : 64
address sizes  : 39 bits physical, 48 bits virtual
power management:
```

**meminfo**
```markdown
pluto@Ubuntu-Server-Lab:/proc$ cat meminfo
MemTotal:        3043724 kB
MemFree:         2467560 kB
MemAvailable:    2684316 kB
Buffers:           26592 kB
Cached:           324048 kB
SwapCached:            0 kB
Active:           317776 kB
Inactive:          67752 kB
Active(anon):      44700 kB
Inactive(anon):        0 kB
Active(file):     273076 kB
Inactive(file):    67752 kB
Unevictable:       27316 kB
Mlocked:           27316 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Zswap:                 0 kB
Zswapped:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:         62240 kB
Mapped:            57492 kB
Shmem:              1060 kB
KReclaimable:      22896 kB
Slab:              71136 kB
SReclaimable:      22896 kB
SUnreclaim:        48240 kB
KernelStack:        2352 kB
PageTables:         2336 kB
SecPageTables:         0 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1521860 kB
Committed_AS:     289072 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       19132 kB
VmallocChunk:          0 kB
Percpu:             2048 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
FileHugePages:         0 kB
FilePmdMapped:         0 kB
Unaccepted:            0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:      112576 kB
DirectMap2M:     3033088 kB
```

**uptime**
```markdown
pluto@Ubuntu-Server-Lab:/proc$ cat uptime
10432.05 30727.01
```

- Tidak Menyimpan Data Secara Fisik<br>
File-file di /proc tidak benar-benar ada di disk, melainkan dibuat secara dinamis oleh kernel saat diakses<br>

Ukuran file biasanya menunjukkan 0 byte jika dilihat dengan ls -l, tetapi saat dibaca berisi data

- Antarmuka ke Kernel<br>
Setiap file mewakili informasi real-time tentang keadaan kernel dan sistem<br>

Saat Anda membaca /proc/cpuinfo, kernel secara langsung mengambil data dari struktur internalnya<br>

Contoh: /proc/meminfo mengambil data langsung dari manajemen memori kernel

- Komunikasi Dua Arah<br>
Beberapa file dapat ditulis untuk mengubah parameter kernel secara dinamis<br>

Contoh: echo 1 > /proc/sys/net/ipv4/ip_forward dapat mengubah setting kernel tanpa reboot

- Data Real-time<br>
Informasi selalu up-to-date karena diambil langsung dari kernel saat file dibaca<br>

Tidak ada "file" fisik yang perlu diperbarui secara berkala

5. Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.
```markdown
pluto@Ubuntu-Server-Lab:~/A$ cd ~pluto
pluto@Ubuntu-Server-Lab:~$
```

6. Ubah kembali ke direktory home Anda.
```markdown
pluto@Ubuntu-Server-Lab:~$ cd /home
pluto@Ubuntu-Server-Lab:/home$
```

7. Buat subdirektory work dan play.
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir work play
pluto@Ubuntu-Server-Lab:~$
```

8. Hapus subdirektory work.
```markdown
pluto@Ubuntu-Server-Lab:~$ rmdir work
pluto@Ubuntu-Server-Lab:~$
```

9. Copy file /etc/passwd ke direktory home Anda.
```markdown
pluto@Ubuntu-Server-Lab:~$ cp /etc/passwd /home/pluto/
pluto@Ubuntu-Server-Lab:~$
```

10. Pindahkan ke subdirectory play.
```markdown
pluto@Ubuntu-Server-Lab:~$ mv passwd play/
pluto@Ubuntu-Server-Lab:~$
```

11. Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang menunjuk ke perangkat tty. Apa yang terjadi jika melakukan hard link ke perangkat tty?
```markdown
pluto@Ubuntu-Server-Lab:~$ cd play
pluto@Ubuntu-Server-Lab:~/play$ ln -s /dev/tty terminal
pluto@Ubuntu-Server-Lab:~/play$ ls -l terminal
lrwxrwxrwx 1 pluto pluto 8 Mar  8 10:02 terminal -> /dev/tty
pluto@Ubuntu-Server-Lab:~/play$
```
Hard link tidak dapat dibuat ke device file karena hard link hanya bekerja pada filesystem yang sama dan untuk file regular

12. Buatlah file bernama hello.txt yang berisi kata "hello word". Dapatkah Anda gunakan "cp" menggunakan "terminal" sebagai file asal untuk menghasilkan efek yang sama?
```markdown
pluto@Ubuntu-Server-Lab:~/play$ echo "hello world" > hello.txt
pluto@Ubuntu-Server-Lab:~/play$ cat hello.txt
hello world
pluto@Ubuntu-Server-Lab:~/play$ cp terminal hello2.txt
hello world
pluto@Ubuntu-Server-Lab:~/play$ cat terminal hello2.txt
hello world
pluto@Ubuntu-Server-Lab:~/play$
```

13. Copy hello.txt ke terminal. Apa yang terjadi?
```markdown
pluto@Ubuntu-Server-Lab:~/play$ cp hello.txt terminal
hello world
pluto@Ubuntu-Server-Lab:~/play$
```

14. Masih di direktory home, copy keseluruhan direktory play ke direktory bernama work menggunakan symbolic link.
```markdown
pluto@Ubuntu-Server-Lab:~$ ln -s play work
pluto@Ubuntu-Server-Lab:~$ ls -l work
lrwxrwxrwx 1 pluto pluto 4 Mar  8 10:17 work -> play
pluto@Ubuntu-Server-Lab:~$ cp -r play/* work/
cp: 'play/hello2.txt' and 'work/hello2.txt' are the same file
cp: 'play/hello.txt' and 'work/hello.txt' are the same file
cp: 'play/passwd' and 'work/passwd' are the same file
cp: 'play/terminal' and 'work/terminal' are the same file
pluto@Ubuntu-Server-Lab:~$
```

15. Hapus direktory work dan isinya dengan satu perintah.
```markdown
pluto@Ubuntu-Server-Lab:~$ rm -rf work
pluto@Ubuntu-Server-Lab:~$
```

## Laporan Resmi
Analisa hasil percobaan yang Anda lakukan:
a. Analisa setiap hasil tampilannya.
b. Pada Percobaan 1 point 3 buatlah pohon dari struktur file dan direktori.
**Jawab**<br>
```markdown
home/
└── user/
    ├── A/
    │   ├── D/
    │   │   └── A/
    │   └── E/
    ├── B/
    │   └── F/
    └── C/
```
c. Bila terdapat pesan error, jelaskan penyebabnya.

Kerjakan latihan diatas dan analisa hasil tampilannya.

Berikan kesimpulan dari praktikum ini.
**Jawab**<br>
- Perintah navigasi: pwd (posisi saat ini), cd (pindah direktori), ls (melihat isi).

- Perintah manipulasi direktori: mkdir (membuat), rmdir (menghapus direktori kosong).

- Perintah manipulasi file: cp (mengkopi), mv (memindah/mengganti nama), rm (menghapus).

- Penggunaan opsi seperti -r (recursive), -i (interactive), -f (force) sangat penting dalam operasi file.

- Hard Link: Membuat nama file tambahan dengan inode yang sama. Jika file asli dihapus, data masih dapat diakses melalui hard link. Terbatas pada satu filesystem dan tidak bisa untuk direktori.

- Soft Link (Symbolic Link): Membuat shortcut yang menunjuk ke nama file. Jika file asli dihapus, link menjadi rusak (broken). Dapat melintasi filesystem dan bisa untuk direktori.

- Perbedaan utama terlihat dari jumlah link pada ls -l dan tipe file (l untuk symbolic link).

- find - Mencari file berdasarkan kriteria (nama, ukuran, waktu) secara real-time.

- locate - Mencari file cepat menggunakan database (diupdate secara periodik).

- which - Mengetahui lokasi executable program.

- grep - Mencari pattern/text di dalam file.


