# gluxinos
linux en windows 
se usa cynus 1.0
tlc/tk como perl
y algunos editores como ed vim http://gnuwin32.sourceforge.net/
se utilizan los directorios mas importantes linux http://mural.uv.es/oshuso/823_directorios_ms_importantes_en_linux.html
se pretende crear un linux en windows creando la interfaz grafica con tlc/tk
[![Alt text](89w4l0.gif)](https://www.youtube.com/watch?v=kNHYKyNpIcA)
 # Guía para Compilar y Cargar Programas en Raspberry Pi Pico usando la Línea de Comandos

Este README explica cómo compilar y cargar un programa básico de **Blink** en tu **Raspberry Pi Pico** usando la línea de comandos y los binarios del IDE de Arduino.

---

## 1. Pre-requisitos

Asegúrate de tener los siguientes componentes:

- **Arduino IDE** instalado (con soporte para Raspberry Pi Pico).
- **Compilador `arm-none-eabi-gcc`** instalado (se incluye en el soporte de Arduino para Raspberry Pi Pico).
- https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain
- 
- **Acceso al puerto USB** donde está conectada la Raspberry Pi Pico.

### Ubicación de los binarios ARM en Arduino IDE:
```txt
C:\Program Files (x86)\Arduino\hardware\tools\arm\bin
2. Crear el Código Blink
Primero, crea un archivo llamado blink.cpp con el siguiente contenido para encender y apagar el LED integrado en la Raspberry Pi Pico:

cpp
Copiar código
#include "pico/stdlib.h"

int main() {
    const uint LED_PIN = 25; // Pin LED integrado en Raspberry Pi Pico
    gpio_init(LED_PIN);
    gpio_set_dir(LED_PIN, GPIO_OUT);

    while (true) {
        gpio_put(LED_PIN, 1); // Enciende el LED
        sleep_ms(500);
        gpio_put(LED_PIN, 0); // Apaga el LED
        sleep_ms(500);
    }
}
3. Compilación del Programa
Abre una terminal (cmd) y navega a la carpeta donde se encuentra tu archivo blink.cpp. Luego, ejecuta los siguientes comandos para compilar y generar el archivo UF2.

Compilar el programa:
cmd
Copiar código
arm-none-eabi-g++ -o blink.elf -DPICO_DEFAULT_LED_PIN=25 -I"C:\Program Files (x86)\Arduino\hardware\arduino\mbed_rp2040\cores\arduino" -I"C:\Program Files (x86)\Arduino\hardware\arduino\mbed_rp2040\variants\RASPBERRY_PI_PICO" blink.cpp
Convertir el archivo ELF a formato BIN (UF2):
cmd
Copiar código
arm-none-eabi-objcopy -O binary blink.elf blink.uf2
4. Cargar el Programa en Raspberry Pi Pico
Conecta tu Raspberry Pi Pico al PC mientras mantienes presionado el botón BOOTSEL.
La Raspberry Pi Pico debería aparecer como una unidad USB.
Copia el archivo blink.uf2 directamente a esta unidad USB.
La Raspberry Pi Pico se reiniciará automáticamente y el programa Blink comenzará a ejecutarse, haciendo que el LED parpadee.

5. Agregar los Binarios al PATH de Windows
Para ejecutar los comandos desde cualquier ubicación sin tener que navegar a la carpeta específica, puedes agregar los binarios del compilador arm-none-eabi-gcc al PATH de Windows.

Pasos para agregar al PATH:
Abre el Panel de Control:

En el menú de inicio, busca "Sistema" → "Configuración avanzada del sistema".
Accede a las Variables de Entorno:

Haz clic en "Variables de entorno".
Edita la Variable Path:

En la sección "Variables del sistema", selecciona Path y haz clic en "Editar".
Agrega las rutas a los binarios de Arduino:

Para Raspberry Pi Pico:
txt
Copiar código
C:\Program Files (x86)\Arduino\hardware\tools\arm\bin
Guarda los cambios y reinicia la terminal.

6. Probar el PATH
Abre la terminal (CMD) y ejecuta:

cmd
Copiar código
arm-none-eabi-gcc --version
Si el comando retorna la versión del compilador, ¡todo está funcionando correctamente!

7. Crear un Script Automatizado (Opcional)
Para mayor comodidad, puedes crear un archivo .bat para automatizar el proceso de compilación y carga. Por ejemplo, crea un archivo llamado compile_pico.bat con el siguiente contenido:

bat
Copiar código
@echo off
arm-none-eabi-g++ -o blink.elf -DPICO_DEFAULT_LED_PIN=25 -I"C:\Program Files (x86)\Arduino\hardware\arduino\mbed_rp2040\cores\arduino" -I"C:\Program Files (x86)\Arduino\hardware\arduino\mbed_rp2040\variants\RASPBERRY_PI_PICO" %1
arm-none-eabi-objcopy -O binary blink.elf blink.uf2
echo Archivo UF2 generado correctamente.
pause
Con esto, ahora podrás compilar tu código desde cualquier ubicación con el siguiente comando:

cmd
Copiar código
compile_pico.bat blink.cpp
Resumen
Compilación y carga del programa Blink en Raspberry Pi Pico usando la línea de comandos.
Agregaste los binarios al PATH para ejecutar los comandos desde cualquier ubicación.
Automatizaste el proceso con un script .bat.
¡Ahora tienes un entorno de desarrollo eficiente para Raspberry Pi Pico! Si encuentras algún problema, no dudes en consultar o preguntar. 🚀😊


---
charla con chatgpt https://chatgpt.com/share/6766f9c6-c3cc-8008-9f69-724a15089a0a
Este **`README.md`** proporciona una guía detallada para configurar el entorno, compilar, y cargar un programa en tu Raspberry Pi Pico, así como cómo automatizar y optimizar el proceso en la línea de comandos.


