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

5. Cek log kernel terbaru
![Tampilkan](Images/Praktikum4_5.png)<br>


## Praktikum 2.5

1. Menambahkan modul untuk auto-load (demo)
![Tampilkan](Images/Praktikum5_1.png)<br>

2. Verifikasi modul aktif
![Tampilkan](Images/Praktikum5_2.png)<br>

3. Contoh blacklist modul
![Tampilkan](Images/Praktikum5_3.png)<br>

## Praktikum 2.6

1. Melihat detail device node disk
![Tampilkan](Images/Praktikum6_1.png)<br>

2. Melihat detail device node terminal
![Tampilkan](Images/Praktikum6_2.png)<br>

3. Mapping disk/partisi
![Tampilkan](Images/Praktikum6_3.png)<br>

**Latihan 2.3**<br>

Dari output ls -l, jelaskan perbedaan penanda file untuk block device dan character device. (Hint: karakter pertama pada permission string)<br>

Perbedaan = character device memasukkan/mengeluarkan data satu karakter sekaligus, sedangkan block device memasukkan/mengeluarkan data blok demi blok. block device menggunakan tanda huruf b, sedangkan character device menggunakan awalan huruf c<br>

## Praktikum 2.7

1. Melihat atribut udev untuk disk
![Tampilkan](Images/Praktikum7_1.png)<br>

2. Monitor event udev
![Tampilkan](Images/Praktikum7_2.png)<br>

## Praktikum 2.8

1. Membuat workspace praktikum
![Tampilkan](Images/Praktikum8_1.png)<br>

2. Membuat workspace praktikum
![Tampilkan](Images/Praktikum8_2.png)<br>

3.  Mengisi file log contoh
![Tampilkan](Images/Praktikum8_3.png)<br>

4. Membaca file dengan less
![Tampilkan](Images/Praktikum8_4.png)<br>

Praktikum 16
Port = 55
Proses/Service = systemd
pid = 1
Biasanya digunakan untuk:
-Aplikasi kustom / internal
- Service testing
- Software tertentu yang dikonfigurasi manual
- Bisa juga indikasi service tidak umum (perlu dicek)
