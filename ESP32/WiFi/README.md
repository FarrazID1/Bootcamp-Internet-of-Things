# Menggunakan WiFi pada ESP32 dengan C++ Arduino

ESP32 adalah mikrokontroler yang sangat kuat dan mendukung konektivitas WiFi, menjadikannya pilihan populer untuk proyek IoT. Dalam panduan ini, kita akan mempelajari cara menghubungkan ESP32 ke jaringan WiFi menggunakan C++ di Arduino IDE.

## Instalasi Library yang Diperlukan

Untuk menggunakan WiFi dengan ESP32 di Arduino IDE, Anda perlu menginstal library `WiFi` yang sudah termasuk dalam ESP32 core.

## Contoh Kode WiFi pada ESP32

Berikut adalah contoh kode untuk menghubungkan ESP32 ke jaringan WiFi:

```cpp
#include <WiFi.h>

const char ssid[] = "nama_jaringan_wifi";
const char pass[] = "kata_sandi_wifi";

void setup() {
  Serial.begin(115200);

  // Memulai koneksi WiFi
  WiFi.begin(ssid, pass);

  Serial.print("Menghubungkan ke WiFi...");
  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(1000);
  }

  Serial.println("\nTerhubung ke WiFi!");
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void loop() {
  // Tidak ada yang dilakukan di loop
}
```

## Kesimpulan

- Konektivitas Nirkabel: Memungkinkan ESP32 untuk terhubung ke internet atau jaringan lokal tanpa kabel.
- Mudah Dikonfigurasi: Hanya membutuhkan beberapa baris kode untuk menginisialisasi dan mengelola koneksi WiFi.
- Kompatibilitas yang Luas: Dapat digunakan dengan berbagai perangkat dan platform IoT.