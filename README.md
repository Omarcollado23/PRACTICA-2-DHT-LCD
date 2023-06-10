# Practica ESP32 con DHT11
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 con una LCD.


### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno Y una (```LCD 16X2 (l2C)```); y en este poder ver digitalmente la temperatura y la hunmedad adquirida por medio del sensor. Cabe aclarar que esta practica se usara en el simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
-LCD 16X2 (l2C)



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");
  delay(1000);
  lcd.setCursor(0, 0);
  lcd.print("DIPLOMADO AUTOMATIZACION");
  lcd.setCursor(0, 1);
  lcd.print("SABADO 6 DE JUNIO");
  delay(1000);
}

```
2. Instalar la libreria de **DHT sensor library for ESPx** y **LiquidCrystal I2C** como se muestra en la siguente imagen.

![](https://github.com/DiegoJm10/PracticaDHT/blob/main/Libreria%20DHT.png?raw=true)

3. Hacer la conexion de **DHT11** con la **ESP32** como se muestra en la siguente imagen.

![](https://raw.githubusercontent.com/Omarcollado23/EJEMPLO-READ/88f9cf65517fc8bf9420919d2ef17de71d84d9a3/20201202_185557.jpg)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11** 

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.

https://github.com/DiegoJm10/PracticaDHT/raw/main/Libreria%20DHT.png?raw=true


## Evidencias

[Video de Youtube](https://https://wokwi.com/)


# Créditos

Desarrollado por Ing. Diego Jasso Miranda

- [GitHub](https://github.com/DiegoJm10)