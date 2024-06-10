## Menggunakan FreeRTOS pada ESP32 dengan C++ Arduino

FreeRTOS adalah sistem operasi real-time yang populer dan banyak digunakan untuk mikrokontroler. Pada ESP32, FreeRTOS sudah terintegrasi dalam SDK-nya, dan kita dapat menggunakannya dalam lingkungan pengembangan Arduino. Dengan FreeRTOS, kita dapat menjalankan beberapa tugas (tasks) secara bersamaan, yang sangat berguna untuk aplikasi yang kompleks.

### Instalasi FreeRTOS pada ESP32

FreeRTOS sudah terintegrasi dengan ESP32 Arduino core, jadi Anda hanya perlu menginstal ESP32 board package melalui Board Manager di Arduino IDE. Berikut adalah langkah-langkahnya:

1. Buka Arduino IDE.
2. Buka `File > Preferences`.
3. Di bagian "Additional Board Manager URLs", tambahkan URL berikut: `https://dl.espressif.com/dl/package_esp32_index.json`.
4. Buka `Tools > Board > Boards Manager`.
5. Cari "ESP32" dan instal "esp32" by Espressif Systems.

### Contoh Penggunaan FreeRTOS pada ESP32

Berikut adalah contoh sederhana penggunaan FreeRTOS untuk menjalankan dua tugas (tasks) secara bersamaan pada ESP32:

```cpp
#include <Arduino.h>

// Deklarasi fungsi task
void Task1(void *pvParameters);
void Task2(void *pvParameters);

void setup() {
  // Memulai Serial Monitor
  Serial.begin(115200);
  
  // Membuat Task 1
  xTaskCreate(
    Task1,    // Fungsi Task 1
    "Task 1", // Nama Task 1
    1000,     // Ukuran stack (dalam kata)
    NULL,     // Parameter task
    1,        // Prioritas task
    NULL      // Handle task
  );

  // Membuat Task 2
  xTaskCreate(
    Task2,    // Fungsi Task 2
    "Task 2", // Nama Task 2
    1000,     // Ukuran stack (dalam kata)
    NULL,     // Parameter task
    1,        // Prioritas task
    NULL      // Handle task
  );
}

void loop() {
  // Tidak ada kode di loop, semua tugas dilakukan dalam tasks
}

// Implementasi Task 1
void Task1(void *pvParameters) {
  (void) pvParameters;
  for (;;) {
    Serial.println("Task 1 running");
    vTaskDelay(1000 / portTICK_PERIOD_MS); // Delay 1 detik
  }
}

// Implementasi Task 2
void Task2(void *pvParameters) {
  (void) pvParameters;
  for (;;) {
    Serial.println("Task 2 running");
    vTaskDelay(2000 / portTICK_PERIOD_MS); // Delay 2 detik
  }
}
```

Pada contoh di atas, kita membuat dua task sederhana yang berjalan secara bersamaan. Task pertama (Task1) mencetak "Task 1 running" setiap 1 detik, sedangkan task kedua (Task2) mencetak "Task 2 running" setiap 2 detik.

## Kesimpulan

- Multitasking: Kemampuan untuk menjalankan beberapa tugas secara bersamaan.
- Pengelolaan Waktu yang Efisien: Setiap tugas dapat memiliki prioritas dan waktu eksekusi yang diatur, membuat penggunaan waktu CPU lebih efisien.
- Komunikasi Antar Tugas: FreeRTOS menyediakan berbagai mekanisme untuk komunikasi antar tugas, seperti queues dan semaphores.