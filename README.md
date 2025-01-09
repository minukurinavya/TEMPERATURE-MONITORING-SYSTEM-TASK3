# TEMPERATURE-MONITORING-SYSTEM-TASK3

*COMPANY*: CODTECH IT SOLUTIONS
*NAME*: MINUKOORI NAVYA
*INTERN ID*:CT12EHE
*DOMAIN*: EMBEDDED SYSTEMS
*BATCH DURATION*:DECEMBER 17th, 2025 TO FEBURARY 17th, 2025
*MENTOR NAME*:NEELA SANTOSH KUMAR

# DESCRIPTION OF THE TASK

OBJECTIVE:
   A Temperature Monitoring System utilizes a temperature sensor to accurately measure and monitor the surrounding environment's temperature. The sensor collects temperature data, which is then processed and displayed either on an LCD screen or through a serial monitor. This system offers real-time feedback, ensuring users can easily observe temperature fluctuations. The primary objective of such a system is to provide a reliable and efficient method for temperature tracking, making it ideal for applications in weather stations, industrial environments, and home automation. It serves as a foundational project for understanding sensor integration and data visualization in embedded systems.

INTRODUCTION:
   A Temperature Monitoring System is an essential tool designed to measure and display temperature data accurately using a temperature sensor. This system reads the temperature of the environment through the sensor and showcases the results in real time, either on an LCD screen or a serial monitor. It serves as a practical application of sensor technology, offering a simple yet effective solution for monitoring temperature changes. Widely used in various fields such as home automation, industrial processes, and environmental studies, this system demonstrates the integration of hardware and software to achieve precise data collection and display.

KEY ACTIVITIES:
1.Temperature Sensing:
Use a temperature sensor to detect ambient temperature.

2.Signal Processing:
Convert the sensor's analog or digital signals into readable data.

3.Data Processing:
Utilize a microcontroller to process and format the temperature data.

4.Data Display:
Show the temperature readings on an LCD screen or serial monitor for easy monitoring.

5.Calibration:
Ensure the temperature sensor is calibrated for accurate measurements.

6.Power Management:
Maintain a stable power supply for consistent system operation.

7.Threshold Alerts (Optional):
Integrate alerts or notifications for predefined temperature limits.

8.Data Logging (Optional):
Store temperature readings for analysis or historical tracking.

SOURCE CODE:
#include <OneWire.h>
#include <DallasTemperature.h>
#include <LiquidCrystal_I2C.h>

const int SENSOR_PIN = 13; // Arduino pin connected to DS18B20 sensor's DQ pin

OneWire oneWire(SENSOR_PIN);         // setup a oneWire instance
DallasTemperature sensors(&oneWire); // pass oneWire to DallasTemperature library
LiquidCrystal_I2C lcd(0x27, 16, 2);  // I2C address 0x27 (from DIYables LCD), 16 column and 2 rows

float tempCelsius;    // temperature in Celsius
float tempFahrenheit; // temperature in Fahrenheit

void setup()
{
  sensors.begin();    // initialize the sensor
  lcd.init();         // initialize the lcd
  lcd.backlight();    // open the backlight 
}

void loop()
{
  sensors.requestTemperatures();             // send the command to get temperatures
  tempCelsius = sensors.getTempCByIndex(0);  // read temperature in Celsius
  tempFahrenheit = tempCelsius * 9 / 5 + 32; // convert Celsius to Fahrenheit

  lcd.clear();
  lcd.setCursor(0, 0);       // start to print at the first row
  lcd.print(tempCelsius);    // print the temperature in Celsius
  lcd.print((char)223);      // print ° character
  lcd.print("C");
  lcd.setCursor(0, 1);       // start to print at the second row
  lcd.print(tempFahrenheit); // print the temperature in Fahrenheit
  lcd.print((char)223);      // print ° character
  lcd.print("F");

  delay(500);
}

CIRCUIT DIAGRAM:https://github.com/minukurinavya/TEMPERATURE-MONITORING-SYSTEM-TASK3/commit/7b74d0dee9d71f4a4c7c5006cc31561dc682d9a6

WORKING:
  The Temperature Monitoring System operates by utilizing a temperature sensor to detect the ambient temperature of its surroundings. The sensor captures the temperature data and converts it into an electrical signal, which is then sent to a microcontroller or processing unit. The microcontroller processes this data, ensuring its accuracy and formatting it for display. The processed temperature readings are then presented in real-time on an LCD screen or transmitted to a serial monitor for monitoring and analysis. Optional features, such as alerts for temperature thresholds or data logging, can also be integrated to enhance functionality. This seamless operation ensures reliable and efficient temperature tracking for various applications.

CONCLUSION:
   In conclusion, the Temperature Monitoring System provides an effective solution for measuring and displaying temperature data in real time. By utilizing a temperature sensor, microcontroller, and display unit such as an LCD or serial monitor, the system ensures accurate and reliable temperature tracking. Its versatility makes it suitable for a wide range of applications, including industrial processes, home automation, and environmental monitoring. The system demonstrates the seamless integration of hardware and software, offering a practical example of modern sensor technology's capabilities. This reliable and user-friendly setup underscores its importance in various fields where temperature control and monitoring are critical.


OUTPUT OF THE PROJECT:https://github.com/minukurinavya/TEMPERATURE-MONITORING-SYSTEM-TASK3/commit/ade2e53568d5719c847d99633d695e3ec5f98d88
