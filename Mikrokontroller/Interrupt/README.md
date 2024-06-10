# Menggunakan Interrupt pada C++ Arduino

Interrupt adalah fitur yang memungkinkan Arduino untuk merespons perubahan status pada pin tertentu dengan segera, bahkan saat sedang menjalankan tugas lain. Ini berguna untuk menanggapi peristiwa luar biasa yang memerlukan penanganan segera, seperti sinyal dari sensor atau tombol.

### Penggunaan Interrupt

```cpp
const int buttonPin = 2;  // Pin untuk tombol
volatile int buttonState = LOW; // Status tombol (volatile digunakan untuk menyatakan variabel dapat berubah di luar kendali program utama)

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  pinMode(buttonPin, INPUT_PULLUP); // Mengatur pin tombol sebagai input dengan pull-up resistor
  attachInterrupt(digitalPinToInterrupt(buttonPin), buttonISR, CHANGE); // Mengaitkan fungsi interrupt ke pin tombol
}

void loop() {
  // Program utama dapat berjalan di sini
}

// Fungsi interrupt untuk menangani perubahan status tombol
void buttonISR() {
  buttonState = digitalRead(buttonPin); // Membaca status tombol
  Serial.print("Button State: ");
  Serial.println(buttonState); // Mencetak status tombol ke Serial Monitor
}
```

Pada contoh di atas, interrupt diatur pada pin 2 dan dipicu setiap kali ada perubahan (CHANGE) pada status tombol. Ketika interrupt terjadi, fungsi buttonISR() akan dipanggil untuk menangani perubahan status tombol.

## Kesimpulan

- Responsif: Interrupt memungkinkan Arduino untuk merespons peristiwa luar biasa dengan segera, tanpa harus menunggu dalam loop utama.
- Multitasking: Dengan menggunakan interrupt, Anda dapat menjalankan tugas-tugas berbeda secara bersamaan, meningkatkan efisiensi program.

## Perhatian

- Keselamatan Memori: Saat menggunakan interrupt, perhatikan penggunaan variabel global dan pembatasan waktu dalam fungsi interrupt untuk menghindari masalah stabilitas program.
- Kompabilitas: Tidak semua pin pada Arduino mendukung interrupt, dan beberapa pin memiliki fungsi khusus saat digunakan dengan interrupt.