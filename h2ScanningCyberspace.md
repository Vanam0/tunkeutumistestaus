







# Scanning Cyberspace



Tässä harjoituksessa toteutan porttiskannauksen virtuaaliympäristössä (VM VirtualBox), jossa käytän Kali Linux -käyttöjärjestelmää, Metasploitable 2 -virtuaalitietokonetta. Tarkoituksena on syventää ymmärrystäni porttiskannauksen perusteista, erilaisista skannaustekniikoista ja niiden vaikutuksista, sekä näden virtuaalikoneiden eristämiminen toisistaan luomassani virtuaaliverkossa.





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

- `sU`: UDP-skannaus onnistuu -sU-optiolla. Voidaan yhdistää muihin skannausmenetelmiin, kuten SYN-skannaukseen, jotta tarkistetaan sekä UDP- että TCP-portit samalla kertaa. Nmap lähettää UDP-skannauksessa tyhjiä paketteja ja tarkkailee ICMP-virheilmoituksia porttien tilan selvittämiseksi. Skannauksen nopeuttamiseksi voidaan kokeilla samanaikaista skannausta useammilta isäntiltä mm. Aloittamalla skannaus suosituimmista porteista ja käyttämällä host timeout -optiota hidastuvien isäntien ohittamiseksi.

> Näiden ohessa lueteltujen tekniikoiden avulla voi syventää tietämsytä kyberturvallisuudesta ja turvata tietoverkkoja. Miten nämä skannaustekniikat vaikuttavat verkon suorituskykyyn? Käyttämällä näitä tietoja voisi jo suunnitella omaa tietoturvastrategiaa omalle labraalustalle.




# Tietomurron yritys ja kyberturvallisuus 

Tässä [dokumentissa](https://finlex.fi/fi/oikeus/kko/kko/2003/20030036) (Luettu 9.4.2024) käsitellään tapausta, jossa henkilöä syytettiin tietomurron yrityksestä ja hänen suorittamasta porttiskannauksesta. Tapauksen käsittelyssä korostui kyberturvallisuuden merkitys ja sen yhteys rikosoikeudelliseen vastuuseen.

Tämä tapaus osoittaa, kuinka tietoverkkoihin kohdistuvat hyökkäykset ja yritykset voivat aiheuttaa merkittävää vahinkoa organisaatioille. Porttiskannaus, jossa henkilö yritti skannata Osuuspankkikeskusen tietojärjestelmän portteja, katsottiin tietomurron yritykseksi. Vaikka syytetty väitti suorittaneensa skannauksen pelkästään kiinnostuksesta, se koitui hänelle rangaistavaksi teoksi, koska skannauksen tarkoituksena oli mahdollistaa pääsy tietojärjestelmään. Tapauksessa Osuuspankkikeskus joutui käyttämään merkittäviä resursseja tapauksen selvittämiseen ja vahinkojen korjaamiseen. Vaikka syyteteyn ikä ja kokemus huomioitiin oikeudenkäynnissä, hänet velvoitettiin silti korvaamaan aiheuttamansa vahingot.

Lukijan näkökulmasta tapaus korostaa tietojärjestelmien turvallisuuden kehittämisen ja ylläpidon tärkeyttä. Vaikka Osuuspankkikeskuksen palomuuri esti henkilön tunkeutumisen tietojärjestelmään. Dokumentti osoittaa, että aktiiviset hyökkäykset tietojärjestelmiin ovat todellinen uhka ja vaativat valmiutta puolustautua. Tämän tyyppisiin tilanteisiin tarvitaan ammattitaitoisia kyberturvallisuuden asiantuntijoita.




 ##  Metasploitable 2 -asennus

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/a31c7308-a399-4efa-bfa3-fac9bd5d3c57)


  > Metasploitable 2:n virtuaalitietokoneen asentaminen manuaalisesti virtuaalikoneympäristöön.

## Virtuaaliverkko

