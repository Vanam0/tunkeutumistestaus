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
Nmap sijoittaa portit tähän tilaan, kun se ei pysty määrittämään, onko portti avoin vai suodatettu. Tämä tapahtuu skannaustyypeissä, joissa avoimet portit eivät anna      vastausta.
- Suljettu tai suodatettu (closed|filtered): 
Tämä tila ilmenee, kun Nmap ei pysty määrittämään, onko portti suljettu vai suodatettu. Tätä tilaa käytetään vain IP ID -lepo-skannauksessa.





















## Lähteet:
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
https://nmap.org/book/man-port-scanning-basics.html
