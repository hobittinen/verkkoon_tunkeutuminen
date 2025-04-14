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


### c) Automaattinen analyysi
Tehtävien tekeminen jatkui 14.4.2025 klo 12.01. Avasin virtuaalikoneen ja kirjauduin sisään. Tämän jälkeen siirryin palvelimelle, jotta pääsin virtuaalikoneella [kurssisivulle](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/). Tarvitsin sivulta tiedoston tehtävää varten, joten päästyäni sivulle, latasin tiedoston virtuaalikoneelle.

Napattuani tiedoston koneelle, siirryin komentoriville. Syötin sinne heti alkuun seuraavan komennon.

    find ~ name "Converted_433.92M_2000k.cs8"

Komennolla sain selville, missä äsken lataamani tiedosto sijaitsee. Seuraavaksi siirryin hakemistoon, josta tiedosto voidaan löytää. Hakemistossa tarkistin vielä olevani oikeassa paikassa.

<img width="251" alt="image" src="https://github.com/user-attachments/assets/ee9143d8-5436-4922-a568-297a3649d523" />

Todettuani kaiken olevan kunnossa, analysoin tiedoston.

<img width="634" alt="image" src="https://github.com/user-attachments/assets/2e7a777b-730a-4167-a8ab-b1368eeb2d77" />
<img width="634" alt="image" src="https://github.com/user-attachments/assets/0746c919-1ec9-4afe-9a48-6025e494f2fe" />

Löysin seuraavia asioita:
- ID: 8785315
- Yksiköt: 0 & 3
- Toiminto: OFF
- Aikaleimat: Signaalia tulee 0.08 sekunnin välein.

Sain tehtävän valmiiksi klo 12.18.


### d) Too compex 16?
Reippaana jatkoin tähän tehtävään heti edellisen tehtävän valmistuttua. Kävin nopeasti [kurssisivulla](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/) katsomassa, oliko tähän tehtävään jotain hyvää vinkkiä tarjolla. Heti löysin tehtävään tarvittavan tiedoston, jonka luonnollisesti latasin. Tietenkin sieltä löytyi myös vinkki jos toinenkin, joten komentoriville tieni vei. Ensimmäisenä selvitin, löytyykö äsken lataamani tiedosto Downloads-hakemistosta.

<img width="569" alt="image" src="https://github.com/user-attachments/assets/46bc9f5d-a1c3-4f61-aad9-bdabc6b7a3f0" />

Sieltähän se löytyi! Seuraavaksi piti muuntaa äsken ladattu tiedosto sellaiseksi, että rtl_433 hyväksyisi sen. Syötin seuraavan komennon.

    cp Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s 433.92M_2000k.cs8

Varmuuden vuoksi tarkistin muunnoksen.

<img width="470" alt="image" src="https://github.com/user-attachments/assets/d8a3b548-06f1-4094-b3e9-1ab777fb5a70" />

Kuten voi huomata, kaikki meni putkeen! Vielä piti analysoida tiedoston sisältö.

<img width="634" alt="image" src="https://github.com/user-attachments/assets/43f23318-7270-44d4-8512-1f1b26d4a7a7" />
<img width="641" alt="image" src="https://github.com/user-attachments/assets/2683496c-3ea1-4e74-b679-33c81d0c0f26" />

Sain selville seuraavat asiat:
- ID: 8785315
- Toiminto: OFF
- Yksiköt: 0 & 3

Tehtävä tuli päätökseensä klo 12.44.
