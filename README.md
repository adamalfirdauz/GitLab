
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
    

# Konfigurasi
[`^ kembali ke atas ^`](#)



# Maintenance
[`^ kembali ke atas ^`](#)




# Otomatisasi
[`^ kembali ke atas ^`](#)


# Cara Pemakaian
[`^ kembali ke atas ^`](#)



# Pembahasan
[`^ kembali ke atas ^`](#)

**Prestashop** ditulis dalam bahasa pemrograman `PHP` yang support untuk penggunaan MySQL. Sebagai salah satu CMS yang paling banyak digunakan di dunia, aplikasi ini menawarkan berbagai kelebihan, diantaranya :
- Aplikasi memiliki panel administrasinya mudah digunakan dan fleksibel, sehingga dapat disesuaikan dengan kebutuhan.
- Mendukung berbagai layanan pembayaran utama, seperti `PayPal`, `VISA`, `MasterCard`, dan `Maestro`.
- Diterjemahkan dalam banyak bahasa, termasuk Bahasa Indonesia.
- Memiliki desain yang *responsive*, sehingga dapat dibuka menggunakan *device* apapun.
- Memiliki lebih dari tiga ratus fitur untuk memudahkan pengguna.
- Banyak pengguna yang berkontribusi pada *discussion boards* dan sejenisnya, sehingga masalah yang dihadapi pengguna dapat cepat terselesaikan.

Tentu saja, sebuah aplikasi pasti memiliki kekurangan. Kekurangan yang dimiliki **Prestashop** antara lain :
- Penggunaan fitur atau modul yang lengkap menyebakan proses loading dari aplikasi ini menjadi sangat lambat
- Penggunaan *resource* memory aplikasi ini cukup besar, terutama ketika menggunakan fitur atau modul yang lengkap.
- Sebagian besar modul dan tema yang tersedia tidak gratis.

Jika dibandingkan dengan CMS sejenisnya seperti **Microweber**, CMS ini memiliki beberapa keunggulan dan kelemahan. Berikut adalah beberapa perbandingan antara kedua CMS ini :
- **Microweber** menyediakan proses design yang fleksibel dengan fitur *Drag and Drop* tanpa batasan, sehingga pengguna bebas mengkreasikan tampilan websitenya. Sedangkan **Prestashop** hanya menyediakan fitur design berupa penggantian template dan logo, adapun template yang tersedia tidak gratis.
- Modul atau plugin yang tersedia pada **Prestashop** jauh lebih banyak dibandingkan pada **Microweber**.
- **Prestashop** memiliki pengguna yang jauh lebih banyak daripada **Microweber** yang aktif pada forum-forum diskusi untuk membantu pengguna pemula.
- **Microweber** lebih ringan daripada **Prestashop** karena modulnya yang sedikit.
- Proses instalasi **Prestashop** lebih mudah karena berbasis PHP saja, sedangkan **Microweber** menggunakan framework laravel sehingga proses instalasi lebih sulit, terutama dalam hal *dependency*.



# Referensi
[`^ kembali ke atas ^`](#)

1. [About PrestaShop](https://www.prestashop.com/) - PrestaShop
2. [How to Log Into a VPS with PuTTY on Windows](https://www.digitalocean.com/community/tutorials/how-to-log-into-a-vps-with-putty-windows-users) - DigitalOcean
3. [How to Install PrestaShop on Ubuntu 16.04](http://idroot.net/linux/install-prestashop-ubuntu-16-04/) - idroot
4. [One Click Install PrestaShop](https://www.prestashop.com/blog/en/how-to-install-prestashop/) - PrestaShop
5. [PrestaShop Review](http://whichshoppingcart.com/prestashop.html) - whishshoppingcart
