# Laporan Sistem Operasi Jobsheet 3


## Latihan 3.1
Buatlah script yang:
1. Menampilkan daftar 10 file terbesar di direktori /var/log/
2. Menyimpan hasilnya ke file large-logs.txt
3. Menampilkan output juga di terminal menggunakan tee
4. Menangani error dengan redirect ke error.log<br>

Kode Program:<br>
```markdown
du -ah /var/log/ 2>error.log | sort -rh | head -n 10 | tee large-logs.txt
```

Hasil:<br>
```markdown
377M    /var/log/
371M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd
371M    /var/log/journal
8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064b10c775b794-f8d27a92954eff8a.journal~
8.1M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064a96da88229b-50504b18faa49ac7.journal~
8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000.journal
8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/user-1000@00064bf6438710d8-314ec7febc7551b8.journal~
8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system.journal
8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf642e801bb-fe79b3cba04be1b0.journal~
8.0M    /var/log/journal/df3c006b6b1b4d1eb2679c433b998cbd/system@00064bf1052d2981-a8f8066f50e2cf99.journal~
```

<br>

## Latihan 3.2
Buat pipeline yang:
1. Membaca /etc/passwd
2. Mengekstrak username (kolom pertama)
3. Mengurutkan alfabetis
4. Menyimpan ke file sorted-users.txt
Hint: Gunakan cut, sort, dan operator redirect.<br>

Kode Program:<br>
```markdown
cut -d: -f1 /etc/passwd | sort > sorted-users.txt
```

Hasil:<br>
```markdown
_apt
backup
bin
daemon
dhcpcd
fwupd-refresh
games
irc
landscape
list
lp
mail
man
messagebus
news
nobody
pluto
polkitd
pollinate
proxy
root
sshd
sync
sys
syslog
systemd-network
systemd-resolve
systemd-timesync
tcpdump
tss
usbmux
uucp
uuidd
www-data
```

<br>

## Latihan 3.3
Tulis script monitoring yang:
1. Mencatat penggunaan CPU dan memory setiap 5 detik
2. Menyimpan log dengan timestamp
3. Berjalan selama 1 menit (12 iterasi)
4. Output ditampilkan di terminal DAN disimpan ke file<br>

Kode Program:<br>

- Script bash<br>

```markdown
#!/bin/bash
LOG_FILE="monitor.log"
INTERVAL=5
ITERATIONS=12

echo "Monitoring started at $(date)" | tee -a "$LOG_FILE"
echo "----------------------------------------" | tee -a "$LOG_FILE"

for ((i=1; i<=ITERATIONS; i++))
do
    TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")

    CPU_IDLE=$(top -bn1 | grep "Cpu(s)" | awk '{print $8}' | sed 's/id,//')
    CPU_USAGE=$(awk "BEGIN {print 100 - $CPU_IDLE}")

    MEM_USAGE=$(free -m | awk '/Mem:/ {printf "%.2f", $3/$2 * 100}')

    OUTPUT="$TIMESTAMP | CPU: ${CPU_USAGE}% | MEM: ${MEM_USAGE}%"

    echo "$OUTPUT" | tee -a "$LOG_FILE"

    sleep $INTERVAL
done

echo "----------------------------------------" | tee -a "$LOG_FILE"
echo "Monitoring finished at $(date)" | tee -a "$LOG_FILE"
```

<br>

- Menyimpan file<br>
```markdown
nano monitor.sh
```
- Permission<br>
```markdown
chmod +x monitor.sh
```
- Menjalankan<br>
```markdown
./monitor.sh
```

Hasil:<br>
```markdown
Monitoring started at Sun Mar  1 03:38:41 PM UTC 2026
----------------------------------------
2026-03-01 15:38:41 | CPU: 32.6% | MEM: 12.08%
2026-03-01 15:38:47 | CPU: 26.5% | MEM: 12.08%
2026-03-01 15:38:52 | CPU: 15.2% | MEM: 12.15%
2026-03-01 15:38:58 | CPU: 29% | MEM: 12.18%
2026-03-01 15:39:03 | CPU: 19.4% | MEM: 12.18%
2026-03-01 15:39:09 | CPU: 12.5% | MEM: 12.18%
2026-03-01 15:39:14 | CPU: 20.6% | MEM: 12.18%
2026-03-01 15:39:19 | CPU: 9.1% | MEM: 12.21%
2026-03-01 15:39:25 | CPU: 3.3% | MEM: 12.21%
2026-03-01 15:39:30 | CPU: 24.2% | MEM: 12.21%
2026-03-01 15:39:36 | CPU: 3.2% | MEM: 12.21%
2026-03-01 15:39:41 | CPU: 20.6% | MEM: 12.21%
----------------------------------------
Monitoring finished at Sun Mar  1 03:39:47 PM UTC 2026
```

<br>

