/* ENSIMMÄINEN PYÖRÄHDYS
	Susa Tyrniluoto, 2022. Avoimen Public domain -lähdekoodin pohjalta.
	Alkuperäinen koodi: BARRAGAN <http://barraganstudio.com> ja Scott Fitzgerald (https://www.arduino.cc/en/Tutorial/LibraryExamples/Sweep)
*/

#include <Servo.h> // ota servo-ohjauksen kirjasto käyttöön
Servo servo1;  // määritä servo-objekti nimellä servo1
int asteluku = 0;  // määritä kokonaisluku-muuttuja nimellä asteluku, johon talletetaan servo-moottorin suunta. Määritetään suunnaksi aluksi nolla

void setup() { // alusta Arduino
  servo1.attach(3);  // Anna Arduinolle tieto, että pinnistä kolme ohjataan servo1-objektia.
}

void loop() { // luo silmukka, jota Arduino toistaa
  for (asteluku = 0; asteluku <= 180; asteluku++) { // luo for-silmukka, joka lisää numero ykkösen, jos asteluku-muuttuja on pienempi kuin 180
    servo1.write(asteluku);              // kirjoita servo1-objektiin uusi asteluku, johon servon tulee kääntyä
    delay(15);                       // odota 15 millisekunttia, jotta servo ehtii kääntyä ja palataan for-silmukan alkuun, jos asteluku on alle 180
  }
  for (asteluku = 180; asteluku >= 0; asteluku--) { // luo for-silmukka, joka lisää numero ykkösen, jos asteluku-muuttuja on suurempi kuin 0
    servo1.write(asteluku);              // kirjoita servo1-objektiin uusi asteluku, johon servon tulee kääntyä
    delay(15);                       // odota 15 millisekunttia, jotta servo ehtii kääntyä ja palataan for-silmukan alkuun, jos asteluku on alle 180
  } // palaa silmukan alkuun
}
