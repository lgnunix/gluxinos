# gluxinos
linux en windows 
se usa cynus 1.0
tlc/tk como perl
y algunos editores como ed vim http://gnuwin32.sourceforge.net/
se utilizan los directorios mas importantes linux http://mural.uv.es/oshuso/823_directorios_ms_importantes_en_linux.html
se pretende crear un linux en windows creando la interfaz grafica con tlc/tk
[![Alt text](89w4l0.gif)](https://www.youtube.com/watch?v=kNHYKyNpIcA)
 # C++ Ardunino cli microcontralador.
 Los binarios que vienen con el IDE de Arduino (como avr-gcc, arm-none-eabi-gcc, y avrdude) pueden ser utilizados desde la línea de comandos (CMD) para compilar, enlazar y cargar programas binarios directamente al microcontrolador.
 Compilación desde la línea de comandos
📂 Ubicación de los binarios:
Para placas AVR:
C:\Program Files (x86)\Arduino\hardware\tools\avr\bin
Para placas ARM (como Raspberry Pi Pico):
C:\Program Files (x86)\Arduino\hardware\tools\arm\bin
Ejemplo de comandos básicos:
🔹 Compilar un archivo fuente en C++ (ejemplo: blink.cpp)
avr-g++ -mmcu=atmega328p -DF_CPU=16000000UL -Os -o blink.elf blink.cpp
🔹 Generar el archivo HEX (para cargar en la placa)
avr-objcopy -O ihex -R .eeprom blink.elf blink.hex
🔹 Cargar el binario en la placa usando avrdude
avrdude -v -p atmega328p -c arduino -P COM3 -b 115200 -D -U flash:w:blink.hex:i
Explicación de los parámetros:
-mmcu: Define el microcontrolador (ej. atmega328p).
-DF_CPU: Define la frecuencia de la CPU (ej. 16 MHz).
-Os: Optimización para tamaño.
-c: Tipo de programador (en este caso, Arduino).
-P: Puerto de comunicación (ej. COM3).
🛠️ 2. Usar Arduino CLI (opción moderna y recomendada)
El Arduino CLI (Command Line Interface) es la herramienta oficial de Arduino para trabajar en la terminal.

📝 Ejemplo con Arduino CLI:
🔹 Compilar un programa:
cmd
Copiar código
arduino-cli compile --fqbn arduino:avr:uno Blink
🔹 Subir un programa:
cmd
Copiar código
arduino-cli upload -p COM3 --fqbn arduino:avr:uno Blink
--fqbn define el nombre de la placa completa (ej. arduino:avr:uno).
Puedes instalar Arduino CLI desde arduino-cli.
📊 3. Crear un script para automatizar el proceso
Puedes crear un script .bat para automatizar los pasos:

bat
Copiar código
@echo off
avr-g++ -mmcu=atmega328p -DF_CPU=16000000UL -Os -o blink.elf blink.cpp
avr-objcopy -O ihex -R .eeprom blink.elf blink.hex
avrdude -v -p atmega328p -c arduino -P COM3 -b 115200 -D -U flash:w:blink.hex:i
pause
Guarda el archivo como compile_upload.bat y ejecútalo.

✅ Conclusión Final
✔️ Sí, puedes usar los binarios de Arduino IDE en la línea de comandos.
✔️ Puedes compilar, enlazar y cargar programas binarios directamente.
✔️ Arduino CLI es una excelente alternativa moderna y más directa.