## Latihan 3.4
Buat perintah yang:
1. Mencari semua file .conf di sistem
2. Membuang pesan "Permission denied"
3. Menghitung jumlah file yang ditemukan
4. Menyimpan daftar path lengkap ke file<br>

Kode Program:<br>
```markdown
find / -type f -name "*.conf" 2>/dev/null | tee daftar_conf.txt | wc -l
```

Hasil:<br>
```markdown
402
```

<br>

## Latihan 3.5
Implementasikan script backup yang:
1. Menggunakan tar untuk backup direktori
2. Menampilkan progress dengan tee
3. Mencatat stdout ke backup-success.log
4. Mencatat stderr ke backup-error.log
5. Menambahkan timestamp di setiap log entry<br>

Kode Program:<br>
- Buat file<br>
```markdown
nano backup.sh
```

<br>

- Script<br>
```markdown
#!/bin/bash

SOURCE_DIR="/etc"          # contoh direktori yang mau dibackup
BACKUP_DIR="/backup"       # contoh direktori penyimpanan backup

TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
BACKUP_FILE="$BACKUP_DIR/backup-$TIMESTAMP.tar.gz"

SUCCESS_LOG="$BACKUP_DIR/backup-success.log"
ERROR_LOG="$BACKUP_DIR/backup-error.log"

log_with_timestamp() {
    while IFS= read -r line; do
        echo "$(date '+%Y-%m-%d %H:%M:%S') - $line"
    done
}

if [ ! -d "$SOURCE_DIR" ]; then
    echo "$(date '+%Y-%m-%d %H:%M:%S') - ERROR: Direktori sumber tidak ditemukan: $SOURCE_DIR"
    exit 1
fi

mkdir -p "$BACKUP_DIR"

echo "$(date '+%Y-%m-%d %H:%M:%S') - Memulai backup $SOURCE_DIR"

tar -czvf "$BACKUP_FILE" "$SOURCE_DIR" \
    > >(log_with_timestamp | tee -a "$SUCCESS_LOG") \
    2> >(log_with_timestamp | tee -a "$ERROR_LOG" >&2)

if [ $? -eq 0 ]; then
    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup BERHASIL: $BACKUP_FILE" | tee -a "$SUCCESS_LOG"
else
    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup GAGAL!" | tee -a "$ERROR_LOG" >&2
    exit 1
fi
```

<br>

- Permission<br>
<code>chmod +x backup.sh</code>
- Menjalankan<br>
<code>sudo ./backup.sh</code><br>

