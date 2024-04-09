


    x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva kustakin artikkelista. Kannattaa lisätä myös jokin oma ajatus, idea, huomio tai kysymys.)
        Lyon 2009: Nmap Network Scanning: Chapter 15. Nmap Reference Guide:
            Port Scanning Basics (opettele, mitä tarkoittavat: open, closed, filtered; muuten vain silmäily)
            Port Scanning Techniques (opettele, mitä ovat: -sS -sT -sU; muuten vain silmäily)
        KKO 2003:36. Alaikäinen tuomittiin Osuuspankkikeskuksen porttiskannaamisesta, korkeimman oikeuden ratkaisu.
        Vapaavalintainen läpikävely 0xdf tai ippsec (Kannattaa valita helppo; esim "Base Points: Easy")






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

Tässä [dokumentissa](https://finlex.fi/fi/oikeus/kko/kko/2003/20030036) käsitellään tapausta, jossa henkilöä syytettiin tietomurron yrityksestä ja hänen suorittamasta porttiskannauksesta. Tapauksen käsittelyssä korostui kyberturvallisuuden merkitys ja sen yhteys rikosoikeudelliseen vastuuseen.

Tämä tapaus osoittaa, kuinka tietoverkkoihin kohdistuvat hyökkäykset ja yritykset voivat aiheuttaa merkittävää vahinkoa organisaatioille. Porttiskannaus, jossa henkilö yritti skannata Osuuspankkikeskusen tietojärjestelmän portteja, katsottiin tietomurron yritykseksi. Vaikka syytetty väitti suorittaneensa skannauksen pelkästään kiinnostuksesta, se koitui hänelle rangaistavaksi teoksi, koska skannauksen tarkoituksena oli mahdollistaa pääsy tietojärjestelmään. Tapauksessa Osuuspankkikeskus joutui käyttämään merkittäviä resursseja tapauksen selvittämiseen ja vahinkojen korjaamiseen. Vaikka syyteteyn ikä ja kokemus huomioitiin oikeudenkäynnissä, hänet velvoitettiin silti korvaamaan aiheuttamansa vahingot.

Lukijan näkökulmasta tapaus korostaa jatkuvan kehityksen ja ylläpidon merkitystä tietojärjestelmien turvajärjestelyissä. Vaikka Osuuspankkikeskuksen palomuuri esti henkilön tunkeutumisen, se osoittaa, että aktiiviset hyökkäykset tietojärjestelmiin ovat todellinen uhka ja vaativat jatkuvaa valppautta sekä valmiutta puolustautua. Tämäntyyppisiin tilanteisiin tarvitaan ammattitaitoisia kyberturvallisuuden asiantuntijoita.

















## Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/

https://nmap.org/book/man-port-scanning-basics.html

https://nmap.org/book/man-port-scanning-techniques.html

https://nmap.org/book/man-port-scanning-basics.html

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036
