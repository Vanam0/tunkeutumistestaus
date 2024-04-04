# h1 - Hacker Warmup

## Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains
        Tiivistelmät 
        
On tärkeää ymmärtää tarkasti kyberuhat, niiden tarkoitukset ja toimintatavat. 
Tietoverkon puolustus on välttämätöntä, koska erillaiset kyberuhat kehittyvät koko ajan.
Teksti sisältää puolustustoimenpiteiden matriisin, joka on linjassa eri vaiheiden kanssa tunkeutumisen tappoketjussa (Kill Chain). Nämä toimet sisältävät mm. havaitsemisen, estämisen, häiritsemisen, heikentämisen, tiedustelun, harhauttamisen ja tuhoamisen. Näiden tarkoituksena on vastustaa hyökkääjän toimintaa eri vaiheissa.

Tunkeutumisen tappoketju (Kill Chain) on siis järjestelmällinen prosessi.
Useita tunkeutumistapauksia analysoidaan myös strategisesti, joka auttaa ajan myötä tunnistamaan niiden yhtenäisä piirteitä ja malleja. Jolloin se auttaa puolustajia arvioimaan puolustusasemaansa ja kehittämään strategioita mahdollisten aukkojen varalta.

APT = Advanced Persistent Threats, ovat edistyneitä ja jatkuvasti läsnä olevia tietoverkkouhkia, jotka pyrkivät hyökkäämään tietoverkkoihin pitkäaikaisesti ja huomaamattomasti. APT:t ovat yleensä suunniteltuja ja toteutettuja organisaatioita tai valtioita vastaan, ja niiden tavoitteena voi olla esim. tietovarkaudet, kybervalkoilu tai infrastruktuurin vahingoittaminen. APT-operaatiot käyttävät tekniikoita ja hyökkäystapoja sekä hyödyntävät usein heikkoja kohtia, kuten tietoturva-aukkoja järjestelmien puolustuksessa. APT-operaatiot voivat olla pitkäkestoisia ja vaikeasti havaittavia, joka tekee torjunnasta haastavaa.

## Get The Art of Hacking (Video Collection) now with the O’Reilly learning platform
O'Reillyn oppimisalustalla oli kattavasti tietoa videoissa erilaisista hakkerointitekniikoista ja tietoturvaan liittyvistä työkaluista.
Mielestäni videot olivat erittäin hyödyllisiä tietosisällöltään. 
Alusta oli itselleni uusi, joten ajattelen sen olevan hyödyllinen aloittelijoille kuin kokeneillekin henkilöille kyberturvallisuuden parissa.

Porttiskannerit:
- Nmap (Yksi hyödyllisimistä ja tunnetuimmista tietoturvatyökaluista, jolla suoritetaan monipuolista verkkoskannausta.)
- Masscan
- Udpprotoscanner

Web Service Review -työkalut:
- EyeWitness (Tallentaa verkkosivujen tilannekuvia ja -tietoja automaattisesti mm. HTTP-ohjauspyyntöjen tiedot, kuten otsikot ja vastaukset.)

Network and Web Vulnerability -skannerit, verkon haavoittuvuusskannukseen:
  
- Nessus
- OpenVAS (avoimen lähdekoodin haavoittuvuustarkastusjärjestelmä)

