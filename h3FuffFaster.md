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

    salasana: summer 

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

`./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 132` Suodatetaan parametrilla `-fs 132` 132 tavua pitkät tulosteet, jotta saadaan olennaisia tulosteita vähemmän. 

  `* FUZZ: wp-admin`, vaikuttaa lupaavalta, joten kokeillan sitä URL-kenttään. Lippu on löydetty.

















# John the Ripper
[Crack File Password With John -esimerkkitiedostot](https://terokarvinen.com/2023/crack-file-password-with-john/)


![kuva](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/626db36f-5371-4043-b6c3-b4a29f2fc41f)

- Aloitan John the Ripper git-kloonauksella:
`$ git clone --depth=1 https://github.com/openwall/john.git`


![d9bb5cf4706f82799844e9859e116776](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/7de8edf2-bbe5-468c-a6d5-64bf8df56b63)

- Teron sivuilla olevaa Zip-tiedosto:
```$ wget https://TeroKarvinen.com/2023/crack-file-password-with-john/tero.zip```

![f8a25899839cb761251ed031677336f0](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/38d31463-d938-492d-a346-1967f39a5e94)

- Käytin zip2john-ohjelmaa purkaakseni tiedostosta nimeltä ´tero.zip´ sisällön ja tallennan sen uuteen tiedostoon: 
`zip2john tero.zip > tero.zip.hash`


![239038a7f27bd991ed788c1fb75e3d81](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/3db2e348-cd53-4c9f-96d9-9fcbbd9e8b09)

- Tiedoston salasana on: `butterfly`, tutoriaali on tehty.











  # Fuffme | [Ffufme harjoitusmaali](https://terokarvinen.com/2023/fuffme-web-fuzzing-target-debian/) 

Latasin tehtävän tekemiseen harjoutusmaalit virtuaalitietokoneelle. 
Ohjeet harjoitusmaaleihin: [Fuffme - Install Web Fuzzing Target on Debian](https://terokarvinen.com/2023/fuffme-web-fuzzing-target-debian/) 

Tietenkin aloitus päivityksellä:
`sudo apt-get update` 
Docker.io sovellus: 
`sudo apt-get install docker.io`
Kloonataan harjoitusmaali: ` git clone https://github.com/adamtlangley/ffufme`. 
Kasataan Ffufme Docker käyttöön: `cd ffufme/` `sudo docker build -t ffufme 
Harjoitusmaalin käynnistys komennolla: `sudo docker run -d -p 80:80 ffufme`
Tarkistetaan onko harjoitusmaali käynnissä: `curl localhost`

![78c8b44a399d2772ea35beeee31b2cd8](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/4b214068-a93b-4a54-a455-1b70c9d92346)

Ennen aloittamista lataan tarvittavat sanalistat: `~/wordlists `-hakemistoon. [Linkki ohjeisiin] (https://terokarvinen.com/2023/fuffme-web-fuzzing-target-debian/)



![97983569de7ea1e94dc2d5a349ecd92c](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/1024e8fe-f2ba-455c-992e-4487be21a871)

```
Komennot:
$ mkdir $HOME/wordlists
$ cd $HOME/wordlists
$ wget http://ffuf.me/wordlist/common.txt
$ wget http://ffuf.me/wordlist/parameters.txt 
$ wget http://ffuf.me/wordlist/subdomains.txt
$ cd -
```

Basic Content Discovery
ffuf -w ~/wordlists/common.txt -u http://localhost/cd/basic/FUZZ
![86bde6c8e0c55cc4d48766eba5318a88](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/a7c4ee7b-0fb8-43b5-bbf7-2cbfbb9ef3f1)


Content Discovery With Recursion
ffuf -w ~/wordlists/common.txt -recursion -u http://localhost/cd/recursion/FUZZ

Content Discovery With File Extensions
ffuf -w ~/wordlists/common.txt -e .log -u http://localhost/cd/ext/logs/FUZZ


![1bdf18f79fe93552c5fe1e784f199bf0](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/17b1d288-7f37-4609-a9f3-a4ea5a677830)


No 404 Status
ffuf -w ~/wordlists/common.txt -u http://localhost/cd/no404/FUZZ (-fs 669)
![731d28c241c58053af62223f2942347e](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/e921e715-0d5b-46be-bb24-b6c47e990f50)


Param Mining
ffuf -w ~/wordlists/parameters.txt -u http://localhost/cd/param/data?FUZZ=1
![6c6120842d87f5422484aba6778c7a25](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/224649ef-e955-45f5-974b-f34bd7c79ddd)

Rate Limited
ffuf -w ~/wordlists/common.txt -u http://ffuf.test/cd/rate/FUZZ -mc 200,429
ffuf -w ~/wordlists/common.txt -t 5 -p 0.1 -u http://ffuf.test/cd/rate/FUZZ -mc 200,429
![4fadcc19335f92e0de9288cb47602c17](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/e2c34411-8ad3-43f8-aba0-5cc9329bddbd)

Subdomains - Virtual Host Enumeration










# Lähteet:

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h3-fuff-faster

https://terokarvinen.com/2022/cracking-passwords-with-hashcat/

https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/

https://terokarvinen.com/2023/crack-file-password-with-john/


