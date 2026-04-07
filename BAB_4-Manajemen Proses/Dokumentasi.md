# Laporan Sistem Operasi Jobsheet 6

## Praktikum 6.1
1. Menampilkan semua proses

Kode Program:<br>
```markdown
ps aux
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  2.5  0.4  21952 13072 ?        Ss   15:04   0:02 /sbin/init splash noprompt noshell automatic-ubiquity
root           2  0.0  0.0      0     0 ?        S    15:04   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    15:04   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-rcu_g]
root           5  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-rcu_p]
root           6  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-slub_]
root           7  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-netns]
root           8  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/0:0-events]
root           9  0.5  0.0      0     0 ?        I    15:04   0:00 [kworker/0:1-events]
root          10  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/0:0H-events_highpri]
root          11  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u6:0-ipv6_addrconf]
root          12  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-mm_pe]
root          13  0.0  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_kthread]
root          14  0.0  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_rude_kthread]
root          15  0.0  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_trace_kthread]
root          16  0.1  0.0      0     0 ?        S    15:04   0:00 [ksoftirqd/0]
root          17  0.3  0.0      0     0 ?        I    15:04   0:00 [rcu_preempt]
root          18  0.0  0.0      0     0 ?        S    15:04   0:00 [migration/0]
root          19  0.0  0.0      0     0 ?        S    15:04   0:00 [idle_inject/0]
root          20  0.0  0.0      0     0 ?        S    15:04   0:00 [cpuhp/0]
root          21  0.0  0.0      0     0 ?        S    15:04   0:00 [cpuhp/1]
root          22  0.0  0.0      0     0 ?        S    15:04   0:00 [idle_inject/1]
root          23  0.4  0.0      0     0 ?        S    15:04   0:00 [migration/1]
root          24  0.0  0.0      0     0 ?        S    15:04   0:00 [ksoftirqd/1]
root          25  0.1  0.0      0     0 ?        I    15:04   0:00 [kworker/1:0-cgroup_destroy]
root          26  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/1:0H-kblockd]
root          27  0.0  0.0      0     0 ?        S    15:04   0:00 [cpuhp/2]
root          28  0.0  0.0      0     0 ?        S    15:04   0:00 [idle_inject/2]
root          29  0.5  0.0      0     0 ?        S    15:04   0:00 [migration/2]
root          30  0.1  0.0      0     0 ?        S    15:04   0:00 [ksoftirqd/2]
root          31  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/2:0-rcu_gp]
root          32  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/2:0H-kblockd]
root          33  1.4  0.0      0     0 ?        I    15:04   0:01 [kworker/u7:0-events_power_efficient]
root          34  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u8:0-events_power_efficient]
root          35  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:0-flush-8:0]
root          36  0.0  0.0      0     0 ?        S    15:04   0:00 [kdevtmpfs]
root          37  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-inet_]
root          38  0.0  0.0      0     0 ?        S    15:04   0:00 [kauditd]
root          39  0.0  0.0      0     0 ?        S    15:04   0:00 [khungtaskd]
root          40  0.0  0.0      0     0 ?        S    15:04   0:00 [oom_reaper]
root          41  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u7:1-events_unbound]
root          42  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u7:2-events_unbound]
root          43  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-write]
root          44  0.0  0.0      0     0 ?        S    15:04   0:00 [kcompactd0]
root          45  0.0  0.0      0     0 ?        SN   15:04   0:00 [ksmd]
root          46  0.0  0.0      0     0 ?        SN   15:04   0:00 [khugepaged]
root          47  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kinte]
root          48  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kbloc]
root          49  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-blkcg]
root          50  0.0  0.0      0     0 ?        S    15:04   0:00 [irq/9-acpi]
root          51  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-tpm_d]
root          52  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ata_s]
root          53  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-md]
root          54  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-md_bi]
root          55  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-edac-]
root          56  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-devfr]
root          57  0.0  0.0      0     0 ?        S    15:04   0:00 [watchdogd]
root          58  0.5  0.0      0     0 ?        I    15:04   0:00 [kworker/1:1-events]
root          59  0.1  0.0      0     0 ?        I<   15:04   0:00 [kworker/0:1H-kblockd]
root          60  0.0  0.0      0     0 ?        S    15:04   0:00 [kswapd0]
root          61  0.0  0.0      0     0 ?        S    15:04   0:00 [ecryptfs-kthread]
root          62  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kthro]
root          63  0.6  0.0      0     0 ?        I    15:04   0:00 [kworker/2:1-events]
root          64  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-acpi_]
root          65  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:1-events_unbound]
root          66  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:2-flush-8:0]
root          67  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u8:1-events_unbound]
root          68  0.0  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_0]
root          69  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root          70  0.0  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_1]
root          71  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root          72  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:3-events_power_efficient]
root          73  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:4]
root          74  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-mld]
root          75  0.5  0.0      0     0 ?        I    15:04   0:00 [kworker/2:2-events]
root          76  0.2  0.0      0     0 ?        I<   15:04   0:00 [kworker/2:1H-kblockd]
root          77  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ipv6_]
root          79  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u6:1-ext4-rsv-conversion]
root          80  0.4  0.0      0     0 ?        I<   15:04   0:00 [kworker/1:1H-kblockd]
root          86  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kstrp]
root          88  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/u10:0]
root          89  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/u11:0]
root          90  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/u12:0]
root          91  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/u13:0]
root          96  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-crypt]
root          97  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/0:2]
root          98  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/0:3-events]
root          99  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/1:2-events]
root         108  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-charg]
root         175  0.0  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_2]
root         176  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root         181  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/2:2H-kblockd]
root         190  0.0  0.0      0     0 ?        I    15:04   0:00 [kworker/u8:2-events_power_efficient]
root         213  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-raid5]
root         258  0.1  0.0      0     0 ?        S    15:04   0:00 [jbd2/sda2-8]
root         259  0.0  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ext4-]
root         324  0.8  0.5  50452 17276 ?        S<s  15:05   0:00 /usr/lib/systemd/systemd-journald
root         345  0.0  0.0      0     0 ?        I    15:05   0:00 [kworker/u7:3-writeback]
root         357  0.0  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-kmpat]
root         358  0.0  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-kmpat]
root         374  0.3  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         383  0.0  0.0      0     0 ?        I    15:05   0:00 [kworker/u8:3-events_power_efficient]
root         406  0.6  0.2  28684  7488 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-udevd
systemd+     428  0.3  0.4  21584 12980 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-resolved
systemd+     429  0.2  0.2  91028  7968 ?        Ssl  15:05   0:00 /usr/lib/systemd/systemd-timesyncd
root         438  0.0  0.0      0     0 ?        I    15:05   0:00 [kworker/1:3]
root         464  0.0  0.0      0     0 ?        S    15:05   0:00 [psimon]
systemd+     473  0.3  0.3  19012  9584 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-networkd
message+     606  0.3  0.1   9792  5432 ?        Ss   15:05   0:00 @dbus-daemon --system --address=systemd: --nofork --n
polkitd      611  0.2  0.2 308164  8072 ?        Ssl  15:05   0:00 /usr/lib/polkit-1/polkitd --no-debug
root         618  0.2  0.2  18128  8832 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-logind
root         619  0.4  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         658  0.6  0.4 392100 13064 ?        Ssl  15:05   0:00 /usr/sbin/ModemManager
syslog       665  0.3  0.1 222508  5964 ?        Ssl  15:05   0:00 /usr/sbin/rsyslogd -n -iNONE
root         666  0.0  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-cfg80]
root         667  0.0  0.0      0     0 ?        I    15:05   0:00 [kworker/2:3-mm_percpu_wq]
root         672  1.0  0.7 109640 23148 ?        Ssl  15:05   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unatt
root         703  0.0  0.0      0     0 ?        S    15:05   0:00 [irq/18-vmwgfx]
root         706  0.0  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-ttm]
root         716  0.0  0.0   6824  2904 ?        Ss   15:05   0:00 /usr/sbin/cron -f -P
root         750  0.1  0.1   6980  4896 tty1     Ss   15:05   0:00 /bin/login -p --
root         947  0.0  0.0      0     0 ?        S    15:05   0:00 [psimon]
pluto        949  0.1  0.3  20092 11304 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd --user
pluto        950  0.0  0.1  21156  3572 ?        S    15:05   0:00 (sd-pam)
pluto        958  0.0  0.1   8656  5652 tty1     S+   15:05   0:00 -bash
root        1004  0.0  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-tls-s]
root        1010  0.0  0.2  12024  8252 ?        Ss   15:05   0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startu
root        1012  0.0  0.3  14964 10640 ?        Ss   15:05   0:00 sshd: pluto [priv]
root        1014  0.0  0.0      0     0 ?        I<   15:06   0:00 [kworker/0:2H]
pluto       1062  0.2  0.2  15124  7136 ?        S    15:06   0:00 sshd: pluto@pts/0
pluto       1063  0.0  0.1   8648  5644 pts/0    Ss   15:06   0:00 -bash
pluto       1072 60.0  0.1  10884  4596 pts/0    R+   15:06   0:00 ps aux
```

