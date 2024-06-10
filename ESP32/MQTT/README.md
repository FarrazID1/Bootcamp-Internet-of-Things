# Menggunakan MQTT pada ESP32 dengan C++ Arduino

MQTT (Message Queuing Telemetry Transport) adalah protokol pesan ringan yang ideal untuk perangkat IoT. ESP32 mendukung MQTT, memungkinkan perangkat untuk berkomunikasi melalui pesan yang diterima dari dan dikirim ke broker MQTT.

## Instalasi Library yang Diperlukan

Untuk menggunakan MQTT dengan ESP32 di Arduino IDE, Anda perlu menginstal dua library berikut:

1. `WiFi` - Sudah termasuk dalam ESP32 core.
2. `MQTT` - Dapat diinstal melalui Library Manager di Arduino IDE.

## Contoh Kode MQTT pada ESP32

Berikut adalah contoh kode lengkap untuk menghubungkan ESP32 ke jaringan WiFi dan broker MQTT, serta untuk mengirim dan menerima pesan MQTT.

```cpp
#include <WiFi.h>
#include <MQTT.h>

const char ssid[] = "ssid";
const char pass[] = "pass";

WiFiClient net;
MQTTClient client;

unsigned long lastMillis = 0;

void connect() {
  Serial.print("memeriksa wifi...");
  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(1000);
  }

  Serial.print("\nmenghubungkan...");
  while (!client.connect("arduino", "public", "public")) {
    Serial.print(".");
    delay(1000);
  }

  Serial.println("\nterhubung!");

  client.subscribe("hello");
}

void messageReceived(String &topic, String &payload) {
  Serial.println(topic + ": " + payload);
}

void setup() {
  Serial.begin(115200);

  // Memulai WiFi dan MQTT
  WiFi.begin(ssid, pass);
  client.begin("public.cloud.shiftr.io", net);
  client.onMessage(messageReceived);

  connect();
}

void loop() {
  client.loop();
  delay(10);

  // Memeriksa apakah terhubung
  if (!client.connected()) {
    connect();
  }

  // Mengirim pesan setiap satu detik
  if (millis() - lastMillis > 1000) {
    lastMillis = millis();
    client.publish("/hello", "world");
  }
}
```

## Kesimpulan

- Ringan: Protokol yang efisien dan hemat bandwidth.
- Asynchronous: Menggunakan mekanisme publish/subscribe yang membuat komunikasi lebih efisien.
- Skalabilitas: Dapat digunakan untuk berbagai perangkat IoT dari yang kecil hingga besar.