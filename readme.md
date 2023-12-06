# Setup PlatformIO to debug Arduino Nano
Example configuration to debug an Arduino Nano ( or any Mega328 micro-processor) using VS Code and PlatformIO

Platformio.ini config
```ini
[env:nanoatmega328]
platform = atmelavr
board = nanoatmega328
framework = arduino

debug_tool = avr-stub
debug_port = COM4 ;modify to use the COM port for your Nano
lib_deps = 
    jdolinay/avr-debugger@^1.5

```

```cpp
#include <Arduino.h>
//Include debugger libraries
#include "avr8-stub.h"
#include "app_api.h"


void setup() {
  debug_init();
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}

```# nano_debug
