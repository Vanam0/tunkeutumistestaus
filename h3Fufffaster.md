johdanto


# Fuff faster


## Ffuf

[Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) 
- Fuzzing-työkalu
- käsitellään Ffuf-työkalun hyödyntämistä piilotettujen verkkohakemistojen systemaattiseen etsintään.
- Fuffia voi käyttää myös fuzzataksesi otsikoita, POST-parametreja...


## Hashcat

 [Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)
 
- Käytännön esimerkkejä hashcatin käytöstä 
-	Salasanojen murtaminen 
-	Ohjeita  Hashcatin käyttöön
-	Hajautus on yksisuuntainen funktio
-	Murtamiseen tarvittavat komennot
-	Hashcatin antamat tulosteet ja niiden tulkinta

## John the Ripper

[Crack File Password With John](https://terokarvinen.com/2023/crack-file-password-with-john/)

- Tiedostojen salasanojen murtaminen 
- Sanakirjatyyppinen hyökkäys 
- Johnin Jumbo -versio

  > Näitä työkaluja tulee käyttää eettisesti. 

###################################################################################


 Hashcat
 ![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/3d55cd7e-dc79-4ee7-b5e1-7a2fb9644d08)











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


