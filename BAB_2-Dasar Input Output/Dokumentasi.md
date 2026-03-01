# Laporan Sistem Operasi Jobsheet 3


Latihan 3.1
Buatlah script yang:
1. Menampilkan daftar 10 file terbesar di direktori /var/log/
2. Menyimpan hasilnya ke file large-logs.txt
3. Menampilkan output juga di terminal menggunakan tee
4. Menangani error dengan redirect ke error.log<br>

Kode Program:<br>
<code> du -ah /var/log/ 2>error.log | sort -rh | head -n 10 | tee large-logs.txt </code><br>

Hasil:<br>
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
Hint: Gunakan cut, sort, dan operator redirect.<br>

Kode Program:<br>
<code>cut -d: -f1 /etc/passwd | sort > sorted-users.txt</code><br>

Hasil:<br>
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
4. Output ditampilkan di terminal DAN disimpan ke file<br>

Kode Program:<br>
- Script bash<br>

>#!/bin/bash<br>
>
>LOG_FILE="monitor.log"<br>
>INTERVAL=5<br>
>ITERATIONS=12<br>
><br>
>echo "Monitoring started at $(date)" | tee -a "$LOG_FILE"<br>
>echo "----------------------------------------" | tee -a "$LOG_FILE"<br>
><br>
>for ((i=1; i<=ITERATIONS; i++))<br>
>do<br>
>    TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")<br>
><br>
>    CPU_IDLE=$(top -bn1 | grep "Cpu(s)" | awk '{print $8}' | sed 's/id,//')<br>
>    CPU_USAGE=$(awk "BEGIN {print 100 - $CPU_IDLE}")<br>
><br>
>    MEM_USAGE=$(free -m | awk '/Mem:/ {printf "%.2f", $3/$2 * 100}')<br>
><br>
>    OUTPUT="$TIMESTAMP | CPU: ${CPU_USAGE}% | MEM: ${MEM_USAGE}%"<br>
><br>
>    echo "$OUTPUT" | tee -a "$LOG_FILE"<br>
><br>
>    sleep $INTERVAL<br>
>done<br>
><br>
>echo "----------------------------------------" | tee -a "$LOG_FILE"<br>
>echo "Monitoring finished at $(date)" | tee -a "$LOG_FILE"

<br>

- Menyimpan file<br>
<code>nano monitor.sh</code>
- Permission<br>
<code>chmod +x monitor.sh</code>
- Menjalankan<br>
<code>./monitor.sh</code><br>

Hasil:<br>
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

<br>

Buat perintah yang:
1. Mencari semua file .conf di sistem
2. Membuang pesan "Permission denied"
3. Menghitung jumlah file yang ditemukan
4. Menyimpan daftar path lengkap ke file<br>

Kode Program:<br>
<code>find / -type f -name "*.conf" 2>/dev/null | tee daftar_conf.txt | wc -l</code><br>

Hasil:<br>
>402

<br>

Implementasikan script backup yang:
1. Menggunakan tar untuk backup direktori
2. Menampilkan progress dengan tee
3. Mencatat stdout ke backup-success.log
4. Mencatat stderr ke backup-error.log
5. Menambahkan timestamp di setiap log entry<br>

Kode Program:<br>
- Buat file<br>
<code>nano backup.sh</code>

<br>

