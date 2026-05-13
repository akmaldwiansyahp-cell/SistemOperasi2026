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

Tantangan<br>
Ubah owner atau group salah satu file uji ke akun atau group lain yang tersedia di sistem, kemudian jelaskan
perubahan output ls -l sebelum dan sesudahnya.<br>

Kode Program:<br>
```markdown
sudo chown nobody:nogroup secret.txt
ls -l secret.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-permissions$ sudo chown nobody:nogroup secret.txt
ls -l secret.txt
-rw------- 1 nobody nogroup 13 May 10 08:02 secret.txt
pluto@Ubuntu-Server-Lab:~/lab-permissions$
```

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

Analisis<br>
1. Mengapa getfacl confidential.txt awalnya tidak menampilkan user tertentu?
**Jawab**<Br>
Karena belum ada ACL tambahan yang ditambahkan, hanya permission standar Unix
2. Setelah setfacl -m u:userA:r confidential.txt, apa perbedaan output ls -l dan getfacl?
**Jawab**<br>
- ls -l menampilkan tanda + pada akhir permission string
- getfacl menampilkan semua entri ACL termasuk named user
3. Mengapa file inherited.txt mewarisi ACL dari direktori shared?
Karena direktori shared memiliki default ACL (-d) yang diwariskan ke semua file dan subdirektori baru<br>

Tantangan<br>
Tambahkan satu ACL lagi agar group readonly-group hanya dapat membaca confidential.txt. Setelah itu, hapus ACL untuk userA dan verifikasi hasil akhirnya dengan getfacl.<br>

Kode Program:<br>
```markdown
setfacl -m g:readonly-group:r confidential.txt
getfacl confidential.txt

setfacl -x u:userA confidential.txt
getfacl confidential.txt
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~/lab-acl$ setfacl -m g:readonly-group:r confidential.txt
getfacl confidential.txt

setfacl -x u:userA confidential.txt
getfacl confidential.txt
setfacl: Option -m: Invalid argument near character 3
# file: confidential.txt
# owner: pluto
# group: pluto
user::rw-
group::r--
other::---

setfacl: Option -x: Invalid argument near character 3
# file: confidential.txt
# owner: pluto
# group: pluto
user::rw-
group::r--
other::---

pluto@Ubuntu-Server-Lab:~/lab-acl$
```

## Praktikum 9.3A

1. Membuat dan Mengelola User

Kode Program:<br>
# Buat dua user
```markdown
sudo useradd -m -s /bin/bash userA
sudo useradd -m -s /bin/bash userB
sudo passwd userA
sudo passwd userB

# Verifikasi
id userA
getent passwd userA

# Modifikasi shell userA
sudo usermod -s /bin/zsh userA
getent passwd userA

# Lock dan unlock userB
sudo usermod -L userB
sudo passwd -S userB
sudo usermod -U userB
sudo passwd -S userB
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ # Buat dua user
sudo useradd -m -s /bin/bash userA
sudo useradd -m -s /bin/bash userB
sudo passwd userA
sudo passwd userB

# Verifikasi
id userA
getent passwd userA

# Modifikasi shell userA
sudo usermod -s /bin/zsh userA
getent passwd userA

# Lock dan unlock userB
sudo usermod -L userB
sudo passwd -S userB
sudo usermod -U userB
sudo passwd -S userB
New password:
Retype new password:
passwd: password updated successfully
New password:
Retype new password:
passwd: password updated successfully
uid=1001(userA) gid=1001(userA) groups=1001(userA)
userA:x:1001:1001::/home/userA:/bin/bash
usermod: Warning: missing or non-executable shell '/bin/zsh'
userA:x:1001:1001::/home/userA:/bin/zsh
userB L 2026-05-13 0 99999 7 -1
userB P 2026-05-13 0 99999 7 -1
pluto@Ubuntu-Server-Lab:~$
```

Analisis:<br>
1. Apa perbedaan output id userA sebelum dan sesudah menambah group?
- id userA menampilkan UID, GID, dan semua group anggota

- Setelah ditambah group, output akan menampilkan group tambahan
2. Bagaimana status passwd -S userB berubah saat akun di-lock?
Menampilkan LK (locked) pada status password

## Praktikum 9.3B

1. Latihan group management

