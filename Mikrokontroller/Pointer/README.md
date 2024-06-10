# Pointer pada C++ Arduino

Pointer adalah variabel yang menyimpan alamat memori variabel lainnya. Dalam Arduino, penggunaan pointer dapat memungkinkan manipulasi memori yang lebih efisien dan fleksibel.

### Penggunaan Pointer

```cpp
int value = 5; // Variabel integer
int *ptr;      // Pointer ke integer

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  ptr = &value;       // Menetapkan alamat variabel value ke pointer ptr
}

void loop() {
  Serial.print("Value: ");
  Serial.println(value);       // Mencetak nilai variabel value
  Serial.print("Pointer: ");
  Serial.println(*ptr);        // Mencetak nilai yang ditunjuk oleh pointer ptr
  delay(1000);
}
```

Pada contoh di atas, pointer ptr menunjuk ke alamat memori variabel value. Dengan menggunakan operator dereference (*ptr), kita dapat mengakses nilai yang ditunjuk oleh pointer.

## Kesimpulan

- Efisiensi Memori: Pointer memungkinkan kita untuk mengakses dan memanipulasi nilai dengan langsung menggunakan alamat memori, menghemat memori dan waktu proses.
- Fleksibilitas: Penggunaan pointer memberikan fleksibilitas dalam manipulasi data dan struktur program yang lebih kompleks.

## Perhatian

- Keamanan Memori: Penggunaan pointer membutuhkan perhatian khusus terhadap manajemen memori untuk menghindari kesalahan akses dan kebocoran memori.
- Kompatibilitas: Beberapa mikrokontroler Arduino mungkin memiliki batasan dalam penggunaan pointer karena keterbatasan memori.