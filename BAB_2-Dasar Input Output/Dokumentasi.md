# Laporan Sistem Operasi Jobsheet 3

>
>Latihan 3.1
>Buatlah script yang:
>1. Menampilkan daftar 10 file terbesar di direktori /var/log/
>2. Menyimpan hasilnya ke file large-logs.txt
>3. Menampilkan output juga di terminal menggunakan tee
>4. Menangani error dengan redirect ke error.log
>

' du -ah /var/log/ 2>error.log | sort -rh | head -n 10 | tee large-logs.txt '

>
>377M    /var/log/
>371M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd
>371M    /var/log/journal
>8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064b10c775b794-f8d27a92954eff8a.journal~
>8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064a96da88229b-50504b18faa49ac7.journal~
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000.journal
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000@00064bf6438710d8-314ec7febc7551b8.journal~
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system.journal
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf642e801bb-fe79b3cba04be1b0.journal~
>8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf1052d2981-a8f8066f50e2cf99.journal~
>