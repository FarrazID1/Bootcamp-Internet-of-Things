## Menggunakan `millis()` pada C++ Arduino

`millis()` adalah fungsi yang digunakan untuk mengambil waktu dalam milisecond (ms) sejak Arduino mulai berjalan. Fungsi ini berguna untuk membuat penundaan (delay) tanpa memblokir program, yang memungkinkan Anda untuk menjalankan tugas lain selama menunggu.

### Contoh Penggunaan `millis()`

```cpp
unsigned long previousMillis = 0;  // Waktu sebelumnya
const long interval = 1000;        // Interval dalam milisecond (misalnya, 1000ms = 1 detik)

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
}

void loop() {
  unsigned long currentMillis = millis(); // Waktu saat ini
  
  if (currentMillis - previousMillis >= interval) {
    // Simpan waktu terakhir saat ini
    previousMillis = currentMillis;

    // Lakukan tugas yang diinginkan
    Serial.println("Hello, World!");
  }
}
```

Pada contoh di atas, millis() digunakan untuk membuat interval waktu 1 detik. Setiap 1 detik, pesan "Hello, World!" akan dicetak ke Serial Monitor.

## Kesimpulan

- Tidak memblokir program: Dibandingkan dengan delay(), penggunaan millis() memungkinkan program untuk menjalankan tugas lain selama menunggu.
- Akurasi waktu: Fungsi ini memberikan waktu dalam milisecond yang sangat akurat, yang berguna untuk jadwal tugas atau pengukuran waktu yang presisi.