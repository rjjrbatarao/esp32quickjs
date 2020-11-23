# QuickJS Javascript Engine

- https://bellard.org/quickjs/
- https://github.com/bellard/quickjs

The main documentation is in doc/quickjs.pdf or doc/quickjs.html.

# Build with platform.io (ESP32)

platformio.ini

```ini
lib_deps = 
	https://github.com/binzume/esp32quickjs.git
```

main.cpp

```c++
#include <Arduino.h>
#include "quickjs.h"

JSRuntime *rt;
JSContext *ctx;

void setup() {
  rt = JS_NewRuntime();
  ctx = JS_NewContext(rt);
  // Do anything.
}

```