Web-haavoittuvuusskannerit:
- Nikito
- SQLMap: (SQL-tietokannat ja SQL-injektiot)
- Zed Attack Proxy (OWASP ZAP)
- Burp Suite (Monipuolinen ja laajalti käytetty tietoturvatyökalu, käytetään web-sovellusten haavoittuvuuksien löytämiseen ja hyödyntämiseen, sekä web-liikenteen analysointiin. Se toimii myös mm. proxyna ja skannerina.


        

## Wargames Bandit-haaste (level 0-2)



Kirjaudutaan Bandit-palvelimelle käyttäen salattua verkkoprotokollaa (Secure Shell). Siispä SSH-yhteys osoitteessa: bandit.labs.overthewire.org , porttiin 2220 käyttäen tunnusta bandit0 ja salasanaa bandit0 seuraavalla SSH-komennolla:

![dca76ff9eebef732bebb3cb894bad451](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/7868316f-71bc-46d4-8584-f9f66874fa59)




![f5d073472805d8b63ea6fbf410063c0f](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/e442d829-95ad-43ff-874d-2f3eac56dc52)

Aloitin tarkastelemalla hakemiston sisältöä käyttämällä komentoa `ls`, tämä komento listaa kaikki tiedostot ja hakemistot nykyisessä sijainnissa.
Tämän jälkeen käytin `cat`-komentoa tulostamaan readme-tiedoston sisällön. Cat on lyhenne sanasta "concatenate". Se yhdistää tiedostojen sisällön ja tulostaa sen terminaaliin.


![f89b547c931b63fc53e219868e44c1f4](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9ed39736-abd6-4a76-8b0e-f8627d52e58c) 

Seuraavaksi, siirryin bandit1-tasolle ja löysin uuden salasanan.



![c8d155630413ca7260eea3671ddf55e9](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/c2951bf8-b76b-4bd4-a693-55b721d2d2f1)



Siirryin bandit2-tasolle ja löysin tiedostosta jälleen uuden salasanan. Samalla käytin komentoa `ls -alps` tarkastaakseni kaikki mahdolliset tiedostot ja hakemistot hakemistossa myös piilotiedostot, jos niitä on. Käyttämällä tätä komentoa sain yksityiskohtaisen listan tiedostojen ja hakemistojen ominaisuuksista: Tiedostoon varatun tilan, joka viittaa siihen määrään levytilaa, jonka tiedosto tai hakemisto käyttää tallennustarkoituksiin. Se sisältää tiedoston datan lisäksi myös tiedoston metatiedot, kuten otsikot, järjestelyt hakemistorakenteessa ja muut yksityiskohdat, jotka vaativat tilaa tallennukseen.










## WebGoat asennus



![acbcd7aad7873ce050a6794d9d6f35bc](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/b7281a8a-2d50-4f68-87e2-f76e90cf2a3f)


Asennetaan WebGoat ja serveri, sekä rekisteröidään käyttäjätili osoitteessa: http://localhost:8080/WebGoat/. Aloitetaan harjoitustehtävien suorittaminen.




WebGoatin ja serverin asennus seuraavasti:

- `$ sudo apt-get update`
- `$ sudo apt-get -y install openjdk-17-jre ufw wget bash-completion`
- `$ sudo ufw enable`
- `$ wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar` Tämä lataa .jar-tiedoston (Java-arkiston), joka sisältää WebGoat-sovelluksen.
- `$ java -jar webgoat-server-8.0.0.M26.jar`  Käynnistää WebGoat-palvelimen paikallisesti Kali Linux -ympäristössä.









### HTTP Basics -WebGoat tehtävä



![d55274daf1478111c6b616e4454c762e](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/87984600-d396-4220-83fd-29ee2c62156d)

Suoritan HTTP Basics -tehtävän, lähettämällä HTTP-pyyntöjä ja tutkimalla vastauksen. Saavutin tehtävä annon tavoitteen, eli `magic_num: "77"`.








### Developer tools -WebGoat tehtävä

![bad1f6aba2531a00002b07b127af9d8a](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/e5e15944-1f48-4de9-9275-a4809a531f6d)
> Selaimen kehittäjätyökalu -näkymä



![44c31fbcef8a7eb71effa91f2f3dfd78](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/8f8c91be-d9e8-4fae-bd58-2fa08d78f2b6)

> Suoritettu JavaScript-funktio, jonka vastaus näkyy konsolissa.







![45cb8e89ab75d581ba163604c61f5c42](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/f8207400-faa0-4d2a-be54-b445548d4370)

 >Tehtävän tarkoituksena oli löytää HTTP-pyyntö ja lukea siitä satunnaisluku. Kopiodaan ja liitetään se syötekenttään.





















### PortSwigger Labs: Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data


![55038a6e367e00202924d8fe644aea2d](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/53120c90-b182-4bdb-9e23-a82968211402)






Muokkasin selaimen osoitekenttää parametrilla "category", sekä käytin yksinkertaisia SQL-lausekkeita, kuten  'OR ja 1=1--.

Puretaan osiin:

-`':`  Heittomerkki aloittaa tai päättää SQL-lausekkeen.
- `OR:` Looginen SQL-operaattori, joka palauttaa totuusarvon, jos jompikumpi tai molemmat ehdot ovat tosia.
- `1=1:` Yksinkertainen ehto, joka palautuu aina, jos ehto on tosi, koska 1 on aina yhtä suuri kuin 1.
- `--:` Tällä lisätään SQL-kommetteja SQL:n, joka tarkoittaa, että kaikki tekstin jälkeinen osa jätetään huomioimatta. Estetämällä alkuperäisen kyselyn jatkumisen, eikä         vaikuta lopputulokseen.


### Nmap

![a58a36d4f7e092ca9e6791201df8a228](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/b67d16a9-94e3-4ce7-a89a-d55e22cf08a9)

Suoritan komennon, `nmap -p-1000 localhost`  joka skannaa TCP-portit numeroväliltä 1-1000 localhostissa. 


Nmap-skannausraportti kertoo seuraavaa:

- Nmapin versio ja ajankohta, jolloin skannaus suoritettiin.
- Skannauskohde: localhost-osoitte, jonka IP-osoitte on: (127.0.0.1), joka siis viittaa omaan tietokoneeseen.
- "Host is up": viesti kertoo, isäntä tietokone(localhost) on käytettävissä ja vastaa verkkopyyntöihin.
- Latenssi: (0.0000050s) kertoo ajasta, joka kului vastauksen saapumiseen.
- Ilmoitus "Other addresses for localhost (not scanned):  Kertoo, että on muitakin localhost-osoitteita, kuten IPv6-osoite (::1), mutta niitä ei skannattu tässä.
- Ignoroidut portit: Ilmoitus "All 1000 scanned ports on localhost (127.0.0.1) are in ignored states", eli kaikki 1000 skannattua TCP-porttia localhostissa ovat "ignored states" -tilassa. Nmap ei siis saanut vastausta näiltä porteilta tai ne on merkitty "ignored" -tilaan, tämä johtunee palomuurista.
- Suljetut TCP-portit: Ilmoitus "Not shown: 1000 closed tcp ports (reset)" kertoo, että kaikki 1000 skannattua TCP-porttia ovat suljettuja (closed) ja ne on merkitty "reset" -tilaan.

![2323c95321ed6c6397f6a92598a169bc](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/416d1e1b-2ca2-4a8f-9ac8-27f1f28aa26f)

`nmap -A localhost`

Tässä skannausraportissa on jonkin verran lisää dataa.

Raportissa nähdään kaksi avointa TCP-porttia localhostissa. Portti 8080 ja portti 9001. Näiden porttien tilaksi on ilmoittu "open", se hyväksyy aktiivisia TCP- ja UDP-yhteyksiä
Portissa 8080 toimii http-proxy-palvelu, mutta HTTP-otsikko puuttuu.
Portissa 9001 toimii JDBC-palvelu, joka on yhteydenottojen hallintapalvelu Java-tietokantoihin.
Näemme myös Fingerprinting-tietoja ja vastauksista eri HTTP-pyynnöille, kuten FourOhFourRequest, GetRequest ja HTTPOptions. Tiedot antavat tarkemman kuvan siitä, millaisia vastauksia palvelu antaa erilaisiin HTTP-pyyntöihin.

Tieto tunnistamattomasta palvelusta: Raportissa mainitaan yksi palvelu, joka ei ole tunnistettu, vaikka se antoi tietoja. Tässä tapauksessa palvelu toimii portissa 8080, mutta sen tarkkaa tunnistetta ei tiedetä. Raportissa pyydetään käyttäjiä ilmoittamaan palvelun tunnistetiedot Nmapin kehittäjille, jos käyttäjä tietävää sen.

![b470054ab26d0058ffb74014379aad29](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/cf56152d-763d-4972-821d-11ab4e8a0850)




### Pwnagotchi
![6e7a430f8326f677312194e85fed6ea5](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/a8aa2834-be2f-415d-a278-6c188cfe563a)


Pwnagotchi on avoimeen lähdekoodiin perustuva projekti, joka hyödyntää bettercapin ohjaamaa A2C-pohjaista tekoälyä. Pwnagotchi toimii Raspberry Pi Zero W -alustalla.
Ensisijaisesti Pwnagotchia käytetään koulutukseen, tutkimukseen, WiFi-verkkojen tietoturvallisuuden testauksessa ja parantamisessa. AI:n avulla Pwnagotchi kerää ympäristöstään dataa, kuten WiFi-verkkojen signaalitietoja, käyttäen näitä tietoja oppiakseen ja tunnistaakseen mahdollisia tietoturvauhkia entistä tarkemmin.

Kerättyä dataa hyödyntämällä Pwnagotchi pystyy tekemään älykkäitä päätelmiä ja reagoimaan dynaamisesti muuttuviin verkkoympäristöihin. Se voi esimerkiksi tunnistaa haavoittuvat verkot, havaita salausavaimia tai heikkoja salauksia sekä ennustaa mahdollisia kyberhyökkäyksiä.

On ehdottoman tärkeää, että Pwnagotchin käyttäjä on tietoinen lakeista, jotka liittyvät verkkojen testaamiseen ja tietojen keräämiseen, käyttäen sitä vain laillisesti. Sitä tulisi käyttää ainoastaan omien verkkojen turvallisuuden testauksessa tai sellaisissa ympäristöissä, joissa on lupa ja oikeudet verkkojen testaamiseen, kuten labraympäristö. 
 










## References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h1-hacker-warmup
https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf
https://supo.fi/apt-operaatiot
https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/
https://www.w3schools.com/sql/
https://pwnagotchi.ai/
https://www.bettercap.org/
