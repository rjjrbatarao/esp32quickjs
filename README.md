# QuickJS Javascript Engine

- https://bellard.org/quickjs/
- https://github.com/bellard/quickjs

The main documentation is in doc/quickjs.pdf or doc/quickjs.html.

# Build with platform.io (ESP32)

Exampes: https://github.com/binzume/esp32quickjs-examples

### platformio.ini

add git url to `lib_deps`.

```ini
lib_deps = 
	https://github.com/binzume/esp32quickjs.git
```

### main.cpp

include `esp/QuickJS.h`.

```c++
#include <Arduino.h>
#include "esp/QuickJS.h"

static const char *jscode = R"CODE(
  console.log('Hello, JavaScript!');
)CODE";

M5QuickJS qjs;

void setup() {
  Serial.begin(115200);
  qjs.begin();
  qjs.exec(jscode);
}
```

# JavaScript API

- console.log(string)
- setTimeout(callback, ms) : int
- setInterval(callback, ms) : int
- clearTimeout(id)

`esp32` module

- esp32.millis() : int
- esp32.digitalRead(pin) : int
- esp32.digitalWrite(pin, value) // value=0: LOW, 1: HIGH
- esp32.pinMode(pin, mode) // mode=1: INPUT, 2: OUTPUT
- esp32.setLoop(func) // func is called every arduino loop().
- esp32.deepSleep(us) // not returns

if WiFi.h is included:

- esp32.isWifiConnected() : bool
- esp32.fetch(url, {method:string, body:string}): Promise<{body:string, status:int}>


# License

MIT License
