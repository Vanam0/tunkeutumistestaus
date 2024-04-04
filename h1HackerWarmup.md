# h1 - Hacker Warmup

## Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains
        Tiivistelmät 
        
On tärkeää ymmärtää tarkasti kyberuhat, niiden tarkoitukset ja toimintatavat. 
Tietoverkon puolustus on välttämätöntä, koska erillaiset kyberuhat kehittyvät koko ajan.
Teksti sisältää puolustustoimenpiteiden matriisin, joka on linjassa eri vaiheiden kanssa tunkeutumisen tappoketjussa. Nämä toimet sisältävät mm. havaitsemisen, estämisen, häiritsemisen, heikentämisen, tiedusteluun, harhauttamisen ja tuhoamisen. Näiden tarkoituksena on vastustaa hyökkääjän toimintaa eri vaiheissa.

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

> Ensinnäkin, aloitin tarkastelemalla hakemiston sisältöä käyttämällä komentoa `ls`, tämä komento listaa kaikki tiedostot ja hakemistot nykyisessä sijainnissa.
> Tämän jälkeen käytin `cat`-komentoa tulostamaan readme-tiedoston sisällön. Cat on lyhenne sanasta "concatenate", se yhdistää tiedostojen sisällön ja tulostaa sen terminaaliin.


![f89b547c931b63fc53e219868e44c1f4](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9ed39736-abd6-4a76-8b0e-f8627d52e58c) 

> Seuraavaksi, siirryin bandit1-tasolle ja löysin uuden salasanan.



![c8d155630413ca7260eea3671ddf55e9](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/c2951bf8-b76b-4bd4-a693-55b721d2d2f1)



> Siirryin bandit2-tasolle ja löysin tiedostosta jälleen uuden salasanan. Samalla käytin komentoa `ls -alps` tarkastaakseni kaikki mahdolliset tiedostot ja hakemistot hakemistossa myös piilotiedostot, jos niitä on. Käyttämällä tätä komentoa sain yksityiskohtaisen listan tiedostojen ja hakemistojen ominaisuuksista: Tiedostoon varatun tilan, joka viittaa siihen määrään levytilaa, jonka tiedosto tai hakemisto käyttää tallennustarkoituksiin. Se sisältää tiedoston datan lisäksi myös tiedoston metatiedot, kuten otsikot, järjestelyt hakemistorakenteessa ja muut yksityiskohdat, jotka vaativat tilaa tallennukseen.




## WebGoat 
HTTP Basics

![acbcd7aad7873ce050a6794d9d6f35bc](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/b7281a8a-2d50-4f68-87e2-f76e90cf2a3f)
> Asennetaan WebGoat Kali Linuxille ja registeröidään käyttäjätili, sekä kirjaudutann sisään osoitteessa: http://localhost:8080/WebGoat/
`$ sudo apt-get update
$ sudo apt-get -y install openjdk-17-jre ufw wget bash-completion
$ sudo ufw enable
$ wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar
$ java -jar webgoat-server-8.0.0.M26.jar`


![d55274daf1478111c6b616e4454c762e](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/87984600-d396-4220-83fd-29ee2c62156d)
> HTTP Basics tehtävä ja selaimen kehittäjätyökalu


 Developer tools

![bad1f6aba2531a00002b07b127af9d8a](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/e5e15944-1f48-4de9-9275-a4809a531f6d)




















## References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h1-hacker-warmup
https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf
https://supo.fi/apt-operaatiot
https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/
