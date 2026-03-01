# Laporan Sistem Operasi Jobsheet 3


Latihan 3.1
Buatlah script yang:
1. Menampilkan daftar 10 file terbesar di direktori /var/log/
2. Menyimpan hasilnya ke file large-logs.txt
3. Menampilkan output juga di terminal menggunakan tee
4. Menangani error dengan redirect ke error.log

<code> du -ah /var/log/ 2>error.log | sort -rh | head -n 10 | tee large-logs.txt </code>


>377M    /var/log/<br>
>371M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd<br>
>371M    /var/log/journal<br>
>8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064b10c775b794-f8d27a92954eff8a.journal~<br>
>8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064a96da88229b-50504b18faa49ac7.journal~<br>
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000.journal<br>
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000@00064bf6438710d8-314ec7febc7551b8.journal~<br>
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system.journal<br>
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf642e801bb-fe79b3cba04be1b0.journal~<br>
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf1052d2981-a8f8066f50e2cf99.journal~<br>

<br>

Latihan 3.2
Buat pipeline yang:
1. Membaca /etc/passwd
2. Mengekstrak username (kolom pertama)
3. Mengurutkan alfabetis
4. Menyimpan ke file sorted-users.txt
Hint: Gunakan cut, sort, dan operator redirect.

<code>cut -d: -f1 /etc/passwd | sort > sorted-users.txt</code>

>_apt<br>
>backup<br>
>bin<br>
>daemon<br>
>dhcpcd<br>
>fwupd-refresh<br>
>games<br>
>irc<br>
>landscape<br>
>list<br>
>lp<br>
>mail<br>
>man<br>
>messagebus<br>
>news<br>
>nobody<br>
>pluto<br>
>polkitd<br>
>pollinate<br>
>proxy<br>
>root<br>
>sshd<br>
>sync<br>
>sys<br>
>syslog<br>
>systemd-network<br>
>systemd-resolve<br>
>systemd-timesync<br>
>tcpdump<br>
>tss<br>
>usbmux<br>
>uucp<br>
>uuidd<br>
>www-data<br>