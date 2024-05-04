# Täysin laillinen sertifikaatti
--------


OWASP 2021: OWASP Top 10:2021

- Pääsynvalvonnan keskeinen tehtävä on valvoa, että käyttäjät toimivat ainoastaan heille osoitetuissa käyttöoikeusrajoissa. 
- Epäonnistuessaan pääsynvalvonta voi johtaa tietovuotoon tai tuhoutumiseen.
- Pääsynvalvonnan tehokkuus edellyttää, että mahdollinen hyökkääjä ei kykene kiertämään valvontaa muokkaamalla todennuksia tai käyttämällä metatietoja hyväkseen. Jotta turvallisuus varmistetaan on tärkeää seurata pääsynvalvonnan epäonnitumisia ja istuntotunnisteita.


A10:2021 – Server-Side Request Forgery (SSRF)


- SSRF-haavoittuvuudet ilmenevät, kun sovellus hakee etäresursseja ilman käyttäjän URL:n validointia.
- Tämä mahdollistaa hyökkääjälle sovelluksen pakottamisen lähettämään pyynnön odottamattomaan kohteeseen.
- Ehkäisykeinoina sovelluskehittäjät voivat toteuttaa verkko- ja sovelluskerroksen suojauksia, kuten eristämistä ja syötteiden puhdistusta.
- SSRF:n avulla hyökkääjät voivat esimerkiksi suorittaa sisäisiä palvelin skannauksia, paljastaa arkaluontoisia tietoja tai päästä käsiksi pilvipalveluiden metatietoihin.

  PortSwigget Academy

Insecure Direct Object References (IDOR):

Hyökkääjä pääsee suoraan käsiksi tietokantaan tai tiedostoihin syöttämällä manipuloituja URL-osoitteita.
`https://.../customer_account?customer_number=132355`
Tässä IDOR-haavoittuvuus esimerkissä asiakasnumeroa käytetään suoraan tietueen indeksinä kyselyissä, jotka suoritetaan tietokannassa. Hyökkääjä voi yksinkertaisesti muuttaa asiakasnumeroarvoa ohittaakseen pääsyoikeudet ja tarkastellakseen muiden asiakkaiden tietueita.


Path Traversal:

Hyökkääjä manipuloi URL-osoitteita päästäkseen palvelimen hakemistoista muihin kansiopolkuihin.
Tämä voi johtaa arkaluontoisten tiedostojen, kuten salasanojen paljastumiseen.

Server-side Template Injection:

Hyökkääjä hyödyntää palvelimen template -syntaksia suorittaakseen komentoja palvelimelle.
Tämä voi johtaa vakaviin haavoittuvuuksiin, koska syötteitä suoritetaan komentoina.

Server-side Request Forgery (SSRF):

Hyökkääjä pakottaa sovelluksen tekemään palvelimelle pyyntöjä toiseen kohteeseen, yleensä sisäverkkoon.
Tämä tapahtuu yleensä manipuloimalla sovelluksen lähettämiä pyyntöjä, esimerkiksi fuzzaamalla.

Cross-site Scripting (XSS):


Hyökkääjä injektoi JavaScript-koodia haavoittuvaan verkkosivuun.
Tämä mahdollistaa käyttäjän selaimen ohjaamisen ja tietojen varastamisen, kuten käyttäjätunnukset ja salasanat.


a) Totally Legit Sertificate. Asenna OWASP ZAP, generoi CA-sertifikaatti ja asenna se selaimeesi. Laita ZAP proxyksi selaimeesi. Laita ZAP sieppaamaan myös kuvat, niitä tarvitaan tämän kerran kotitehtävissä. Osoita, että hakupyynnöt ilmestyvät ZAP:n käyttöliittymään. (Ei toimi localhost:lla ilman Foxyproxya)

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/8e469bea-12ca-4416-a9e4-f08a9ba817b1)





FoxyProxy on Mozilla Firefox -selaimelle tarkoitettu lisäosa, joka toimii välityspalvelimena ja mahdollistaa localhost-liikenteen ohjautumisen ZAP-palvelimelle.
Kun tietokone lähettää pyynnön esimerkiksi osoitteeseen google.com, pyynnöt ensin ohjataan FoxyProxyyn ja sieltä edelleen ZAP-proxyyn.

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/50a7af26-b733-4f80-a22a-018e89de3d95)


> Näkymä asetuksistani









## Lähteet

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h5-taysin-laillinen-sertifikaatti