- Script<br>
>#!/bin/bash
>
>SOURCE_DIR="/etc"          # contoh direktori yang mau dibackup
>BACKUP_DIR="/backup"       # contoh direktori penyimpanan backup
>
>TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
>BACKUP_FILE="$BACKUP_DIR/backup-$TIMESTAMP.tar.gz"
>
>SUCCESS_LOG="$BACKUP_DIR/backup-success.log"
>ERROR_LOG="$BACKUP_DIR/backup-error.log"
>
>log_with_timestamp() {
>    while IFS= read -r line; do
>        echo "$(date '+%Y-%m-%d %H:%M:%S') - $line"
>    done
>}
>
>if [ ! -d "$SOURCE_DIR" ]; then
>    echo "$(date '+%Y-%m-%d %H:%M:%S') - ERROR: Direktori sumber tidak ditemukan: $SOURCE_DIR"
>    exit 1
>fi
>
>mkdir -p "$BACKUP_DIR"
>
>echo "$(date '+%Y-%m-%d %H:%M:%S') - Memulai backup $SOURCE_DIR"
>
>tar -czvf "$BACKUP_FILE" "$SOURCE_DIR" \
>    > >(log_with_timestamp | tee -a "$SUCCESS_LOG") \
>    2> >(log_with_timestamp | tee -a "$ERROR_LOG" >&2)
>
>if [ $? -eq 0 ]; then
>    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup BERHASIL: $BACKUP_FILE" | tee -a "$SUCCESS_LOG"
>else
>    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup GAGAL!" | tee -a "$ERROR_LOG" >&2
>    exit 1
>fi

<br>

- Permission<br>
<code>chmod +x backup.sh</code>
- Menjalankan<br>
<code>sudo ./backup.sh</code><br>

