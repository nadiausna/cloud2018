# Modul 1 - Vagrant

#### Disusun oleh :
	Yosua Nove P        5113100071
	Nadia Zhafirah U    5113100087

## Soal Tugas
1. Buat vagrant virtualbox dan buat user 'awan' dengan password 'buayakecil'.
2. Buat vagrant virtualbox dan lakukan provisioning install Phoenix Web Framework
3. Buat vagrant virtualbox dan lakukan provisioning install:
	1. php
	2. mysql
	3. composer
	4. nginx
	
	setelah melakukan provioning, clone https://github.com/fathoniadi/pelatihan-laravel.git pada folder yang sama dengan vagrantfile di komputer host. Setelah itu sinkronisasi folder pelatihan-laravel host ke vagrant ke **/var/www/web** dan jangan lupa install vendor laravel agar dapat dijalankan. Setelah itu setting root document nginx ke **/var/www/web**. webserver VM harus dapat diakses pada port 8080 komputer host dan mysql pada vm dapat diakses pada port 6969 komputer host
4. Buat vagrant virtualbox dan lakukan provisioning install:
	1. Squid proxy
	2. Bind9

#### Sebelum mengerjakan jawaban, lakukan instalasi Virtualbox, Vagrant, dan membuat virtualisasi seperti yang ada di modul Cloud. Pengerjaan jawaban hanya dimulai dalam kondisi siap menjalankan vagrant.

## Jawaban


### No. 2

1. Masuk ke direktori Vagrant via Terminal.
	
	`cd vagrant_2`
2. Jalankan virtualisasi.
	vagrant up

3. Masuk ke dalam virtualisasi.
	vagrant ssh

4. Tambahkan Erlang Solution repository
	wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && sudo dpkg -i erlang-solutions_1.0_all.deb

5. Run `sudo apt-get update`

6. Install Erlang/OTP platform dan semua aplikasinya

`sudo apt-get install esl-erlang`

7. Install Elixir: `sudo apt-get install elixir`


### No. 3
(Nama folder : vagrant3)

* Install php

1. Masuk ke direktori Vagrant via Terminal.
	
	`cd vagrant3`
2. Jalankan virtualisasi.

		vagrant up

3. Masuk ke dalam virtualisasi.

		vagrant ssh

4. Pada Terminal, masukkan:

		`apt-get install -y php5`
5. Untuk memeriksa apakah php sudah terinstall, ketik
	
	`php -m`
   Jika sudah terinstall akan muncul modul-modul dari php.


* Install mysql

1. Masuk ke direktori Vagrant via Terminal.
	
	`cd vagrant3`
2. Jalankan virtualisasi.

		vagrant up

3. Masuk ke dalam virtualisasi.

		vagrant ssh

4. Pada Terminal, masukkan:

		`apt-get install -y mysql-server`
5. Ketika muncul pop up password, masukkan password yang diinginkan.
6. Untuk memastikan apakah mysql telah terinstall, masukkan

	`mysql -u root -p`
   kemudian masukkan password yang sudah diinputkan sebelumnya.

7. Jika berhasil terinstall maka akan muncul penjelasan MySQL.


* Install nginx

1. Masuk ke direktori Vagrant via Terminal.
	
	`cd vagrant3`
2. Jalankan virtualisasi.

		vagrant up

3. Masuk ke dalam virtualisasi.

		vagrant ssh

4. Pada Terminal, masukkan:

		`apt-get install nginx`
5. Untuk memeriksanya, masukkan:

		'nginx -V'


* Install composer

1. Masuk ke direktori Vagrant via Terminal.
	
	`cd vagrant3`
2. Jalankan virtualisasi.

		vagrant up

3. Masuk ke dalam virtualisasi.

		vagrant ssh

4. Pada Terminal, install curl utility dengan cara

	`apt-get install curl`
5. Download installer dengan cara

	`curl -s https://getcomposer.org/install | php`
6. Pindahkan file **composer.phar** 

	mv composer.phar/ usr/local/bin/composer
7. Untuk memeriksanya, masukkan

	`composer -V`

##### Provisioning telah selesai dilakukan.

* Cara clone github

1. Buka Terminal, masukkan

	`git clone https://github.com/fathoniadi/pelatihan-laravel.git`

2. Sinkronisasikan folder dengan mengubah file Vagrantfile.
   Tambahkan

   		config.vm.synced_folder "pelatihan-laravel/", "/var/www/web"

   	setelah baris
   		
   		config.vm.synced_folder "src/", "/var/www"

3. Jalankan virtualisasi.
		
		vagrant up

4. Masuk ke dalam virtualisasi.
		
		vagrant ssh


* Cara setting root document nginx

1. Masuk ke dalam virtualisasi.
		
		vagrant ssh

2. Buka pengaturan default nginx, masukkan

	sudo nano /etc/nginx/sites-enabled/default

3. Pada file default, ubah
	
	root

   menjadi

   	root/var/www/web

   kemudian exit.


* Cara mengubah port webserver ke port 8080

1. Masuk ke dalam virtualisasi.
		
		vagrant ssh

2. Pada Terminal, masukkan

	sudo nano /etc/apache2/port-conf

3. Ubah `listen 80` menjadi `listen 8080`, close nano.

4. Cek pada browser dengan ketik "localhost:8080", maka akan keluar "welcome to nginx".


* Cara mengubah port MySQL ke port 6969

1. Buka Terminal, masukkan 

	sudo nano /etc/mysql/my-cnf

2. Ubah `port 3306` menjadi `port 6969`.

