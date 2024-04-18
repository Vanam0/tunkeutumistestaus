# Fuff faster
Tässä harjoituksessa tutkitaan tietoturvatyökaluja. Hyödynnän läppäriä, sekä virtuaaliympäristöä, joka toimii Oracle VM VirtualBox -alustalla, jossa on asennettuna Kali Linux -käyttöjärjestelmä. Lisäksi käytän pöytätietokonettani, joten tehtävien kuvissa Kali Linux -käyttäjänimi voi vaihdella.

---

## Ffuf

[Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) 
- Fuzzing-työkalu
- käsitellään Ffuf-työkalun hyödyntämistä piilotettujen verkkohakemistojen systemaattiseen etsintään.
- Fuffia voi käyttää myös fuzzataksesi otsikoita ja POST-parametreja


## Hashcat

 [Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)
 
-	Hashin eli hajautuksen murtamisohjelma
-	Hajautus on yksisuuntainen funktio
-	Murtamiseen tarvittavat komennot


## John the Ripper

[Crack File Password With John](https://terokarvinen.com/2023/crack-file-password-with-john/)

- Tiedostojen salasanojen murtaminen 
- Sanakirjatyyppinen hyökkäys 
- Johnin Jumbo -versio

  > Näitä työkaluja tulee käyttää eettisesti. 



# Hashcat


Hashcatia ei tarvinnut asentaa, sillä Kali Linuxissani oli se jo valmiina, joten testasin Hashcatin toimintaa murtamalla esimerkkisalasanan:[ohjeiden](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)  mukaan.

```
Aloitin luomalla uuden hakemiston:
$ mkdir hashed
$ cd hashed


Rockyou.txt -sanalista: 
$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
$ tar xf rockyou.txt.tar.gz
$ rm rockyou.txt.tar.gz
```


- Hashcat tarvitsee hajautuksen tyypin murtamiseen, ja sen numeron annetaan -m-parametrina esim. `hashid -m 6b1628b016dff46e6fa35684be6acc96`
- Hajautuksen murtaminen:

`hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved`

![2e6314d451135f64092243ea47902b62](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/d5a876d8-14e4-42d7-9824-5fbadd927b83)


> Voit nähdä murretun hajautuksen komennolla: `--show`

    6b1628b016dff46e6fa35684be6acc96:summer //Hash on murrettu.

Komennot:

-  `-m 0` hajautuksen tyyppi
'6b1628b016dff46e6fa35684be6acc96' hajautus, jonka haluamme murtaa
- `-o solved` tallenna tekstimuodossa uuteen tiedostoon "solved" -hakemistoon.








# Fuff

Esimerkkikohde, jossa on salainen sivu ja ajetaan se. Käyttämällä [Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/)  -ohjeita.



![fuzzkuva2](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/056d8bc3-2c6b-4cb0-8800-cf4e9eb1fefe)
> Harjoituskohde on käynnissä.



























    b) Salainen, mutta ei multa. Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf






    c) Asenna John the Ripper ja testaa sen toiminta murtamalla jonkin esimerkkitiedoston salasana.






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
https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
https://terokarvinen.com/2023/crack-file-password-with-john/