Hasil:<br>
```markdown
2026-03-01 17:30:14 - Memulai backup /etc<br>
2026-03-01 17:30:14 - /etc/<br>
2026-03-01 17:30:14 - tar: Removing leading `/' from member names<br>
2026-03-01 17:30:14 - /etc/rsyslog.conf<br>
2026-03-01 17:30:14 - /etc/papersize<br>
2026-03-01 17:30:14 - /etc/os-release<br>
2026-03-01 17:30:14 - /etc/resolv.conf<br>
2026-03-01 17:30:14 - /etc/pam.conf<br>
2026-03-01 17:30:14 - /etc/hosts.deny<br>
2026-03-01 17:30:14 - /etc/sysctl.d/<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-zeropage.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-magic-sysrq.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-ipv6-privacy.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-ptrace.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/README.sysctl<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-console-messages.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-kernel-hardening.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-map-count.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/99-sysctl.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-network-security.conf<br>
2026-03-01 17:30:14 - /etc/sysctl.d/10-bufferbloat.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan2.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-gb1.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-korea1.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-cns1.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan1.conf<br>
2026-03-01 17:30:14 - /etc/ghostscript/fontmap.d/<br>
2026-03-01 17:30:14 - /etc/ghostscript/fontmap.d/10fonts-urw-base35.conf<br>
2026-03-01 17:30:14 - /etc/needrestart/<br>
2026-03-01 17:30:14 - /etc/needrestart/needrestart.conf<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.conf<br>
2026-03-01 17:30:14 - /etc/needrestart/hook.d/<br>
2026-03-01 17:30:14 - /etc/needrestart/hook.d/90-none<br>
2026-03-01 17:30:14 - /etc/needrestart/hook.d/20-rpm<br>
2026-03-01 17:30:14 - /etc/needrestart/hook.d/10-dpkg<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.d/<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.d/400-notify-send<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.d/600-mail<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.d/200-write<br>
2026-03-01 17:30:14 - /etc/needrestart/notify.d/README.needrestart<br>
2026-03-01 17:30:14 - /etc/needrestart/iucode.sh<br>
2026-03-01 17:30:14 - /etc/needrestart/restart.d/<br>
2026-03-01 17:30:14 - /etc/needrestart/restart.d/sysv-init<br>
2026-03-01 17:30:14 - /etc/needrestart/restart.d/README.needrestart<br>
2026-03-01 17:30:14 - /etc/needrestart/restart.d/systemd-manager<br>
2026-03-01 17:30:14 - /etc/needrestart/restart.d/dbus.service<br>
2026-03-01 17:30:14 - /etc/needrestart/conf.d/<br>
2026-03-01 17:30:14 - /etc/needrestart/conf.d/README.needrestart<br>
2026-03-01 17:30:14 - /etc/crontab<br>
2026-03-01 17:30:14 - /etc/networks<br>
2026-03-01 17:30:14 - /etc/debian_version<br>
2026-03-01 17:30:14 - /etc/sudo.conf<br>
2026-03-01 17:30:14 - /etc/lsb-release<br>
2026-03-01 17:30:14 - /etc/hdparm.conf<br>
2026-03-01 17:30:14 - /etc/iproute2/<br>
2026-03-01 17:30:14 - /etc/iproute2/ematch_map<br>
2026-03-01 17:30:14 - /etc/iproute2/rt_realms<br>
2026-03-01 17:30:14 - /etc/iproute2/group<br>
2026-03-01 17:30:14 - /etc/iproute2/bpf_pinning<br>
2026-03-01 17:30:14 - /etc/iproute2/rt_tables.d/<br>
2026-03-01 17:30:14 - /etc/iproute2/rt_tables.d/README<br>
2026-03-01 17:30:14 - /etc/iproute2/rt_scopes<br>
2026-03-01 17:30:15 - /etc/iproute2/rt_protos<br>
2026-03-01 17:30:15 - /etc/iproute2/rt_tables<br>
2026-03-01 17:30:15 - /etc/iproute2/nl_protos<br>
2026-03-01 17:30:15 - /etc/iproute2/rt_dsfield<br>
2026-03-01 17:30:15 - /etc/iproute2/rt_protos.d/<br>
2026-03-01 17:30:15 - /etc/iproute2/rt_protos.d/README<br>
2026-03-01 17:30:15 - /etc/update-motd.d/<br>
2026-03-01 17:30:15 - /etc/update-motd.d/97-overlayroot<br>
2026-03-01 17:30:15 - /etc/update-motd.d/90-updates-available<br>
2026-03-01 17:30:15 - /etc/update-motd.d/91-contract-ua-esm-status<br>
2026-03-01 17:30:15 - /etc/update-motd.d/50-motd-news<br>
2026-03-01 17:30:15 - /etc/update-motd.d/10-help-text<br>
2026-03-01 17:30:15 - /etc/update-motd.d/98-reboot-required<br>
2026-03-01 17:30:15 - /etc/update-motd.d/95-hwe-eol<br>
2026-03-01 17:30:15 - /etc/update-motd.d/00-header<br>
2026-03-01 17:30:15 - /etc/update-motd.d/92-unattended-upgrades<br>
2026-03-01 17:30:15 - /etc/update-motd.d/85-fwupd<br>
2026-03-01 17:30:15 - /etc/update-motd.d/50-landscape-sysinfo<br>
2026-03-01 17:30:15 - /etc/update-motd.d/98-fsck-at-reboot<br>
2026-03-01 17:30:15 - /etc/update-motd.d/91-release-upgrade<br>
2026-03-01 17:30:15 - /etc/credstore.encrypted/<br>
2026-03-01 17:30:15 - /etc/cryptsetup-initramfs/<br>
2026-03-01 17:30:15 - /etc/cryptsetup-initramfs/conf-hook<br>
2026-03-01 17:30:15 - /etc/wgetrc<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/update-initramfs.conf<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-bottom/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-premount/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-top/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-top/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/panic/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-bottom/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-premount/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-top/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-bottom/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-premount/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/initramfs.conf<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/modules<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/conf.d/<br>
2026-03-01 17:30:15 - /etc/initramfs-tools/hooks/<br>
2026-03-01 17:30:15 - /etc/xattr.conf<br>
2026-03-01 17:30:15 - /etc/grub.d/<br>
2026-03-01 17:30:15 - /etc/grub.d/10_linux<br>
2026-03-01 17:30:15 - /etc/grub.d/35_fwupd<br>
2026-03-01 17:30:15 - /etc/grub.d/00_header<br>
2026-03-01 17:30:15 - /etc/grub.d/20_linux_xen<br>
2026-03-01 17:30:15 - Backup BERHASIL: /backup/backup-2026-03-01_17-30-14.tar.gz<br>
```