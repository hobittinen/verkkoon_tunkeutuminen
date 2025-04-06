# h2 - Lempiväri: violetti

## Lukemiset


## Tehtävät

### Kaikissa tehtävissä on käytetty lähteenä Tero Karvisen verkkosivuilta löytyvää [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/)

### a) Apache log
Aloitin tehtävän tekemisen 6.4.2025 klo 13.52 vilkaisemalla [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/), jotta sain selville mitä ylipäätään piti alkaa tekemään. Tässä tehtävässä ideana käyttää Apachea. Luonnollisesti käyttö tapahtuisi virtuaalikoneella, joten sinne tieni vei. Kirjauduin sisälle virtuaalikoneeseeni ja siirryin komentoriville. Syötin seuraavat komennot, jotta sain asennettua ja käynnistettyä Apachen.

    sudo apt-get update
    sudo apt-get install apache2
    sudo systemctl start apache2

Seuraavaksi siirryin virtuaalikoneen palvelimelle. Siellä surffasin salaamattomalla HTTP-yhteydellä. Eteeni aukesi seuraava näkymä:

<img width="562" alt="image" src="https://github.com/user-attachments/assets/404acb7d-3016-41fa-89f3-deb4005bcc02" />

Ei tuosta näkymästä itsestään saa oikein mitään lokeihin liittyvää irti, joten syötin komentoriville seuraavan komennon.

    sudo tail /var/log/apache2/access.log

Kyseisellä komennolla sain näkyville live-lokin. Valitsin sieltä kuvassa rajatun lokirivin.

<img width="634" alt="Näyttökuva 2025-04-06 162152" src="https://github.com/user-attachments/assets/c4f8e305-f12b-4562-a974-b7d300288cf4" />

Lokiriviltä voimme huomata pyynnön tulleen IP-osoitteesta 127.0.0.1. Kyseinen osoite on virtuaalikoneen oma. Käyttäjätunnusta ei ole tunnistettu eli se on autentikoitumaton. Pyyntö on saatu aikaleiman mukaan 6.4.2025 noin klo 12. Lokiriviltä ilmenee kyseessä olleen HTTP-pyyntö: GET on metodityyppi, / on pyyntö palvelimen juurisivulle ja HTTP/1.1 protokollaversio. Pyyntötyyppiä seuraa HTTP-vastauskoodi, joka on 200. Vastauksen koko on 3380 tavua. Seuraavaksi voimme huomata viittaavan sivun olleen tyhjä. Viimeinen havainto on se, että "Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0" on selaimen tunnistetieto.

Tehtävä tuli valmiiksi 6.4.2025 klo 14.23.
