# Menggunakan Kodular dengan ESP32

Kodular adalah platform pengembangan aplikasi mobile berbasis blok yang memungkinkan pengguna untuk membuat aplikasi Android tanpa menulis kode. Menggunakan Kodular bersama dengan ESP32 memungkinkan Anda untuk membangun aplikasi IoT yang terhubung dengan perangkat keras melalui protokol MQTT.

## Apa Itu Kodular?

Kodular adalah platform yang memungkinkan Anda untuk membuat aplikasi Android dengan antarmuka pengguna yang intuitif dan mudah digunakan. Anda dapat mengembangkan aplikasi dengan cara menggabungkan blok-blok visual yang merepresentasikan logika pemrograman.

## Apa Itu ESP32?

ESP32 adalah mikrokontroler yang kuat dengan kemampuan WiFi dan Bluetooth terintegrasi. ESP32 sering digunakan dalam proyek IoT karena kemampuannya untuk berkomunikasi dengan perangkat lain melalui jaringan nirkabel.

## Mengapa Menggunakan MQTT?

MQTT (Message Queuing Telemetry Transport) adalah protokol pesan ringan yang ideal untuk perangkat IoT. MQTT memungkinkan komunikasi yang andal dan efisien antara aplikasi Kodular dan perangkat ESP32.

## Langkah-langkah Menggunakan Kodular dengan ESP32

### 1. Akses dan Instalasi Kodular

1. Buka [Kodular](https://www.kodular.io) di browser Anda.
2. Daftar atau masuk dengan akun Anda.
3. Buat proyek baru untuk memulai pengembangan aplikasi Anda.

### 2. Mengunduh dan Memasang Ekstensi MQTT untuk Kodular

1. Unduh ekstensi MQTT untuk Kodular dari tautan berikut: [LibraryMQTTKodular](https://s.id/LibraryMQTTKodular).
2. Unggah ekstensi tersebut ke proyek Kodular Anda dengan cara:
    - Buka proyek Anda di Kodular.
    - Navigasi ke bagian "Ekstensi" dan pilih "Impor Ekstensi".
    - Pilih file ekstensi yang telah Anda unduh dan unggah.

### 3. Menyiapkan Aplikasi Kodular

1. Tambahkan komponen MQTT dari ekstensi yang diunggah ke layar aplikasi Anda.
2. Atur parameter koneksi MQTT seperti server, port, username, dan password sesuai dengan broker MQTT yang Anda gunakan.
3. Gunakan blok untuk berlangganan (subscribe) dan mengirim (publish) pesan ke topik yang sesuai dengan topik yang digunakan oleh ESP32.

### 4. Contoh Kode ESP32

Berikut adalah contoh kode ESP32 untuk menghubungkan ke jaringan WiFi dan broker MQTT, serta mengirim dan menerima pesan MQTT yang dapat dihubungkan dengan aplikasi Kodular:

```cpp
#include <WiFi.h>
#include <MQTT.h>

const char ssid[] = "nama_jaringan_wifi";
const char pass[] = "kata_sandi_wifi";

WiFiClient net;
MQTTClient client;

unsigned long lastMillis = 0;

void connect() {
  Serial.print("Menghubungkan ke WiFi...");
  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(1000);
  }

  Serial.print("\nMenghubungkan ke broker MQTT...");
  while (!client.connect("ESP32Client", "public", "public")) {
    Serial.print(".");
    delay(1000);
  }

  Serial.println("\nTerhubung!");

  client.subscribe("kodular/esp32");
}

void messageReceived(String &topic, String &payload) {
  Serial.println(topic + ": " + payload);
  // Tambahkan logika penanganan pesan di sini
}

void setup() {
  Serial.begin(115200);

  // Memulai koneksi WiFi dan MQTT
  WiFi.begin(ssid, pass);
  client.begin("public.cloud.shiftr.io", net);
  client.onMessage(messageReceived);

  connect();
}

void loop() {
  client.loop();
  delay(10);

  // Memeriksa apakah terhubung
  if (!client.connected()) {
    connect();
  }

  // Mengirim pesan setiap detik
  if (millis() - lastMillis > 1000) {
    lastMillis = millis();
    client.publish("kodular/esp32", "Hello from ESP32");
  }
}
```