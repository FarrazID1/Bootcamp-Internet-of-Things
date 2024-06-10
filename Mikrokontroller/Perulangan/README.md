# Perulangan pada C++ Arduino

Perulangan adalah konsep penting dalam pemrograman yang memungkinkan kita untuk mengeksekusi blok kode berulang kali. Dalam C++ pada Arduino, kita menggunakan pernyataan `for`, `while`, dan `do-while` untuk mengimplementasikan perulangan.

## Pernyataan For

Pernyataan `for` digunakan untuk mengeksekusi blok kode sejumlah tertentu. Biasanya digunakan ketika jumlah iterasi sudah diketahui sebelumnya.

### Sintaks

```cpp
for (inisialisasi; kondisi; iterasi) {
  // Blok kode yang akan dieksekusi
}
```

### Contoh

```cpp
void setup() {
  Serial.begin(9600);
  for (int i = 0; i < 10; i++) {
    Serial.println(i); // Mencetak nilai i dari 0 hingga 9
  }
}

void loop() {
  // Kosong
}
```
## Pernyataan While

Pernyataan while digunakan untuk mengeksekusi blok kode selama kondisi tertentu bernilai true.

### Sintaks

```cpp
while (kondisi) {
  // Blok kode yang akan dieksekusi
}
```

### Sintaks

```cpp
void setup() {
  Serial.begin(9600);
  int i = 0;
  while (i < 10) {
    Serial.println(i); // Mencetak nilai i dari 0 hingga 9
    i++;
  }
}

void loop() {
  // Kosong
}
```

## Pernyataan Do-While

Pernyataan do-while mirip dengan while, tetapi blok kode dieksekusi setidaknya sekali sebelum kondisi diuji.

### Sintaks

```cpp
do {
  // Blok kode yang akan dieksekusi
} while (kondisi);
```

### Contoh

```cpp
void setup() {
  Serial.begin(9600);
  int i = 0;
  do {
    Serial.println(i); // Mencetak nilai i dari 0 hingga 9
    i++;
  } while (i < 10);
}

void loop() {
  // Kosong
}
```

## Contoh Program Lengkap

Berikut adalah contoh program lengkap yang menggunakan berbagai jenis perulangan untuk mengontrol LED berdasarkan nilai sensor.

```cpp
int sensorPin = A0; // Pin untuk sensor
int ledPin = 13;   // Pin untuk LED

void setup() {
  pinMode(ledPin, OUTPUT); // Mengatur pin LED sebagai output
  Serial.begin(9600);      // Memulai komunikasi serial
}

void loop() {
  int sensorValue = analogRead(sensorPin); // Membaca nilai dari sensor
  Serial.print("Sensor Value: ");
  Serial.println(sensorValue); // Mencetak nilai sensor ke Serial Monitor

  // Menggunakan perulangan for untuk menyalakan dan mematikan LED
  for (int i = 0; i < 5; i++) {
    digitalWrite(ledPin, HIGH); // Menyalakan LED
    delay(500);                 // Menunggu selama 500 milidetik
    digitalWrite(ledPin, LOW);  // Mematikan LED
    delay(500);                 // Menunggu selama 500 milidetik
  }

  // Menggunakan perulangan while untuk menunggu nilai sensor tertentu
  while (sensorValue < 700) {
    sensorValue = analogRead(sensorPin); // Membaca nilai sensor
    Serial.print("Waiting for sensor value to exceed 700. Current value: ");
    Serial.println(sensorValue);
    delay(1000); // Menunggu selama 1 detik
  }

  // Menggunakan perulangan do-while untuk mematikan LED setidaknya sekali
  int i = 0;
  do {
    digitalWrite(ledPin, LOW);  // Mematikan LED
    delay(500);                 // Menunggu selama 500 milidetik
    i++;
  } while (i < 3);

  delay(1000); // Menunggu selama 1 detik sebelum mengulangi loop
}
```

## Kesimpulan

Perulangan adalah fitur penting dalam pemrograman Arduino yang memungkinkan kita mengeksekusi blok kode berulang kali. Dengan menggunakan pernyataan for, while, dan do-while, kita dapat mengontrol aliran program dan merespons berbagai kondisi dengan cara yang berbeda.