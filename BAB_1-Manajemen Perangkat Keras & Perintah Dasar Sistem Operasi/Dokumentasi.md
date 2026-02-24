# Laporan Sistem Operasi Jobsheet 2
<h4>Nama : Muhammad Akmal Dwiansyah Putra<h4>
<h4>NIM : 254107020110<h4>
<h4>Kelas : TI_1G<h4>


## Praktikum 2.1
1. Melihat informasi CPU
![Tampilkan informasi cpu](Images/Praktikum1_1.png)<br>

2. Melihat Penggunaan Memori
![Tampilkan penggunaan memori](Images/Praktikum1_2.png)<br>

3. Informasi DMI
![Informasi DMI](Images/Praktikum1_3.png)<br>

**Latihan 2.1**<br>
Catat: (1) jumlah CPU(s), core/thread, (2) total RAM, (3) total swap. Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat.<br>
* Cpu = 1 <br>
* threads = 1 <br>
* core = 3 <br>
* RAM = 2.9 Gi <br>
* swap = 0 <br>
Perbedaan = Perbedaan dari RAM dan swap adalah, RAM merupakan memori utama yang digunakan oleh komputer untuk menyimpan data, sedangkan swap adalah storage yang digunakan sebagai memori virtual cadangan saat RAM mulai penuh<br>

## Praktikum 2.2
1. Daftar perangkat PCI
![Tampilkan dafta perangkat pci](Images/Praktikum2_1.png)<br>

2.  Melihat driver perangkat PCI
![Tampilkan dafta perangkat pci](Images/Praktikum2_2.png)<br>

3. Mencari info NIC dan drivernya
![Tampilkan dafta perangkat pci](Images/Praktikum2_3.png)<br>

4. Daftar perangkat USB<br>
![Tampilkan dafta perangkat pci](Images/Praktikum2_4.png)<br>

5. Topologi perangkat USB
![Tampilkan dafta perangkat pci](Images/Praktikum2_5.png)<br>

**Latihan 2.2**<br>
Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.<br>

Nama Perangkat = Intel Corporation 82801AA AC'97 Audio Controller<br>
Device ID = 8086:2415<br>
Kernel Module = snd_intel8x0<br>
Deskripsi = Digunakan untuk mengkontrol Audio<br>

## Praktikum 2.3

1. Melihat block device dan filesystem
![Tampilkan](Images/Praktikum3_1.png)<br>

2. Melihat UUID filesystem
![Tampilkan](Images/Praktikum3_2.png)<br>

3. Melihat device untuk root filesystem<br>
![Tampilkan](Images/Praktikum3_3.png)<br>


## Praktikum 2.4

1. Cek versi kernel<br>
![Tampilkan](Images/Praktikum4_1.png)<br>

2. Daftar modul aktif<br>
![Tampilkan](Images/Praktikum4_2.png)<br>

3. Detail modul dengan modinfo
![Tampilkan](Images/Praktikum4_3.png)<br>

4. Load modul dan verifikasi<br>
![Tampilkan](Images/Praktikum4_4.png)<br>

5. Cek log kernel terbaru<br>
![Tampilkan](Images/Praktikum4_5.png)<br>


## Praktikum 2.5

1. Menambahkan modul untuk auto-load (demo)
![Tampilkan](Images/Praktikum5_1.png)<br>

2. Verifikasi modul aktif<br>
![Tampilkan](Images/Praktikum5_2.png)<br>

3. Contoh blacklist modul
![Tampilkan](Images/Praktikum5_3.png)<br>

## Praktikum 2.6

1. Melihat detail device node disk<br>
![Tampilkan](Images/Praktikum6_1.png)<br>

2. Melihat detail device node terminal<br>
![Tampilkan](Images/Praktikum6_2.png)<br>

3. Mapping disk/partisi<br>
![Tampilkan](Images/Praktikum6_3.png)<br>

**Latihan 2.3**<br>

Dari output ls -l, jelaskan perbedaan penanda file untuk block device dan character device. (Hint: karakter pertama pada permission string)<br>

Perbedaan = character device memasukkan/mengeluarkan data satu karakter sekaligus, sedangkan block device memasukkan/mengeluarkan data blok demi blok. block device menggunakan tanda huruf b, sedangkan character device menggunakan awalan huruf c<br>

## Praktikum 2.7

1. Melihat atribut udev untuk disk
![Tampilkan](Images/Praktikum7_1.png)<br>

2. Monitor event udev<br>
![Tampilkan](Images/Praktikum7_2.png)<br>

## Praktikum 2.8

1. Membuat workspace praktikum<br>
![Tampilkan](Images/Praktikum8_1.png)<br>

2. Membuat workspace praktikum
![Tampilkan](Images/Praktikum8_2.png)<br>

3.  Mengisi file log contoh
![Tampilkan](Images/Praktikum8_3.png)<br>

4. Membaca file dengan less<br>
![Tampilkan](Images/Praktikum8_4.png)<br>

## Praktikum 2.9

1. grep sederhana<br>
![Tampilkan](Images/Praktikum9_1.png)<br>

2. grep case-insensitive<br>
![Tampilkan](Images/Praktikum9_2.png)<br>

3. grep dengan nomor baris<br>
![Tampilkan](Images/Praktikum9_3.png)<br>

4. grep invert match<br>
![Tampilkan](Images/Praktikum9_4.png)<br>

