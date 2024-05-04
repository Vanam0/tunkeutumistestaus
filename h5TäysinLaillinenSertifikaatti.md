# Täysin laillinen sertifikaatti
--------


OWASP 2021: OWASP Top 10:2021

- Pääsynvalvonnan keskeinen tehtävä on valvoa, että käyttäjät toimivat ainoastaan heille osoitetuissa käyttöoikeusrajoissa. 
- Epäonnistuessaan pääsynvalvonta voi johtaa tietovuotoon tai tuhoutumiseen.
- Pääsynvalvonnan tehokkuus edellyttää, että mahdollinen hyökkääjä ei kykene kiertämään valvontaa muokkaamalla todennuksia tai käyttämällä metatietoja hyväkseen. Jotta turvallisuus varmistetaan on tärkeää seurata pääsynvalvonnan epäonnitumisia ja istuntotunnisteita.

--

A10:2021 – Server-Side Request Forgery (SSRF)


- SSRF-haavoittuvuudet ilmenevät, kun sovellus hakee etäresursseja ilman käyttäjän URL:n validointia.
- Tämä mahdollistaa hyökkääjälle sovelluksen pakottamisen lähettämään pyynnön odottamattomaan kohteeseen.
- Ehkäisykeinoina sovelluskehittäjät voivat toteuttaa verkko- ja sovelluskerroksen suojauksia, kuten eristämistä ja syötteiden puhdistusta.
- SSRF:n avulla hyökkääjät voivat esimerkiksi suorittaa sisäisiä palvelin skannauksia, paljastaa arkaluontoisia tietoja tai päästä käsiksi pilvipalveluiden metatietoihin.
---


# PortSwigget Academy

Insecure Direct Object References (IDOR):

Hyökkääjä pääsee suoraan käsiksi tietokantaan tai tiedostoihin syöttämällä manipuloituja URL-osoitteita.
`https://.../customer_account?customer_number=132355`
Tässä IDOR-haavoittuvuus esimerkissä asiakasnumeroa käytetään suoraan tietueen indeksinä kyselyissä, jotka suoritetaan tietokannassa. Hyökkääjä voi yksinkertaisesti muuttaa asiakasnumeroarvoa ohittaakseen pääsyoikeudet ja tarkastellakseen muiden asiakkaiden tietueita.

-----

Path Traversal:

Hyökkääjä manipuloi URL-osoitteita päästäkseen palvelimen hakemistoista muihin kansiopolkuihin.
Tämä voi johtaa arkaluontoisten tiedostojen, kuten salasanojen paljastumiseen.

Server-side Template Injection:

Hyökkääjä hyödyntää palvelimen template -syntaksia suorittaakseen komentoja palvelimelle.
Tämä voi johtaa vakaviin haavoittuvuuksiin, koska syötteitä suoritetaan komentoina.

Server-side Request Forgery (SSRF):

Hyökkääjä pakottaa sovelluksen tekemään palvelimelle pyyntöjä toiseen kohteeseen, yleensä sisäverkkoon.
Tämä tapahtuu yleensä manipuloimalla sovelluksen lähettämiä pyyntöjä, esimerkiksi fuzzaamalla.
----

Cross-site Scripting (XSS):


Hyökkääjä injektoi JavaScript-koodia haavoittuvaan verkkosivuun.
Tämä mahdollistaa käyttäjän selaimen ohjaamisen ja tietojen varastamisen, kuten käyttäjätunnukset ja salasanat.

----

![5d7e18d33d736d0b3b5d8c6e15f9604b](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/8c4f2ec7-385b-46df-9dd2-49c5c6e029c5)

> Näkymä asetuksistani



- FoxyProxy on Mozilla Firefox -selaimelle tarkoitettu lisäosa, joka toimii välityspalvelimena ja mahdollistaa localhost-liikenteen ohjautumisen ZAP-palvelimelle.
Kun tietokone lähettää pyynnön esimerkiksi osoitteeseen google.com, pyynnöt ensin ohjataan FoxyProxyyn ja sieltä edelleen ZAP-proxyyn.

![image](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/50a7af26-b733-4f80-a22a-018e89de3d95)


- ZAP luo automaattisesti "väärennetyn" sertifikaatin, joka on saatavilla ZAP-valikon kautta sijainnissa Tools -> Preferences -> Network -> Server Certificates.

----

# PortSwigger Labs


![3b9dc0d850c70dcaa73aef91077b6150](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/620e1339-ccfd-465a-8720-9e3fcf803bc9)
- Tutkin sisältöä ja oli viittaus 2.txt -tiedostoon. Päätin kokeilla vaihtaa nimi 1.txt -tiedostoon, mikä vastasi puuttuvaa tiedostoa keskusteluhistoriassa.
Vastauksena saatiin lokitiedosto 1.txt, joka sisälsi käyttäjä `carlos` salasanan.
(IDOR) tietoturvaongelma johtuu siitä, kun käyttäjän oikeuksia ei valvota.

![0832183df1aa419170ece58a449a9f5c](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/65f89fcb-8460-45a8-b77d-ef57ddc9f5c6)
- Tässä manipuloidaan tiedostopolkua, joka mahdollisti pääsyn arkaluontoisiin tiedostoihin palvelimella. 
Muutetaam tiedostopolku `/image?filename=../../../etc/passwd`
Eli navigoidaan ylöspäin hakemistopuussa, juurikansioon, ja eteenpäin /etc/passwd-kansioon.

![b8f9df9bedd39531e6e814513baeaffc](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/13cde8c4-b674-4a38-ac8e-cc3e10b4f31c)

- Hyvin samankaltainen tehtävä kuin edellinen.

![7f9a4cbfe648e3470ed94966f46e3ef7](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/8b2f2594-8b70-406e-9ef5-a0b368a7d424)

- Tässä `filename?=image` -pyyntöä on manipuloitu lisäämällä `!....//....//....//etc/passwd`, joka pyrkii päsemään käsiksi tiedostoon.

------


# WebGoat


![016ad85ad543c0f1b49193c45cd5c3bf](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/fd81b4b5-7ad2-4fa4-a65b-66016e46a060)

- Tässä hyödynnetään kaksivaiheisen todennuksen heikkoutta. 



![177f57f7233283d9b6caba109b8a6ec1](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/176cc34b-0bde-4048-9f1a-aa79424fb693)




- Kirjautumispyyntö lähetetään palvelimelle. Tarkastellaan sen tietoa ja salasana, sekä käyttäjätunnus löytyi.


![08458036044cdd05eccd1cf033066e46](https://github.com/Vanam0/tunkeutumistestaus/assets/122449444/55526002-6539-4b2c-847d-be076e8163cf)
> Server-Side Request Forgery (SSRF) on tietoturva-aukko, jossa hyökkääjä voi manipuloida verkkosivustoa tekemään HTTP-pyyntöjä palvelimen puolesta. Tämä voi mahdollistaa pääsyn sisäverkon ulkopuolelle tai palomuurin taakse, joihin hyökkääjällä ei muuten olisi pääsyä.

- Tehtävänä oli siis painaa "Steal the cheese"-nappia WebGoat -saitilla ja etsiä ZAP-työkalun avulla siepatun liikenteen joukosta POST-pyyntö, muokata parametrin arvo `url=images%2Ftom.png` arvoksi `url=images%2Fjerry.png` ja lähettää muokattu pyyntö uudelleen ZAP-työkalun kautta.  




## Lähteet

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/#h5-taysin-laillinen-sertifikaatti

https://portswigger.net/web-security/ssrf

