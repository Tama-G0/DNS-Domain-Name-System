# Tugas-Jaringan 1
TugasKomunikasi dan Jaringan

## 1. Clone Dari Github
Clone socket dari github dengan link https://github.com/ferryastika/socket-programming-simple-server-and-client

## 2. Jalankan Program
1. Buka app terminal
2. Masuk ke direktori cd socket-programing-simple-server-and-client
3. Jalankan perintah make
4. Jalankan perintah ./server
5. Jalankan perintah ./client
   
![Screenshot from 2024-11-25 19-36-47](https://github.com/user-attachments/assets/48d274fc-60bf-4f22-a267-7b011cffdf84)

6. Kirim plaintext ke server
7. Kemudian kita terminate app client, Ctrl+C

![Screenshot from 2024-11-25 19-36-52](https://github.com/user-attachments/assets/4d0c86f3-64af-4dae-b78b-e87a954df130)


## 3. Analisis Wireshark

1. Jalankan perintah sudo wireskark untuk membuka aplikasi Wireshark
2. Pilih loopback: lo

![Screenshot from 2024-11-25 19-37-55](https://github.com/user-attachments/assets/2a7dd10e-8488-488a-a120-32a88eb638a6)

3. Klik kanan lalu pilih follow TCP Stream

![Screenshot from 2024-11-25 19-40-01](https://github.com/user-attachments/assets/40697b1d-f269-45e7-888e-aca1eec75944)

4. Maka aplikasi Wireshark hanya akan menampilkan packet TCP yang di stream saja
5. Kemudian pilih menu Statistic -> Flow Graph
6. Tampil hasil Flow Graph TCP. Centang Limit to display filter. Flow type: TCP FLows
   
![Screenshot from 2024-11-25 19-39-47](https://github.com/user-attachments/assets/12c5282e-4067-4a7f-afc5-f265a24e82f4)

