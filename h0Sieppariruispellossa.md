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

Wiresharkissa on erillaisia värikoodeja:
Vihreä: on onnistunut ja hyväksytty TCP-yhteys (Transmission Control Protocol, tietojen siirtäminen verkkoon) 
Punainen: tarkoittaa ongelmia sisältäviä paketteja, jotka voivat olla hylättyjä tai virheellisiä
Sininen: TCP-protokollaan liittyvät tapahtumat, kuten handshaket (kädenpuristusvaiheet) tai yhteyden sulkemiset.
Harmaa: Poistetut tai suljetut paketit 

Seuravaaksi haluan filteröidä vain ACK-paketteja, koska ACK-paketti on TCP-protokollan käyttämä viesti, joka vahvistaa tietyn datan vastaanottamisen varmistamalla tiedonsiirron luotettavuuden.
![f220c2c57aeec8ed5c88da62c1cfe7d1](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/5ffa0117-6a5d-413b-8b46-6a056137716b)
Huomioitavaa, että (RST-paketteja käytetään yleensä yhteyden sulkemiseen tai sen nollaamiseen eikä tietojen vahvistamiseen.)
Lähdeportti: 18472
Kohdeportti: 80 (HTTP-protokolla)








## References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h0-sieppari-ruispellossa
Metropolia Basic Network Analyzing with Wireshark -kurssimateriali
https://youtu.be/t5OJephyw8I?si=siYoUYOEysa-XahJ


