## ITI0202 - Programmeerimise põhikursus
### 1. loeng

---

## Tere

Minu nimi: Ago Luberg

---

## Küsimusi?

---

## Python 2?

@ul
- Ei, aga korraldus sarnane
- Süva 100p ja eksami 100p asemel
- Projekt 150p, Gomoku 50p
- Eksam 500p
@ulend

---

## Veel küsimusi?

---

## Aine

@ul
- Ainekood: ITI0202
- EAP: 6EAP
- Sisu: Java programmeerimine
- Eeldus: Algkursuse läbimine
- Kui Algkursus läbimata, siis:
 
 - arvestage, et see aine ei ole lihtsam kui algkursus
 - kirjuta "motivatsioonikiri" ago.luberg@ttu.ee, miks peaks põhikursus minema teisiti kui algkursus
@ulend

---

## Deklareerimine

@ul
- Kursus on tunniplaanis IAIB tudengitele
- Vabaõppesse võib igaüks selle aine võtta
- Kui teil on enda õppekavas Java kursus, peaksite selle võtma
- Asendus on võimalik vaid siis, kui õppekava- või programmijuht seda lubab.
@ulend

---

## Korraldus

@ul
- 8 loengut (paaritu T 10)
- 16 praktikumi (K 10, K 12)
- 8 projekti praktikumi (paaris T 10)
@ulend

@ul
- Kursuse jooksul lahendatakse iseseisvaid ülesandeid, mis annavad punkte
- Punktid liidetakse
- Kokku kuni 1000 punkti, 501p => "1", .., 901p "5"
@ulend

---

## PR/EX ülesanded

@ul
- Esimesed 15 nädalat:
- PR ülesanne 5p
- EX ülesanne 15p
- Kokku 300p
@ulend

---

## Tunnikontroll

@ul
- Toimub 5. nädala praksis
- Seega PR05 ülesannet pole, selle asemel on tunnikontroll
- 5p (nagu PR ülesanne)
- Eksamieeldus: 1p tunnikontrollist
@ulend

---

## Kontrolltöö

@ul
- Toimub 10. nädala praksis
- PR10, EX10 asemel, annab 20p
- Eksamieeldus: 10p kontrolltööst
@ulend

---

## Projekt

@ul
- Suurem töö paaridena (n-ö tiim)
- Teema võite ise valida
- Eelistatult mõni mäng
- Paaris nädala praktikumides tegeleme sellega
- Kokku võimalik saada 150p
- Täpsemalt 2. nädala projekti praktikumis
- Mõelge juba paarilise/teema peale
- Eksamieeldus
@ulend

---

## Gomoku

@ul
- Kahe mängija mäng, kus käiakse nuppe kordamööda lauale
- Võidab see, kes suudab esimesena 5 oma nuppu kõrvuti (reas, veerus, diagonaalis) saada
- Teile antakse valmis GUI
- Peate kirjutama mänguloogika, mis suudaks võita erineva tugevusega vastaseid
- Käigu tegemiseks on piiratud aeg
- Sisuliselt realiseerite ühe meetodi, kuhu antakse ette hetkeseis
- Meetod peab tagastama teie poolt leitud parima käigu
@ulend

---

## Gomoku

@ul[ul-80]

- Vastased erineva tasemega:
 - nõrgema vastase võitmine 50p
 - tugevama vastase võitmine 50p
- Semestri lõpus korraldame turniiri, kus teie lahendused võistlevad omavahel
- Turniirilt saab lisapunkte
- Gomokut saab teha kahekesi
- Märksõnad: rekursioon, *game tree*, *minimax*, *alpha-beta pruning*.

@ulend

---

## Punktid kokku

@ul
- **Väiksed ülesanded**: 300p
 - **PR** 13 x 5p = 65p
 - **EX** 14 x 15p = 210p
 - **Tunnikontroll** 5p
 - **Kontrolltöö** 20p
- **GUI Projekt** 150p
- **Gomoku** 50p
- **Eksam** 500p
@ulend

---

## Üldised nõuded ülesannetele

@ul
- **Plagiaadikontroll**
- Lahendused tuleb laadida gitlab.cs.ttu.ee
- Ülesannet võib enne tähtaeg esitada mitu korda
- Arvesse läheb parim tulemus
- Üldiselt saab tudeng oma esituse kohta automaatse tagasiside emailile
- Tudeng peab **oma** lahendusest aru saama
 - mõistab igat sümbolit
 - on valmis tegema väiksemaid muudatusi
