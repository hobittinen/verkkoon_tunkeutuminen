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

![image](https://github.com/user-attachments/assets/1e09554e-b274-407d-9919-f24fff5a79b5)

Palasin takaisin evilginx-työkalun pariin. Tosin ensin paluuta kävin ChatGPT:n juttusilla kyselemässä mitä pitäisi tehdä. Vastauksen saamisen jälkeen määrittelin uudelleen domainin ja ipv4-osoitteen. Sen lisäksi määritin example phishletsin localtestiksi, koska miksikäs ei. Halusin kokeilla tätäkin muutosta.

![image](https://github.com/user-attachments/assets/205745fa-73a8-4b9f-ba0e-413ba2b8f544)

Kuten kuvasta huomataan, meni vähän v*tuiksi. Eikun vaan uusiksi tekemään! Tein alla olevassa kuvassa näkyvät muutokset.

![image](https://github.com/user-attachments/assets/c2879ce5-ae23-41e9-8715-af58e6cab6d6)

Onnistumisen ilossa siirryin eteen päin. Piti tehdä url-osoite, joka hoitaa liikenteen huijaamisen. Kysyin tähänkin apua ChatGPT:ltä, joka ystävällisesti antoi minulle oikein hyvän ja selvän ohjeen! Alkuun tein uuden tiedoston, jonka sisällön näkee alla olevasta kuvasta.

![image](https://github.com/user-attachments/assets/5e958e65-ec1b-4fa1-93b6-8bb20da452cd)

Tiedoston luomisen jälkeen käynnistin HTTP-palvelimen Pythonin avulla.

    sudo python3 -m http.server 8080

Jännittyneenä siirryin virtuaalikoneen selaimelle. Tärisevin käsin syötin sinne seuraavanlaisen osoitteen.

    http://localhost:8080/hobittinen.html

Ja lopputulokseksi sain tällaisen kaunokaisen!

![image](https://github.com/user-attachments/assets/08ea9787-6587-4157-966f-3a1bdbda2cae)

Nopeasti huomasin tämänkin yrityksen menneen v*tuiksi. Enhän pysty käyttämään tuota sivua ja evilginx-työkalua samaan aikaan! Taas käännyin ChatGPT:n puoleen, joka suositteli alkuun tekemään uuden tiedoston, jonka sisältö näkyy kuvassa.

![image](https://github.com/user-attachments/assets/69d94fd4-4d17-4374-927c-f0270a61d265)

Vaihteeksi palauduin takaisin evilginx-työkalun pariin. Siellä loin uuden urlin, kuten kuvasta huomaa.

![image](https://github.com/user-attachments/assets/4a39d55c-a5fa-4e71-ac71-fbad565ac6c3)


### b) TCP SYN-Flood hyökkäys
Päätin tässä tehtävässä kysyä apua rakkaalta ystävältäni ChatGPT:ltä. Se antoi jälleen arvokkaan ohjenuoran, jota lähdin seuraamaan. Alkuun loin Mininet-ympäristön seuraavalla komennolla:

    sudo mn --topo single,3 --mac --switch ovsk --controller=remote

Kun ympäristö oli luotu, oli vuoro tehdä hyökkäys! Kuvassa näkyy palvelimen käynnistys portissa 80 h2:lla ja sen kuunteleminen.

![image](https://github.com/user-attachments/assets/c2e6ed69-91e0-43a9-be5a-db51bcd6c7b1)

Seuraavaksi oli hyökkäyksen vuoro! Tein sen seuraavalla komennolla:

    h1 hping3 -S -p 80 --flood h2

Tähän se jäikin. Yritin lisäksi pingailla noita osoitteita, mutta eipä ne löytäneet toisiaan :))) Jospa jossain välissä keksisi ratkaisun tähän. Nyt sitä ideaa ei valitettavasti tullut.


## Lähteet

Evilginx-dokumentaatio (2025). Evilginx2:n virallinen dokumentaatio. Haettu 7.5.2025 osoitteesta https://help.evilginx.com/

Hping3-ohjeet (2025). Hping3:n virallinen dokumentaatio. Haettu 7.5.2025 osoitteesta http://www.hping.org/

Kurssin Moodle-sivut (2025). Laboratorio- ja simulaatioympäristöt hyökkäyksissä -materiaali.

Mininet-ympäristön dokumentaatio (2025). Mininetin virallinen dokumentaatio. Haettu 7.5.2025 osoitteesta http://mininet.org/
