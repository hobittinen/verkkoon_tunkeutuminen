# h5 - Laboratorio- ja simulaatioympäristöt hyökkäyksissä

## Tehtävät

### Tehtävissä on käytetty lähteinä kurssin Moodle-sivua, [evilginx-dokumenttia](https://help.evilginx.com/) ja edellisen tunnin tuntitehtäviä!

### a) Evilginx2
Asensin evilginx2-työkalun. Aloitin asennuksen päivittämällä pakettilistat ja asentamalla saatavilla olevat päivitykset seuraavilla komennoilla.

    sudo apt update
    sudo apt upgrade -y

Kun pakettilistat ja päivitykset oli saatu hoidettua, asensin evilginx2:n vaatimat käännöstyökalut. Samassa syssyssä latasin itse evilginx2.

    sudo apt install git make gcc libpcap-dev
    git clone https://github.com/kgretzky/evilginx2.git

Nyt pääsin itse asiaan! Siirryin evilginx2-hakemistoon, kuten allaolevasta kuvasta voi huomata.

<img width="136" alt="image" src="https://github.com/user-attachments/assets/d511cff0-f98c-45d4-b008-59b94b8d535b" />

Tässä vaiheessa tajusin, että vielä yksi tärkeä osanen puuttui! Palauduin takaisin "normihakemistooni", jossa suoritin kuvassa näkyvät komennot.

<img width="314" alt="image" src="https://github.com/user-attachments/assets/93f79d13-7aa2-49b2-bd5d-4429da5a6fc5" />

Seuraavaksi siirryin takaisin evilginx2-hakemistoon. Siellä tein seuraavat toimenpiteet.

![image](https://github.com/user-attachments/assets/5638a9f7-01df-4e99-a106-7bc885ffcabe)

Kuten kuvasta pystyi huomaamaan, evinginxillä ei ollut hakemistosijaintia phisleteille. Ratkaisin tämän ongelman [dokumentin](https://help.evilginx.com/) ohjeiden mukaisesti. Asetin myös domainin ja ipv4.

![image](https://github.com/user-attachments/assets/6a95aeb7-b7eb-4f4d-bae8-739e0c8a1182)
![image](https://github.com/user-attachments/assets/3c0f011f-c477-4533-ac52-2308c98e1bb9)

Seuraavaksi vuorossa oli työkalun TURVALLINEN käyttökokeilu. En halua joutua nuorena ja kauniina vankilaan, joten tein kokeilun localhostilla. Aloitin kokeilun muokkaamalla /etc/hosts -tiedostoa kuvassa näkyvällä tavalla.

![image](https://github.com/user-attachments/assets/ef938550-21b7-41af-9cbe-5b993553a53b)




### b) TCP SYN-Flood hyökkäys
Päätin tässä tehtävässä kysyä apua rakkaalta ystävältäni ChatGPT:ltä. Se antoi jälleen arvokkaan ohjenuoran, jota lähdin seuraamaan. Alkuun loin Mininet-ympäristön seuraavalla komennolla:

    sudo mn --topo single,3 --mac --switch ovsk --controller=remote

Kun ympäristö oli luotu, oli vuoro tehdä hyökkäys! Kuvassa näkyy palvelimen käynnistys portissa 80 h2:lla ja sen kuunteleminen.

![image](https://github.com/user-attachments/assets/c2e6ed69-91e0-43a9-be5a-db51bcd6c7b1)

Seuraavaksi oli hyökkäyksen vuoro! Tein sen seuraavalla komennolla:

    h1 hping3 -S -p 80 --flood h2

