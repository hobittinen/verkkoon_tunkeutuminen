# h4 - NFC & RFID



## Tehtävät

### Tehtävissä on käytetty lähteenä kurssin Moodle-sivua!


### 1. Käytössä olevat RFID tuotteet
Tarkastelin seuraavia tuotteita:
- Lemmikkien mikrosirut
- Pankkikortti
- Kanta-asiakaskortit
- Auton avaimet

Luonnollisesti lemmikkien mikrosirut ovat lemmikkien sisällä (omillani on niskassa/hartiassa), joten siellä ne ovat turvassa. En usko kenenkään tulevan skalpelli kädessä varastamaan niitä. Pankkikorttia ja kanta-asiakaskortteja säilytän puhelimeni kuorissa. Ilokseni huomasin kuorien olevan RFID-suojatut! Tosin saatan hävittää puhelimeni, jolloin myös korttini häviävät - mikä on riski. Ehkä huonoiten suojattuna on autoni avaimet. Ne yleensä lojuvat kotonani ties missä, kiitos huolimattomuuteni. Lisäksi kodin ulkopuolella niitä säilytetään joko repussa tai laukussa ilman suurempaa suojausta.



### 2. APDU-komennot
Etin tietoa APDUsta CardLogix Corporationin [artikkelin](https://www.cardlogix.com/glossary/apdu-application-protocol-data-unit-smart-card/). Application Protocol Data Unit eli APDU on älykorttien ja lukijalaitteiden välinen viestintäyksikkö. Se on määritelty ISO/IEC 7816-4 -standardissa. APDU-komentoja käytetään älykorttien ja lukijalaitteiden kommunikoinnissa. Tarkemmin sanottuna olemassa on komennot (C-APDU) ja vastaukset (R-APDU).

C-APDU:n rakenne:
- CLA: minkä tyyppinen komento on kyseessä.
- INS: mitä kortilla halutaan tehdä.
- P1 & P2: lisäasetukset.
- Data: itse lähetettävä tieto, max 255 tavua.
- Le: miten paljon vastausta odotetaan (tavumäärä).

R-APDU:n rakenne:
- Data: mahdollinen saatava tieto.
- SW! & SW: miten komento onnistui.

Yleisiä APDU-komentoja ovat esimerkiksi SELECT FILE, UPDATE BINARY ja READ BINARY.



### 3. RFID hakkerointi uutinen
Löysin mielenkiintoisen uutisen [SecurityWeekin](https://www.securityweek.com/major-backdoor-in-millions-of-rfid-cards-allows-instant-cloning/) sivulta. Uutisessa kerrotaan ranskalaisen tietoturvayritys Quarkslabin huomanneen vakavan löydön: kiinalaisen udan Microelectronicsin valmistamissa RFID-korteissa on takaportti, joka mahdollistaa korttien kloonauksen hetkessä. Kyseessä olevat kortit kuuluivat MIFARE Classic -korttiperheeseen, ja niitä käytetään hotellien ja toimistojen ovikorteissa ympäri maailmaa. Tutkija Philippe Teuwen havaitsi korteissa olevan laitteistotason takaportin, joka mahdollistaa kortin kloonauksen ilman alkuperäistä avainta. Samalla hän löysi yleisavaimen, joka toimii kaikissa kyseisen mallin korteissa.

Mielestäni kyseinen löytö on erittäin huolestuttava, koska hyökkäys tapahtuu vain muutamassa minuutissa. Takaportin olemassaolo tarkoitta, ettei korttien vaihtaminen uusiin poista ongelmaa, jos sama valmistaja tarjoaakin uusia haavoittuvia kortteja.




## Lähteet

CardLogix Corporation. APDU – Application Protocol Data Unit (Smart Card). Haettu 21.4.2025 osoitteesta https://www.cardlogix.com/glossary/apdu-application-protocol-data-unit-smart-card/

Kurssin Moodle-sivut (2025). NFC & RFID -materiaali.

Naraine, R. (20.8.2024). Major Backdoor in Millions of RFID Cards Allows Instant Cloning. SecurityWeek. Haettu 21.4.2025 osoitteesta https://www.securityweek.com/major-backdoor-in-millions-of-rfid-cards-allows-instant-cloning/
