## ITI0202 - Programmeerimise põhikursus
### Projektipraktikum 1
#### Ago Luberg

---

## Mis toimub?

Paaris nädalatel toimub projekti praktikum.

---

## Mis on projekt?

@ul
- Suurem "kodutöö", mida teete kahekesi terve semestri jooksul
- Eesmärk on tutvuda projektihaldusega, plaanida oma tööd, realiseerida terviklik lahendus.
- Tavaline projekti tulemus on mäng.
- Kokku 150 punkti.
- Eksamieeldus.
@ulend

---

## OK

---

## Punktid

@ul
- 150 punkti kokku
- 75 punkti projektihaldus
- 75 punkti programmeerimine (funktsionaalsus)
- Mõlemast osast peab üle poolte punktide saama
@ulend

---

## Praktikum

@ul
- 1\. praktikum (2. nädal, täna) - korraldus ja info gitlabi kohta
- 2\. praktikum (4. nädal) - esitate projektiplaani
- ...
- **7. praktikum - esitamistähtaeg**
- Praktikumides toimuvad lühikesed ettekanded
- Igast tiimist vähemalt üks inimene peab kohal olema
@ulend

---

## Praktikum

@ul
- Iga tiim kannab ette oma seisu - tutvustavad projekti, selle edenemist, mis on tehtud, mis on plaanis
- Igast tiimist peab vähemalt üks liige kohal olema
- Hindame ettekannet ja edenemist kuni 15 punktiga
- Kokku semestri jooksul vähemalt 5 sellist ettekandmist
- Võimalik teenida 5 x 15p = 75 punkti
@ulend

---

## Projektihaldus

@ul
- Projekt gitlab.cs.ttu.ee portaalis
- Planeerite 2 nädalast tsüklit kahe praktikumi vahel - tähtpunkt (*milestone*)
- Loote ülesanded (*issue*)
- Mahukamatele ülesannetele määrate ajahinnangu (ntks 5h) ja proovite märkida reaalselt kulunud aja
- Iga ülesande jaoks Giti haru (*branch*)
- Otseselt ei hinnata seda, kas ajaplaneering oli täpne
- Pigem hinnatakse seda, et ülesanded on planeeritud ja on näha, mis on tehtud ja mis mitte.
@ulend

---

## Mille eest punktid tulevad?

@ul
- Ettekande puhul jagatakse kuni 15 punkti
- Kui tiimist ühtegi liiget kohal ei ole, saab 0p
- Kui tiim on kohal, hinnatakse järgmisi aspekte:
 - ettekanne
 - gitlabi ajalugu (*commit*'id, *issue*'d)
 - edenemine projekti eesmärgi suunas
@ulend

---

## Ettekanded

@ul
- Korraldame ettekanded neljas väiksemas grupis
- Jaguneme IAIB mentorite järgi
- Kes on muust õpperühmast, teid jagame ise ära
- IAIB tudengitel on juba tuttavad mentorid
- ... või siiski?
@ulend

---

## Funktsionaalsus

@ul
- Võimalik punktisumma jaguneb kolmeks etapiks:
 - 40p - minimaalne tase
 - 55p - normaalne tase
 - 75p - suurepärane tase
- Projektiplaani koostades kirjutab tiim, millist taset jahitakse
@ulend

---

## Veel punkte

@ul
- Viimases praktikumis (16. nädal) toimuvad paremate tiimide ettekanded
- Toimub hääletus tudengite seas
- Parimad tiimid saavad boonuspunkte
@ulend

---

## Teemad

@ul
- Üldine eesmärk on realiseerida JavaFX-is mäng
- Peale JavaFX-i võib realiseerida Androidi rakenduse või kasutada mõnda muud raamistikku
- On võimalik ka erinevad muud teemad kokkuleppel õppejõuga.
- Näiteks Gert pakub robootika ülesandeid.
@ulend

---

## Minimaalne funktsionaalsus (40p)

@ul
- Rakendus peab töötama
- Rakendus kasutab OOP printsiipe (klassid erinevate komponentide jaoks)
- Clean code
- javadoc, stiil korras
- Projekti aktiivne ajalugu gitis (projektihalduse osa täidetud)
- Lühike kasutusjuhend
@ulend

---

## Normaalne funktsoinaalsus (55p)

@ul[ul-70]
- Kõik mis 40p puhul
- MVC või mõne analoogse mustri kasutamine. Rakenduse loogika ja presentatsiooni (UI) kiht peaks mingil kujul olema eraldatud
- Ühiktestid (mitte UI osale). See eeldab, et eelnev punkt on realiseeritud - rakenduse loogika, mida peaks testima, on eraldatud UI-st.
- Rakenduse visuaal on stiliseeritud (ei ole default vormi elemendid, mustad/sinised ringid/ruudud). CSS-i kasutamine
- Animatsioonid (mängu puhul on see loomulikum; muu rakenduse puhul tuleks midagi vägisi külge panna)
- Timeline (thread). Rakenduses peaks olema paar erinevat timeline'i (thread'i). Näiteks korduvad tegevused, taustaprotsess vms.
@ulend

---

## Suurepärane tase (75p)

@ul[ul-80]
- See tähendab, et tuleks midagi keerukamat juurde lisada, näiteks:
 - Välise teenuse liidestamine (näiteks Facebook vms sotsiaalvõrgustik).
 - Multiplayer mäng (kahel erineval seadmel saab mängida)
 - Andmebaasiga liidestamine. Jällegi, nimetatud punktide saamiseks peaks rakenduses olema rohkem kui 1-2 tabelit.
 - Rakendus töötab erinevate seadmete peal (desktop + android)
 - 3D animatsioon/mäng
 - AI - mängule tehisintellekti loomine. See peaks olema rohkem kui mõned if-laused.
@ulend
 
---
 
## Järgmised sammud: tiimi moodustamine

@ul
- Pühapäeva õhtuks moodusta tiim
- Aine lehel  (ained.ttu.ee) on "projekti tiimid" komponent
- Loo endale tiim või liitu olemasolevaga
- Kui sul on hea idee, kirjuta paar rida infoks (et teised saaksid liituda)
- Kui sul ideed pole, otsi mõni olemasolev tiim, kus pole paarilist
@ulend

---

## Järgmised sammud: projekt gitlabis

@ul
- Loo projekt `iti0202-gui`
- Lisa paarilisele ligipääs (Settings -> Members -> lisa paariline, `Developer` roll)
- Siia alla lisage projektiplaan README.md failina
@ulend

---

## projektiplaan

@ul[ul-80]
- Järgmiseks praktikumiks (2 nädala pärast) koosta projektiplaan
- Peaks sisaldama vähemalt järgmisi osi:
 - lühike rakenduse kirjeldus
 - funktsionaalsuse kirjeldus
 - ajakava nädalate või kahe nädala kaupa (projektipraktikume silmas pidades)
 - võimalik kasutatava tehnoloogia ülevaade (Android, JavaFX, libGFX vms)
 - soovitav punktisumma
@ulend
 
---
 
## Projektiplaan

@ul
- Koosta kohe tähtpunktid (*milestone*)
- Koosta README.md fail (markdown või rst süntaks)
- Lisa kohe ülesanded (*issue*)
- Jaga ülesanded ära 
- Proovi kohe hinnata ka aega (saad hiljem muuta ja võrrelda tegelikkusega)
@ulend

---

## Küsimusi?

---

