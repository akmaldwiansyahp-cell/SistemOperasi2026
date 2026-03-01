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

<br>

Tulis script monitoring yang:
1. Mencatat penggunaan CPU dan memory setiap 5 detik
2. Menyimpan log dengan timestamp
3. Berjalan selama 1 menit (12 iterasi)
4. Output ditampilkan di terminal DAN disimpan ke file


- Script bash<br>
``#!/bin/bash<br>
<br>
LOG_FILE="monitor.log"<br>
INTERVAL=5<br>
ITERATIONS=12<br>
<br>
echo "Monitoring started at $(date)" | tee -a "$LOG_FILE"<br>
echo "----------------------------------------" | tee -a "$LOG_FILE"<br>
<br>
for ((i=1; i<=ITERATIONS; i++))<br>
do<br>
    TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")<br>
<br>
    # Ambil CPU usage (persen)<br>
    CPU_IDLE=$(top -bn1 | grep "Cpu(s)" | awk '{print $8}' | sed 's/id,//')<br>
    CPU_USAGE=$(awk "BEGIN {print 100 - $CPU_IDLE}")<br>
<br>
    # Ambil memory usage<br>
    MEM_USAGE=$(free -m | awk '/Mem:/ {printf "%.2f", $3/$2 * 100}')<br>
<br>
    OUTPUT="$TIMESTAMP | CPU: ${CPU_USAGE}% | MEM: ${MEM_USAGE}%"<br>
<br>
    # Tampilkan ke terminal dan simpan ke file<br>
    echo "$OUTPUT" | tee -a "$LOG_FILE"<br>
<br>
    sleep $INTERVAL<br>
done<br>
<br>
echo "----------------------------------------" | tee -a "$LOG_FILE"<br>
echo "Monitoring finished at $(date)" | tee -a "$LOG_FILE"``

- Menyimpan file<br>
<code>nano monitor.sh</code>
- Permission<br>
<code>chmod +x monitor.sh</code>
- Menjalankan<br>
<code>./monitor.sh</code>

>Monitoring started at Sun Mar  1 03:38:41 PM UTC 2026<br>
>----------------------------------------<br>
>2026-03-01 15:38:41 | CPU: 32.6% | MEM: 12.08%<br>
>2026-03-01 15:38:47 | CPU: 26.5% | MEM: 12.08%<br>
>2026-03-01 15:38:52 | CPU: 15.2% | MEM: 12.15%<br>
>2026-03-01 15:38:58 | CPU: 29% | MEM: 12.18%<br>
>2026-03-01 15:39:03 | CPU: 19.4% | MEM: 12.18%<br>
>2026-03-01 15:39:09 | CPU: 12.5% | MEM: 12.18%<br>
>2026-03-01 15:39:14 | CPU: 20.6% | MEM: 12.18%<br>
>2026-03-01 15:39:19 | CPU: 9.1% | MEM: 12.21%<br>
>2026-03-01 15:39:25 | CPU: 3.3% | MEM: 12.21%<br>
>2026-03-01 15:39:30 | CPU: 24.2% | MEM: 12.21%<br>
>2026-03-01 15:39:36 | CPU: 3.2% | MEM: 12.21%<br>
>2026-03-01 15:39:41 | CPU: 20.6% | MEM: 12.21%<br>
>----------------------------------------<br>
>Monitoring finished at Sun Mar  1 03:39:47 PM UTC 2026<br>