Hasil:<br>
```markdown
2026-03-01 17:30:14 - Memulai backup /etc
2026-03-01 17:30:14 - /etc/
2026-03-01 17:30:14 - tar: Removing leading `/' from member names
2026-03-01 17:30:14 - /etc/rsyslog.conf
2026-03-01 17:30:14 - /etc/papersize
2026-03-01 17:30:14 - /etc/os-release
2026-03-01 17:30:14 - /etc/resolv.conf
2026-03-01 17:30:14 - /etc/pam.conf
2026-03-01 17:30:14 - /etc/hosts.deny
2026-03-01 17:30:14 - /etc/sysctl.d/
2026-03-01 17:30:14 - /etc/sysctl.d/10-zeropage.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-magic-sysrq.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-ipv6-privacy.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-ptrace.conf
2026-03-01 17:30:14 - /etc/sysctl.d/README.sysctl
2026-03-01 17:30:14 - /etc/sysctl.d/10-console-messages.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-kernel-hardening.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-map-count.conf
2026-03-01 17:30:14 - /etc/sysctl.d/99-sysctl.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-network-security.conf
2026-03-01 17:30:14 - /etc/sysctl.d/10-bufferbloat.conf
2026-03-01 17:30:14 - /etc/ghostscript/
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan2.conf
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-gb1.conf
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-korea1.conf
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-cns1.conf
2026-03-01 17:30:14 - /etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan1.conf
2026-03-01 17:30:14 - /etc/ghostscript/fontmap.d/
2026-03-01 17:30:14 - /etc/ghostscript/fontmap.d/10fonts-urw-base35.conf
2026-03-01 17:30:14 - /etc/needrestart/
2026-03-01 17:30:14 - /etc/needrestart/needrestart.conf
2026-03-01 17:30:14 - /etc/needrestart/notify.conf
2026-03-01 17:30:14 - /etc/needrestart/hook.d/
2026-03-01 17:30:14 - /etc/needrestart/hook.d/90-none
2026-03-01 17:30:14 - /etc/needrestart/hook.d/20-rpm
2026-03-01 17:30:14 - /etc/needrestart/hook.d/10-dpkg
2026-03-01 17:30:14 - /etc/needrestart/notify.d/
2026-03-01 17:30:14 - /etc/needrestart/notify.d/400-notify-send
2026-03-01 17:30:14 - /etc/needrestart/notify.d/600-mail
2026-03-01 17:30:14 - /etc/needrestart/notify.d/200-write
2026-03-01 17:30:14 - /etc/needrestart/notify.d/README.needrestart
2026-03-01 17:30:14 - /etc/needrestart/iucode.sh
2026-03-01 17:30:14 - /etc/needrestart/restart.d/
2026-03-01 17:30:14 - /etc/needrestart/restart.d/sysv-init
2026-03-01 17:30:14 - /etc/needrestart/restart.d/README.needrestart
2026-03-01 17:30:14 - /etc/needrestart/restart.d/systemd-manager
2026-03-01 17:30:14 - /etc/needrestart/restart.d/dbus.service
2026-03-01 17:30:14 - /etc/needrestart/conf.d/
2026-03-01 17:30:14 - /etc/needrestart/conf.d/README.needrestart
2026-03-01 17:30:14 - /etc/crontab
2026-03-01 17:30:14 - /etc/networks
2026-03-01 17:30:14 - /etc/debian_version
2026-03-01 17:30:14 - /etc/sudo.conf
2026-03-01 17:30:14 - /etc/lsb-release
2026-03-01 17:30:14 - /etc/hdparm.conf
2026-03-01 17:30:14 - /etc/iproute2/
2026-03-01 17:30:14 - /etc/iproute2/ematch_map
2026-03-01 17:30:14 - /etc/iproute2/rt_realms
2026-03-01 17:30:14 - /etc/iproute2/group
2026-03-01 17:30:14 - /etc/iproute2/bpf_pinning
2026-03-01 17:30:14 - /etc/iproute2/rt_tables.d/
2026-03-01 17:30:14 - /etc/iproute2/rt_tables.d/README
2026-03-01 17:30:14 - /etc/iproute2/rt_scopes
2026-03-01 17:30:15 - /etc/iproute2/rt_protos
2026-03-01 17:30:15 - /etc/iproute2/rt_tables
2026-03-01 17:30:15 - /etc/iproute2/nl_protos
2026-03-01 17:30:15 - /etc/iproute2/rt_dsfield
2026-03-01 17:30:15 - /etc/iproute2/rt_protos.d/
2026-03-01 17:30:15 - /etc/iproute2/rt_protos.d/README
2026-03-01 17:30:15 - /etc/update-motd.d/
2026-03-01 17:30:15 - /etc/update-motd.d/97-overlayroot
2026-03-01 17:30:15 - /etc/update-motd.d/90-updates-available
2026-03-01 17:30:15 - /etc/update-motd.d/91-contract-ua-esm-status
2026-03-01 17:30:15 - /etc/update-motd.d/50-motd-news
2026-03-01 17:30:15 - /etc/update-motd.d/10-help-text
2026-03-01 17:30:15 - /etc/update-motd.d/98-reboot-required
2026-03-01 17:30:15 - /etc/update-motd.d/95-hwe-eol
2026-03-01 17:30:15 - /etc/update-motd.d/00-header
2026-03-01 17:30:15 - /etc/update-motd.d/92-unattended-upgrades
2026-03-01 17:30:15 - /etc/update-motd.d/85-fwupd
2026-03-01 17:30:15 - /etc/update-motd.d/50-landscape-sysinfo
2026-03-01 17:30:15 - /etc/update-motd.d/98-fsck-at-reboot
2026-03-01 17:30:15 - /etc/update-motd.d/91-release-upgrade
2026-03-01 17:30:15 - /etc/credstore.encrypted/
2026-03-01 17:30:15 - /etc/cryptsetup-initramfs/
2026-03-01 17:30:15 - /etc/cryptsetup-initramfs/conf-hook
2026-03-01 17:30:15 - /etc/wgetrc
2026-03-01 17:30:15 - /etc/initramfs-tools/
2026-03-01 17:30:15 - /etc/initramfs-tools/update-initramfs.conf
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-bottom/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-premount/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-top/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-top/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/panic/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/init-bottom/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-premount/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-top/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/local-bottom/
2026-03-01 17:30:15 - /etc/initramfs-tools/scripts/nfs-premount/
2026-03-01 17:30:15 - /etc/initramfs-tools/initramfs.conf
2026-03-01 17:30:15 - /etc/initramfs-tools/modules
2026-03-01 17:30:15 - /etc/initramfs-tools/conf.d/
2026-03-01 17:30:15 - /etc/initramfs-tools/hooks/
2026-03-01 17:30:15 - /etc/xattr.conf
2026-03-01 17:30:15 - /etc/grub.d/
2026-03-01 17:30:15 - /etc/grub.d/10_linux
2026-03-01 17:30:15 - /etc/grub.d/35_fwupd
2026-03-01 17:30:15 - /etc/grub.d/00_header
2026-03-01 17:30:15 - /etc/grub.d/20_linux_xen
2026-03-01 17:30:15 - Backup BERHASIL: /backup/backup-2026-03-01_17-30-14.tar.gz<
```