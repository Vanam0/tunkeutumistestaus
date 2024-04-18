# Fuff faster
Tässä harjoituksessa tutkitaan tietoturvatyökaluja. Hyödynnän läppäriä, sekä virtuaaliympäristöä, joka toimii Oracle VM VirtualBox -alustalla, jossa on asennettuna Kali Linux -käyttöjärjestelmä. Lisäksi käytän pöytätietokonettani, joten tehtävien kuvissa Kali Linux -käyttäjänimi voi vaihdella.

---

## Ffuf

[Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) 
- Käsitellään Ffuf-työkalun hyödyntämistä piilotettujen verkkohakemistojen systemaattiseen etsintään, jota voidaan kutsua fuzzaamiseksi.
- Fuff on nopea ohjelma, joka lähettää tuhansia GET-pyyntöjä tarkistaakseen vastaako verkkosivu pyyntöihin.


## Hashcat

 [Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)
 
 - Hashcat on työkalu, jota käytetään salasanatiivisteiden (hash) murtamiseen
 - Salasanatiiviste on salasana, joka on muunnettu tietyn algoritmin avulla
 - Hashcat tarvitsee toimiakseen sanalistan. Yksi suosituimmista sanalistoista on Rockyou.txt, jossa on yli 14 miljoonaa tyypillistä tiivistettä.


## John the Ripper

[Crack File Password With John](https://terokarvinen.com/2023/crack-file-password-with-john/)

- John the Ripper on salasanan murtamisohjelma, jota käytetään salasanojen tiivistefunktioiden murtamiseen.
- Sanakirjatyyppinen hyökkäys on yksi salasananmurtamismenetelmä, johon John the Ripperiä käytetään
- John the Ripperin Jumbo-versiossa on enmmän ominaisuuksia, kuten ZIP-arkistojen salasanojen murtaminen


  > Näitä työkaluja tulee käyttää eettisesti. 



# Hashcat


Hashcatia ei tarvinnut asentaa, sillä Kali Linuxissani oli se jo valmiina, joten testasin Hashcatin toimintaa murtamalla esimerkkisalasanan: [ohjeiden](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)  mukaan.

```
Aloitin luomalla uuden hakemiston:
$ mkdir hashed
$ cd hashed


Rockyou.txt -sanalista: 
$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
$ tar xf rockyou.txt.tar.gz
$ rm rockyou.txt.tar.gz
```


- Hashcatin komento `hashcat -m 0` purkaa MD5-algoritmin, käyttäen rockyou.txt-sanalistaa.
- `-o solved` Parametrin avulla määritetään tallennus tiedostoon: 'solved'.

> `hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved`

![2e6314d451135f64092243ea47902b62](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/d5a876d8-14e4-42d7-9824-5fbadd927b83)


> Voit nähdä murretun salasanatiivisteen komennolla: `--show`

    6b1628b016dff46e6fa35684be6acc96:summer //Hash on murrettu.

Komennot:

-  `-m 0` salasanatiivisteen tyyppi mm. MD5-algoritmin arvo on 0
- `'6b1628b016dff46e6fa35684be6acc96'` salasanatiiviste, jonka haluamme murtaa
- `-o solved` tallentaa tekstimuodossa uuteen tiedostoon "solved"








# Fuff

Esimerkkikohde, jossa on salainen sivu ja ajetaan se. Käyttämällä [Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/)  -ohjeita.


Aloitin challengella dirfuz-1, ladataan paketti Teron sivuilta.
`wget https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/dirfuzt-1`

Komennot:
* `chmod u+z dirfuzt-1`: Suoritusoikeudet tiedostolle

* `./dirfuzt-1`: Suorittaa tiedoston hakemistossa
     
![fuzzkuva2](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/056d8bc3-2c6b-4cb0-8800-cf4e9eb1fefe)
> Harjoituskohde on käynnissä.



![kuva](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/548f1dd1-0f83-4e09-b703-203fcd87bffb)

`./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 132` Suodatetaan parametrilla `-fs 132` 132 tavua pitkät tulosteet. 

  `* FUZZ: wp-admin`, vaikuttaa lupaavalta, joten kokeillan sitä URL-kenttään. Lippu on löydetty.

















# John the Ripper
[Crack File Password With John -esimerkkitiedostot](https://terokarvinen.com/2023/crack-file-password-with-john/)


![kuva](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/626db36f-5371-4043-b6c3-b4a29f2fc41f)

Koska John oli jo asennettunna, aloitan John the Ripper, Jumbo-version git-kloonauksella, joka kopio koko projektin:
`$ git clone --depth=1 https://github.com/openwall/john.git`


















    






    d) Fuffme. Asenna Ffufme harjoitusmaali paikallisesti omalle koneellesi. Ratkaise tehtävät (kaikki paitsi ei "Content Discovery - Pipes")
  
        Basic Content Discovery
        Content Discovery With Recursion
        Content Discovery With File Extensions
        No 404 Status
        Param Mining
        Rate Limited
        Subdomains - Virtual Host Enumeration








    e) Tee msfvenom-työkalulla haittaohjelma, joka soittaa kotiin (reverse shell). Ota yhteys vastaan metasploitin multi/handler -työkalulla.
        Haittaohjelma ei saa olla automaattisesti leviävä. Msfvenom tekee tunnilla opetelluilla asetuksilla ohjelman, joka avaa reverse shellin, kun sen ajaa, mutta joka ei leviä eikä tee muutenkaan mitään itsestään.
        Raporttiin riittävät pelkät komennot haitakkeen tekemiseen, itse binääriä ei ole pakko laittaa verkkoon. Mikäli laitat binäärin verkkoon, pakkaa se salakirjoitettuun zip-pakettiin ja laita salasanaksi "infected". Latauslinkin yhteydessä on oltava selkeä varoitus siitä, että binääriä ei tule ajaa oikeilla koneilla. Salasanan voit halutessasi kertoa varoitusten yhteydessä.


    f) Asenna Windows virtuaalikoneeseen. Voi olla esimerkiksi Metasploitable 3 tai Microsoftin sivuilta saatava ilmainen kokeiluversio.






    g) Ota Windowsiin graafinen etähallintayhteys Linuxista. Käytä RDP:tä eli Remote Desktop Protocol.












# Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h3-fuff-faster

https://terokarvinen.com/2022/cracking-passwords-with-hashcat/

https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/

https://terokarvinen.com/2023/crack-file-password-with-john/