**Latihan 2.4**<br>

Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau
WARN dari data.log. (Hint: gunakan grep -E dengan pola alternatif)<br>

![Tampilkan](Images/Praktikum9_TUGAS.png)<br>

## Praktikum 2.10

1. Membuat file config latihan<br>
![Tampilkan](Images/Praktikum10_1.png)<br>

2. sed substitusi tanpa in-place
![Tampilkan](Images/Praktikum10_2.png)<br>

3. sed in-place
![Tampilkan](Images/Praktikum10_3.png)<br>

4. sed global replacement
![Tampilkan](Images/Praktikum10_4.png)<br>

## Praktikum 2.11

1. Output df -h<br>
![Tampilkan](Images/Praktikum11_1.png)<br>

2. awk print kolom tertentu
![Tampilkan](Images/Praktikum11_2.png)<br>

3. awk filter berdasarkan kondisi
![Tampilkan](Images/Praktikum11_3.png)<br>

## Praktikum 2.12

1. ps aux
![Tampilkan](Images/Praktikum12_1.png)<br>

2. Filter proses dengan grep
![Tampilkan](Images/Praktikum12_2.png)<br>

## Praktikum 2.13

1. Menjalankan top
![Tampilkan](Images/Praktikum13_1.png)<br>

## Praktikum 2.14

1. Membuat proses dummy
![Tampilkan](Images/Praktikum14_1.png)<br>

2. Mencari PID sleep<br>
![Tampilkan](Images/Praktikum14_2.png)<br>

3. Mengirim SIGTERM
![Tampilkan](Images/Praktikum14_3.png)<br>

4. Verifikasi proses sudah berhenti<br>
![Tampilkan](Images/Praktikum14_4.png)<br>

5. Mengirim SIGKILL <br>
![Tampilkan](Images/Praktikum14_5.png)<br>

## Praktikum 2.15

1. Cek kapasitas disk
![Tampilkan](Images/Praktikum15_1.png)<br>

2. Cek ukuran direktori (contoh /var)
![Tampilkan](Images/Praktikum15_2.png)<br>

3. Cek load average<br>
![Tampilkan](Images/Praktikum15_3.png)<br>

4. Service yang gagal
![Tampilkan](Images/Praktikum15_4.png)<br>

5. Log error terbaru
![Tampilkan](Images/Praktikum15_5.png)<br>

## Praktikum 2.16

1. Cek IP address
![Tampilkan](Images/Praktikum16_1.png)<br>

2. Cek routing
![Tampilkan](Images/Praktikum16_2.png)<br>

3. Cek port listening
![Tampilkan](Images/Praktikum16_3.png)<br>

**Latihan 2.5**<br>

Pilih satu port yang listening dari output ss -tulpn(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat.<br>

Port = 55<br>
Proses/Service = systemd<br>
pid = 1<br>
Biasanya digunakan untuk:<br>
- Aplikasi kustom / internal
- Service testing
- Software tertentu yang dikonfigurasi manual
- Bisa juga indikasi service tidak umum (perlu dicek)

# LATIHAN SOAL

2.A Jalankan lspci -nnk. Pilih 1 perangkat PCI dan tuliskan: nama perangkat, ID vendor:device, dan kernel driver in use.<br>
**jawab:** <br>
Nama Perangkat = Intel Corporation 82801AA AC'97 Audio Controller<br>
Device ID = 8086:2415<br>
Kernel Module = snd_intel8x0<br>
Deskripsi = Digunakan untuk mengkontrol Audio<br>
![Tampilkan dafta perangkat pci](Images/Praktikum2_2.png)<br>

2.B Tentukan device root filesystem dengan findmnt /. Lalu cocokkan dengan lsblk -f dan tuliskan tipe filesystem serta UUID-nya.<br>
**jawab:** <br>
FileSystem: ext4<br>
UUID: 695ba52b-32a2-4a47-b706-a96aff037c4a<br>

2.C Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO,WARN, ERROR. Gunakan grep untuk menampilkan hanya baris ERROR.<br>
**jawab:** <br>
![Tampilkan dafta perangkat pci](Images/Latihan2c.png)<br>

2.D Gunakan sed untuk mengganti semua kata server menjadi node pada file latihan. Tunjukkan sebelum dan sesudah.<br>
**jawab:** <br>
Sebelum<br>
![Tampilkan dafta perangkat pci](Images/2D_sebelum.png)<br>

Sesudah<br>
![Tampilkan dafta perangkat pci](Images/2D_sesudah.png)<br>

2.E Gunakan df -h lalu awk untuk menampilkan filesystem yang penggunaan disk di atas 70%.<br>
**jawab:** <br>
![Tampilkan dafta perangkat pci](Images/2E.png)<br>

2.F Jalankan sleep 600 &. Temukan PID-nya dengan ps. Hentikan dengan SIGTERM. Jelaskan beda SIGTERM vs SIGKILL.<br>
**jawab:** <br>
Perbedaan dari SIGTERM dan SIGKILL adalah SIGTERM menutup file secara aman, sedangkan SIGKILL memaksa mematikan file yang dapat membuat file tersebut corrupt. Serta SIGTERM menggunakan terminated dan SIGKILL menggunakan killed<br>

2.G Gunakan systemctl –failed. Jika tidak ada yang gagal, pilih satu service aktif (misal ssh) dan tampilkan status serta 30 baris log terakhirnya.<br>
**jawab:** <br>
![Tampilkan dafta perangkat pci](Images/2G.png)<br>

