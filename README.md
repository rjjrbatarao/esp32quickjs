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
