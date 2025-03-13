# Pertemuan ke 2 <img src=https://seeklogo.com/images/E/elephpant-mascot-php-logo-4C78D1AC4E-seeklogo.com.png width="120px" >
 
 ## Profil
 |  |  |
 | -------- | --- |
 | **Nama** | Samuel Damatta Tindaon |
 | **Kelas** | TI.23.A.5 |
 | **NIM**  | 312310462 |
 | **Mata Kuliah** | Pemrograman Web 2 |
 
 # Praktikum 1: PHP Framework (Codeigniter)
 
 ## Langkah-langkah Praktikum
 ## Persiapan
 Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4.
 Berikut beberapa ekstensi yang perlu diaktifkan:
 * php-json ekstension untuk bekerja dengan JSON;
 * php-mysqlnd native driver untuk MySQL;
 * php-xml ekstension untuk bekerja dengan XML;
 * php-intl ekstensi untuk membuat aplikasi multibahasa;
 * libcurl (opsional), jika ingin pakai Curl.
 
 Untuk mengetahui ekstensi tersebut telah aktif atau belum, kita bisa mengetahui nya melalui powershell atau command prompt dengan cara:
 
 ### Catatan : mulai dari PHP 7.0, ekstensi JSON biasanya sudah termasuk secara bawaan.
 ![ekstensi](https://github.com/user-attachments/assets/6eada84d-9426-4e91-93cc-12e1ea580e37)

 
 Lalu kalian bisa mencari ekstensi yang kalian butuhkan, jika ada yang belum diaktivasi kalian dapat mengaktifkan ekstensi tersebut, melalu XAMPP Control Panel, pada bagian Apache
 klik Config -> PHP.ini :
![ekstensi2](https://github.com/user-attachments/assets/ff093a58-1cb5-4032-9e33-168ee69932a5)

 
 ![intl](https://github.com/user-attachments/assets/81acec29-018e-41f5-adb4-1e272b6f9887)

 * Contohnya disini extension=intl belum aktif, maka cara mengaktivasinya adalah dengan menghilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.
 
 ## Instalasi Codeigniter 4
 Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual
 dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.
 * Unduh Codeigniter dari website https://codeigniter.com/download
 * Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
 * Ubah nama direktory codeigniter4-framework-v4.x.xx menjadi ci4.
 * Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/
 
![localhost1](https://github.com/user-attachments/assets/4716aad2-6d0e-4d75-8eca-cbcd17f2cefb)

 
 ## Menjalankan CLI (Command Line Interface)
 Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka Shell pada XAMPP.
 
![Shell](https://github.com/user-attachments/assets/5a3cec5b-5f28-48c6-805c-367d32055ca9)

 
 Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (Contoh : cd htdocs/lab11_ci/ci4)
 
 Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:
 
 ### php spark
![spark](https://github.com/user-attachments/assets/82de5a27-563f-41eb-8f39-6c2c1492de97)

 
 ## Mengaktifkan Mode Debugging
 Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.
 
 Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut.
 
![Whoops](https://github.com/user-attachments/assets/ab571c36-7d4c-442e-936d-bc8f33e4dbe7)

 
 Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya,
 maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment
 variable CI_ENVIRONMENT menjadi development.
 ![development](https://github.com/user-attachments/assets/a2f2d739-2571-46d3-93c0-93cf331fec1a)

 
 Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable
 CI_ENVIRONMENT menjadi development.
 #### Catatan : Kadang, CodeIgniter tidak membaca file .env karena masih dikomentari, pastikan tidak ada tanda # di depan CI_ENVIRONMENT.
 
![error](https://github.com/user-attachments/assets/c2bf2cbd-cbeb-4253-a6b5-449314a037d2)

 
 Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
 app/Controller/Home.php hilangkan titik koma pada akhir kode return view('welcome_message').
 ![coba](https://github.com/user-attachments/assets/f75c944a-e671-4299-9a58-41b876b5a613)

 
 ## Memahami konsep MVC
 Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-
 Controller. MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan
 tampilan. Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan diletakkan pada direktori View.
 
 Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.
 
 Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun sumber lainnya.
 
 View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.
 
 Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian diproses dengan menghubungkan bagian model dan view.
 
 ## Routing dan Controller
 Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. Controller
 adalah class atau script yang bertanggung jawab merespon sebuah request.
 
 Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk
 meudian oleh router tesebut diarahkan ke Controller.
 
 Router terletak pada file app/config/Routes.php
![Routes](https://github.com/user-attachments/assets/9fa64af3-c588-44fd-a21b-2b7ed4834de2)

 
 Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
 Contoh:
 ```` python
 $routes->get('/', 'Home::index');
 ````
 Kode tersebut akan mengarahkan rute untuk halaman home.
 
 #### Membuat Route Baru.
 Tambahkan kode berikut di dalam Routes.php
 ```` python
 $routes->get('/about', 'Page::about');
 $routes->get('/contact', 'Page::contact');
 $routes->get('/faqs', 'Page::faqs');
 ````
 Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.
 
 php spark routes
![spark routes](https://github.com/user-attachments/assets/ff274791-e425-4426-a954-e45e80dcfee4)

 
 Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about
![404](https://github.com/user-attachments/assets/48a49800-dd39-4c9f-9017-876d8d8417e5)

 
 Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.
 
 #### Membuat Controller
 Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.
 
 ```` python
 <?php
 
 namespace App\Controllers;
 
 class Page extends BaseController
 {
     public function about()
     {
         echo "Ini halaman About";
     }
     public function contact()
     {
         echo "Ini halaman Contact";
     }
     public function faqs()
     {
         echo "Ini halaman FAQ";
     }
 }
 ````
 
 ![about](https://github.com/user-attachments/assets/58c151b5-a801-485f-a8fe-12557d1d15d4)

 
 #### Auto Routing
 Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.
 
 ```` python
 $routes->get('page/tos', 'Page::tos');
 $routes->setAutoRoute(true);
 ````
 
 Tambahkan method baru pada Controller Page seperti berikut.
 ```` python
 public function tos()
 {
     echo "ini halaman Term of Services";
 }
 ````
 
 Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos
![tos](https://github.com/user-attachments/assets/e87f152c-69b5-44f1-ba4f-4751b44a28fc)

 
 ### Membuat View
 Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori Views (app/Views/about.php) kemudian isi kodenya seperti berikut.
 ```` python
 <!DOCTYPE html>
 <html lang="en">
 
 <head>
     <meta charset="UTF-8">
     <title><?= $title; ?></title>
 </head>
 
 <body>
     <h1><?= $title; ?></h1>
     <hr>
     <p><?= $content; ?></p>
 </body>
 
 </html>
 ````
 
 Ubah method about pada class Controller Page menjadi seperti berikut:
 ``` python
     public function about()
     {
         return view('about', [
             'title' => 'Halaman About',
             'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
         ]);
     }
 ```
 
 Kemudian lakukan refresh pada halaman tersebut.
 
![About2](https://github.com/user-attachments/assets/6cb5a8aa-02bd-4d07-90fc-7a65f9a58367)

 
 ### Membuat Layout Web dengan CSS
 Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.
 
 Buat file css pada direktori public dengan nama style.css
 
 ![style](https://github.com/user-attachments/assets/8ec3ebd2-8e6c-45f6-a27c-d09d19645fdc)

 
 Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php
 
 File app/Views/template/header.php
 ```python
 <!DOCTYPE html>
 <html lang="en">
 
 <head>
     <meta charset="UTF-8">
     <title><?= $title; ?></title>
     <link rel="stylesheet" href="<?= base_url('/style.css'); ?>">
 </head>
 
 <body>
     <div id="container">
         <header>
             <h1>Layout Sederhana</h1>
         </header>
         <nav>
             <a href="<?= base_url('/'); ?>" class="active">Home</a>
             <a href="<?= base_url('/artikel'); ?>">Artikel</a>
             <a href="<?= base_url('/about'); ?>">About</a>
             <a href="<?= base_url('/contact'); ?>">Kontak</a>
         </nav>
         <section id="wrapper">
             <section id="main"></section>
 ```
 
 File app/Views/template/footer.php
 ```python
 </section>
 <aside id="sidebar">
     <div class="widget-box">
         <h3 class="title">Widget Header</h3>
         <ul>
             <li><a href="#">Widget Link</a></li>
             <li><a href="#">Widget Link</a></li>
         </ul>
     </div>
     <div class="widget-box">
         <h3 class="title">Widget Text</h3>
         <p>Vestibulum lorem elit, iaculis in nisl volutpat,
             malesuada tincidunt arcu. Proin in leo fringilla, vestibulum mi porta,
             faucibus felis. Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
     </div>
 </aside>
 </section>
 <footer>
     <p>&copy; 2021 - Universitas Pelita Bangsa</p>
 </footer>
 </div>
 </body>
 
 </html>
 ```
 
 Kemudian ubah file app/Views/about.php seperti berikut.
 ```python
 <?= $this->include('template/header'); ?>
 <h1><?= $title; ?></h1>
 <hr>
 <p><?= $content; ?></p>
 <?= $this->include('template/footer'); ?>
 ```
 
 Selanjutnya refresh tampilan pada alamat http://localhost:8080/about
 ![alt text](img/About3.png)
 
