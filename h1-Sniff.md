# h1 - Sniff

## Tiivistelmät

### [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/)

### [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/)


## Tehtävät

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
