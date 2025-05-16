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