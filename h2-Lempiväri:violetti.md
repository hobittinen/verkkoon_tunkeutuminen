# h2 - Lempiväri: violetti

## Lukemiset

### [Tuskan pyramidi](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)
Tuskan pyramidin idea on kuvastaa kyberturvallisuusuhkien analysoinnissa esiintyviä haasteita eri pyramidin tasoilla. Pyramidin alimmat tasot sisältävät helposti tunnistettavia uhkia, kun taas ylempänä on vaikeammin havaittavat ja torjuttavat hyökkäykset.

### [Timanttimalli](https://kravensecurity.com/diamond-model-analysis/)
Timanttimalli on uhkamallinnus, jossa tarkastellaan kyberturvallisuushyökkäyksiä neljän pääkomponentin kautta: hyökkääjä, hyökkäys, kohde ja seuraus. Mallin tarkoituksena on auttaa analysoimaan ja ymmärtämään, miten kyseiset komponentit vuorovaikuttuvat keskenään.


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


### b) Nmapped
Pienen ruoka- ja lepotauon jälkeen palasin asiaan 6.4.2025 klo 16.35. Nyt oli vuorossa oman weppipalvelimen porttiskannausta. Kävin tuumasta toimeen ja suuntasin virtuaalikoneelleni. Siirryin suoraan komentoriville, jonne syötin seuraavat komennot:

    sudo apt-get update
    sudo apt-get install nmap

Kyseisillä komennoilla päivitin pakettivarastot ja asensin nmap-työkalun. Nyt pääsin todennäköisesti itse asiaan. Alla olevista kuvista näkyy nmap-työkalun käyttö.

