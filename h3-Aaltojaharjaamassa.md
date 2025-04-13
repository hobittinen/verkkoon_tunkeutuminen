# h3 - Aaltoja harjaamassa

## Tiivistelmät


## Tehtävät

### Kaikissa tehtävissä on käytetty lähteenä Tero Karvisen verkkosivuilta löytyvää [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/)!

### a) WebSDR
Aloitin tehtävän tekemisen 13.4.2025 klo 18.06 siirtymällä osoitteeseen http://websdr.org/. Sivustolta löytyvästä listasta valitsin kuunneltavaksi WebSDR Maasbree High -aseman Alankomaista. Minulla meni jonkin aikaa, että löysin muutakin ääntä kuin pelkkää pörinää ja kohinaa. Lukuisten tuskaisten etsintäyritysten jälkeen onnistuin löytämään ääntä!

<img width="769" alt="image" src="https://github.com/user-attachments/assets/8889cc6a-ef76-4a30-81ec-670333a0f5a4" />

Kuvasta pystyy näkemään, kaikki tarvittavat tiedot, mutta selitän ne vielä.
- Taajuus: 21 305,25 kHz/21,30525 MHz
- Aallonpituus: Noin 14m
- Modulaatio: AM


### b) rtl_433
Saatuani edellisen tehtävän valmiiksi klo 18.25, siirryin suoraan rtl_433-tehtävän kimppuun. Kävin hakemassa ohjeistusta [kurssisivun](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/) lisäksi myös [Projektin Github-sivulta](https://github.com/merbanan/rtl_433/). Löydettyäni tehtävän aloittamiseen tarvittavat komennot, siirryin virtuaalikoneen komentoriville ja syötin sinne seuraavat komennot.

    sudo apt-get update
    sudo apt-get install rtl-433

Kyseisillä komennoilla päivitin pakettivarastot ja asensin rtl_433. Seuraavaksi vuorossa oli tarkastaa, että kaikki meni putkeen. Otin testistä kuvan.

<img width="635" alt="image" src="https://github.com/user-attachments/assets/18e49f65-1797-4c00-9c6e-88e1aee39377" />

Kuten kuvasta voidaan huomata, meni kaikki hyvin! Tehtävä saatiin päätökseen 13.4.2025 klo 18.45.
