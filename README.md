# QuickJS Javascript Engine

- https://bellard.org/quickjs/
- https://github.com/bellard/quickjs

The main documentation is in doc/quickjs.pdf or doc/quickjs.html.

# Build with platform.io (ESP32)

platformio.ini

```ini
lib_deps = 
  ...
	https://github.com/binzume/esp32quickjs.git
```

main.cpp

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

# APIs



- console.log(string)
- setTimeout(callback, ms)
- setInterval(callback, ms)
- esp32.millis
- esp32.digitalRead(pin)
- esp32.digitalWrite(pin, value)
- esp32.pinMode(pin, mode)
- esp32.registerLoop(func) : func is called every arduino loop().

if WiFi.h is included:

- esp32.wifiIsConnected : bool
- esp32.fetch(url, {method:string, body:string}): Promise<{body:string, status:int}>


# License

MIT License