![Näyttökuva 2025-04-06 165618 r](https://github.com/user-attachments/assets/95f7220c-8065-48d3-b79a-686cff8c1a3d)

Mitä sain selville kuvissa näkyviltä riveiltä? Ainakin sen, että portti 80 on auki ja sillä on HTTP-palvelin. Palvelin on vastannut syn-ack-viestillä (kuuluu TCP handshakeen), mikä tarkoittaa sitä, että yhteys on luotettavasti muodostettu. Palvelimella toimii Apache HTTP Server versio 2.4.62, joka on asennettu Debianiin. Nmapin NSE-skripteistä löytyi oletussivun nimi ("It works") ja tuetut HTTP-metodit, esim. POST ja OPTIONS. OS-arvio on todennäköisesti epätarkka, koska oli ainoastaan yksi portti aukinaisena.

Pidin tehtävän aikana luovan tauon. Sain loppujen lopuksi tehtävän valmiiksi 6.4.2025 klo 18.00.

### c) Skriptit
Jatkoin suoraan edellisestä tehtävästä. Tutkailin edellisessä tehtävässä esiintyvää kuvaa, jossa esiteltiin nmap-työkalun käyttöä. Huomasin kuvan avulla, että -A parametria käytettäessä seuraavat skriptit olivat automaattisesti käynnissä:
- http-server-header; tehtävänä hakea HTTP-palvelimen otsikkotiedot.
- http-title; tehtävänä tunnistaa oletussivun nimi.
- http-methods; tehtävänä löytää mitä HTTP-pyyntömetodeja tuetaan (esim. HEAD).


### d) Jäljet lokissa
Selkeästi olin tänään laiskalla päällä. Pidin taas taukoa, jolta palasin kiltisti 6.4.2025 klo 18.54. Vilkaisin [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/) ja kävin työntekoon. Siirryin virtuaalikoneen komentoriville ja tein kuvassa näkyvän asian.

![image](https://github.com/user-attachments/assets/61bf5c67-34c3-4a21-94a3-3fa0824a7899)

Näkymähän on pitkälti sama kuin a-kohdassa. IP-osoite on edelleen 127.0.01, mikä tarkoittaa sitä, että virtuaalikone teki pyynnöt. Huomasin GET-pyyntöjä juurisivulle, faviconille ja kuvalle. Käytetty selain oli luonnollisesti Firefox.

Seuraavaksi päätin selvitellä nmapin porttiskannauksen jälkiä. Käytin selvitykseen seuraavia komentoja:

    sudo grep -i nmap /var/log/apache2/access.log
    sudo grep -i nmap /var/log/apache2/access.log | head

Käytin tuota jälkimmäistä komentoa, koska ensimmäinen komento antoi hirmu pitkän listan rivejä. Koin tarpeelliseksi lyhentää rivimäärää, jotta sain otettua kuvan.

![image](https://github.com/user-attachments/assets/40eff7a5-4cdb-4b92-908c-596435a4cf20)

Kuten kuvasta näkyy, porttiskannauksesta jäi jälkiä Apache-lokiin. Paljastava tekijä on User-Agent-kentästä löytyvä teksti "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)". Tämä kertoo, että kyseessä olevat HTTP-pyynnöt tulivat nmapista, ei tavallisesta selaimesta. Lisäksi huomasin pari erikoista pyyntöä, esim. GET /sdk ja GET /.git/HEAD. Pyynnöt voivat liittyä nmapin skriptien etsimiin haavoittuvuuksiin.

Sain tehtävän valmiiksi 6.4.2025 klo 19.14.


### e) Wire sharking
Palasin takaisin koneen äärelle 7.4.2025 klo 11.20. Nyt olisi vuorossa Wiresharkin käyttöä, joten virtuaalikoneelle tieni vei. Siirryin tuttuun tapaan komentoriville, josta sukkuloin Wiresharkiin. Valitsin siepattavaksi Loopback:lo:n, koska se vastaa localhostia.

<img width="515" alt="image" src="https://github.com/user-attachments/assets/56ec83ad-25ab-4659-8b0d-932ece117432" />

Aloitin sieppauksen. Porttiskannauksen hoidin komentorivillä jo ennestään tutulla komennolla.

    sudo nmap -T4 -vv -A -p 80 localhost

Kuvassa on todistusaineistoa siitä, että sain kaapattua paketteja.

<img width="519" alt="image" src="https://github.com/user-attachments/assets/68381cae-35f9-490b-a914-89e48474ca14" />

Tehtävänannon mukaisesti tallensin pcap-tiedoston.

<img width="638" alt="image" src="https://github.com/user-attachments/assets/b67bdf0d-e4a6-4f53-a0e3-319dfcf74ea7" />

Seuraavaksi vuorossa oli pakettien tarkastelua ja suodattelua. Suodatin paketit sillä perusteella, että ne sisälsivät "nmap". Suodatukseen käytin lisäämällä Wiresharkin kenttään seuraavan komennon.

    frame contains "nmap"

<img width="637" alt="image" src="https://github.com/user-attachments/assets/3b75d310-5c24-473d-a5cc-bb9f7f474a56" />

Huomasin pakettien koostuneen HTTP-protokollista (GET, OPTIONS, POST, PROFIND). Mukana oli myös muutama TCP-paketti. Löysin User-Agent-kentästä kohdan "Nmap Scripting Engine".

Tehtävä saatiin valmiiksi klo 11.43.


### f) Net grep
Pienen tauon jälkeen palasin koneelle 7.4.2025 klo 12.10. Aloitin tehtävän tekemisen päivittämällä pakettivarastot ja asentamalla ngrep-työkalun.

    sudo apt-get update
    sudo apt-get install ngrep

Kun ngrep-työkalu oli saatu asennettua, pääsin itse tehtävän kimppuun. Tehtävän ideana oli siepata verkkoliikennettä ngrepillä, joten niin tein.

<img width="257" alt="image" src="https://github.com/user-attachments/assets/afccfae9-edb3-458e-a619-1ae40060a778" />

Kuvasta näkyykin koko komento. Ngrep on luonnollisesti työkalu, kun taas -d lo -osuus määrittelee kuunneltavan kohteen. Komennon viimeinen osuus, -i nmap, tekee kirjainkoosta merkityksettömän ja etsii "nmap"-merkkijonoja.

Avasin toisen komentorivi-ikkunan, jonne syötin seuraavan komennon:

    sudo nmap -T4 -vv -A -p 80 localhost

Tämän jälkeen ensimmäiselle komentorivi-ikkunaani alkoi suorastaan vyöryä paketteja!

<img width="632" alt="image" src="https://github.com/user-attachments/assets/c7b45d2c-0581-47ec-9de0-478cf1860fd6" />

Tutkaillessani paketteja, tein seuraavia huomioita:
- Paketit on TCP-paketteja.
- Hostina on localhost.
- Siepatun paketin numero on esim. #290.
- User-Agentina on tuttuun tapaan Nmap Scripting Engine.
- Virtuaalikoneen ja nmapin välinen liikenne: 127.0.0.1:51678 -> 127.0.0.1:80.

Sain tehtävän valmiiksi 7.4.2025 klo 12.30.


### g) Agentti & h) 
Aloittelin tehtävien tekoa 7.4.2025 klo 12.36. Ajattelin tehdä nämä tehtävät yhdessä, koska miksi ei. Olen itseni herra, joten teen mitä haluan. Kävin vilkaisemassa [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/), minkä jälkeen siirryin takaisin virtuaalikoneeni komentoriville. Päätin käyttää siellä Teron antamaa esimerkkikomentoa omilla lisäyksilläni.

<img width="634" alt="image" src="https://github.com/user-attachments/assets/5c5ba949-08f7-4bea-8da2-0ac5628f6e6d" />

Avasin Wiresharkin, jotta pystyin tarkastamaan sainko kaiken toimimaan, kuten piti. Wiresharkissa suodatin näkyville vain nmap-viittauksen sisältämät paketit.

<img width="645" alt="image" src="https://github.com/user-attachments/assets/acc4565c-8aec-40ef-b75a-b18f071ee1a2" />
<img width="641" alt="image" src="https://github.com/user-attachments/assets/c1aae4df-b155-4c1e-8d8a-514a6f77016b" />

Tämän jälkeen palasin takaisin komentoriville. Syötin seuraavan komennon:

    sudo tail -f /var/log/apache2/access.log

Komennon seurauksena pääsin käsiksi Apache-lokiin. Tarkastelin lokia ja totesin onnistuneeni. Ei löytynyt nmap-viitettä!

![image](https://github.com/user-attachments/assets/81960329-91e3-402b-af95-aa567e39558e)

Tehtävä saatiin päätökseen 7.4.2025 klo 12.57.


### i) LoWeR ChEcK
Palauduin ruoka- ja lepotauoiltani 7.4.2025 klo 15.06. Jännityksestä täristen kirjauduin takaisin virtuaalikoneelle. Syötin komentoriville ensimmäisen komennon.

    cd /usr/share/nmap

Päädyin /usr/share/nmap-hakemistoon. Saadakseni selville hakemiston sisältämät tiedostot käytin kuvassa näkyvää komentoa.

![image](https://github.com/user-attachments/assets/f55ac42d-7b39-47db-89ad-229f7fd4567a)

Kysyin nopeasti ChatGPT-työkalulta neuvoa, mihin tiedostoon pitäisi suunnata. Se ehdotti nselib-tiedostoa. Tosin se ei ollut tiedosto, vaan osa hakemistoa. Avasin uuden hakemiston.

![image](https://github.com/user-attachments/assets/75bf4c59-6eb8-49ee-91a4-809a4f0617e1)

Tutkailin uutta hakemistoa
