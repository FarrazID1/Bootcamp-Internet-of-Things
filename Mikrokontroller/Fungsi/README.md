# Fungsi pada C++ Arduino

Fungsi adalah blok kode yang dirancang untuk melakukan tugas tertentu. Penggunaan fungsi mempermudah pembacaan, pemeliharaan, dan pengembangan program dengan memungkinkan kita untuk memecah kode menjadi bagian-bagian yang lebih kecil dan terorganisir.

## Definisi dan Deklarasi Fungsi

Fungsi pada C++ Arduino didefinisikan dengan menyebutkan tipe nilai balik, nama fungsi, parameter (jika ada), dan tubuh fungsi yang berisi kode yang akan dieksekusi.

### Sintaks

```cpp
tipe_nilai_balik namaFungsi(parameter1, parameter2, ...) {
  // Blok kode yang akan dieksekusi
  return nilai;
}
```
## Contoh Fungsi Sederhana

Berikut adalah contoh fungsi sederhana yang menjumlahkan dua angka dan mengembalikan hasilnya.

### Contoh Fungsi Sederhana

```cpp
int tambah(int a, int b) {
  int hasil = a + b;
  return hasil;
}
```
## Fungsi Void

Fungsi void tidak mengembalikan nilai. Fungsi ini digunakan ketika kita hanya perlu mengeksekusi sekumpulan perintah tanpa mengembalikan hasil.

### Contoh Fungsi Void

```cpp
void nyalakanLED(int pin) {
  digitalWrite(pin, HIGH);
}
```

## Fungsi dengan Parameter

Fungsi dapat menerima parameter yang digunakan sebagai input untuk operasi di dalam fungsi tersebut. Parameter ditentukan dalam tanda kurung setelah nama fungsi.

### Contoh Fungsi dengan Parameter

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int hasil = tambah(5, 3); // Memanggil fungsi tambah dengan parameter 5 dan 3
  Serial.println(hasil); // Mencetak hasil penjumlahan
  delay(1000); // Menunggu selama 1 detik
}

int tambah(int a, int b) {
  int hasil = a + b;
  return hasil;
}
```

## Contoh Program Lengkap

Berikut adalah contoh program lengkap yang menggunakan beberapa fungsi untuk mengontrol LED berdasarkan input sensor.

```cpp
int sensorPin = A0; // Pin untuk sensor
int ledPin = 13;   // Pin untuk LED

void setup() {
  pinMode(ledPin, OUTPUT); // Mengatur pin LED sebagai output
  Serial.begin(9600);      // Memulai komunikasi serial
}

void loop() {
  int sensorValue = bacaSensor(sensorPin); // Membaca nilai dari sensor
  tampilkanNilai(sensorValue);             // Menampilkan nilai sensor
  kontrolLED(sensorValue, ledPin);         // Mengontrol LED berdasarkan nilai sensor
  delay(1000);                             // Menunggu selama 1 detik
}

int bacaSensor(int pin) {
  int nilai = analogRead(pin); // Membaca nilai analog dari sensor
  return nilai;
}

void tampilkanNilai(int nilai) {
  Serial.print("Sensor Value: ");
  Serial.println(nilai); // Mencetak nilai sensor ke Serial Monitor
}

void kontrolLED(int nilaiSensor, int pin) {
  if (nilaiSensor > 500) {
    digitalWrite(pin, HIGH); // Menyalakan LED jika nilai sensor lebih dari 500
  } else {
    digitalWrite(pin, LOW);  // Mematikan LED jika nilai sensor 500 atau kurang
  }
}
```

## Kesimpulan

Fungsi adalah fitur penting dalam pemrograman Arduino yang memungkinkan kita memecah program menjadi bagian-bagian yang lebih kecil dan terorganisir. Dengan menggunakan fungsi, kita dapat meningkatkan keterbacaan dan pemeliharaan kode, serta memudahkan pengembangan lebih lanjut.