Molemmat virtuaalitietokoneet Kali Linux että Metasploitable 2, ovat liitetty luomaani host-only -verkkoon, näin se on eristetyssä ympäristössä ja turvallinen harjoittelua varten, virtuaaliverkko luotiin VirtualBoxin hallintapaneelin kautta. Sammutan myös verkkoyhteyden harjoittelun ajaksi. 
Kirjaudutaan sisälle msfadmin -tunnuksilla 

 ![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9bc2c5f1-2ce4-47eb-bc59-3e764fd874e0)
 
Varmistamme, ettei Metasploitable 2:lla ole Internet-yhteyttä suorittamalla ping-komento ulkoisella IP-osoitteella, Google DNS:lle 8.8.8.8. 


## Sniffaus



![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/29909b05-106c-46c1-9fe1-be2046e3482c)

- Aloitan koko tehtävän, käynnistämällä PostgreSQL-tietokantapalvelimen, jota käytetään tallentamaan Metasploit Frameworkin tietokantaan kerättyä tietoa.
komenolla: `systemctl start postgresql`.

- Alustetaan Metasploit Frameworkin tietokanta, luoden tarvittavat tietokantataulut ja asetukset PostgreSQL-tietokantaan, komennolla: `msfdb init`

Käynnistetään Metasploit Frameworkin `msfconsole` -shell, joka on interaktiivinen työkalu haavoittuvuuksien analysointiin ja hyökkäysten suorittamiseen.


![-sn komento](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/4c04eab3-eb74-4b44-8476-93ae915ca5ea)

- `db_nmap -sn` Komento suorittaa Nmap-skannauksen ja tallentaa tulokset Metasploit-tietokantaan, käytetään targettina IP-osoitetta.

![-A komento](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/940490a6-5136-4bda-bd06-1901a82770e4)

- `db_nmap -A -p0-` suorittaa Metasploit Frameworkin db_nmap -porttiskannauksen. Tässä käytetään `-A` -parametria, joka suorittaa laajan skannauksen, `-p0` -parametri määrittää skannaamaan kaikki portit.

Lopuksi suoritin komennon `script -fa log001.txt`, tallentaakseen shell-session tekstitiedostoon script-työkalulla.



  
## Analysointi

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/d8b489b8-d7c8-4f43-80ce-3949793f4cc8)


> Wireshark -näkymä


Esimerkki: Lähetettiin TCP-paketti kohti kohdeporttia: 23 (SYN, "Vastaatko?"). Kohde vastasi TCP-paketilla (SYN, ACK; "Vastaan!"). Tämän jälkeen osapuoli katkaisi yhteyden (RST "Heippa!"). Telnet kuunteli yhteyksiä.

Huomaamme myös: 
Wiresharkin näyttämässä paketissa "[FIN, PSH, URG] SEG=1 WIN=1073725440 seuraavat asiat:

- `FIN`: Tarkoittaa TCP-paketin "Finish" -lippua, joka kertoo, että lähettäjä on valmis sulkemaan yhteyden Kalin ja Meta2 välillä.
- `PSH`: Tarkoittaa "Push" -lippua, eli tietoja tulisi "pushata" vastaanottavaan sovellukseen mahdollisimman nopeasti.
- `URG`: Tämä on "Urgent" -lippu, joka osoittaa, että paketissa on tärkeitä tietoja, jotka tulisi käsitellä kiireellisesti.
- `SEG=1`: Tämä ilmaisee, että paketin numero on 1. Tämä auttaa järjestämään ja seuraamaan paketteja.
- `WIN=1073725440`: Tämä on TCP-ikkunan koko, joka kertoo vastaanottajalle, kuinka paljon paketteja lähettäjä voi lähettää ennen kuin odottaa vastausta

> Tyypillisesti, TCP-pakettien otsakkeet sisältävät tietoja kuten lähettäjän ja vastaanottajan porttinumerot, sekvenssinumeron, tunnisteet, otsakepituuksen, kontrollibitit (esimerkiksi SYN, ACK, FIN jne.) ja tarkistussumman. Näitä tietoja käytetään pakettien reitittämiseen ja yhteyden hallintaan.


![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/30b98645-956e-4daf-967b-921e6c695568)

Halusin tarkastella lisää TCP-paketteja Wiresharkissa, erityisesti kiinnittäen huomiota URG-lipun esiintymiseen ja heksadesimaalikoodiin `ff`.

