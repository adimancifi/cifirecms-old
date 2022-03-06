-------------------------------------------------------------
---            CiFireCMS - Makes You Feel Home            ---
-------------------------------------------------------------

CiFireCMS adalah platform CMS open source gratis Indonesia dibuat menggunakan framework CodeIgniter3. Dengan konsep yang menarik dan mudah digunakan oleh siapa saja.



-------------------------------------------------
---            PERSYARATAN SYSTEM             ---
-------------------------------------------------

Minimum System Requirements
+--------------+----------------+
|  System      |  Version       |
+--------------+----------------+
|  Web server  |  Apache 2.4.x  |
|  PHP         |  7.3.x, 5.6.x  |
|  MySQL       |  5.7.x         |
|  MariaDB     |  10.3.x        |
+--------------+----------------+

Ekstensi PHP.
+--------------+----------+
|  Extension   |  Config  |
+--------------+----------+
|  pdo_mysql   |  ON      |
|  pdo_sqlite  |  ON      |
|  pdo_sqlite  |  ON      |
|  json        |  ON      |
|  fileinfo    |  ON      |
|  intl        |  ON      |
+--------------+----------+



-------------------------------------------------
---                INSTALASI                  ---
-------------------------------------------------

1. Download source code CiFireCMS dari github https://github.com/CiFireCMS/cifirecms
2. Extract file "cifirecms.zip" di directory web Anda. Pastikan file ".htaccess" ter-copy dengan baik.
3. Buat database baru untuk menampung semua tabel konfigurasi CiFireCMS.
4. Jalankan browser dan masuk ke alamat web anda.
   Jika tidak ada kesalahan, anda akan langsung di arahkan ke halaman instalasi.
5. Ikuti dengan benar prosedur dan langkah-langkah instalasi.
6. Jika instalasi sudah selesai dan berhasil,
   jangan lupa untuk menghapus folder "install" dan file-file lainnya kecuali file "index.php" 
   dan ".htaccess".
7. CiFireCMS siap digunakan.




-------------------------------------------------
---           KONFIGURASI LANJUTAN            ---
-------------------------------------------------

## Permission
Ubah user permission folder-folder berikut menjadi 775.

folder-web-anda
├── content
│   ├── temp    --> 775
│   ├── thumbs  --> 775
└── └── uploads --> 775




-------------------------------------------------
---                 REDIRECT                  ---
-------------------------------------------------

Konfigurasi file ".htaccess" seperti berikut.

RewriteEngine On
RewriteCond $1 !^(index\.php|resources|robots\.txt)
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1 [L,QSA]


Untuk menentukan web anda di akses dengan alamat "http://" atau "https://" silahkan ubah konfigurasi file ".htaccess" dan tambahkan kode berikut di bawah baris kode "RewriteEngine On".


#- Redirect HTTP to HTTPS - non-www to www.

RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} !^www\. [NC]
RewriteCond %{HTTP_HOST} ^(?:www\.)?(.+)$ [NC]
RewriteRule ^ https://www.%1%{REQUEST_URI} [L,NE,R=301]


- Redirect HTTP to HTTPS - www to non-www.

RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteCond %{HTTP_HOST} ^(?:www\.)?(.+)$ [NC]
RewriteRule ^ https://%1%{REQUEST_URI} [L,NE,R=301]


- Redirect HTTPS to HTTP -  non-www to www.

RewriteCond %{HTTPS} on [OR]
RewriteCond %{HTTP_HOST} !^www\. [NC]
RewriteCond %{HTTP_HOST} ^(?:www\.)?(.+)$ [NC]
RewriteRule ^ http://www.%1%{REQUEST_URI} [L,NE,R=301]


- Redirect HTTPS to HTTP -  www to non-www.

RewriteCond %{HTTPS} on [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteCond %{HTTP_HOST} ^(?:www\.)?(.+)$ [NC]
RewriteRule ^ http://%1%{REQUEST_URI} [L,NE,R=301]





-------------------------------------------------
---                PRODUCTION                 ---
-------------------------------------------------

Jika web sudah siap di online-kan silahkan ubah kode pada "index.php"

- Cari baris kode berikut :
define('ENVIRONMENT', isset($_SERVER['CI_ENV']) ? $_SERVER['CI_ENV'] : 'development');

- Ubah menjadi seperti berikut :
define('ENVIRONMENT', isset($_SERVER['CI_ENV']) ? $_SERVER['CI_ENV'] : 'production');



-------------------------------------------------
---              AKSES HALAMAN                ---
-------------------------------------------------

- Login halaman administrator : http://nama-web-anda/l-admin
- Masukkan data login seperti yg telah diinputkan pada saat proses instalasi.

- Login halaman member : http://nama-web-anda/l-member
- Register member : http://nama-web-anda/l-member/register





-------------------------------------------------
---                   MAIL                    ---
-------------------------------------------------

 protocol    = SMTP
 smtp_host   = ssl://nama.smtp.host
 smtp_port   = 465