@ulend

---

## Stiilikontroll

@ul
- Kood peab vastama stiilinõuetele
- Kasutame Checkstyle pistikprogrammi
- Saate selle IntelliJ-le installida, et enne esitamist stiili kontrollida
- Kui esineb vähemalt üks stiiliviga, on kogu tulemus 0
- Tagasiside stiilivigade kohta tuleb emailile
- Täpne nõue stiilile võib varieeruda ülesandeti
@ulend

---

## Ülesannete tähtajad

@ul
- PR ülesanne praktikumi päeva (kolmapäev) õhtul 23:59.
- EX ülesanne järgmise nädala teisipäeval 23:59.
 - pärast saab kuni 50% järgmise teisipäeva õhtuni 23:59
- PR01 ülesande eest saab 5p kuni 30.01 23:59 (kolmap õhtu)
 - 2.5p (50%) kuni 5.02 23:59 (teisip õhtu)
- EX01 ülesande eest saab 15p kuni 5.02 23:59 (teisip õhtu)
 - 7.5p (50%) kuni 12.02 23:50 (nädal hiljem teisip õhtu)
@ulend
 
---

## Tunnikontroll

@ul
- Toimub 5. nädala praktikumis
- Antakse 5 ülesannet
- Võimalik saada 5 punkti
- Eksamieeldus on vähemalt 1 punkti saamine
- Üks kord võimalik järele teha
@ulend

---

## Kontrolltöö

@ul
- Toimub 10. või 11. nädala praktikumis
- Kokku 20 punkti
- Eksamieeldus on vähemalt 10 punkti saamine
- Üks kord võimalik järele teha
@ulend

---

## Teemad (1-8 nädal)

Umbkaudne teemade nimekiri:

@ul
- Sissejuhatus, korraldus, muutuja, tingimuslause, tsükkel
- Sõne, massiiv, järjend, andmestruktuurid
- OOP sissejuhatus, nähtavus, static/non-static
- OOP, getter/setter, konstruktor
- OOP, polümorfism, instants
- OOP, abstraktsioon, liides, *default* meetod
- *functional interface*
- JavaFX
@ulend

---

## Teemad (9-16 nädal)

@ul
- JavaFX
- JavaFX
- Stream API
- Stream API
- Rekursioon
- Mingi teema
- Kordamine
@ulend

---

## Õppematerjalid

- Avalikud õppematerjalid: https://ained.ttu.ee/javadoc/
 - Lähtekood githubis - kõigil võimalik panustada
- Loengumaterjalid, ülesanded, punktid jms: https://ained.ttu.ee/

Õpik:
Introduction to Java Programming (Brief version) (Daniel Liang)

---

## Täiendavaid materjale

- http://math.hws.edu/javanotes/ (üldiselt hea, GUI osa aegunud)
- https://docs.oracle.com/javase/tutorial/ (Oracle Java juhendid)
- http://greenteapress.com/thinkjava6/thinkjava.pdf Think Java

---

## Iseseisev harjutamine

- https://codera.cs.ttu.ee/ (Ülesandeid eelmisest aastast)
- https://codingbat.com/java (saab alustada lihtsamatest ja liikuda keerulisemate juurde)
- https://www.codecademy.com/learn/learn-java
- http://www.learnjavaonline.org/
- https://www.hackerrank.com/
- https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-092-introduction-to-programming-in-java-january-iap-2010/

---

## Enne esimest praktikumi

@ul
- **Registreeruge** ained.ttu.ee lehel ainesse
- Installige arvutisse **JDK** (Java Development Kit)
 - https://jdk.java.net/11/ (sobib ka versioon 8 või hilisem)
- **IntelliJ IDEA** (või mõni muu IDE, nt Eclipse, NetBeans vms)
 - https://www.jetbrains.com/student/ - tudengi litsents, võimaldab kasutada Ultimate versiooni
 - Community versioon tasuta kättesaadav - on piisav aine läbimiseks
- Git Bash Windowsile:
 - https://gitforwindows.org/
@ulend

---

## Eksperiment - jagatud projekt

@ul
- Lõime jagatud projekti: https://gitlab.cs.ttu.ee/iti0202-2019/information
- Sinna saab igaüks uni-idga sisse
- Kasutage näiteks probleemide/ülesannete korral (*issue*)
- Proovime kasutada näidislahenduste jaoks (*merge request*)
@ulend

---

## Küsimused?