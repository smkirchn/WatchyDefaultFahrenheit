# WatchyDefaultFahrenheit
Forked from tapecanvas/WatchyDefaultFahrenheit

Instructions to set the default 7seg watch face's weather info to your location and change temperature display to fahrenheit.


Follow these instructions to use the CITY_NAME and COUNTRY_CODE API call, skip to the bottom to use CITY_ID API call.

1. First find where your arduino sketchbook folder is located. For example: mine is Documents/Arduino.
2. Enter the arduino folder and then enter the "libraries" folder.
3. Find the "Watchy" folder then enter into the "src" folder.
4. Open the file "config.h" in a text editor such as Atom, VisualStudio, notepad, etc..

5. On line 28 (#define CITY_NAME "NEW+YORK"), replace "NEW+YORK" with your city's name. If your city has a space between words use the "+" in its place.
6. Change line 29 to your country's code if needed.

7. Next, go to https://home.openweathermap.org/users/sign_up and create a free account.
8. Create a new api key and copy the generated key.
9. Back in the "config.h" file from above, on line 30, replace the default key with the one you just generated.
10. On line 31, insert your city name and api key like so: (#define OPENWEATHERMAP_URL "http://api.openweathermap.org/data/2.5/weather?q={yourcityname}&appid={yourapikey}"
11. On line 32, change metric to imperial (#define TEMP_UNIT "imperial" //use "imperial" for Fahrenheit"

12. Now open Arduino program and go to file/examples/Watchy/WatchFaces/7_SEG
13. Select the "Watchy_7_SEG.cpp tab
14. Scroll down to line 107 and change "metric" to "imperial" and ==0 ? to ==1 ?
15. To finish, click the checkmark in the top left to compile the code (this can take a minute)
16. The output console should read:
WARNING: library DS3232RTC claims to run on avr architecture(s) and may be incompatible with your current board which runs on esp32 architecture(s).
Sketch uses 1783902 bytes (90%) of program storage space. Maximum is 1966080 bytes.
Global variables use 58392 bytes (17%) of dynamic memory, leaving 269288 bytes for local variables. Maximum is 327680 bytes.--------------------------Compilation complete.
17. Connect your Watchy to your computer using a usb data cable. [data vs charge](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/)
18. Hit the upload button and wait for the watchy to reboot. Your temperature should now be accurate to your locale and in degrees F.



Follow these instructions to use the CITY_ID API call:

1. First find where your arduino sketchbook folder is located. For example: mine is Documents/Arduino.
2. Enter the arduino folder and then enter the "libraries" folder.
3. Find the "Watchy" folder then enter into the "src" folder.
4. Open the file "config.h" in a text editor such as Atom, VisualStudio, notepad, etc..

5. Find the "weather api" section and change it to:

  //weather api
  #define CITY_ID "5128581" //find your city id by searching your city on https://openweathermap.org/ ,your city id will appear in the address bar. Ex: https://openweathermap.org/city/5128581 <-- the number is your city id
  #define OPENWEATHERMAP_APIKEY "f058fe1cad2afe8e2ddc5d063a64cecb" //use your own API key :)
  #define OPENWEATHERMAP_URL "http://api.openweathermap.org/data/2.5/weather?id="
  #define TEMP_UNIT "imperial" //use "metric" for Celsius"
  #define WEATHER_UPDATE_INTERVAL 30 //minutes

6. Next, go to https://home.openweathermap.org/users/sign_up and create a free account.
7. Create a new api key and copy the generated key.
8. Back in the "config.h" file from above, replace the default api key with the one you just generated.

9. Now open Arduino program and go to file/examples/Watchy/WatchFaces/7_SEG
10. Select the "Watchy_7_SEG.cpp tab
11. Scroll down to line 107 and change "metric" to "imperial" and ==0 ? to ==1 ?

12. Now go back to the "Watchy/src" folder and open the "Watchy.cpp" file in a text editor.
13. Find line 596, which should look like this:

  String weatherQueryURL = String(OPENWEATHERMAP_URL) + String(CITY_NAME) + String(",") + String(COUNTRY_CODE) + String("&units=") + String(TEMP_UNIT) + String("&appid=") + String(OPENWEATHERMAP_APIKEY);

and replace it with:

  String weatherQueryURL = String(OPENWEATHERMAP_URL) + String(CITY_ID) + String("&units=") + String(TEMP_UNIT) + String("&appid=") + String(OPENWEATHERMAP_APIKEY);

14. To finish, click the checkmark in the top left to compile the code (this can take a minute)
15. The output console should read:
WARNING: library DS3232RTC claims to run on avr architecture(s) and may be incompatible with your current board which runs on esp32 architecture(s).
Sketch uses 1783902 bytes (90%) of program storage space. Maximum is 1966080 bytes.
Global variables use 58392 bytes (17%) of dynamic memory, leaving 269288 bytes for local variables. Maximum is 327680 bytes.--------------------------Compilation complete.
16. Connect your Watchy to your computer using a usb data cable. [data vs charge](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/)
17. Hit the upload button and wait for the watchy to reboot. Your temperature should now be accurate to your locale and in degrees F.
