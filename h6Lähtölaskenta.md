
# Cheatsheet 



 ## Nmap

Porttiskanneri

- `$ Nmap 192.168.10.1` Normaali skannaus
- `# nmap <kohde> -O `  Skannaus ja käyttöjärjestelmän tunnistaminen
-  `$ nmap -sP 10.0.0.0/24` Verkon skannaus pingillä ja laitteiden listaus
-  `$ nmap -iL ip-osoitteet.txt` IP-osotteiden skannus tekstitiedostosta
-  `$ nmap scanme.nmap.org` Skannaa domain
-  `iR nmap -iR 100` Skannaa 100 satunnaista hostia 
- `nmap -sV -p- <kohde>`  Skannaa kohteen kaikki portit ja yrittää tunnistaa käytössä olevat palvelut (sV)
- `nmap -A <kohde> `  Aggressiivisen skannaus mm. versiotiedot (käytetään harkiten)
- `nmap -sn` Suorittaa normaalinen ping -kyselyn


Salasanojen murtamistyökalut:
  
## John The Ripper



- `john --show` Näyttää murtamisen tulokset 
- `./john tero.zip.hash` Murtaa salasanan zip-tiedostolle
- `john --wordlist=rockyou.txt hash.txt` Määrittää sanakirjan tiedoston




## Hashcat

- `hashcat -m 0 -a 0 hashes.txt wordlist.txt` Valitsin `-m` osoittaa tivisteen ja `-a 0`, tarkoittaa perinteistä brute force -hyökkäystä. `-a 3` Taas kohdistaisi yhdistelmähyökkäyksen: sanakirja, sekä brute force -hyökkäys.
- `-o` -valitsin määrittää tulostiedoston nimen, johon Hashcat tallentaa löydetyt salasanat. Esimerkiksi -o solved.txt määrittäisi tiedostonimen ja tallentaa löydetyt salasanat.
- `cat solved.txt` Cat on Unix-pohjaisen käyttöjärjestelmän komento, joka lukee tiedostoja ja tulostaa sisällön.



FFuF

Verkkokohteiden haavoittuvuuksien löytämiseen tarkoitettu ohjelma esim. HTTP-parametrit ja URL-polut.

- Esim.`./ffuf -w common.txt -u http://localhost:8000/FUZZ` Käytetään paikallista tiedostoa `common.txt` Valistin `-w` määrittää sanakirjatiedoston ja valitsin `-u` määrittää kohteel URL-osoitteen.





Msfvenom metasploitable

-
-
-

Bruteforce

-
-
-




























    a) Cheatsheet. Kerää parhaat komennot lipunryöstöä varten. Lähteinä voit käyttää omia ja kurssikavereiden läksyraportteja, vanhoja cheatsheet:eja sekä vierailijoiden kalvoja. (Kerää nimenomaan ne komennot ja sisältö, ei pelkkää linkkilistaa, ei pelkkää kuvailua. Tässä alakohdassa komentoja ei tarvitse kokeilla koneella).


    
    b) Review. Etsi ja tiivistä vertaisarviotu katsausartikkeli valitsemaltasi kyberturvallisuuden tai hakkeroinnin alalta.
        "review" - yleensä katsausartikkeli nimessä on sana "review". Se pyrkii antamaan käsityksen alan tutkimuksesta juuri tällä hetkellä. Scholarlissa on myös nappi, jolla se yrittää näyttää vain review-artikkelit.
        Tuoretta, jos ei löydy alle 2v, niin edes alle 5v.
        1 <= jufo. Julkaistu arvostetussa vertaisarvioidussa lehdessä. Eli lehti löytyy Jufosta eli Julkaisufoorumin portaalista https://jfp.csc.fi/, ja sen taso on vähintään yksi.
        Myös muualta kuin lehden kotisivulta ladattu kappale julkaistua artikkelia kelpaa, esim "final draft" sopii.
        Ei yleistajuisia kirjoja tai lehtiartikkeleita: ei Mikrobitti, ei Tietotekiikan perusteet osa I, ei "Tiede 2000" -aikakauslehti
        Älä maksa artikkeleista. Yleensä ilmainen latauslinkki löytyy Google Scholarlista oikealta. Haaga-Helian maksamat saa näkyviin Settings: Library Links: Haaga-Helia.
        Englanninkielinen käyttöliittymä toimii paremmin https://scholar.google.com/ncr
        Olennaisin sisältö tiivistelmään. Ei pelkkää metatekstiä tai artikkelin kuvailua:
            Väärin: "Artikkeli kertoo uusista tuulista tietotekniikan parissa. Mukana on yllättävä havainto kiristyshaitakkeista"
            Oikein: "Kiristyshaitakkeiden määrä kasvoi 30% vuoden 2023 aikana Foobarstanissa"
        Suppeahko tiivistelmä ranskalaisilla viivoilla riittää
        Kannattaa lisätä omat huomiot tai kysymykset mukaan. Merkitse selkeästi, mitkä ovat omaa pohdintaa.
        Jos artikkeli on pitkä (yli 4 sivua), voit silmäillä sen lukemisen sijasta.


        
    c) Valmiina lipunryöstöön. Asenna läppärillesi tarvittavat työkalut lipunryöstöön. Hyökkäyskone voi olla virtuaalikone. Se ei saa sisältää luottamuksellisia tietoja, koska sitä voi olla tarpeen tarkistaa ja tutkia harjoituksen yhteydessä. Koneella saatetaan ajaa testibinäärejä ja kontteja; sekä tarkastamiseen liittyviä ohjelmia. Harjoituksessa saattaa olla Docker-kontteja, kokeile, että Docker toimii (Muistaakseni 'sudo apt-get -y install docker.io').

    
    d) Vapaaehtoinen: Seurantaan: Tee haku, joka lähettää alasi artikkelit automaattisesti sähköpostiin. Kannattaa miettiä tässä tulevaa opinnnäytetyön aihetta. Yleensä aluksi artikkeleita tilataan liikaa, ja sitten tiukennetaan seulaa joka kerta kun saa uusia artikkeleita.

    
  









# Lähteet: 

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h6-lahtolaskenta

https://denizhalil.com/2023/11/01/hashcat-password-cracking/