2. Menampilkan proses dengan thread

Kode Program:<br>
```markdown
ps aux -L
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ps aux -L
USER         PID     LWP %CPU NLWP %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1       1  0.4    1  0.4  21952 13072 ?        Ss   15:04   0:03 /sbin/init splash noprompt noshell autom
root           2       2  0.0    1  0.0      0     0 ?        S    15:04   0:00 [kthreadd]
root           3       3  0.0    1  0.0      0     0 ?        S    15:04   0:00 [pool_workqueue_release]
root           4       4  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-rcu_g]
root           5       5  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-rcu_p]
root           6       6  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-slub_]
root           7       7  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-netns]
root           8       8  0.2    1  0.0      0     0 ?        I    15:04   0:01 [kworker/0:0-events]
root           9       9  0.1    1  0.0      0     0 ?        I    15:04   0:00 [kworker/0:1-mm_percpu_wq]
root          11      11  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u6:0-ipv6_addrconf]
root          12      12  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-mm_pe]
root          13      13  0.0    1  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_kthread]
root          14      14  0.0    1  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_rude_kthread]
root          15      15  0.0    1  0.0      0     0 ?        I    15:04   0:00 [rcu_tasks_trace_kthread]
root          16      16  0.0    1  0.0      0     0 ?        S    15:04   0:00 [ksoftirqd/0]
root          17      17  0.0    1  0.0      0     0 ?        I    15:04   0:00 [rcu_preempt]
root          18      18  0.0    1  0.0      0     0 ?        S    15:04   0:00 [migration/0]
root          19      19  0.0    1  0.0      0     0 ?        S    15:04   0:00 [idle_inject/0]
root          20      20  0.0    1  0.0      0     0 ?        S    15:04   0:00 [cpuhp/0]
root          21      21  0.0    1  0.0      0     0 ?        S    15:04   0:00 [cpuhp/1]
root          22      22  0.0    1  0.0      0     0 ?        S    15:04   0:00 [idle_inject/1]
root          23      23  0.0    1  0.0      0     0 ?        S    15:04   0:00 [migration/1]
root          24      24  0.0    1  0.0      0     0 ?        S    15:04   0:00 [ksoftirqd/1]
root          25      25  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/1:0-cgroup_destroy]
root          26      26  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/1:0H-kblockd]
root          27      27  0.0    1  0.0      0     0 ?        S    15:04   0:00 [cpuhp/2]
root          28      28  0.0    1  0.0      0     0 ?        S    15:04   0:00 [idle_inject/2]
root          29      29  0.0    1  0.0      0     0 ?        S    15:04   0:00 [migration/2]
root          30      30  0.0    1  0.0      0     0 ?        R    15:04   0:00 [ksoftirqd/2]
root          34      34  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u8:0-events_unbound]
root          35      35  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:0-events_unbound]
root          36      36  0.0    1  0.0      0     0 ?        S    15:04   0:00 [kdevtmpfs]
root          37      37  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-inet_]
root          38      38  0.0    1  0.0      0     0 ?        S    15:04   0:00 [kauditd]
root          39      39  0.0    1  0.0      0     0 ?        S    15:04   0:00 [khungtaskd]
root          40      40  0.0    1  0.0      0     0 ?        S    15:04   0:00 [oom_reaper]
root          41      41  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u7:1-events_unbound]
root          43      43  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-write]
root          44      44  0.0    1  0.0      0     0 ?        S    15:04   0:00 [kcompactd0]
root          45      45  0.0    1  0.0      0     0 ?        SN   15:04   0:00 [ksmd]
root          46      46  0.0    1  0.0      0     0 ?        SN   15:04   0:00 [khugepaged]
root          47      47  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kinte]
root          48      48  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kbloc]
root          49      49  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-blkcg]
root          50      50  0.0    1  0.0      0     0 ?        S    15:04   0:00 [irq/9-acpi]
root          51      51  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-tpm_d]
root          52      52  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ata_s]
root          53      53  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-md]
root          54      54  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-md_bi]
root          55      55  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-edac-]
root          56      56  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-devfr]
root          57      57  0.0    1  0.0      0     0 ?        S    15:04   0:00 [watchdogd]
root          58      58  0.9    1  0.0      0     0 ?        I    15:04   0:06 [kworker/1:1-events]
root          59      59  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/0:1H-kblockd]
root          60      60  0.0    1  0.0      0     0 ?        S    15:04   0:00 [kswapd0]
root          61      61  0.0    1  0.0      0     0 ?        S    15:04   0:00 [ecryptfs-kthread]
root          62      62  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kthro]
root          63      63  0.2    1  0.0      0     0 ?        I    15:04   0:01 [kworker/2:1-events]
root          64      64  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-acpi_]
root          65      65  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u9:1-flush-8:0]
root          68      68  0.0    1  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_0]
root          69      69  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root          70      70  0.0    1  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_1]
root          71      71  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root          74      74  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-mld]
root          75      75  0.3    1  0.0      0     0 ?        I    15:04   0:02 [kworker/2:2-events]
root          76      76  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/2:1H-kblockd]
root          77      77  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ipv6_]
root          79      79  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u6:1-ipv6_addrconf]
root          80      80  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/1:1H-kblockd]
root          86      86  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-kstrp]
root          88      88  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/u10:0]
root          89      89  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/u11:0]
root          90      90  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/u12:0]
root          91      91  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/u13:0]
root          96      96  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-crypt]
root         108     108  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-charg]
root         175     175  0.0    1  0.0      0     0 ?        S    15:04   0:00 [scsi_eh_2]
root         176     176  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-scsi_]
root         181     181  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/2:2H-kblockd]
root         190     190  0.0    1  0.0      0     0 ?        I    15:04   0:00 [kworker/u8:2-flush-8:0]
root         213     213  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-raid5]
root         258     258  0.0    1  0.0      0     0 ?        S    15:04   0:00 [jbd2/sda2-8]
root         259     259  0.0    1  0.0      0     0 ?        I<   15:04   0:00 [kworker/R-ext4-]
root         324     324  0.1    1  0.5  66844 17336 ?        S<s  15:05   0:00 /usr/lib/systemd/systemd-journald
root         345     345  0.0    1  0.0      0     0 ?        I    15:05   0:00 [kworker/u7:3-events_power_efficient]
root         357     357  0.0    1  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-kmpat]
root         358     358  0.0    1  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-kmpat]
root         374     374  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     385  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     388  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     389  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     390  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     393  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         374     394  0.0    7  0.8 288988 27324 ?        SLsl 15:05   0:00 /sbin/multipathd -d -s
root         383     383  0.0    1  0.0      0     0 ?        I    15:05   0:00 [kworker/u8:3-flush-8:0]
root         406     406  0.0    1  0.2  28684  7488 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-udevd
systemd+     428     428  0.0    1  0.4  21584 12980 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-resolved
systemd+     429     429  0.0    2  0.2  91028  7972 ?        Ssl  15:05   0:00 /usr/lib/systemd/systemd-timesyncd
systemd+     429     485  0.0    2  0.2  91028  7972 ?        Ssl  15:05   0:00 /usr/lib/systemd/systemd-timesyncd
root         464     464  0.0    1  0.0      0     0 ?        S    15:05   0:00 [psimon]
systemd+     473     473  0.0    1  0.3  19012  9584 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-networkd
message+     606     606  0.0    1  0.1   9792  5496 ?        Ss   15:05   0:00 @dbus-daemon --system --address=systemd:
polkitd      611     611  0.0    4  0.2 308164  8072 ?        Ssl  15:05   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      611     647  0.0    4  0.2 308164  8072 ?        Ssl  15:05   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      611     648  0.0    4  0.2 308164  8072 ?        Ssl  15:05   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      611     650  0.0    4  0.2 308164  8072 ?        Ssl  15:05   0:00 /usr/lib/polkit-1/polkitd --no-debug
root         618     618  0.0    1  0.2  18128  8924 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd-logind
root         619     619  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         619     634  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         619     635  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         619     642  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         619     669  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         619     689  0.0    6  0.4 468968 13548 ?        Ssl  15:05   0:00 /usr/libexec/udisks2/udisksd
root         658     658  0.0    4  0.4 392100 13068 ?        Ssl  15:05   0:00 /usr/sbin/ModemManager
root         658     674  0.0    4  0.4 392100 13068 ?        Ssl  15:05   0:00 /usr/sbin/ModemManager
root         658     679  0.0    4  0.4 392100 13068 ?        Ssl  15:05   0:00 /usr/sbin/ModemManager
root         658     691  0.0    4  0.4 392100 13068 ?        Ssl  15:05   0:00 /usr/sbin/ModemManager
syslog       665     665  0.0    4  0.1 222508  5964 ?        Ssl  15:05   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       665     685  0.0    4  0.1 222508  5964 ?        Ssl  15:05   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       665     686  0.0    4  0.1 222508  5964 ?        Ssl  15:05   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       665     687  0.0    4  0.1 222508  5964 ?        Ssl  15:05   0:00 /usr/sbin/rsyslogd -n -iNONE
root         666     666  0.0    1  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-cfg80]
root         672     672  0.1    2  0.7 109640 23148 ?        Ssl  15:05   0:00 /usr/bin/python3 /usr/share/unattended-u
root         672     768  0.0    2  0.7 109640 23148 ?        Ssl  15:05   0:00 /usr/bin/python3 /usr/share/unattended-u
root         703     703  0.0    1  0.0      0     0 ?        S    15:05   0:00 [irq/18-vmwgfx]
root         706     706  0.0    1  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-ttm]
root         716     716  0.0    1  0.0   6824  2904 ?        Ss   15:05   0:00 /usr/sbin/cron -f -P
root         750     750  0.0    1  0.1   6980  4896 tty1     Ss   15:05   0:00 /bin/login -p --
root         947     947  0.0    1  0.0      0     0 ?        S    15:05   0:00 [psimon]
pluto        949     949  0.0    1  0.3  20092 11304 ?        Ss   15:05   0:00 /usr/lib/systemd/systemd --user
pluto        950     950  0.0    1  0.1  21156  3572 ?        S    15:05   0:00 (sd-pam)
pluto        958     958  0.0    1  0.1   8656  5652 tty1     S+   15:05   0:00 -bash
root        1004    1004  0.0    1  0.0      0     0 ?        I<   15:05   0:00 [kworker/R-tls-s]
root        1010    1010  0.0    1  0.2  12024  8252 ?        Ss   15:05   0:00 sshd: /usr/sbin/sshd -D [listener] 0 of
root        1012    1012  0.0    1  0.3  14964 10640 ?        Ss   15:05   0:00 sshd: pluto [priv]
root        1014    1014  0.0    1  0.0      0     0 ?        I<   15:06   0:00 [kworker/0:2H]
pluto       1062    1062  0.4    1  0.2  15124  7136 ?        S    15:06   0:02 sshd: pluto@pts/0
pluto       1063    1063  0.0    1  0.1   8648  5652 pts/0    Ss   15:06   0:00 -bash
fwupd-r+    1073    1073  0.0    5  0.9 440036 27676 ?        Ssl  15:07   0:00 /usr/bin/fwupdmgr refresh
fwupd-r+    1073    1074  0.0    5  0.9 440036 27676 ?        Ssl  15:07   0:00 /usr/bin/fwupdmgr refresh
fwupd-r+    1073    1075  0.0    5  0.9 440036 27676 ?        Ssl  15:07   0:00 /usr/bin/fwupdmgr refresh
fwupd-r+    1073    1076  0.1    5  0.9 440036 27676 ?        Ssl  15:07   0:00 /usr/bin/fwupdmgr refresh
fwupd-r+    1073    1077  0.0    5  0.9 440036 27676 ?        Ssl  15:07   0:00 /usr/bin/fwupdmgr refresh
root        1078    1078  0.1    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1078    1079  0.0    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1078    1080  0.0    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1078    1081  0.0    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1078    1082  0.0    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1078    1084  0.0    6  1.3 551772 41712 ?        Ssl  15:07   0:00 /usr/libexec/fwupd/fwupd
root        1085    1085  0.0    4  0.3 314140  9276 ?        Ssl  15:07   0:00 /usr/libexec/upowerd
root        1085    1087  0.0    4  0.3 314140  9276 ?        Ssl  15:07   0:00 /usr/libexec/upowerd
root        1085    1088  0.0    4  0.3 314140  9276 ?        Ssl  15:07   0:00 /usr/libexec/upowerd
root        1085    1089  0.0    4  0.3 314140  9276 ?        Ssl  15:07   0:00 /usr/libexec/upowerd
root        1100    1100  0.4    1  0.0      0     0 ?        I    15:11   0:01 [kworker/2:0-events]
root        1109    1109  0.0    1  0.0      0     0 ?        I    15:15   0:00 [kworker/u7:0-events_unbound]
pluto       1111    1111  100    1  0.1  11012  4604 pts/0    R+   15:15   0:00 ps aux -L
```


