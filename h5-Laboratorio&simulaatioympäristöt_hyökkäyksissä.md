# h5 - Laboratorio- ja simulaatioympäristöt hyökkäyksissä

## Tehtävät

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

