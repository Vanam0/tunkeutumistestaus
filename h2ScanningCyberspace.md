#
clear
echo -n " 
 █▀▄ ▄▀▄ █   █ █▄ █ █▀▄ █▀▄ ▄▀▄ █▄ ▄█ ██▀   ▄▀▀ █▄█ ██▀ ▄▀▀ █▄▀ ██▀ █▀▄
 █▀  █▀█ █▄▄ █ █ ▀█ █▄▀ █▀▄ ▀▄▀ █ ▀ █ █▄▄   ▀▄▄ █ █ █▄▄ ▀▄▄ █ █ █▄▄ █▀▄
	

"
sleep 1
                                                                      
echo -n 'Type  '







# Scanning Cyberspace



Tässä harjoituksessa toteutan porttiskannauksen virtuaaliympäristössä (VM virtualBox), jossa käytän Kali Linux -käyttöjärjestelmää, Metasploitable 2 -virtuaalitietokonetta. Tarkoituksena on syventää ymmärrystäni porttiskannauksen perusteista, erilaisista skannaustekniikoista ja niiden vaikutuksista, sekä näden virtuaalikoneiden eristämiminen toisistaan luomassani virtuaaliverkossa.





# Porttiskaunnauksen perusteet

- Avoin (open):
 Palvelu hyväksyy aktiivisesti TCP-yhteyksiä, UDP-datagrammeja tai SCTP-liittymiä kyseisellä portilla. Kyberhyökkääjät ja pentestaajat haluavat hyödyntää avoimia portteja. Järjestelmänvalvojat yrittävät sulkea tai suojata niitä palomuurilla. Avoin portti on kiinnostava myös ei-turvallisuuteen liittyvissä skannauksissa, koska se osoittaa verkossa käytettävissä olevat palvelut.
- Suljettu (closed):
 Portti on saavutettavissa, mutta mikään palvelu ei kuuntele suljettua porttia. Suljetut portit voi osoittaa, että isäntä on aktiivinen IP-osoitteessa (a host is up), nämä ovat osa käyttöjärjestelmän tunnistusta.
- Suodatettu (filtered): 
Nmap ei voi määrittää, onko portti avoin, koska pakettisuodatus estää sen testilähetykset tavoittamasta porttia.  Nämä portit ärsyttävät kyberhyökkääjiä, koska ne tarjoavat niin vähän dataa. Tämä hidastaa skannausta merkittävästi. Joskus nämä vastaavat ICMP-virheviesteillä, kuten: Tyyppi 3 koodi 13 (määränpää ei tavoitettavissa, kommunikaatio hallinnollisesti estetty).
- Suodattamaton (unfiltered):
 Porttiin pääsee käsiksi, mutta Nmap ei pysty määrittämään, onko portti avoin vai suljettu. Tämä tila on yleensä seurausta palomuurien konfiguroinnista.
- Avoin tai suodatettu (open|filtered): 
Nmap sijoittaa portit tähän tilaan, kun se ei pysty määrittämään, onko portti avoin vai suodatettu. Tämä tapahtuu skannaustyypeissä, joissa avoimet portit eivät anna vastausta.
- Suljettu tai suodatettu (closed|filtered): 
Tämä tila ilmenee, kun Nmap ei pysty määrittämään, onko portti suljettu vai suodatettu. Tätä tilaa käytetään vain IP ID -lepo-skannauksessa.

# Porttiskannus -tekniikat


Porttiskannauksen tekniikat:

- `sS:`:
SYN-skannaus on oletusarvoinen ja suosituin vaihtoehto. Se suoritetaan nopeasti, skannaten tuhansia portteja sekunnissa nopealla verkolla, eikä sitä hidasta rajoittavat palomuurit. SYN-skannaus on myös suhteellisen huomaamaton, koska se ei täydennä TCP-yhteyksiä. Lisäksi se toimii minkä tahansa yhteensopivan TCP-pinon kanssa ja mahdollistaa selkeän erottelun avointen, suljettujen ja suodatettujen tilojen välillä.

