# h0 - sieppari ruispellossa

Käytän materiaalina aiempaa Wireshark tehtävääni Wireshark -haastetta, eli kyseessä on siis täysin valmiiksi tallennettu verkkopakettitiedosto, jotta pystyisin analysoimaan kahta erillaista skenaariota ja vertailemaan niitä keskenään. 
Aloitan avaamalla tiedoston challenge101-6.pcapng (Packet Capture Next Generation) -tiedostomuoto, jota käytetään verkkopakettien tallentamiseen ja analysointiin. 


Ylälaidassa näkyy tietoja, kuten:
- Paketin numero (No.)
- Aika (time)
- Kohde, eli IP-osoitte tai verkkolöaite, johon paketti on tarkoitettu (Destination)
- Lähde, IP-osoite tai verkkolaite johon paketti on lähetetty (Source)
- Verkkoprotokolla TCP, UDP, HTTP, DNS jne. (Protocol)
- Paketin pituus tavuina, joka kertoo kuinka monta tavua paketti sisältää. Se on erityisen tärkeää verkkoliikenteen tunnistamisessa mm. valvontapaketit (Length)


![2073a7145d3ebf69103b780da3a8a476](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/4496bf99-9b94-4da2-8545-8c80b399c218)

Wiresharkissa on erillaisia värikoodeja:
Vihreä, on onnistunut ja hyväksytty (HTTP HyperText Transfer Protocol)
Punainen, tarkoittaa ongelmia sisältäviä paketteja, jotka voivat olla hylättyjä tai virheellisiä (TCP-yhteys Transmission Control Protocol)
Harmaa: TCP-protokollaan liittyvät tapahtumat, kuten handshaket (kädenpuristusvaiheet) tai yhteyden sulkemiset.
Vaalensininen: UDP (User Datagram Protocol)

Seuravaaksi haluan filteröidä vain ACK-paketteja, koska ACK-paketti on TCP-protokollan käyttämä viesti, joka vahvistaa tietyn datan vastaanottamisen varmistamalla tiedonsiirron luotettavuuden.
![f220c2c57aeec8ed5c88da62c1cfe7d1](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/5ffa0117-6a5d-413b-8b46-6a056137716b)
Huomioitavaa, että (RST-paketteja käytetään yleensä yhteyden sulkemiseen tai sen nollaamiseen eikä tietojen vahvistamiseen.)
Lähdeportti: 18472
Kohdeportti: 80/443 (HTTPS/HTTP-protokolla)




Oman verkkoliikenteeni analysointia
![65dfc77c20db68f40a78ba7d56000fdb](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/64193389-461d-46f9-9d0f-173d1fdf7754)
Ilmenee Multicast Listeners Report Message 130 -viesti, joka ei ole epätavallinen, koska se on osa IPv6-verkon hallintaa ja reititystä.
IGMPv3 (Internet Group Management Protocol version 3) -liittymisraportti keltaisella värikoodilla on myös vastaava multicast-ryhmään liittymisviesti kuin ylempi kuuntelijaraporttiviesti IPv6:ssa. 
Näkyy myös 224.0.0.253 IP-osoite, joka on tarkoitettu käytettäväksi vain paikallisessa verkkoympäristössä eikä se reitity internetin ulkopuolelle, eli liikenne on täysin normaalia eikä siinä ole mitään huomioitavaa.


Yhteenvetona voisin todeta, että omassa verkkoliikenteessäni ei näy mitään jännittävää, mutta Wireshark Challengessa on näkyvillä enemmän värikoordeja, joten halusin vertailla näitä kahta keskenään. 



## References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h0-sieppari-ruispellossa
Metropolia Basic Network Analyzing with Wireshark -kurssimateriali
https://youtu.be/t5OJephyw8I?si=siYoUYOEysa-XahJ
https://learningnetwork.cisco.com/s/question/0D53i00000Kt6xVCAR/what-do-ipv6-multicast-listener-report-messages-do


