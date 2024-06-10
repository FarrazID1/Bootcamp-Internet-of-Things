# EEPROM pada C++ Arduino

EEPROM (Electrically Erasable Programmable Read-Only Memory) adalah bagian dari memori non-volatile yang tersedia di mikrokontroler Arduino. EEPROM dapat digunakan untuk menyimpan data secara permanen, yang tetap akan ada bahkan setelah daya Arduino dimatikan.

## Penggunaan EEPROM

EEPROM pada Arduino digunakan untuk menyimpan dan mengambil data secara permanen. Hal ini berguna untuk menyimpan pengaturan konfigurasi, nilai-nilai kalibrasi, atau data lain yang perlu dipertahankan meskipun daya Arduino dimatikan.

### Contoh Penggunaan EEPROM

```cpp
#include <EEPROM.h>

int address = 0; // Alamat awal EEPROM
int value = 10; // Nilai yang akan disimpan

void setup() {
  Serial.begin(9600); // Memulai komunikasi serial
  EEPROM.write(address, value); // Menyimpan nilai ke EEPROM
}

void loop() {
  int storedValue = EEPROM.read(address); // Membaca nilai dari EEPROM
  Serial.print("Stored Value: ");
  Serial.println(storedValue); // Mencetak nilai yang disimpan ke Serial Monitor
  delay(1000); // Menunggu selama 1 detik
}
```

Pada contoh di atas, nilai 10 disimpan di alamat 0 EEPROM pada saat setup, dan kemudian nilai tersebut dibaca dan dicetak di loop utama.

## Kesimpulan

EEPROM adalah komponen penting dalam mikrokontroler Arduino yang memungkinkan penyimpanan data secara permanen. Dengan EEPROM, kita dapat menyimpan konfigurasi, pengaturan, atau data lain yang perlu dipertahankan meskipun daya Arduino dimatikan.