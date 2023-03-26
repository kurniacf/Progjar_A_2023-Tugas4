# Tugas 4 Pemrograman Jaringan
- Nama: Kurnia Cahya Febryanto
- NRP: 5025201073
- Kelas: Pemrograman Jaringan A

## Daftar Isi
- [Deskripsi](#deskripsi)
    - [1. Upload File](#1-upload-file) 


## Deskripsi
Pada file server protocol (progjar4a), tambahkan kemampuan
### 1. Upload File
- Untuk menambahkan `Upload` pada program, maka pada perlu penambahan beberapa fungsi program di beberapa file yang diperlukan.
- Pada file `file_interface.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227750855-60294d29-db2a-49f2-9513-69ada2937369.png" width="500"/> </br>
Fungsi ini menerima parameter yaitu nama file (`filename`) dan isi konten dari file yang telah di encode dalam Base64. Setelah itu, melakukan open file dan membaca file tersebut. Jika aman, maka akan diupload.

- Pada file `file_protocol.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751061-9e3836a5-6ef2-4433-88fe-c93c96311593.png" width="300"/> </br>
Pada bagian ini, terjadi pengecekan terhadap request `upload` yang diterima oleh server.

- Pada file `file_client_cli.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751091-7b39f241-7fbb-494b-95cf-40deaa69bbf7.png" width="300"/> </br>
Fungsi ini digunakan untuk mengupload file ke server secara remote. Dalam fungsi ini, menerima satu argumen yaitu `filename` yang merupakan nama file yang akan diunggah. Kemudian membuat string ‘<b>UPLOAD</b>’ untuk mengirim ke server. Jika status OK maka sukses dan mengembalikan nilai <b>TRUE</b>. Jika gagal maka akan return <b>FALSE</b>.

### 2. Hapus File
- Untuk menambahkan `Delete` pada program, maka pada perlu penambahan beberapa fungsi program di beberapa file yang diperlukan.
- Pada file `file_interface.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751141-740851a4-f8c4-4b30-bf33-90e1839a646e.png" width="500"/> </br>
Fungsi ini digunakan untuk menghapus file yang ada di server dengan menerima argumen `params` yang berisikan nama file yang akan dihapus. Menggunakan `os.remove()` untuk melakukan hapus file. Setelah itu, jika OK maka file berhasil dihapus. 

- Pada file `file_protocol.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751163-7c17f673-066e-48a3-978d-ed79b5bb7484.png" width="300"/> </br>
Pada bagian ini berfungsi untuk menjalankan fungsi delete ketika ada perintah dari client untuk melakukan delete.

- Pada file `file_client_cli.py`, dilakukan penambahan kode program sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751184-0c44aecd-4be4-46ad-9cd7-895e8019c83b.png" width="300"/> </br>
Pada fungsi ini digunakan untuk menghapus file secara remote pada server. Dalam fungsi ini, menerima satu argumen yaitu `filename` yang merupakan nama file yang akan dihapus. Kemudian membuat string ‘<b>DELETE</b>’ untuk dikirimkan ke server. Jika status OK maka akan mengembalikan <b>TRUE</b> dan berlaku sebaliknya.

## Implementasi Operasi Server & Client
- Untuk file yang akan saya lakukan percobaan upload, saya membuat file `test.txt` sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751227-d50d600b-85c7-4ab5-b243-e47885ad3c73.png" width="500"/> 

- Untuk file-file yang ada di folder `files` adalah sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751259-17facf9e-30f5-4484-8c9a-eb8aa07af419.png" width="300"/> 

- Pada terminal 1, jalankan server dengan perintah `python3 file_server.py` sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751278-3b451552-3e66-4dad-a58b-d527e475359b.png" width="500"/>

- Pada terminal 2, jalankan `client` dengan perintah `python3 file_client_cli.py`, maka menghasilkan output sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751302-a81baa02-19cd-4aca-ac64-996c1fcb341d.png" width="500"/>

- Bisa dilihat pada terminal client, bahwa client dijalankan dan terhubung ke server pada address `0.0.0.0` dengan port `6666`. Pada hasil terminal juga dilakukan aksi oleh klien seperti mengambil file (GET), mengunggah file (UPLOAD), dan menghapus file (DELETE). 
- Pada terminal 1, lihat kembali terminal `server` dan memiliki ouput sebagai berikut: </br>
<img src="https://user-images.githubusercontent.com/70510279/227751328-4de5d66d-0e82-468e-a793-6009983d5ffb.png" width="500"/>

- Output yang ditampilkan menunjukkan bahwa server telah dijalankan dan mendengarkan request dari client. Proses yang diterima oleh server dari klien yaitu <b>LIST</b>, <b>GET</b>, <b>UPLOAD</b>, dan <b>DELETE</b>.
- Dari hasil yang dilakukan, bisa dilihat pada folder `files` bahwa mengalami perubahan isi yaitu file dengan nama `test.txt` diunggah sehingga berhasil ditambahkan ke dalam folder files. Kemudian file `mountain.jpg` berhasil dihapus sehingga tidak ada di dalam folder files. </br>
<img src="https://user-images.githubusercontent.com/70510279/227751364-5ec31ebd-9956-4531-8d78-c4d02e58aca2.png" width="300"/>