Kode Program:<br>
```markdown
# Buat group
sudo groupadd labgroup
sudo groupadd readonly-group

# Tambahkan user ke group
sudo usermod -aG labgroup,readonly-group userA
sudo usermod -aG readonly-group userB

# Verifikasi
id userA
id userB
getent group labgroup
getent group readonly-group
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ # Buat group
sudo groupadd labgroup
sudo groupadd readonly-group

# Tambahkan user ke group
sudo usermod -aG labgroup,readonly-group userA
sudo usermod -aG readonly-group userB

# Verifikasi
id userA
id userB
getent group labgroup
getent group readonly-group
uid=1001(userA) gid=1001(userA) groups=1001(userA),1003(labgroup),1004(readonly-group)
uid=1002(userB) gid=1002(userB) groups=1002(userB),1004(readonly-group)
labgroup:x:1003:userA
readonly-group:x:1004:userA,userB
pluto@Ubuntu-Server-Lab:~$
```

Analisis:<br>
1. Apa yang ditampilkan id userA vs groups userA?
- id userA menampilkan UID, GID, dan semua group lengkap dengan ID-nya

- groups userA hanya menampilkan nama-nama group
2. Mengapa -a pada usermod -aG penting?
-a (append) menambahkan group baru tanpa menghapus group lama. Tanpa -a, semua group supplementary akan diganti.


## Praktikum 9.3C

1. Latihan password policy

Kode Program:<br>
```markdown
# Set aging policy
sudo chage -M 60 -W 7 -m 1 userA
sudo chage -l userA

# Paksa ganti password
sudo chage -d 0 userA

# Lock/unlock userB
sudo passwd -l userB
sudo passwd -S userB
sudo passwd -u userB
sudo passwd -S userB
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ # Set aging policy
sudo chage -M 60 -W 7 -m 1 userA
sudo chage -l userA

# Paksa ganti password
sudo chage -d 0 userA

# Lock/unlock userB
sudo passwd -l userB
sudo passwd -S userB
sudo passwd -u userB
sudo passwd -S userB
Last password change                                    : May 13, 2026
Password expires                                        : Jul 12, 2026
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 1
Maximum number of days between password change          : 60
Number of days of warning before password expires       : 7
passwd: password changed.
userB L 2026-05-13 0 99999 7 -1
passwd: password changed.
userB P 2026-05-13 0 99999 7 -1
pluto@Ubuntu-Server-Lab:~$
```

Analisis:<br>
1. Apa arti nilai yang ditampilkan chage -l userA?
- Last password change : kapan terakhir ganti password

- Password expires : kapan password akan expired

- Minimum : hari minimal sebelum boleh ganti

- Maximum : hari maksimal password berlaku

- Warning : hari peringatan sebelum expired
2. Bagaimana cara membuktikan userB terkunci dari output passwd -S?
Output menampilkan status LK (locked)
3. Kapan sebaiknya menggunakan chage -d 0 vs passwd -e?
Keduanya sama-sama memaksa ganti password, passwd -e adalah alias dari chage -d 0<br>

Tantangan<br>
Buat user bernama intern yang:<br>
- memiliki shell /bin/bash;
- menjadi anggota labgroup;
- dipaksa ganti password pada login pertama;
- password expired setelah 45 hari dengan warning 7 hari sebelumnya.

Kode Program:<br>
```markdown
sudo useradd -m -s /bin/bash intern
sudo usermod -aG labgroup intern
sudo passwd intern
sudo chage -M 45 -W 7 -d 0 intern
sudo chage -l intern
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo useradd -m -s /bin/bash intern
sudo usermod -aG labgroup intern
sudo passwd intern
sudo chage -M 45 -W 7 -d 0 intern
sudo chage -l intern
New password:
Retype new password:
passwd: password updated successfully
Last password change                                    : password must be changed
Password expires                                        : password must be changed
Password inactive                                       : password must be changed
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 45
Number of days of warning before password expires       : 7
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 9.4

1. Membuat file sudoers terpisah

Kode Program:<br>
```markdown
sudo visudo -f /etc/sudoers.d/lab-userA
```

2. Isi konfigurasi sudo untuk userA

Kode Program:<br>
```markdown
userA ALL=(root) NOPASSWD: /usr/bin/apt update, /usr/bin/apt upgrade
userA ALL=(root) /bin/systemctl status *
```

3. Verifikasi hak sudo dan log

Kode Program:<br>
```markdown
sudo -l -U userA
sudo grep "userA" /var/log/auth.log | tail -10
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo -l -U userA
sudo grep "userA" /var/log/auth.log | tail -10
Matching Defaults entries for userA on Ubuntu-Server-Lab:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty

User userA may run the following commands on Ubuntu-Server-Lab:
    (root) NOPASSWD: /usr/bin/apt update, /usr/bin/apt upgrade
    (root) /bin/systemctl status *
