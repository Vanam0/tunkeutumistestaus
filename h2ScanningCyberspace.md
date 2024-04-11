







# Scanning Cyberspace



Tässä harjoituksessa toteutan porttiskannauksen virtuaaliympäristössä (VM virtualBox), jossa käytän Kali Linux -käyttöjärjestelmää, Metasploitable 2 -virtuaalitietokonetta. Tarkoituksena on syventää ymmärrystäni porttiskannauksen perusteista, erilaisista skannaustekniikoista ja niiden vaikutuksista, sekä näden virtuaalikoneiden eristämiminen toisistaan luomassani virtuaaliverkossa.





# Porttiskaunnauksen perusteet

- Avoin (open):
Avoimet portit hyväksyy TCP-yhteyksiä, UDP-datagrammeja tai SCTP-protokollaä kyseisellä portilla, johon muun muassa Apache ja SSH voivat olla määritetty kuuntelemaan liikennettä. Avoimet portit paljastavat myös verkon käytössä olevat palvelut.
- Suljettu (closed):
Suljetut portit eivät ole aktiivisessa kuuntelutilassa, ei odota saapuvia paketteja. Ne voivat kuitenkin viitata, että isäntä on aktiivinen IP-osoitteessa. Tämä voi olla osa käyttöjärjestelmän tunnistusta, mutta se ei suoraan osoita isännän aktiivisuutta (host is up).
- Suodatettu (filtered): 
Suodatetut portit vaikeuttavat Nmapin kaltaisia skannereita määrittämään portin tilaa, koska pakettisuodatus estää testilähetykset tavoittamasta porttia. Tämä hidastaa skannausta ja antaa vähän tietoa hyökkääjille. Vastauksena ne voivat lähettää mm. ICMP-virheviestejä, kuten "Määränpää ei tavoitettavissa, kommunikaatio hallinnollisesti estetty" (tyyppi 3, koodi 13).






# Porttiskannus -tekniikat


Porttiskannauksen tekniikat:

- `sS:`:
SYN-skannaus on yleisin ja suosituin skannausmenetelmä. Se on nopea ja tehokas, skannaten tuhansia portteja sekunnissa. Palomuurit eivät hidasta skannausta. Koska SYN-skannaus ei täydennä TCP-yhteyksiä, se on huomaamaton. Toimii kaikkien yhteensopivien TCP-pinojen kanssa ja erottaa selkeästi avoimet, suljetut ja suodatetut portit

- `sT` (TCP connect scan): Oletus TCP-skannausvaihtoehto, kun SYN-skannaus ei ole mahdollinen. Se käyttää korkean tason järjestelmäkutsua yhteyden muodostamiseksi, mikä voi aiheuttaa pidempää latenssia ja lisääntyneen havaitsemisen riskin, eli se voi aiheuttaa merkintöjä järjestelmän lokitiedoissa tai jopa palveluiden kaatumisen, joka voi paljastaa skannauksen.

- `sU`: UDP-skannaus onnistuu -sU-optiolla. Voidaan yhdistää muihin skannausmenetelmiin, kuten SYN-skannaukseen, jotta tarkistetaan sekä UDP- että TCP-portit samalla kertaa. Nmap lähettää UDP-skannauksessa tyhjiä paketteja ja tarkkailee ICMP-virheilmoituksia porttien tilan selvittämiseksi. Skannauksen nopeuttamiseksi voidaan kokeilla samanaikaista skannausta useammilta isäntiltä, aloittaa skannaus suosituimmista porteista ja käyttää host timeout -optiota hidastuvien isäntien ohittamiseksi.

> Näiden ohessa lueteltujen tekniikoiden avulla voi syventää tietämsytä kyberturvallisuudesta ja turvata tietoverkkoja. Miten nämä skannaustekniikat vaikuttavat verkon suorituskykyyn? Käyttämällä näitä tietoja voisi jo suunnitella omaa tietoturvastrategiaa omalle labraalustalle.

> Esimerkki: nmap -sS -sU -p 1-1000 target_ip


# Tietomurron yritys ja kyberturvallisuus 

Tässä [dokumentissa](https://finlex.fi/fi/oikeus/kko/kko/2003/20030036) (Luettu 9.4.2024) käsitellään tapausta, jossa henkilöä syytettiin tietomurron yrityksestä ja hänen suorittamasta porttiskannauksesta. Tapauksen käsittelyssä korostui kyberturvallisuuden merkitys ja sen yhteys rikosoikeudelliseen vastuuseen.

Tämä tapaus osoittaa, kuinka tietoverkkoihin kohdistuvat hyökkäykset ja yritykset voivat aiheuttaa merkittävää vahinkoa organisaatioille. Porttiskannaus, jossa henkilö yritti skannata Osuuspankkikeskusen tietojärjestelmän portteja, katsottiin tietomurron yritykseksi. Vaikka syytetty väitti suorittaneensa skannauksen pelkästään kiinnostuksesta, se koitui hänelle rangaistavaksi teoksi, koska skannauksen tarkoituksena oli mahdollistaa pääsy tietojärjestelmään. Tapauksessa Osuuspankkikeskus joutui käyttämään merkittäviä resursseja tapauksen selvittämiseen ja vahinkojen korjaamiseen. Vaikka syyteteyn ikä ja kokemus huomioitiin oikeudenkäynnissä, hänet velvoitettiin silti korvaamaan aiheuttamansa vahingot.

Lukijan näkökulmasta tapaus korostaa tietojärjestelmien turvallisuuden kehittämisen ja ylläpidon tärkeyttä. Vaikka Osuuspankkikeskuksen palomuuri esti henkilön tunkeutumisen tietojärjestelmään. Dokumentti osoittaa, että aktiiviset hyökkäykset tietojärjestelmiin ovat todellinen uhka ja vaativat valmiutta puolustautua. Tämän tyyppisiin tilanteisiin tarvitaan ammattitaitoisia kyberturvallisuuden asiantuntijoita.




 ##  Metasploitable 2 asennus

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/a31c7308-a399-4efa-bfa3-fac9bd5d3c57)


  > Metasploitable 2:n virtuaalitietokoneen asentaminen manuaalisesti virtuaalikoneympäristöön.

## Virtuaaliverkko

Molemmat virtuaalitietokoneet Kali Linux että Metasploitable 2, ovat liitetty luomaani host-only -verkkoon, näin se on eristetyssä ympäristössä ja turvallinen harjoittelua varten, virtuaaliverkko luotiin VirtualBoxin hallintapaneelin kautta. Sammutan myös verkkoyhteyden harjoittelun ajaksi. 
Kirjaudutaan sisälle msfadmin -tunnuksilla 
 ![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9bc2c5f1-2ce4-47eb-bc59-3e764fd874e0)
> Internet-yhteys katkeaa, voidaan suorittaa ping-komento ulkoisella IP-osoitteella, Google DNS:lle 8.8.8.8.

Vastaako?

#sniifaus
`db_nmap -sn`







## Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h2-scanning-cyberspace

https://nmap.org/book/man-port-scanning-basics.html

https://nmap.org/book/man-port-scanning-techniques.html

https://nmap.org/book/man-port-scanning-basics.html

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036
