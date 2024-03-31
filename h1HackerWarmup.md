# h1 - Hacker Warmup

## Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains
        Tiivistelmät 
        
On tärkeää ymmärtää tarkasti kyberuhat, niiden tarkoitukset ja toimintatavat. 
Tietoverkon puolustus on välttämätöntä, koska erillaiset kyberuhat kehittyvät koko ajan.
Teksti sisältää puolustustoimenpiteiden matriisin, joka on linjassa eri vaiheiden kanssa tunkeutumisen tappoketjussa. Nämä toimet sisältävät mm. havaitsemisen, estämisen, häiritsemisen, heikentämisen, tiedusteluun, harhauttamisen ja tuhoamisen. Näiden tarkoituksena on vastustaa hyökkääjän toimintaa eri vaiheissa.

Tunkeutumisen tappoketju (Kill Chain) on siis järjestelmällinen prosessi.
Useita tunkeutumistapauksia analysoidaan myös strategisesti, joka auttaa ajan myötä tunnistamaan niiden yhtenäisä piirteitä ja malleja. Jolloin se auttaa puolustajia arvioimaan puolustusasemaansa ja kehittämään strategioita mahdollisten aukkojen varalta.

APT = Advanced Persistent Threats, ovat edistyneitä ja jatkuvasti läsnä olevia tietoverkkouhkia, jotka pyrkivät hyökkäämään tietoverkkoihin pitkäaikaisesti ja huomaamattomasti. APT:t ovat yleensä suunniteltuja ja toteutettuja organisaatioita tai valtioita vastaan, ja niiden tavoitteena voi olla esim. tietovarkaudet, kybervalkoilu tai infrastruktuurin vahingoittaminen. APT-operaatiot käyttävät tekniikoita ja hyökkäystapoja sekä hyödyntävät usein heikkoja kohtia, kuten tietoturva aukkoja järjestelmien puolustuksessa. APT-operaatiot voivat olla pitkäkestoisia ja vaikeasti havaittavia, joka tekee torjunnasta haastavaa.

## Get The Art of Hacking (Video Collection) now with the O’Reilly learning platform
O'Reillyn oppimisalustalla oli kattavasti tietoa videoissa erilaisista hakkerointitekniikoista ja tietoturvaan liittyviä työkaluista.
Mielestäni videot olivat erittäin hyödyllisiä tietosisällöltään. 
Alusta oli itselleni uusi, joten ajattelen sen olevan hyödyllinen aloittelijoille kuin kokeneillekin henkilöille kyberturvallisuuden parissa.

Porttiskannerit:
- Nmap (Yksi hyödyllisimistä ja tunnetuimmista tietoturvatyökaluista, jolla suoritetaan monipuolisia verkkoskannausta.)
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
> Katsotaan hakemiston sisältö `ls` ja tulostetaan readme-tiedoston sisältö komennolla `cat`


![f89b547c931b63fc53e219868e44c1f4](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/9ed39736-abd6-4a76-8b0e-f8627d52e58c) 
> Jatketaan bandit1 ja saadaan uusi salasana. 



![c8d155630413ca7260eea3671ddf55e9](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/c2951bf8-b76b-4bd4-a693-55b721d2d2f1)
> Pääsemme bandit2 levelille, ja löydämme tiedostosta uuden salasanan. 





 


















## References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h1-hacker-warmup
https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf
https://supo.fi/apt-operaatiot
