# Sensor pada C++ Arduino

Sensor adalah perangkat yang digunakan untuk mendeteksi dan mengukur perubahan dalam lingkungan fisik, seperti cahaya, suhu, kelembaban, tekanan, dan banyak lagi. Dengan menggunakan sensor, kita dapat membuat proyek Arduino yang dapat merespons lingkungan sekitarnya.

## Jenis-Jenis Sensor

### 1. Sensor Cahaya (LDR)

LDR (Light Dependent Resistor) adalah sensor yang mengukur intensitas cahaya. Nilai resistansinya berubah sesuai dengan intensitas cahaya yang diterimanya.

### Contoh Menggunakan LDR

```cpp
int ldrPin = A0; // Pin untuk LDR
int ldrValue = 0; // Variabel untuk menyimpan nilai LDR

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
}

void loop() {
  ldrValue = analogRead(ldrPin); // Membaca nilai dari LDR
  Serial.print("LDR Value: ");
  Serial.println(ldrValue); // Mencetak nilai LDR ke Serial Monitor
  delay(1000); // Menunggu selama 1 detik
}
```

### 2. Sensor Suhu (LM35)

LM35 adalah sensor suhu yang memberikan output tegangan yang sebanding dengan suhu dalam derajat Celcius.

### Contoh Menggunakan LM35

```cpp
int tempPin = A1; // Pin untuk LM35
float tempValue = 0; // Variabel untuk menyimpan nilai suhu

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
}

void loop() {
  int sensorValue = analogRead(tempPin); // Membaca nilai dari sensor suhu
  tempValue = sensorValue * 0.48828125; // Mengonversi nilai analog ke suhu dalam derajat Celcius
  Serial.print("Temperature: ");
  Serial.print(tempValue);
  Serial.println(" C"); // Mencetak nilai suhu ke Serial Monitor
  delay(1000); // Menunggu selama 1 detik
}
```

### 3. Sensor Jarak (Ultrasonik)

Sensor ultrasonik digunakan untuk mengukur jarak menggunakan gelombang ultrasonik. Salah satu sensor ultrasonik yang umum digunakan adalah HC-SR04.

### Contoh Menggunakan Sensor Ultrasonik HC-SR04

```cpp
#define trigPin 9
#define echoPin 10

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  pinMode(trigPin, OUTPUT); // Mengatur pin trig sebagai output
  pinMode(echoPin, INPUT);  // Mengatur pin echo sebagai input
}

void loop() {
  long duration, distance;
  
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2); 
  
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  
  duration = pulseIn(echoPin, HIGH);
  
  distance = (duration / 2) / 29.1; // Menghitung jarak dalam cm
  
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm"); // Mencetak jarak ke Serial Monitor
  
  delay(1000); // Menunggu selama 1 detik
}
```

### Contoh Program Lengkap

Berikut adalah contoh program lengkap yang menggunakan beberapa sensor untuk membuat proyek interaktif.

```cpp
#define trigPin 9
#define echoPin 10
int ldrPin = A0; // Pin untuk LDR
int tempPin = A1; // Pin untuk LM35

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  pinMode(trigPin, OUTPUT); // Mengatur pin trig sebagai output
  pinMode(echoPin, INPUT);  // Mengatur pin echo sebagai input
}

void loop() {
  int ldrValue = analogRead(ldrPin); // Membaca nilai dari LDR
  Serial.print("LDR Value: ");
  Serial.println(ldrValue); // Mencetak nilai LDR ke Serial Monitor

  int tempSensorValue = analogRead(tempPin); // Membaca nilai dari sensor suhu
  float tempValue = tempSensorValue * 0.48828125; // Mengonversi nilai analog ke suhu dalam derajat Celcius
  Serial.print("Temperature: ");
  Serial.print(tempValue);
  Serial.println(" C"); // Mencetak nilai suhu ke Serial Monitor
  
  long duration, distance;
  
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2); 
  
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  
  duration = pulseIn(echoPin, HIGH);
  
  distance = (duration / 2) / 29.1; // Menghitung jarak dalam cm
  
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm"); // Mencetak jarak ke Serial Monitor
  
  delay(1000); // Menunggu selama 1 detik
}
```

## Kesimpulan

Sensor adalah komponen penting dalam proyek Arduino yang memungkinkan kita mendeteksi dan mengukur perubahan dalam lingkungan fisik. Dengan menggunakan berbagai jenis sensor seperti LDR, LM35, dan sensor ultrasonik, kita dapat membuat proyek yang lebih interaktif dan responsif terhadap lingkungan sekitarnya.