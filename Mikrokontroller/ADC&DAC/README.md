# ADC, DAC, dan PWM pada C++ Arduino

ADC (Analog to Digital Converter), DAC (Digital to Analog Converter), dan PWM (Pulse Width Modulation) adalah komponen penting dalam Arduino yang memungkinkan kita berinteraksi dengan sinyal analog dan mengendalikan perangkat analog.

## PWM (Pulse Width Modulation)

PWM adalah teknik yang digunakan untuk menghasilkan sinyal analog menggunakan sinyal digital dengan mengatur lebar pulsa sinyal. Dalam konteks Arduino, PWM dapat digunakan untuk mengendalikan kecerahan LED atau kecepatan motor.

Dalam kode di atas, fungsi analogWrite() digunakan untuk mengatur kecerahan LED dengan mengubah lebar pulsa sinyal. Nilai yang diberikan ke analogWrite() berada dalam rentang 0 (mati) hingga 255 (maksimum kecerahan).

## ADC (Analog to Digital Converter)

ADC pada Arduino digunakan untuk mengubah sinyal analog menjadi sinyal digital. Ini memungkinkan kita untuk membaca nilai dari sensor analog seperti suhu, cahaya, atau jarak.

### Contoh Penggunaan ADC

```cpp
int sensorPin = A0; // Pin untuk sensor analog
int sensorValue = 0; // Variabel untuk menyimpan nilai sensor

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
}

void loop() {
  sensorValue = analogRead(sensorPin); // Membaca nilai dari sensor analog
  Serial.print("Sensor Value: ");
  Serial.println(sensorValue); // Mencetak nilai sensor ke Serial Monitor
  delay(1000); // Menunggu selama 1 detik
}
```
## DAC (Digital to Analog Converter)

DAC pada Arduino digunakan untuk mengubah sinyal digital menjadi sinyal analog. Meskipun Arduino Uno tidak memiliki DAC bawaan, kita dapat menggunakan PWM (Pulse Width Modulation) untuk mensimulasikan sinyal analog.

### Contoh Penggunaan PWM sebagai DAC

```cpp
int ledPin = 9; // Pin untuk LED
int brightness = 0; // Variabel untuk kecerahan LED

void setup() {
  pinMode(ledPin, OUTPUT); // Mengatur pin LED sebagai output
}

void loop() {
  for (int i = 0; i <= 255; i++) {
    brightness = i; // Mengatur kecerahan LED
    analogWrite(ledPin, brightness); // Mengatur PWM untuk mengendalikan kecerahan LED
    delay(10); // Menunggu sebentar sebelum meningkatkan kecerahan
  }
  for (int i = 255; i >= 0; i--) {
    brightness = i; // Mengatur kecerahan LED
    analogWrite(ledPin, brightness); // Mengatur PWM untuk mengendalikan kecerahan LED
    delay(10); // Menunggu sebentar sebelum mengurangi kecerahan
  }
}
```

## Contoh Program Lengkap Menggunakan ADC dan PWM

Berikut adalah contoh program lengkap yang menggunakan ADC untuk membaca nilai dari sensor LDR dan menggunakan PWM sebagai DAC untuk mengendalikan kecerahan LED.

```cpp
int ldrPin = A0; // Pin untuk sensor LDR
int ledPin = 9;  // Pin untuk LED
int brightness = 0; // Variabel untuk kecerahan LED

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  pinMode(ledPin, OUTPUT); // Mengatur pin LED sebagai output
}

void loop() {
  int sensorValue = analogRead(ldrPin); // Membaca nilai dari sensor LDR
  Serial.print("LDR Value: ");
  Serial.println(sensorValue); // Mencetak nilai sensor ke Serial Monitor
  
  brightness = map(sensorValue, 0, 1023, 0, 255); // Mengonversi nilai sensor menjadi rentang PWM
  analogWrite(ledPin, brightness); // Mengatur PWM untuk mengendalikan kecerahan LED
  
  delay(1000); // Menunggu selama 1 detik sebelum mengulangi loop
}
```

## Kesimpulan

ADC dan DAC adalah fitur penting dalam Arduino yang memungkinkan kita untuk berinteraksi dengan dunia analog. Dengan menggunakan ADC, kita dapat membaca nilai dari sensor analog, sedangkan dengan menggunakan DAC (melalui PWM), kita dapat menghasilkan sinyal analog untuk mengendalikan perangkat seperti LED atau motor.