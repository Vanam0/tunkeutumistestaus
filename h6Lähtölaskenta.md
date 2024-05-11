
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
- `nmap -sS -T4 <IP-osoite>` Lähettää tiedustelu TCP SYN-paketin ja asettaa skannauksen nopeuden aggressiiviseksi määrrittäen myös tarkkuuden


Salasanojen murtamistyökalut:
  
## John The Ripper



- `john --show` Näyttää murtamisen tulokset 
- `./john tero.zip.hash` Murtaa salasanan zip-tiedostolle
- `john --wordlist=rockyou.txt hash.txt` Määrittää sanakirjan tiedoston




## Hashcat

- `hashcat -m 0 -a 0 hashes.txt wordlist.txt` Valitsin `-m` osoittaa tivisteen ja `-a 0`, tarkoittaa perinteistä brute force -hyökkäystä. `-a 3` Taas kohdistaisi yhdistelmähyökkäyksen: sanakirja, sekä brute force -hyökkäys.
- `-o` -valitsin määrittää tulostiedoston nimen, johon Hashcat tallentaa löydetyt salasanat. Esimerkiksi -o solved.txt määrittäisi tiedostonimen ja tallentaa löydetyt salasanat.
- `cat solved.txt` Cat on Unix-pohjaisen käyttöjärjestelmän komento, joka lukee tiedostoja ja tulostaa sisällön.



## FFuF

Verkkokohteiden haavoittuvuuksien löytämiseen tarkoitettu ohjelma esim. HTTP-parametrit ja URL-polut.

- Esim.`./ffuf -w common.txt -u http://localhost:8000/FUZZ` Käytetään paikallista tiedostoa `common.txt` Valistin `-w` määrittää sanakirjatiedoston ja valitsin `-u` määrittää kohteel URL-osoitteen.
- `-H` -valitsin lisää mukautettuja otsikoita, kuten User-Agent tai Referer pyynnöt.
- `-fc`-valitsin ​​määrittää, kuinka monta vastausta katsotaan virheellisiksi (false positive) 404-virheen sijasta, kun skannataan verkkosivustoja.



## Msfvenom metasploitable

```
msfconsole
use multi/handler/payload
SET payload <haittaohjelma>
SET LHOST <kuuntelijan osoite>
SET LPORT <kuuntelijan portti>
run -j  Ajaa multihandlerin taustalla


background #Siirtää käynnissä olevan moduulin taustalle msfconsole-käyttöliittymässä.
````





  


# Lähteet: 

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h6-lahtolaskenta

https://denizhalil.com/2023/11/01/hashcat-password-cracking/
