# Pengkondisian pada C++ Arduino

Pengkondisian adalah konsep penting dalam pemrograman yang memungkinkan kita untuk membuat keputusan berdasarkan kondisi tertentu. Dalam C++ pada Arduino, kita menggunakan pernyataan `if`, `else if`, `else`, dan `switch case` untuk mengimplementasikan pengkondisian.

## Pernyataan If

Pernyataan `if` digunakan untuk mengeksekusi blok kode tertentu jika kondisi yang diberikan bernilai `true`.

### Sintaks

```cpp
if (kondisi) {
  // Blok kode yang akan dieksekusi jika kondisi bernilai true
}
```

```cpp
int sensorValue = analogRead(A0);

if (sensorValue > 500) {
  digitalWrite(13, HIGH); // Menyalakan LED jika nilai sensor lebih dari 500
}
```
## Pernyataan If-Else

Pernyataan if-else digunakan untuk mengeksekusi salah satu dari dua blok kode, tergantung pada apakah kondisi yang diberikan bernilai true atau false.

```cpp
if (kondisi) {
  // Blok kode yang akan dieksekusi jika kondisi bernilai true
} else {
  // Blok kode yang akan dieksekusi jika kondisi bernilai false
}
```

```cpp
int sensorValue = analogRead(A0);

if (sensorValue > 500) {
  digitalWrite(13, HIGH); // Menyalakan LED jika nilai sensor lebih dari 500
} else {
  digitalWrite(13, LOW); // Mematikan LED jika nilai sensor 500 atau kurang
}
```

## Pernyataan If-Else If-Else

Pernyataan if-else if-else digunakan untuk memeriksa beberapa kondisi. Blok kode pertama yang kondisinya bernilai true akan dieksekusi.

```cpp
if (kondisi1) {
  // Blok kode yang akan dieksekusi jika kondisi1 bernilai true
} else if (kondisi2) {
  // Blok kode yang akan dieksekusi jika kondisi2 bernilai true
} else {
  // Blok kode yang akan dieksekusi jika semua kondisi bernilai false
}
```

```cpp
int sensorValue = analogRead(A0);

if (sensorValue > 700) {
  digitalWrite(13, HIGH); // Menyalakan LED jika nilai sensor lebih dari 700
} else if (sensorValue > 300) {
  digitalWrite(13, LOW); // Mematikan LED jika nilai sensor antara 301 dan 700
} else {
  digitalWrite(13, LOW); // Mematikan LED jika nilai sensor 300 atau kurang
}
```

## Pernyataan Switch Case

Pernyataan switch case digunakan untuk memilih salah satu dari beberapa blok kode yang akan dieksekusi berdasarkan nilai variabel.

```cpp
switch (variabel) {
  case nilai1:
    // Blok kode yang akan dieksekusi jika variabel sama dengan nilai1
    break;
  case nilai2:
    // Blok kode yang akan dieksekusi jika variabel sama dengan nilai2
    break;
  // Tambahkan lebih banyak kasus sesuai kebutuhan
  default:
    // Blok kode yang akan dieksekusi jika tidak ada kasus yang cocok
}
```

```cpp
int mode = 2;

void setup() {
  pinMode(13, OUTPUT);
}

void loop() {
  switch (mode) {
    case 1:
      digitalWrite(13, HIGH); // Menyalakan LED jika mode adalah 1
      break;
    case 2:
      digitalWrite(13, LOW);  // Mematikan LED jika mode adalah 2
      break;
    default:
      digitalWrite(13, LOW);  // Mematikan LED jika tidak ada mode yang cocok
      break;
  }
}
```

## Contoh Program Lengkap

Berikut adalah contoh program lengkap yang menggunakan pengkondisian untuk mengontrol LED berdasarkan nilai sensor dan mode yang berbeda.

```cpp
int sensorPin = A0; // Pin untuk sensor
int ledPin = 13;   // Pin untuk LED
int mode = 0;      // Mode operasi

void setup() {
  pinMode(ledPin, OUTPUT); // Mengatur pin LED sebagai output
  Serial.begin(9600);      // Memulai komunikasi serial
}

void loop() {
  int sensorValue = analogRead(sensorPin); // Membaca nilai dari sensor
  Serial.print("Sensor Value: ");
  Serial.println(sensorValue); // Mencetak nilai sensor ke Serial Monitor

  if (sensorValue > 700) {
    mode = 1; // Set mode ke 1 jika nilai sensor lebih dari 700
  } else if (sensorValue > 300) {
    mode = 2; // Set mode ke 2 jika nilai sensor antara 301 dan 700
  } else {
    mode = 3; // Set mode ke 3 jika nilai sensor 300 atau kurang
  }

  switch (mode) {
    case 1:
      digitalWrite(ledPin, HIGH); // Menyalakan LED jika mode adalah 1
      break;
    case 2:
      digitalWrite(ledPin, LOW);  // Mematikan LED jika mode adalah 2
      break;
    case 3:
      digitalWrite(ledPin, LOW);  // Mematikan LED jika mode adalah 3
      break;
    default:
      digitalWrite(ledPin, LOW);  // Mematikan LED jika tidak ada mode yang cocok
      break;
  }

  delay(1000); // Menunggu selama 1 detik
}
```

## Kesimpulan

Pengkondisian adalah fitur penting dalam pemrograman Arduino yang memungkinkan kita membuat keputusan berdasarkan kondisi tertentu. Dengan menggunakan pernyataan if, else if, else, dan switch case, kita dapat mengontrol aliran program dan merespons berbagai kondisi dengan cara yang berbeda.