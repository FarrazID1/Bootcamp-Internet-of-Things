# Belajar Variabel pada C++ Arduino

Materi ini menjelaskan penggunaan variabel dalam pemrograman Arduino menggunakan C++. 

## Tipe Data Umum

1. `int`: Menyimpan bilangan bulat dari -32,768 hingga 32,767.
2. `long`: Menyimpan bilangan bulat lebih besar dari `int`, dari -2,147,483,648 hingga 2,147,483,647.
3. `float`: Menyimpan bilangan desimal.
4. `char`: Menyimpan karakter tunggal.
5. `boolean`: Menyimpan nilai `true` atau `false`.

## Deklarasi dan Inisialisasi Variabel

Deklarasi variabel adalah proses mendefinisikan nama dan tipe variabel tanpa memberikan nilai awal. Inisialisasi variabel adalah proses memberikan nilai awal pada saat deklarasi.

```cpp
int ledPin;        // Deklarasi variabel ledPin dengan tipe int
int sensorValue = 0; // Deklarasi dan inisialisasi variabel sensorValue dengan nilai 0
```

## Menggunakan Variabel dan Tipe Data dalam Program

Mari kita lihat contoh program sederhana yang menggunakan variabel untuk mengontrol LED pada Arduino.

```cpp
void setup() {
  // Inisialisasi komunikasi serial pada baud rate 9600
  Serial.begin(9600);
  
  // Deklarasi variabel dengan berbagai tipe data
  int integerVar = 42;          // Tipe data integer
  float floatVar = 3.14;        // Tipe data float
  char charVar = 'A';           // Tipe data char
  bool boolVar = true;          // Tipe data boolean
  String stringVar = "Hello!";  // Tipe data string

  // Mengirim nilai variabel ke Serial Monitor
  Serial.print("Nilai integer: ");
  Serial.println(integerVar);
  
  Serial.print("Nilai float: ");
  Serial.println(floatVar);
  
  Serial.print("Nilai char: ");
  Serial.println(charVar);
  
  Serial.print("Nilai boolean: ");
  Serial.println(boolVar);
  
  Serial.print("Nilai string: ");
  Serial.println(stringVar);
}

void loop() {
  // Tidak ada yang dilakukan dalam loop ini
}
```

```cpp
// Deklarasi dan inisialisasi variabel
int ledPin = 13;   // Pin dimana LED terhubung
int delayTime = 1000; // Waktu tunda dalam milidetik

void setup() {
  // Mengatur pin LED sebagai output
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Menyalakan LED
  digitalWrite(ledPin, HIGH);
  // Menunggu selama delayTime milidetik
  delay(delayTime);
  // Mematikan LED
  digitalWrite(ledPin, LOW);
  // Menunggu selama delayTime milidetik
  delay(delayTime);
}
```
Pada contoh di atas, kita menggunakan variabel ledPin untuk menyimpan nomor pin tempat LED terhubung dan delayTime untuk menyimpan waktu tunda dalam milidetik. Ini membuat kode lebih mudah dibaca dan dipelihara, karena kita bisa dengan mudah mengubah nilai-nilai tersebut tanpa perlu mencari dan mengganti setiap kemunculan di seluruh kode.

## Variabel Global dan Lokal

Variabel di Arduino dapat berupa global atau lokal:

- Variabel Global: Dideklarasikan di luar fungsi dan dapat diakses oleh semua fungsi dalam program.
- Variabel Lokal: Dideklarasikan di dalam fungsi dan hanya dapat diakses oleh fungsi tersebut.

Contoh Variabel Global dan Lokal:

```cpp
int globalVar = 5; // Variabel global

void setup() {
  int localVar = 10; // Variabel lokal
  Serial.begin(9600);
  Serial.println(globalVar); // Akses variabel global
  Serial.println(localVar);  // Akses variabel lokal
}

void loop() {
  // Hanya globalVar yang bisa diakses disini
  Serial.println(globalVar);
  // Serial.println(localVar); // Ini akan menghasilkan error karena localVar tidak dikenal di sini
}
```

## Kesimpulan 

Memahami penggunaan variabel sangat penting dalam pemrograman Arduino. Dengan menggunakan variabel, kita dapat membuat program yang lebih terstruktur, mudah dibaca, dan lebih mudah untuk dikelola.