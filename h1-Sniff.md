# h1 - Sniff

## Tiivistelmät

### [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/)
- Wireshark on verkon analysointiin käytettävä työkalu.
- Jotta voi käyttää kaikkia Wiresharkin ominaisuuksia, pitää olla Wireshark-ryhmän jäsen.
- Liikenteen erotteluun voi käyttää suodattimia, esim. dns, tls, http.

### [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/)
- Verkkoliitäntä on vähän kuin "verkkokortti", mutta se ei välttämättä ole fyysinen laite.
- Linuxissa verkkoliitäntöjen nimet määräytyvät systemd:n mukaan.
- Etuliitteet määrittelevät käyttöliittymän tyypin.
- Oman liittymät voi tarkastaa seuraavilla komennoilla:

      ip a
      ip route


## Tehtävät

### Kaikissa tehtävissä on käytetty lähteenä Tero Karvisen verkkosivuilta löytyvää [kurssisivua](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/)

### a) Linux
Asensin Debian Linuxin virtuaalikoneeseen käyttäen Tero Karvisen [ohjetta](https://terokarvinen.com/2021/install-debian-on-virtualbox/).

### b) Ei voi kalastaa
Aloitin tehtävän tekemisen 29.3.2025 klo 23.52 avaamalla virtuaalikoneeni. Sen avauduttua siirryin komentoriville, jonne syötin kuvassa näkyvän komennon.

<img width="518" alt="image" src="https://github.com/user-attachments/assets/e853d16c-6e8e-4288-898f-0e1aab56a396" />

Sain selville Ethernetin olevan enp0s3. Jotta saisin virtuaalikoneen Internet-yhteyden pois päältä, syötin seuraavan komennon:
   
    sudo ip link set enp0s3 down.

Tarkistin komennon toiminnon siirtymällä virtuaaalikoneessa selaimeen, Firefoxiin. Laitoin hakusanaksi Youtube.com. Sain seuraavanlaisen näkymän.

<img width="634" alt="image" src="https://github.com/user-attachments/assets/a9dff791-7133-4dd2-8799-b3016792d09d" />

Virtuaalikoneeni Internet-yhteys oli selkeästi pois päältä. Seuraavaksi piti laittaa se takaisin päälle. Siihen käytin komentoa:
    
    sudo ip link set enp0s3 up

Kuten aiemminkin, kävin nytkin tarkastamassa toiminnon toimivuuden Firefoxissa.

<img width="509" alt="image" src="https://github.com/user-attachments/assets/af840609-5986-4fb0-aef6-2922c9291821" />

Kuten kuvasta näkee, Internet-yhteys oli saatu takaisin päälle! Sain tehtävän päätökseen 30.3.2025 klo 0.01.

### c) Wireshark
Palasin takaisin tehtävien pariin 30.3.2025 klo 11.38. Kuten viime yönä, myös nyt aloitin tehtävänteon käynnistämällä virtuaalikoneeni. Tosin jouduin melkeinpä heti palaamaan takaisin fyysiselle koneelle, koska enhän minä osannut asentaa Wiresharkia! Hain ohjenuoran Wiresharkiin Tero Karvisen [verkkosivulta](https://terokarvinen.com/wireshark-getting-started/). Löydettyäni hyödylliset komennot, suuntasin takaisin virtuaalikoneen komentoriville. Syötin sinne seuraavat komennot:

    sudo apt-get update
    sudo apt-get install wireshark

Seuraavaksi vuorossa olikin itseni lisääminen sniff-porukkaan! Suoritin sen kuvassa näkyvällä tavalla.

<img width="236" alt="image" src="https://github.com/user-attachments/assets/70d78ff4-7f1c-4332-95f5-6e34e4d5d21d" />

Nyt kun olin päässyt sniff-porukkaan mukaan, päätin siepata liikennettä Wiresharkilla. Suoritin sen seuraavalla komennolla.

    wireshark

Syötettyäni ylläolevan komennon, eteeni aukesi kuvan näkymä.

<img width="380" alt="image" src="https://github.com/user-attachments/assets/8fabdbf5-6bc6-4e76-8238-9ed069e79f98" />

Luonnollisesti valitsin siepattavaksi liikenteeksi Ethernettini. Valittuani sen, siirryin virtuaalikoneen selaimeen ja näpyttelin sinne Reddit.com.

<img width="377" alt="image" src="https://github.com/user-attachments/assets/2ecfadc9-726c-4cfc-a49a-a69a12101ff2" />

Siepattuani tarpeeksi liikennettä, pysäytin Wiresharkin ja poistuin sieltä. Tehtävä tuli valmiiksi klo 12.07.

### d) Oikeesti TCP/IP
Paluu tehtävien pariin tapahtui 31.3.2025 klo 15.35, kun avasin [kurssisivun](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/). Nyt oli vuorossa TCP/IP-mallin osoittamista. Siirryin virtuaalikoneelle, jolla luonnollisesti tekisin tehtävän. Koneelle kirjautumisen jälkeen tieni vei komentoriville. Syötin sinne aikaisemmasta tehtävästä tutun komennon.

    wireshark

Komento sai aikaiseksi seuraavan näkymän.

<img width="502" alt="image" src="https://github.com/user-attachments/assets/138c1795-33cd-490d-bb28-421f8d20f6c9" />

Valitsin siepattavaksi verkkoliitännäksi enp0s3. Valitsin paketin ja otin seuraavan kuvan, johon merkitsin TCP/IP-mallin kerroksia.

<img width="513" alt="tcpip" src="https://github.com/user-attachments/assets/28e67664-6cc3-4128-8859-ca44764ce124" />

Kuvassa oranssilla rajattu alue on verkkokerros. Se sisältää MAC-osoitteet, joita paketin siirrossa tarvitaan. Vaaleansinisellä alueella rajattu alue on Internet-kerros, joka sisältää sekä lähde- että kohde-IP:n. Molempia IP:tä käytetään paketin reitittämiseen. Punaisella rajattu alue taasen on kuljetuskerros. Sieltä löytyy lähde- ja kohdeportit, joiden avulla TCP hallitsee tietoliikennettä. Sovelluskerrosta ei kuvasta suoraan näy, koska paketti liittyy HTTPS-liikenteeseen, joka käyttää TLS-salausta.

Tehtävä tuli valmiiksi 31.3.2025 klo 16.06.

### e) Mitäs tuli surffattua?
Pienen ruokatauon jälkeen palasin koneen äärelle 31.3.2025 klo 16.36. Avasin virtuaalikoneen ja suuntasin sen selaimella [kurssisivulle](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h1-sniff), jotta sain napattua virtuaalikoneelle surfing-secure.pcapin. Avasin tiedoston Wiresharkissa ja aloin tutkailemaan sitä.

Löysin kaappauksesta kaksi IP-osoitetta eli liikennettä oli kahden laitteen välillä. Löysin tämän tiedon "Statistics"-valikon "Endpoints"-välilehdeltä. Seuraavaksi tutkailin saman valikon "Protocol Hierarchy"-välilehteä. Sieltä sain selville, että IPv4-liikenne on hallitsevaa, TCP-protokollaa on käytetty eniten kuljetuksessa ja TLS-liikennettäkin löytyi. Viimeksi mainittu viittaa siihen, että verkkosivut käyttivät HTTPS-protokollaa. Kaapattuja paketteja oli 283. Kaappaus kesti noin seitsemän sekuntia, mikä viittaa esimerkiksi lyhyeen verkkosivun lataamiseen.

Sain tehtävän valmiiksi 31.3.2025 klo 16.38.

### g) Minkä merkkinen verkkokortti käyttäjällä on?
Aloin selvittelemään käyttäjän verkkokorttia 31.3.2025 klo 17.15. Suuntasin tuttuun tapaan Wiresharkin pariin ja avasin siellä surfing-secure.pcapin. Tiedostosta etsin mistä tahansa paketista Ethernet II -osion, josta pystyisin selvittämään käyttäjän verkkokortin. Sain selville käyttäjän verkkokortin olevan RealTekU.

<img width="325" alt="image" src="https://github.com/user-attachments/assets/6c7efbf9-523b-47fa-b675-cac82f421994" />

Tehtävä tuli päätökseensä 31.3.2025 klo 17.25.

### h) Millä weppipalvelimella käyttäjä on surffaillut?
Kerrankin aloin tekemään tehtävää heti edellisen tehtävän jälkeen! Aloitin tämän tehtävän tekemisen tutkailemalla Wiresharkia. Kirjoitin hakuun seuraavan:

    tls.handshake.extensions_server_name.
    
Tämä ei antanut mitään ihmeempää tietoa, joten suuntasin nokkani kohti Internetiä! Hetken metsästyksen jälkeen löysin [Wiresharkin verkkosivun](https://osqa-ask.wireshark.org/questions/55754/whata-a-display-filter-that-matches-dns-queries-for-a-particular-host-name/). Verkkosivulta sain altalöytyvän komennon.

    dns.qry.name

Komennolla pystyin näkemään, millä weppipalvelimilla käyttäjä on surffaillut! Löytyi google.com ja terokarvinen.com. Näiden tietojen myötä päätin tehtävän klo 17.48.

### i) Analyysi
Nopean tauon jälkeen päätin rutistaa vielä tämän viimeisenkin tehtävän. Tässä kohtaa kello oli 17.58. Palasin takaisin Wiresharkin pariin. Tosin avasin uuden ikkunan, koska nyt piti siepata omaa liikennettä. Valitsin verkkoliitynnäksi enp0s3. Sieppasin sen liikennettä neljän paketin verran ennen kuin pysäytin sieppaamisen.

<img width="640" alt="image" src="https://github.com/user-attachments/assets/86872025-3d59-4e45-aec1-4786aac1f16a" />

Sain selville, ensimmäisen ja viimeisen, eli neljännen, paketin saapuneen hyvin lyhyen ajan sisällä toisistaan. Ei mikään ihme, kun liikennettä seurattiin vain muutaman paketin ajan. Paketit ovat mahdollisesti tulleet samasta TCP-istunnosta. Protokollana on toiminut TCP ja TLSv1.2. TCP on hoitanut luotettavan tiedonsiirron. Samalla TLSv1.2 on salannut tietoja ja varmistanut tietoturvaa sovellustasolla. Ensimmäisen ja viimeisen paketin lähdeosoitteena on ollut 10.0.2.15 ja kohdeosoitteena 34.117.188.166. Toisella ja kolmannella paketilla osoitteet olivat toisinpäin, eli lähdeosoite oli 34.11.188.166 ja kohdeosoite 10.0.2.15. Osoite 34.117.188.166 on etäkohteen, kun taas 10.0.2.15 on lähtöisin paikallisesta koneestani.

Tehtävä tuli valmiiksi klo 18.17.



## Lähteet

### Kurssisivu
Karvinen, T. (2025). Verkkoon tunkeutuminen ja tiedustelu. Haettu 31.3.2025, osoitteesta: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/

### Asennus ja Wireshark
Karvinen, T. (2021). Install Debian on VirtualBox. Haettu 29.3.2025, osoitteesta: https://terokarvinen.com/2021/install-debian-on-virtualbox/
Karvinen, T. (2025). Wireshark - Getting Started. Haettu 30.3.2025, osoitteesta: https://terokarvinen.com/wireshark-getting-started/

### Liikenteen kaappaus
Karvinen, T. (2025). Network Interface Names on Linux. Haettu 30.3.2025, osoitteesta: https://terokarvinen.com/network-interface-linux/
Karvinen, T. (2025). Wireshark - Getting Started. Haettu 30.3.2025, osoitteesta: https://terokarvinen.com/wireshark-getting-started/
Wireshark Q&A. What a display filter that matches DNS queries for a particular host name? Haettu 31.3.2025, osoitteesta: https://osqa-ask.wireshark.org/questions/55754/whata-a-display-filter-that-matches-dns-queries-for-a-particular-host-name/
