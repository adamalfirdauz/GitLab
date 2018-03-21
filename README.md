
<h1 align="center"><img src="https://about.gitlab.com/images/press/logo/wm_no_bg.svg"></h1>

[Sekilas Tentang GitLab](#sekilas-tentang-gitlab) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:



# Sekilas Tentang GitLab
[`^ kembali ke atas ^`](#)

**GitLab** adalah sebuah manajer repositori [Git](https://id.wikipedia.org/wiki/Git "Git") berbasis web dengan fitur [wiki](https://id.wikipedia.org/wiki/Wiki "Wiki") dan [pelacakan masalah](https://id.wikipedia.org/w/index.php?title=Pelacakan_masalah&action=edit&redlink=1 "Pelacakan masalah (halaman belum tersedia)"), menggunakan lisensi [sumber terbuka](https://id.wikipedia.org/wiki/Sumber_terbuka "Sumber terbuka"), dikembangkan oleh ***GitLab Inc***. Perangkat lunak ini ditulis oleh [Dmitriy Zaporozhets](https://id.wikipedia.org/w/index.php?title=Dmitriy_Zaporozhets&action=edit&redlink=1 "Dmitriy Zaporozhets (halaman belum tersedia)") dan [Valery Sizov](https://id.wikipedia.org/w/index.php?title=Valery_Sizov&action=edit&redlink=1 "Valery Sizov (halaman belum tersedia)") dari [Ukraina](https://id.wikipedia.org/wiki/Ukraina "Ukraina"). Kode yang ditulis adalah [`Ruby`](https://id.wikipedia.org/wiki/Ruby_(bahasa_pemrograman) "Ruby (bahasa pemrograman)"). Kemudian, beberapa bagian telah ditulis ulang di `Go`. Pada bulan Desember 2016, **GitLab** memiliki 150 anggota tim[\[3\]](https://id.wikipedia.org/wiki/GitLab#cite_note-3) dan lebih dari 1400 kontributor sumber terbuka. **GitLab** telah digunakan oleh organisasi seperti [IBM](https://id.wikipedia.org/wiki/IBM "IBM"), [Sony](https://id.wikipedia.org/wiki/Sony "Sony"), [Jülich Research Center](https://id.wikipedia.org/w/index.php?title=J%C3%BClich_Research_Center&action=edit&redlink=1 "Jülich Research Center (halaman belum tersedia)"), [NASA](https://id.wikipedia.org/wiki/NASA "NASA"), [Alibaba](https://id.wikipedia.org/w/index.php?title=Alibaba_Group&action=edit&redlink=1 "Alibaba Group (halaman belum tersedia)"), [Invincea](https://id.wikipedia.org/w/index.php?title=Invincea&action=edit&redlink=1 "Invincea (halaman belum tersedia)"), [O’Reilly Media](https://id.wikipedia.org/w/index.php?title=O%E2%80%99Reilly_Media&action=edit&redlink=1 "O’Reilly Media (halaman belum tersedia)"), [Leibniz-Rechenzentrum (LRZ)](https://id.wikipedia.org/w/index.php?title=Leibniz-Rechenzentrum&action=edit&redlink=1 "Leibniz-Rechenzentrum (halaman belum tersedia)"), [CERN](https://id.wikipedia.org/wiki/CERN "CERN").[\[4\]](https://id.wikipedia.org/wiki/GitLab#cite_note-4)[\[5\]](https://id.wikipedia.org/wiki/GitLab#cite_note-5)[\[6\]](https://id.wikipedia.org/wiki/GitLab#cite_note-6), dan [SpaceX](https://id.wikipedia.org/wiki/SpaceX "SpaceX").[\[7\]](https://id.wikipedia.org/wiki/GitLab#cite_note-7)

Gitlab terdiri dari 4 versi, yaitu *Gitlab Community Edition*, *Gitlab Enterprise Edition*, *Gitlab.com* , dan *Gitlab CI*. Pada kali ini kita akan menginstall ***GitLab Community Edition***.

# Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan Sistem :
- Unix, Linux atau Windows.
- Ruby 2.3.
- CPU 2 cores+.
- Storage 7200 RPM+.
- RAM 4GB.
- Database PostgreSQL.
- Akses Root.
- Prasyarat lain yang lebih spesifik seperti `openssh-server`, `ca-certificates`, dan `postfix`.

#### Proses Instalasi :
1. Login kedalam server menggunakan SSH. Untuk pengguna windows bisa menggunakan aplikasi [PuTTY](http://www.putty.org/), sedangkan pengguna Linux atau UNIX bisa langsung melalui terminal.
    ```
    $ ssh student@localhost -p 2222
    ```

2. Pastikan seluruh paket sistem *up-to-date*, dan install seluruh kebutuhan sistem seperti  `openssh-server`, `ca-certificates`, `postfix`, `Ruby`, dan `PostgreSQL`.
    ```
    $ sudo apt-get update
    $ sudo apt-get -y install curl openssh-server ca-certificates postfix
    ```
    Pada saat menginstall postfix akan muncul kotak dialog yang meminta kita  untuk mengonfigurasikan mail server.
    - Kotak dialog yang pertama akan memberikan keterangan mengenai maksud dari pilihan yang akan muncul pada dialog berikutnya. Pilih **OK**.
	    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/postfix-conf-01.png"></div>
    - Selanjutnya akan diminta untuk memilih tipe konfigurasi email, pilih saja Internet Site.
	    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/postfix-conf-02.png"></div>
	 - Kemudian beri nama domain, karena pada kali ini tidak ada domain yang disiapkan serta bersifat lokal, maka isi saja dengan *gitlab.local*
		 <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/postfix-conf-03.png"></div>
        

3. Unduh **GitLab** ke dalam direktori kita. 
    ```
    $ curl -LJO https://packages.gitlab.com/gitlab/gitlab-ce/packages/ubuntu/trusty/gitlab-ce_10.5.4-ce.0_amd64.deb/download.deb
    ```
    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/download-gitlab.png"/></div>
    Untuk mengunduh versi lain dapat mengunjung situs resmi **GitLab** \[[source](https://packages.gitlab.com/gitlab/gitlab-ce/)\].

4. Jalankan file yang sudah diunduh tadi menggunakan perintah `dpkg` untuk menginstall **GitLab**.
    ```
    $ sudo dpkg -i gitlab-ce_10.5.4-ce.0_amd64.deb
    ```
    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/success-install-gitlab.png"/></div>

5. Sesuai dengan keterangan setelah install gitlab, kita perlu mengubah `external_url`. Ubah ke `http://gitlab.local` karena kita tidak memiliki domain asli.
    ```
    $ sudo nano /etc/gitlab/gitlab.rb
    ```
    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/external-url.png"/></div>

6. Jalankan konfigurasi.
    ```
    $ sudo gitlab-ctl reconfigure
    ```
	<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/configure-done.png"/></div>
7. Setelah konfigurasi selesai dijalankan, buka alamat IP web server menggunakan browser.
    ```
    http://localhost:8888
    ```
    Pada saat pertama kali membuka **GitLab** akan muncul form untuk mengubah password root. Isi dan *submit* password baru tersebut.
    <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/image.png"/></div>

# Konfigurasi
[`^ kembali ke atas ^`](#)



# Maintenance
[`^ kembali ke atas ^`](#)




# Otomatisasi
[`^ kembali ke atas ^`](#)


# Cara Pemakaian
[`^ kembali ke atas ^`](#)
1. Sebagai salah satu manajer repository, **GitLab** memiliki segudang fitur yang ditawarkan kepada para penggunanya. Namun sebelum merasakan fitur-fitur tersebut, pengguna terlebih dulu harus memiliki akun **GitLab**. Untuk melakukan registrasi akun, cukup membuka halaman awal.
<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-01-register.png"/></div>

2. Setelah melakukan registrasi, kita perlu login untuk masuk ke dalam **GitLab**.

<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-02-login.png"/></div>

3. Setelah masuk, kita akan berada pada halaman *dashboard*. Pada halaman ini kita dapat Pada halaman ini kita dapat membuat *project* dan grup. 
<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-03-awal.png"/></div>

4. Membuat *project*.  
	1. *Blank Project*, membuat proyek kosong.
		<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-04-blank.png"/></div>
	2. *Create from template*, membuat proyek dari template yang telah disediakan oleh gitlab.
		 <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-04-template.png"/></div>
	 3. *Import project*, memasukan proyek dari aplikasi manajemen repositori lain. 
		 <div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-04-import.png"/></div>
5. Membuat grup.
	1. Grup adalah kumpulan dari beberapa proyek. Jika anda mengatur proyek anda di bawah grup, maka ini akan bekerja seperti folder. Anda dapat mengelola izin anggota grup dan akses ke setiap proyek dalam grup.
	<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-05-grup.png"/></div>

	2. Pada dashboard grup, anda dapat membuat proyek baru yang nantinya akan dikerjakan bersama oleh anggota grup. 
	<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-05-grup-dashboard.png"/></div>

	3. Anda juga dapat mengatur keanggotaan grup melalui menu *Members*
	<div align="center"><img src="https://github.com/adamalfirdauz/GitLab/raw/master/img/fitur-05-grup-member.png"/></div>


# Pembahasan
[`^ kembali ke atas ^`](#)

**Gitlab CE** merupakan versi komunitas dari Gitlab dimana semua kode sumbernya bersifat open source, sehingga dapat diakses oleh semua kalangan kemudian dari pada itu dapat membantu pengembangannya. Penulisan kode Gitlab Gitilab ditulis dengan menggunakan bahasa Ruby. Tentunya Gitlab memiliki kelebihan dan kekurangan tersendiri seperti yang dituliskan dibawah ini:
#### Kelebihan
1. Memiliki fitur *public* dan *private* sehingga user dapat memilih modenya sesuai dengan kebutuhannya. Jika kita menggunakan status _private_maka project kita hanya dapat diubah dan dilihat oleh kita secara pribadi. Namun jika kita menggunakan status _public_ maka project kita dapat diubah, dilihat, dan diunduh oleh siapa saja.
2. Unlimited Repo. Sehingga kita dapat membuat repo sesuai dengan kebutuhan kita, meskipun hanya berskala kecil
3. Project Importing, kita tidak hanya dapat meng-import project dari Github saja, namun kita dpat meng-import project dari BitBucket, Google Code, Fogbugz, atau git repo dengan URL
4.  API (_Aplication Programming Interface_  ) , Kita dapat mengontrol Gitlab dengan set API yang kuat.
5. Gitlab didukung dengan LFS (  _Large File Storage_  ). Sehingga mempermudah pengguna yang ingin mengupload materi di repo secara gratis.

#### Kekurangan
1.  Jika kita mencari komunitas pengguna, kemungkinan komunitas Gitlab masih minim. Sehingga ketika kita menemukan suatu masalah mungkin sedikit lebih sulit dalam menemukan solusinya.
2.  Gitlab belum mengizinkan untuk melakukan pegeditian yang dilakukan oleh pengguna hulu di cabang.
3. Belum memiliki fungsi *drag and drop* seperti yang dimiliki leh Github.
4. Gitlab juga belum mensupport penggunaan IPv6.
5. Gitlab bellum memiliki kemampuan untuk menentukan pemilik kode sumber dan mengulas/reviewers dalam repository

## Gitlab Vs Github
-   **Penawaran Public dan Private Project**

Fitur  _public_  dan  _private_  yang disediakan github dapat diakses dan digunakan secara gratis. Tidak seperti Github yang hanya menyediakan layanan  _public_  saja yang gratis, sementara layanan  _private_  berbayar.

-   **Snippet support**

Gitlab memiliki fitur  _Snippet Support_  , yaitu fitur yang memungkinkan pengguna dapat berbagi potongan kecil source code project tanpa berbagi keseluruhan project.

-   **Issue Tracking atau Pelacakan Masalah**

Gitlab menawarkan fitur Issue Tracker yang kuat sehingga kita dapat melakukan perubahan dan pengalihan terhadap beberapa masalah dalam waktu yang sama. Github pun menawarkan fitur Github Issue yang berfungsi untuk melakukan pelacakan masalah dalam project.

-   **Progress Status**

Dalam Gitlab, Para pengembang dapat memberikan label dalam project yang sedang dikerjakan dengan label  _"Work in Progress"_  sehingga memberikan kejelasan atas Project yang sedang dikerjakan. Ini memang sebuah hal yang kecil , namun ini pasti akan sangat membantu para pengembang aplikasi dan web karena Fitur ini mencegah kode yang sedang digarap digabung dengan kode lain sebelum code tersebut benar-benar selesai.

-   **Integrasi**

Github dan Gitlab mengintegrasikan versi sistem kontrol milik kita dengan aplikasi lain untuk memperkaya alur kerja dan dapat meningkatkan produktivitas pengembangan kita.

-   **Github Comunnity**

Jika Kita ingin mnencari komunitas pengembang aplikasi dan web , kemungkinan besar Github adalah tempat yang lebih baik karena Github menempatkan dirinya dalam komunitas tersebut. Apalagi popularitasnya didorong dengan para anggota komunitas Github yang aktif.


# Referensi
[`^ kembali ke atas ^`](#)


1. [Maintenance Command](https://docs.gitlab.com/omnibus/maintenance/README.html) - GitLab
2. [Github Vs Gitlab kamu pilih mana?](https://www.codepolitan.com/github-vs-gitlab-kamu-pilih-mana-58808e62c2b28) - CodePolitan
3. [Gitlab](https://id.wikipedia.org/wiki/GitLab) - Wikipedia
4. [GitLab compared to other tools](https://about.gitlab.com/comparison/) - GitLab
5. [How To Install Gitlab on Debian 8 (Jessie)](https://www.howtoforge.com/tutorial/how-to-install-gitlab-on-debian-8/) - HowToForge
