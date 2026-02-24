# Laporan Sistem Operasi Jobsheet 1
<h4>Nama : Muhammad Akmal Dwiansyah Putra<h4>
<h4>NIM : 254107020110<h4>
<h4>Kelas : TI_1G<h4>

## 1.10.1. Latihan Konseptual
1. Jelaskan 5 fungsi utama sistem operasi dengan contoh konkret dari minimal 2 OS berbeda (Windows, macOS, atau Linux).<br>
**jawab:** <br>  
1.Process Management  
<b>Sistem operasi bertanggung jawab untuk:</b>  
• Process scheduling — Menentukan proses mana yang mendapat CPU time  
• Process creation dan termination — Membuat dan mengakhiri proses  
• Process synchronization — Mengkoordinasikan multiple processes  
• Inter-process communication (IPC) — Memfasilitasi komunikasi antar
proses  
<b>Contoh implementasi: </b> 
• Windows: Task Manager menampilkan proses yang berjalan dan penggunaan
sumber daya   
• Linux: Perintah ps, top, dan htop untuk memantau proses  
• macOS: Activity Monitor untuk mengelola proses<br><br>
2.Memory Management  
<b>Fungsi memory management meliputi:</b>  
• Memory allocation — Memberikan memori ke proses yang membutuhkan  
• Virtual memory — Menggunakan disk sebagai extension dari RAM  
• Memory protection — Mencegah satu proses mengakses memori proses lain  
• Paging dan swapping — Teknik untuk optimasi penggunaan memori<br><br>
3.File Management  
<b>Sistem operasi menyediakan:</b>  
• Organisasi file system — Struktur hirarkis (direktori, subdirektori)
• Operasi file — Membuat, membaca, menulis, menghapus file  
• Kontrol akses — Izin (permissions) untuk keamanan  
• Mounting file system — Mengintegrasikan perangkat penyimpanan ke sistem  
<b>Contoh file systems:</b>  
• Windows: NTFS (New Technology File System)  
• macOS: APFS (Apple File System)  
• Linux: ext4, XFS, Btrfs<br><br>
4.I/O Management  
<b>Manajemen Input/Output mencakup:</b>  
• Device drivers — Perangkat lunak untuk berkomunikasi dengan perangkat
keras  
• Buffering — Penyimpanan sementara untuk kelancaran operasi I/O  
• Interrupt handling — Merespon sinyal dari perangkat keras  
• Spooling — Antrean untuk perangkat seperti printer
Security dan Protection  
<b>Contoh Impelentasi:</b>
* Windows: Saat kita memasukkan flashdisk USB, Windows secara otomatis mendeteksi perangkat tersebut dan menggunakan driver yang sesuai (misalnya usbstor.sys) untuk berkomunikasi dengan perangkat keras. Proses ini terjadi di latar belakang tanpa perlu campur tangan pengguna.  
* Linux: Di Linux, ketika perangkat baru seperti printer atau scanner terhubung melalui USB, kernel menggunakan driver seperti usbcore dan usb-storage untuk mengakses perangkat. Pengguna juga bisa melihat daftar driver yang digunakan melalui perintah lsmod atau melihat perangkat di /dev.<br><br>
5. Aspek keamanan meliputi:  
• Authentication — Verifikasi identitas pengguna (password, biometrik)  
• Authorization — Kontrol akses ke sumber daya berdasarkan izin (permissions)  
• Encryption — Proteksi data (BitLocker di Windows, FileVault di macOS)  
• Auditing — Pencatatan aktivitas sistem untuk pemantauan keamanan
<b>Contoh Impelemntasi:</b>  
• Windows: Windows memiliki fitur BitLocker yang digunakan untuk mengenkripsi seluruh drive. Misalnya, jika laptop dicuri, data di dalamnya tetap aman karena tidak bisa diakses tanpa kunci pemulihan atau password.  
• Linux: Di Linux, pengguna bisa menggunakan LUKS (Linux Unified Key Setup) untuk enkripsi disk. Saat instalasi Ubuntu, pengguna bisa memilih opsi Encrypt the entire disk untuk melindungi data.
<br><br>
2. Kapan sebaiknya menggunakan Windows vs Linux vs macOS? Analisis berdasarkan use case: gaming, development, server, creative work, dan enterprise.<br>
**jawab:** <br>
Ketiga Sistem Operasi tersebut memiliki keunikan masing masing dan kegunaan masing masing, untuk user friendly dan compatibility yang besar, windows merupakan Operating System yang layak untuk gaming, presentasi maupun daily-use. Sedangkan linux memiliki kelebihan di customizability, development dan server, dengan bentuk yang sederhana, linux tidak perlu memakan banyak tenaga untuk perangkat seperti laptop. Dan untuk creative work dan enterprise, MacOS merupakan pillihan yang paling bagus dikarenakan memiliki ecosystem yang bagus dibandingkan kedua OS lainnya. Mudah untuk mengirim dan menerima dengan aplikasi seperti apple airdrop.<br>

## 1.10.2. Latihan Praktikal
Install Ubuntu Server 22.04 LTS di VirtualBox dengan langkah berikut:<br>
1. Download Ubuntu Server ISO dari website resmi<br>
2. Create VM baru di VirtualBox (RAM: 2GB, Disk: 25GB)<br>
3. Install dengan automatic partitioning (guided)<br>
4. Buat user account dengan password yang kuat<br>
5. Reboot dan login ke sistem<br>
6. Dokumentasikan proses instalasi dengan screenshot key steps<br>

![Tampilkan dafta perangkat pci](Images1/1.png)<br>
![Tampilkan dafta perangkat pci](Images1/2.png)<br>
![Tampilkan dafta perangkat pci](Images1/3.png)<br>
![Tampilkan dafta perangkat pci](Images1/4.png)<br>
![Tampilkan dafta perangkat pci](Images1/5.png)<br>
![Tampilkan dafta perangkat pci](Images1/6.png)<br>

Setelah instalasi Ubuntu Server, lakukan tasks berikut:<br>
1. Update package list: sudo apt update<br>
2. Upgrade packages: sudo apt upgrade<br>
3. Install neofetch: sudo apt install neofetch<br>
4. Jalankan neofetch dan screenshot hasilnya<br>
5. Check disk usage dengan df -h<br>
6. Check memory dengan free -h<br>
7. Dokumentasikan output dari setiap command<br>


Eksplorasi sistem yang baru diinstall:<br>
1. Tampilkan informasi OS: cat /etc/os-release<br>
2. Tampilkan versi kernel: uname -r<br>
3. List partisi: lsblk<br>
4. Check network connectivity: ping -c 4 google.com<br>
5. Install dan jalankan htop untuk melihat resource usage<br>
6. Buat laporan singkat tentang konfigurasi sistem Anda<br>

## 1.10.3. Latihan Refleksi

Ceritakan pengalaman Anda dengan sistem operasi:<br>
1. Sistem operasi apa yang Anda gunakan sehari-hari? (Windows, macOS, Linux, atau lainnya)<br>
2. Berapa lama Anda menggunakan sistem operasi tersebut?<br>
3. Apa yang Anda sukai dari sistem operasi tersebut?<br>
4. Apa tantangan atau masalah yang pernah Anda hadapi?<br>
5. Apakah Anda pernah menggunakan sistem operasi lain? Bandingkan pengalaman Anda.<br>
6. Setelah mempelajari bab ini, apakah ada sistem operasi lain yang ingin Anda coba? Mengapa?<br>
Tulis refleksi Anda dalam 300-500 kata disertai dengan dokumentasi.<br>