3. Detail proses shell saat ini

Kode Program:<br>
```markdown
echo $$
ps -p $$ -f
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ echo $$
1063
pluto@Ubuntu-Server-Lab:~$ ps -p $$ -f
UID          PID    PPID  C STIME TTY          TIME CMD
pluto       1063    1062  0 15:06 pts/0    00:00:00 -bash
pluto@Ubuntu-Server-Lab:~$
```

4. Pohon proses

Kode Program:<br>
```markdown
pstree -p
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ pstree -p
systemd(1)─┬─ModemManager(658)─┬─{ModemManager}(674)
           │                   ├─{ModemManager}(679)
           │                   └─{ModemManager}(691)
           ├─cron(716)
           ├─dbus-daemon(606)
           ├─fwupd(1078)─┬─{fwupd}(1079)
           │             ├─{fwupd}(1080)
           │             ├─{fwupd}(1081)
           │             ├─{fwupd}(1082)
           │             └─{fwupd}(1084)
           ├─fwupdmgr(1073)─┬─{fwupdmgr}(1074)
           │                ├─{fwupdmgr}(1075)
           │                ├─{fwupdmgr}(1076)
           │                └─{fwupdmgr}(1077)
           ├─login(750)───bash(958)
           ├─multipathd(374)─┬─{multipathd}(385)
           │                 ├─{multipathd}(388)
           │                 ├─{multipathd}(389)
           │                 ├─{multipathd}(390)
           │                 ├─{multipathd}(393)
           │                 └─{multipathd}(394)
           ├─polkitd(611)─┬─{polkitd}(647)
           │              ├─{polkitd}(648)
           │              └─{polkitd}(650)
           ├─rsyslogd(665)─┬─{rsyslogd}(685)
           │               ├─{rsyslogd}(686)
           │               └─{rsyslogd}(687)
           ├─sshd(1010)───sshd(1012)───sshd(1062)───bash(1063)───pstree(1120)
           ├─systemd(949)───(sd-pam)(950)
           ├─systemd-journal(324)
           ├─systemd-logind(618)
           ├─systemd-network(473)
           ├─systemd-resolve(428)
           ├─systemd-timesyn(429)───{systemd-timesyn}(485)
           ├─systemd-udevd(406)
           ├─udisksd(619)─┬─{udisksd}(634)
           │              ├─{udisksd}(635)
           │              ├─{udisksd}(642)
           │              ├─{udisksd}(669)
           │              └─{udisksd}(689)
           ├─unattended-upgr(672)───{unattended-upgr}(768)
           └─upowerd(1085)─┬─{upowerd}(1087)
                           ├─{upowerd}(1088)
                           └─{upowerd}(1089)
```

