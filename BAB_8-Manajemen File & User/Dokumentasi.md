# Laporan Sistem Operasi Jobsheet 11

## Praktikum 9.1

1. Menyiapkan file uji permission

Kode Program:<br>
```markdown
mkdir ~/lab-permissions && cd ~/lab-permissions
echo "data rahasia" > secret.txt
echo '#!/bin/bash' > myscript.sh
echo 'echo Hello' >> myscript.sh
ls -la
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/praktikum-os/week11$ mkdir ~/lab-permissions && cd ~/lab-permissions
echo "data rahasia" > secret.txt
echo '#!/bin/bash' > myscript.sh
echo 'echo Hello' >> myscript.sh
ls -la
total 16
drwxrwxr-x  2 pluto pluto 4096 May 10 08:02 .
drwxr-x--- 21 pluto pluto 4096 May 10 08:02 ..
-rw-rw-r--  1 pluto pluto   23 May 10 08:02 myscript.sh
-rw-rw-r--  1 pluto pluto   13 May 10 08:02 secret.txt
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

2. Membuat file privat

Kode Program:<br>
```markdown
chmod 600 secret.txt
ls -l secret.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-permissions$ chmod 600 secret.txt
ls -l secret.txt
-rw------- 1 pluto pluto 13 May 10 08:02 secret.txt
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

3. Menjadikan skrip executable

Kode Program:<br>
```markdown
chmod 755 myscript.sh
ls -l myscript.sh
./myscript.sh
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-permissions$ chmod 755 myscript.sh
ls -l myscript.sh
./myscript.sh
-rwxr-xr-x 1 pluto pluto 23 May 10 08:02 myscript.sh
Hello
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

4. Direktori bersama dengan SGID

Kode Program:<br>
```markdown
mkdir shared-dir
chmod g+s shared-dir
ls -ld shared-dir
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-permissions$ mkdir shared-dir
chmod g+s shared-dir
ls -ld shared-dir
drwxrwsr-x 2 pluto pluto 4096 May 10 09:35 shared-dir
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

5. Mengamati efek umask

Kode Program:<br>
```markdown
umask
umask 027
touch testfile-027
ls -l testfile-027
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-permissions$ umask
umask 027
touch testfile-027
ls -l testfile-027
0002
-rw-r----- 1 pluto pluto 0 May 10 09:38 testfile-027
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

Analisis:<br>
1. Mengapa secret.txt tidak dapat dibaca oleh group dan others setelah chmod 600?
**Jawab**<br>
Karena permission 600 berarti rw------- — hanya owner yang memiliki hak baca (r) dan tulis (w), sementara group dan others tidak memiliki izin sama sekali (---).
2. Apa perbedaan arti 600 dan 755 terhadap file yang diuji?
**Jawab**<br>
600 = owner bisa baca/tulis, group/others tidak punya akses (cocok untuk file rahasia)<br>
755 = owner bisa baca/tulis/eksekusi, group/others hanya baca/eksekusi (cocok untuk program publik)
3. Setelah umask 027, permission apa yang dihasilkan untuk file baru, dan mengapa bukan 777?
**Jawab**<br>
File baru: 666 - 027 = 640 → rw-r-----<br>
Direktori baru: 777 - 027 = 750 → rwxr-x---

## Praktikum 9.2

1. Menyiapkan file uji ACL

Kode Program:<br>
```markdown
mkdir ~/lab-acl && cd ~/lab-acl
echo "Data petting" > confidential.txt
chmod 640 confidential.txt
ls -l confidential.txt
getfacl confidential.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ mkdir ~/lab-acl && cd ~/lab-acl
echo "Data petting" > confidential.txt
chmod 640 confidential.txt
ls -l confidential.txt
getfacl confidential.txt
mkdir: cannot create directory ‘/home/pluto/lab-acl’: File exists
-rw-r----- 1 pluto pluto 13 May 10 10:43 confidential.txt
# file: confidential.txt
# owner: pluto
# group: pluto
user::rw-
group::r--
other::---

pluto@Ubuntu-Server-Lab:~$
```

2. Menambahkan ACL untuk satu user

Kode Program:<br>
```markdown
setfacl -m u:userA:r confidential.txt
ls -l confidential.txt
getfacl confidential.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ setfacl -m u:userA:r confidential.txt
ls -l confidential.txt
getfacl confidential.txt
setfacl: Option -m: Invalid argument near character 3
-rw-r----- 1 pluto pluto 13 May 10 10:43 confidential.txt
# file: confidential.txt
# owner: pluto
# group: pluto
user::rw-
group::r--
other::---

pluto@Ubuntu-Server-Lab:~$
```

3. Default ACL pada direktori

Kode Program:<br>
```markdown
mkdir shared
setfacl -d -m u:userA:rwx shared
setfacl -d -m u:userB:r-x shared
getfacl shared

touch shared/inherited.txt
getfacl shared/inherited.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-acl$ mkdir shared
setfacl -d -m u:userA:rwx shared
setfacl -d -m u:userB:r-x shared
getfacl shared

touch shared/inherited.txt
getfacl shared/inherited.txt
setfacl: Option -m: Invalid argument near character 3
setfacl: Option -m: Invalid argument near character 3
# file: shared
# owner: pluto
# group: pluto
user::rwx
group::rwx
other::r-x

# file: shared/inherited.txt
# owner: pluto
# group: pluto
user::rw-
group::rw-
other::r--

pluto@Ubuntu-Server-Lab:~/lab-acl$
```

