# Modul 1 - Vagrant

#### Disusun oleh :
	Yosua Nove P        5113100071
	Nadia Zhafirah U    5113100087

### Soal Tugas
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

#### Sebelum mengerjakan jawaban, lakukan instalasi Virtualbox, Vagrant, dan membuat virtualisasi seperti yang ada di modul Cloud. 

### Jawaban

#### No. 3

1. Buatlah folder baru untuk meletakkan konfigurasi.

	`mkdir vagrant_3`
2. Masuk ke dalam folder yang telah di buat.

	`cd vagrant_3`
3. Inisialisasi projek vagrant

	`vagrant init`
4. Download **Vagrant Box** dengan cara

	`vagrant box add hashicorp/precise64`
5. Pilih **virtual box**, kemudian ubah

		config.vm.box = "base"
	menjadi
		config.vm.box = "hashicorp/precise64"
   Simpan file Vagrantfile.
6. Uncomment konfigurasi

		config.vm.provider "virtualbox" do |vb|
		   # Display the VirtualBox GUI when booting the machine
		   # vb.gui = true
		
		   # Customize the amount of memory on the VM:
			vb.memory = "1024"
		end
7. Tambahkan 

	`vb.cpus = 2`
	pada baris sebelum **end**.
8. 