## Latihan 6.1
Jalankan ps aux dan amati outputnya:
1. Berapa total proses yang berjalan? Proses apa yang memiliki PID terkecil?
**Jawab**<br>
Terdapat 126 proses<br>
```markdown
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.4  21952 13112 ?        Ss   15:04   0:03 /sbin/init splash noprompt noshell automatic-ubiquity
```
2. Jalankan pstree -p dan temukan proses bash Anda. Proses apa yang menjadi induk (PPID) dari bash tersebut?
**Jawab**<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ pstree -p | grep bash
           |-login(750)---bash(958)
           |-sshd(1010)---sshd(1012)---sshd(1062)---bash(1063)-+-grep(1264)
```
```markdown
    PID    PPID CMD
   1063    1062 -bash
```
3. Bandingkan output ps aux dan ps aux -L. Apa perbedaan yang Anda lihat?
**Jawab**<br>
ps aux menampilkan satu baris untuk setiap proses, sedangkan ps aux -L menampilkan satu baris untuk setiap thread di dalam satu proses

## Praktikum 6.2

1. Mengamati kondisi proses

Kode Program:<br>
```markdown
sleep 60 &
ps aux | grep sleep
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sleep 60 &
[1] 1271
pluto@Ubuntu-Server-Lab:~$ ps aux | grep sleep
pluto       1271  0.0  0.0   5684  2108 pts/0    S    15:32   0:00 sleep 60
pluto       1273  0.0  0.0   6544  2332 pts/0    S+   15:32   0:00 grep --color=auto
```

2. Mengamati exit code

Kode Program:<br>
```markdown
ls / tmp
echo " Sukses : $?"
ls / direktori - tidak - ada
echo " Gagal : $?"
```

Hasil Program:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ls / tmp
echo " Sukses : $?"
ls / direktori - tidak - ada
echo " Gagal : $?"
ls: cannot access 'tmp': No such file or directory
/:
backup  bin.usr-is-merged  cdrom  etc   lib    lib.usr-is-merged  media  opt   root  sbin                snap  sys  usr
bin     boot               dev    home  lib64  lost+found         mnt    proc  run   sbin.usr-is-merged  srv   tmp  var
 Sukses : 2
ls: cannot access 'direktori': No such file or directory
ls: cannot access 'tidak': No such file or directory
ls: cannot access 'ada': No such file or directory
-  -

/:
backup  bin.usr-is-merged  cdrom  etc   lib    lib.usr-is-merged  media  opt   root  sbin                snap  sys  usr
bin     boot               dev    home  lib64  lost+found         mnt    proc  run   sbin.usr-is-merged  srv   tmp  var
 Gagal : 2
```

