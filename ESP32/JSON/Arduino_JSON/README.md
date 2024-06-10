## Menggunakan Arduino_JSON pada C++ Arduino

Arduino_JSON adalah sebuah library yang memungkinkan Arduino untuk berinteraksi dengan data dalam format JSON. Dengan Arduino_JSON, Anda dapat dengan mudah mengurai dan membuat data dalam format JSON, yang sering digunakan dalam berbagai aplikasi, seperti komunikasi antar perangkat lunak dan pengiriman data melalui protokol HTTP.

### Instalasi Arduino_JSON

Anda dapat menginstal Arduino_JSON melalui Arduino IDE Library Manager. Cukup cari "Arduino_JSON" di Library Manager, lalu instal versi terbaru.

### Penggunaan Arduino_JSON

Berikut adalah contoh penggunaan Arduino_JSON untuk mengurai dan membuat data JSON:

```cpp
#include <Arduino_JSON.h>

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  
  // Membuat objek JSON
  JSONVar obj;
  
  // Menambahkan data ke objek JSON
  obj["sensor"] = "temperature";
  obj["value"] = 25.5;

  // Mengonversi objek JSON menjadi string dan mencetaknya
  Serial.println(JSON.stringify(obj));

  // Mengurai string JSON menjadi objek JSON
  String jsonString = "{\"sensor\":\"humidity\",\"value\":60}";
  JSONVar parsedObj = JSON.parse(jsonString);

  // Mendapatkan nilai dari objek JSON yang diurai
  String sensor = parsedObj["sensor"];
  float value = parsedObj["value"];
  
  // Mencetak nilai yang diurai
  Serial.print("Sensor: ");
  Serial.println(sensor);
  Serial.print("Value: ");
  Serial.println(value);
}

void loop() {
  // Program utama dapat berjalan di sini
}
```

Pada contoh di atas, kita membuat objek JSON menggunakan JSONVar, menambahkan data ke objek tersebut, dan kemudian mengonversi objek JSON menjadi string menggunakan JSON.stringify(). Selanjutnya, kita mengurai string JSON menjadi objek JSON menggunakan JSON.parse() dan mendapatkan nilai dari objek JSON yang diurai.

## Kesimpulan

- Kemudahan Penggunaan: Arduino_JSON menyediakan antarmuka yang mudah digunakan untuk mengurai dan membuat data JSON di Arduino.
- Kompatibilitas: Library ini kompatibel dengan berbagai versi Arduino dan banyak platform mikrokontroler lainnya.
- Ringan dan Cepat: Arduino_JSON dirancang untuk memiliki ukuran memori yang kecil dan kinerja yang cepat.