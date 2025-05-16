**Tutorial 9 Pemrograman Lanjut (Advanced Programming) 2024/2025 Genap**
* Nama    : Muhammad Almerazka Yocendra
* NPM     : 2306241745
* Kelas   : Pemrograman Lanjut - A

## Berapa banyak data yang terkirim oleh program publisher ke message broker?
Pada program _publisher_, terdapat 5 `publish_event`, dan setiap `publish_event` mengirimkan satu `UserCreatedEventMessage` yang berisi data seperti `user_id` dan `user_name` ke _message broker_. Oleh karena itu, dalam satu kali eksekusi program (satu _run_), program akan mengirimkan sebanyak 5 pesan ke _message broker_.

## Publisher dan Subscriber mengakses URL yang sama. Apa artinya?
URL `amqp://guest:guest@localhost:5672` menunjukkan bahwa baik _publisher_ maupun _subscriber_ terhubung ke _broker_ **RabbitMQ** yang sama, yang berjalan di mesin lokal, menggunakan protokol **AMQP**, dengan kredensial `default (guest:guest)` dan port **AMQP** `default (5672)`. Keduanya memanggil server **AMQP** yang sama dan berkomunikasi dengan _message broker_ yang sama. Dengan demikian, pesan yang dikirim oleh _publisher_ akan diterima oleh _subscriber_ yang juga terhubung ke server yang sama.

## Running RabbitMQ as Message Broker
![image](https://github.com/user-attachments/assets/efb59dc8-72d6-42e3-a48d-c18d90f848eb)

## Sending and Processing Event
![image](https://github.com/user-attachments/assets/5f81c570-9777-4728-aa2d-4b0d0aa7382f)

Pada gambar di atas, kita dapat melihat proses komunikasi antara _Publisher_ dan _Subscriber_ yang terhubung ke _Message Broker_ (**RabbitMQ**) yang berjalan di terminal pertama (paling bawah).

1. **Terminal Pertama** - Menjalankan **RabbitMQ** (_Message Broker_) :
Di terminal pertama, kita menjalankan **RabbitMQ** menggunakan perintah **Docker**. **RabbitMQ** berjalan pada port 5672 untuk **AMQP** (protokol komunikasi) dan port 15672
2. **Terminal Kedua** - Menjalankan _Publisher_ :
Di terminal kedua, _Publisher_ dijalankan menggunakan perintah `cargo run` dari project _publisher_. _Publisher_ mengirimkan data ke _message broker_ (**RabbitMQ**). Data yang dikirim adalah pesan dengan tipe `UserCreatedEventMessage` yang berisi informasi seperti `user_id` dan `user_name`
3. **Terminal Ketiga** - Menjalankan _Subscriber_ :
Di terminal ketiga, _Subscriber_ dijalankan menggunakan perintah `cargo run` dari project _subscriber_. _Subscriber_ mendengarkan dan menerima pesan yang dikirim oleh _Publisher_ melalui **RabbitMQ**.
    - Log pada terminal _subscriber_ menunjukkan bahwa setiap pesan yang diterima oleh _subscriber_ dicetak ke terminal. Setiap kali _Publisher_ mengirimkan data, _Subscriber_ menerima pesan dengan informasi pengguna yang berbeda, seperti `user_id` dan `user_name`.