## Latihan 6.2
1. Jalankan sleep 120 & dan amati kolom STAT pada ps aux. Kondisi apa yang ditampilkan? Mengapa proses sleep berada di kondisi tersebut?
**Jawab**<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ sleep 120 &
[1] 1287
pluto@Ubuntu-Server-Lab:~$ ps aux | grep sleep
pluto       1287  0.0  0.0   5684  2108 pts/0    S    15:37   0:00 sleep 120
pluto       1289 50.0  0.0   6544  2332 pts/0    S+   15:37   0:00 grep --color=auto sleep
```

Proses sleep sedang menunggu timeout selama 120 detik. Selama menunggu:
- Proses tidak menggunakan CPU (karena tidak ada komputasi yang dilakukan).
- Proses berada dalam keadaan sleep sampai timer selesai.
- Karena dapat diinterupsi oleh sinyal (misalnya SIGINT dari Ctrl+C), statusnya adalah interruptible sleep (S), bukan D (uninterruptible sleep).
2. Jalankan beberapa perintah yang berhasil dan yang gagal, lalu catat exit code masing-masing. Pola apa yang Anda temukan?
**Jawab**<br>
Berhasil:<br>
```python
pluto@Ubuntu-Server-Lab:~$ ls /home
echo $?
pluto
0
```
Gagal:<br>
```markdown
pluto@Ubuntu-Server-Lab:~$ ls /Direktori_Palsu
echo $?
ls: cannot access '/Direktori_Palsu': No such file or directory
2
```
Pola yang ditemukan:<br>
- Exit code 0 → Selalu berarti sukses (tidak ada error).

- Exit code bukan 0 (1, 2, 127, dll) → Gagal. Semakin besar angka tidak selalu berarti semakin parah, tetapi tergantung program.

- Exit code mencerminkan status dari command terakhir yang dieksekusi.
Perintah yang berhasil secara logika (misal grep tidak menemukan pola) bisa tetap mengembalikan 1 (gagal dari sudut pandang pencarian, bukan eksekusi perintah).

- Konsistensi: Semua perintah yang berhasil mengembalikan 0, semua yang gagal mengembalikan nilai bukan 0. Tidak ada program sukses yang mengembalikan 1.



