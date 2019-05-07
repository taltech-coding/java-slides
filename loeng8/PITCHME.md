## Programmeerimise põhikursus (ITI0202)

Loeng 8 - eksam jm info

Ago Luberg

---

## Eksamiajad

- Klassiruumid ICT-121, ICT-122
- 21.05.2019 (teisipäev)
- 29.05.2019 (kolmapäev)
- 06.06.2019 (neljapäev)
- Konsultatsioon eelmisel päeval kell 10

---

## Eksamieeldus

- 250p semestri jooksul (ülesanded, projekt jms)
- Kontrolltöö vähemalt 10p
- **Projekt kaitstud**

---

## Eksamipunktid

- Kokku 500p
- Läbisaamiseks vaja saada vähemalt 251p
- 500p jaguneb
 - 250p "vaba oop" - testideta ülesanne, kus vaja ise ülesande struktuur välja mõelda
 - 50p reskursiooni ülesanne
 - 100p OOP ülesanne testidega
 - 100p algoritmilised ülesandeid (a la CodingBat)
 
---

## Progemisvõistlus

- 13\. mai kell 14.00 - 17.30 ruumis ICT-121
- 3-liikmeline võistkond
- paremad tiimid lähevad 25. mail Soome võistlema
- registreerimiseks ained.ttu.ee -> Programmeerimisvõistlused -> HIIT eelvõistlus..
- loo grupp ja lase tiimikaaslastel liituda

---

## Gomoku

@ul[ul-80]
- 16\. nädala praktikumis toimub võistlus
- Võistlusel osalemine annab +5p (ilma võistluseta max 45p)
- Peab võitma tugevamat vastast
- Parim tiim (mõlemad tudengid) saab 100p, teine koht 50p
- Võistlusel osalemiseks tuleb regada hiljemalt 16. nädala teisipäeval
- Saatke kood (üks java fail) meiliga: ago.luberg@taltech.ee
 - emaili pange võistkonna liikmete nimed ja uniid-d
@ulends

---

## Projektide hindamine

- Avalikustame hääletamise, kus iga tudeng saab valida 5 erinevat projekti (1. koht, 2. koht jne)
- Selleks lisa `iti0202-2019-gui` projekti `info.md`, milles on:
 - üks pilt mängust
 - link jar-failile
 - lühike tekst
- Koostame nimekirja, kus kõik projektid on kättesaadavad
- Loomulikult võid sõpradele reklaamida ise ka oma mängu

---

## Projektide hindamine

- Parimad 5 projekti saavad boonuspunkte:
 - 1\. koht 50p
 - 5\. koht 10p
- Eeldab, et projekti liikmed ise on ka hääletanud
- Eeldab, et projekt on kaitstud (või saab kaitstud)

---

## Kaitsmine sessi ajal

- Ülesanded, mida saab teha sessi ajal:
 - EX09 ComputerShop (15p)
 - EX13 Weather (7.5p)
 - EX14 Furniture (15p)
 - EX15 Casino (15p)
 - Projekt (60p)
 - Gomoku (45p)
 
---

## Lisaks saab kaitsta

- Muud ülesanded -50%
- Giti tähtaeg kehtib
- Võimalik kaitsta vanu ülesandeid

---

## Projekt sessi ajal

- Võimalus saada eksamieeldus kätte
- Projektihalduse eest maksimaalselt 30p
 - Eeldab, et gitlabis on *issue*'d ja *commit*'id näha mõistlikult + kaitsmisel ettekanne projektihaldusest
- Projekti sisu (kood jms) eest (kui pole eelnevalt näidanud) maksimaalselt 30p

---

## Järeljärelkontrolltöö

- 20\. mai kell 10:00 ICT-122
- Registreerumine ained.ttu.ee lehel (Järeljärelkontrolltööle registreerumine)

---

## Punktiseis

@ul
- Võimalik veel teenida:
 - 52.5p 4 x EX, 
 - 60p projekt, 
 - 45p Gomoku
 - 20p KT
- **Kokku: 177.5p**
@ulend

---

## Tule abiõppejõuks

- Sügisel Pythoni kurusele appi
- Saab 3 EAP-d (õpetamispraktika)
- Saab stipendiumi (u 70 eurot kuus)
- Kirjuta: ago.luberg@taltech.ee
 - Miks sa tahad abiõppejõuks?
 - Paari lausega, kuidas sa tahaksid kursust *veel* paremaks teha
- **Tähtaeg: 15. mai**

---

## Abiõppejõud

- Sügisel uus kursus: programmeerimise täiendusõpe
- Suvel: 
 - täiendame pydoci
 - mõtleme täiendusõppe korralduse
 - ülesannete loomine
- Sügisel:
 - praktikumid, konsultatsioonid jms
 
---

## Küsimused?

---

## Gomoku

@ul
- vt minimaxi videost
- vaata igast positsioonist igas suunas tekkivad nuppude järjestused
- loe kokku, mitu nuppu järjest on
- anna erinevad punktid vastavalt kogusele
 - nt enda "lahtine 4" (== võit) - 100 000 punkti
 - "poollahtine 4" - 10 000 punkti
 - enda "lahtine 3" - 1000 punkti
@ulend

---

## Gomoku

@ul
- Optimeeri
 - alpha-beta minimaxi asemel
 - milliseid ruute tasub läbi käia?
 - millistes suundades on vaja vaadata?
- Lisa ajapiirang 1 sekund
@ulend

---

## Vaba OOP

- Mõned näited KT1, KT2 koodidest

![oop](loeng8/oop_private_fields.png)

---

## Vaba OOP

![oop](loeng8/oop_type_string.png)

---

## Vaba OOP

![oop](loeng8/oop_constructor.png)

---

## Vaba OOP

![oop](loeng8/oop_optional.png)

---

## Vaba OOP

![oop](loeng8/oop_oet_add_dog.png)