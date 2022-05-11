# Arduino-servojen-ohjauksen-alkeita
Servojen ohjauksen alkeita Arduinolla

*Tämä opas saattaa sisältää virheitä, vaikka olen pyrkinyt huolellisesti tarkistamaan sen. En ota vastuuta mahdollisista vahingoista, jotka ovat syntyneet noudattaessasi ohjeitani. Muistathan tarkistaa elektroniikka-kytkennät ennen virran kytkemistä huolella ja varautua ennalta mahdollisiin vahinkoihin.*

### Aloittelijan opas Arduinon asentamiseen ja ohjelmointiin

Sain idean rakentaa taiteelliseen veistokseeni robottisilmät, jotka seuraavat ohikulkevia ihmisiä. Ajatukseni oli liikuttaa silmiä servo-moottorien avulla. Tiesin, että tämä pitäisi onnistua Arduino-mikro-ohjaimen avulla, mutta en ollut kokeillut sitä kuin kerran, joskus kymmenen vuotta aiemmin. Ensimmäinen viikkoni kului siis [mikro-ohjainten](https://fi.wikipedia.org/wiki/Mikrokontrolleri) ([microcontrollers](https://en.wikipedia.org/wiki/Microcontroller)) perusasioita opiskellessa. 

Mikro-ohjaimet ovat olleet suosittuja harraste-elektroniikan rakentajien piireissä siitä alkaen, kun Arduino julkaisi ensimmäisen avoimeen lähdekoodin perustuvan ohjaimen, joka oli hinnaltaan harrastajillekin sopiva. Sittemmin markkinoille on ilmestynyt lukuisia avoimen lähdekoodin [ohjaimia](https://en.wikipedia.org/wiki/List_of_open-source_hardware_projects), mutta Arduino lienee edelleen tunnetuin näistä. (lue lisää Arduinon historiasta esimerkiksi [IEEE:n](https://fi.wikipedia.org/wiki/IEEE) julkaisemasta [artikkelista](https://spectrum.ieee.org/the-making-of-arduino))

Aloitin projektini kokeilemalla erilaisia vaihtoehtoja seurata konenäön avulla ohikulkevia ihmisiä. Olin tehnyt kymmenen vuotta aiemmin yhden taiteellisen teoksen, jossa käytin konenäön ohjelmointiin [Quartz Composer](https://en.wikipedia.org/wiki/Quartz_Composer) sovellusta [OpenCV](https://opencv.org)-kirjaston avulla. Seurasin teoksessa yleisön liikkumista Microsoft [Kinect](https://fi.wikipedia.org/wiki/Kinect)-kameran avulla, mutta ohjelmassa oli melko paljon vikoja, eikä se toiminut aivan toivotulla tavalla. 

Kokeilin konenäön ohjelmointia tällä kertaa [Max8-](https://cycling74.com/products/max)sovelluksella sekä Wolfram-ohjelmointikielellä. Kirjoitan näistä tarkemmin seuraavissa artikkeleissani, mutta kirjoitan aluksi Arduino-ohjaimen ohjelmoinnin alkeita.

### Arduinon testausta

Olen [Tampereen Hacklab yhdistyksen](https://tampere.hacklab.fi) jäsen ja sain sieltä Arduino UNO-kortin lainaksi sen asentamisen ja ohjelmoinnin opettelua varten. Ostin servo-moottorin testausta varten [Mekanisaatio Oy:ltä](https://www.mekanisaatio.fi), jonka toimisto on Tampere Hacklab yhdityksen tiloissa. Sain Mekanisaation yrittäjältä/Hacklab-konkarilta, Arnolta kaupan päälle erinomaisia vinkkejä Arduinon käyttöön, joten uskalsin kokeilla laitetta ilman pelkoa sen käräyttämisestä.

Testasin aluksi Arduino-kortilla olevan led-valon vilkuttamista ohjelman avulla. Mikro-ohjainta voi kokeilla siis melko helposti lataamalla ensin Arduino-korttien ohjaamiseksi tarvittava [*Arduino IDE kehitysympäristö](https://www.arduino.cc/en/software),* liittämällä Arduino tietokoneeseen USB-johdon avulla, ja lataamalla Arduino IDE kehitysympäristön esimerkkiohjelmista löytyvän Blink-ohjelma Arduinoon (Tiedosto > Esimerkit > 0.1.Basics > Blink).

Onnistuttuani led-valon vilkuttamisessa, testasin seuraavaksi servo-moottorin ohjausta. Liitin servo-moottorin [koekytkentälevyn](https://fi.wikipedia.org/wiki/Koekytkentälevy) kautta Arduino-korttiin: ruskea maa-johto Arduinon GND-pinniin, punainen virta-johto +5 V pinniin sekä servoa ohjaavan keltaisen johdon Arduino-kortin PWM-pinniin numero ~3. Eri servo-moottoreissa on erivärisiä johtoja, joten näiden värikoodi kannattaa tarkistaa laitteen jälleenmyyjältä.

![IMG_0747](https://user-images.githubusercontent.com/45873948/167785781-38b1a05d-f426-4d1d-aa56-7df3eef3817a.jpeg)

![IMG_0750](https://user-images.githubusercontent.com/45873948/167785820-6011ac33-a340-4cf8-8189-a2a486379de7.jpeg)

Servon ohjaamiseen löytyy esimerkki-koodaus Arduinon [kehitysympäristöstä](https://www.arduino.cc/en/software) (Tiedosto > Esimerkit > Servo > Sweep) , mutta sitä pitää muokata hieman, jos tämä servoa ohjaava johto on liitetty eri pinniin, mitä ohjelmassa (esimerkki-ohjelmassa oli käytetty pinniä numero 9, joten vaihdoin tämän numeroon kolme, koska olin asentanut servoa ohjaavan johdon jo tähän).

Ohjelman lataamisen Arduino-ohjaimelle jälkeen servo-moottori pitäisi kääntyä 180 astetta molempiin suuntiin, kunnes irroitat virran (USB-johdon), tai kunnes lataat Arduino-ohjaimelle toisen ohjelman.

Jos ohjelman lataamisessa syntyy seuraava virhe: avrdude: ser_open(): can't open device "/dev/cu.usbmodem101": No such file or directory, Arduino IDE ei löytänyt oikeaa porttia, jonka kautta se voi ladata ohjelman Arduinoon. – Valitse oikea portti Arduino IDE ylävalikosta Työkalut > Portti > (esim. Arduino UNO)