- `sT` (TCP connect scan): Oletus TCP-skannausvaihtoehto, kun SYN-skannaus ei ole mahdollinen. Se käyttää korkean tason järjestelmäkutsua yhteyden muodostamiseksi, mikä voi aiheuttaa pidempiä skannausaikoja ja lisääntyneen havaitsemisen riskin, eli se voi aiheuttaa merkintöjä järjestelmän lokitiedoissa tai jopa palveluiden kaatumisen, joka voi paljastaa skannauksen.

- `sU`: UDP-skannaus käyttää -sU-optiota. Se voidaan yhdistää TCP-skannustyyppiin, kuten SYN-skannaukseen, jotta voidaan tarkistaa molemmat protokollat samalla suorituksella. Nmap käyttää UDP-skannauksessa tyhjiä paketteja ja ICMP-virheilmoituksia porttien tilan tunnistamiseen. UDP-skannauksen nopeuttamiseksi voidaan kokeilla useampien isäntien skannaamista samanaikaisesti, aloittaa skannaus suosituimmista porteista ja käyttää host timeout -optiota hidastuvien isäntien ohittamiseksi.

> Näiden ohessa lueteltujen tekniikoiden avulla voi syventää tietämsytä kyberturvallisuudesta ja turvata tietoverkkoja. Miten nämä skannaustekniikat vaikuttavat verkon suorituskykyyn? Käyttämällä näitä tietoja voisi jo suunnitella omaa tietoturvastrategiaa omalle labraalustalle.

> Esimerkki: nmap -sS -sU -p 1-1000 target_ip


# Tietomurron yritys ja kyberturvallisuus 

Tässä [dokumentissa](https://finlex.fi/fi/oikeus/kko/kko/2003/20030036) (Luettu 9.4.2024) käsitellään tapausta, jossa henkilöä syytettiin tietomurron yrityksestä ja hänen suorittamasta porttiskannauksesta. Tapauksen käsittelyssä korostui kyberturvallisuuden merkitys ja sen yhteys rikosoikeudelliseen vastuuseen.

Tämä tapaus osoittaa, kuinka tietoverkkoihin kohdistuvat hyökkäykset ja yritykset voivat aiheuttaa merkittävää vahinkoa organisaatioille. Porttiskannaus, jossa henkilö yritti skannata Osuuspankkikeskusen tietojärjestelmän portteja, katsottiin tietomurron yritykseksi. Vaikka syytetty väitti suorittaneensa skannauksen pelkästään kiinnostuksesta, se koitui hänelle rangaistavaksi teoksi, koska skannauksen tarkoituksena oli mahdollistaa pääsy tietojärjestelmään. Tapauksessa Osuuspankkikeskus joutui käyttämään merkittäviä resursseja tapauksen selvittämiseen ja vahinkojen korjaamiseen. Vaikka syyteteyn ikä ja kokemus huomioitiin oikeudenkäynnissä, hänet velvoitettiin silti korvaamaan aiheuttamansa vahingot.

Lukijan näkökulmasta tapaus korostaa tietojärjestelmien turvajärjestelyiden kehittämisen ja ylläpidon tärkeyttä. Vaikka Osuuspankkikeskuksen palomuuri esti henkilön tunkeutumisen tietojärjestelmään. Dokumentti osoittaa, että aktiiviset hyökkäykset tietojärjestelmiin ovat todellinen uhka ja vaativat valmiutta puolustautua. Tämän tyyppisiin tilanteisiin tarvitaan ammattitaitoisia kyberturvallisuuden asiantuntijoita.




 ##  Metasploitable 2 asennus

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/a31c7308-a399-4efa-bfa3-fac9bd5d3c57)


 Metasploitable 2:n virtuaalitietokoneen asentaminen manuaalisesti.


 msfadmin
 ![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9bc2c5f1-2ce4-47eb-bc59-3e764fd874e0)


Vastaako?

#sniifaus
`db_nmap -sn`







## Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/

https://nmap.org/book/man-port-scanning-basics.html

https://nmap.org/book/man-port-scanning-techniques.html

https://nmap.org/book/man-port-scanning-basics.html

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036