grep: /var/log/auth.log: binary file matches
pluto@Ubuntu-Server-Lab:~$
```

Analisis<br>
1. Mengapa aturan disimpan di /etc/sudoers.d//, bukan langsung di /etc/sudoers?
- Agar lebih terorganisir dan tidak mengubah file utama /etc/sudoers yang bisa berisiko

- Memudahkan backup dan removal konfigurasi spesifik
2. Mana perintah yang bisa dijalankan tanpa password, dan mana yang masih perlu autentikasi?
- Tanpa password: apt update dan apt upgrade (ada NOPASSWD)

- Perlu autentikasi: systemctl status * (tanpa NOPASSWD)
3. Informasi apa saja yang dicatat di log sudo?
- User yang menjalankan

- Perintah yang dijalankan

- Working directory

- Status sukses/gagal

Tantangan<br>
Tambahkan satu aturan baru agar userA boleh menjalankan /bin/systemctl restart ssh tetapi tidak boleh
menjalankan reboot.<br>

Kode Program:<br>
```markdown
userA ALL=(root) /bin/systemctl restart ssh
# userA tidak boleh reboot (tidak ditambahkan aturan reboot)
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo -l -U userA
sudo grep "userA" /var/log/auth.log | tail -10
Matching Defaults entries for userA on Ubuntu-Server-Lab:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty

User userA may run the following commands on Ubuntu-Server-Lab:
    (root) NOPASSWD: /usr/bin/apt update, /usr/bin/apt upgrade
    (root) /bin/systemctl status *
    (root) /bin/systemctl restart ssh
grep: /var/log/auth.log: binary file matches
pluto@Ubuntu-Server-Lab:~$
```

## Praktikum 9.5

1. Menyiapkan filesystem uji quota

Kode Program:<br>
```markdown
sudo dd if=/dev/zero of=/tmp/quota-test.img bs=1M count=100
sudo mkfs.ext4 /tmp/quota-test.img
sudo mkdir -p /mnt/quota-test
sudo mount -o loop,usrquota,grpquota /tmp/quota-test.img /mnt/quota-test
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo dd if=/dev/zero of=/tmp/quota-test.img bs=1M count=100
sudo mkfs.ext4 /tmp/quota-test.img
sudo mkdir -p /mnt/quota-test
sudo mount -o loop,usrquota,grpquota /tmp/quota-test.img /mnt/quota-test
100+0 records in
100+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 0.661128 s, 159 MB/s
mke2fs 1.47.0 (5-Feb-2023)
Discarding device blocks: done
Creating filesystem with 25600 4k blocks and 25600 inodes

Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done

pluto@Ubuntu-Server-Lab:~$
```

2. Inisialisasi dan aktivasi quota

Kode Program:<br>
```markdown
sudo quotacheck -cug /mnt/quota-test
sudo quotaon -v /mnt/quota-test
sudo repquota /mnt/quota-test
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo quotacheck -cug /mnt/quota-test
sudo quotaon -v /mnt/quota-test
sudo repquota /mnt/quota-test
quotaon: Your kernel probably supports ext4 quota feature but you are using external quota files. Please switch your filesystem to use ext4 quota feature as external quota files on ext4 are deprecated.
/dev/loop0 [/mnt/quota-test]: group quotas turned on
/dev/loop0 [/mnt/quota-test]: user quotas turned on
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --      20       0       0              2     0     0


pluto@Ubuntu-Server-Lab:~$
```

3. Menetapkan quota untuk userA

Kode Program:<br>
```markdown
sudo edquota -u userA
# Set: soft block 5120, hard block 10240
sudo repquota /mnt/quota-test
```

4. Pembersihan quota test

Kode Program:<br>
```markdown
sudo quotaoff /mnt/quota-test
sudo umount /mnt/quota-test
sudo rm /tmp/quota-test.img
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo quotaoff /mnt/quota-test
sudo umount /mnt/quota-test
sudo rm /tmp/quota-test.img
pluto@Ubuntu-Server-Lab:~$ 
```

Analisis<br>
1. Apa perbedaan soft limit dan hard limit saat quota mulai terlampaui?
- Soft limit: Boleh dilampaui sementara (sesuai grace period)

- Hard limit: Batas mutlak yang tidak boleh dilampaui
2. Mengapa praktikum ini memakai loopback filesystem, bukan langsung /home/?
- Aman tanpa memodifikasi filesystem utama

- Tidak perlu repartisi disk

- Mudah dibersihkan setelah praktikum
3. Dari output repquota, informasi apa yang menunjukkan quota sudah aktif?
Menampilkan kolom used, soft, hard, grace untuk setiap user

Tantangan<br>
Coba atur quota baru untuk userA dengan batas inode yang sangat kecil, kemudian jelaskan kapan pembatasan
inode lebih penting daripada pembatasan block.<br>

Kode Program:<br>
```markdown
sudo setquota -u userA 5120 10240 5 10 /mnt/quota-test
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sudo setquota -u userA 5120 10240 5 10 /mnt/quota-test

```