Suoritin suodatuksen Wiresharkissa ilmaisemalla `TCP.flags.urg == 1:`. Tämä suodatin näytti meille kaikki ne TCP-paketit, joissa Urgent-lippu oli asetettu. Tämä auttoi tunnistamaan kaikki tärkeät paketit, joissa on kiireellistä tietoa.

Heksakoodi `ff`:
Tutkin tarkemmin heksadesimaalikoodia `ff`, joka esiintyy usein Wiresharkin näyttämässä pakettitietojen heksaesitykysessä. `ff` edustaa 8-bittistä binääritietoa.
Tämä 8-bittinen binääriluku, jonka binäärimuoto on 11111111, toimii usein monissa verkkoprotokollissa joko datan käytön merkkinä tai protokollan tunnisteena. Mielenkiintoista on, että yhdistämällä ff URG-lippuun voidaan tarkkailla verkkoliikennettä ja tunnistaa mahdollisia poikkeavuuksia.







# Telnet vs. SSH


![telnet1](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/8f3a2161-a1f1-4884-ab79-9059490df82a)

Seuraavaksi haluan ottaa Telnet-protokollan (-p23) mukaan analyysiin vertailutarkoituksessa, koska sen avulla voidaan havaita haavoittuvuuksia, kuten avoin Telnet-portti, joka voi altistaa haavoittuvuuksille, erityisesti jos käytössä on vanhentunut Telnet-palvelinversio.

- Wireshark -näkymässä huomaamme, että käyttäjän syöttämät tiedot: salasana, lähetetään salaamattomana verkon yli. Kun käyttäjä kirjautuu Metasploitableen Telnetin avulla, sniffer voi havaita ja tallentaa kaiken Telnet-liikenteen. SSH-protokolla tarjoaisi turvallisen vaihtoehdon Telnetin käytölle, sillä se salaa verkkoliikenteen, mutta tämä vertailun vuoksi.

>Telnetiä ei enää laajasti käytetäkään nykyaikaisissa ympäristöissä tietoturvasyistä.

## Ammatillinen mielipide

Mielestäni tämä lähestymistapa on vanha, mutta silti erittäin relevantti tietoturvatehtävissä. Telnetin käyttö tietoturvariskeinä on tunnettu jo pitkään, ja sen vertaaminen turvallisempaan protokollaan, (SSH) havainnollistaa tietoturvan merkitystä.
Se toimii konkreettisena esimerkinä siitä, miten herkästi arkaluontoiset tiedot, kuten salasanat voivat vuotaa, jos käytetään vanhentunutta ja epäsalattua protokollaa, joten kannattaa suosia turvallisempia vaihtoehtoja.




## man nmap: runtime interaction

Nmapin ajonaikaiset toiminnot ovat hyödyllisiä skannauksen suorittamisen aikana.

Esimerkkejä:

- Verbosity Level Adjustment 'v' / 'V': Lisää tai vähentää tulostustason yksityisyyttä.
  
- Debugging Level Adjustment 'd' / 'D': Säätää vianetsintätason määrää.
  
- Packet Tracing (Pakettien jäljitys) 'p' / 'P': Käynnistää tai pysäyttää pakettien jäljityksen.
- Runtime Interaction Help Screen '?': Näyttää ohjesivun skannauksesta.

Muilla näppäimillä saa tilailmoituksen, joka kertoo skannauksen tilasta ja mahdollisista muutoksista.









## Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h2-scanning-cyberspace

https://nmap.org/book/man-port-scanning-basics.html

https://nmap.org/book/man-port-scanning-techniques.html

https://nmap.org/book/man-port-scanning-basics.html

https://youtu.be/VhUzVYccVKE?si=l6X6t_ri_e25VYH1 (TCP Urgent Bit and Urgent Pointer Field)

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036

https://www.hackers-arise.com/post/2017/01/25/metasploit-part-1-getting-started-with-metasploit

https://gist.github.com/fabionoth/ba46407d9cd03144150225715697c47f

https://nmap.org/book/man-runtime-interaction.html
