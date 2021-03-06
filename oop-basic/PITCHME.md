

## Programmeerimise põhikursus (ITI0202)

Loeng

OOP (*Object oriented programming*)

Ago Luberg

---

## Objektorienteeritud programmeerimine (OOP)

@ul
- Java on objektorienteeritud programmeerimiskeel (OOP)
- Objektorienteeritud programmeerimine (OOP) on programmeerimise paradigma, mis kasutab objekte
- OOP üldiselt lihtsustab suurte süsteemide arendamist
- Javas igasugune "väike" kood on juba OOP
@ulend

---

## OOP printsiibid

@ul[ul-90]
- **Kapseldamine** (*encapsulation*). Andmete ja oleku seostamine uueks ühtseks andmeühikuks (objektiks).
- **Abstraheerimine** (*abstraction*). Implementatsiooni peitmine kasutaja eest, kirjeldatakse vaid vajalik (abstraktne) käitumine.
- **Pärimine** (*inheritance*). Objektitüübist saab tuletada uusi objektitüüpe (laiendamine). Järglased (alamklass) pärib eellase (ülemkass) omadused (andmed + meetodid).
- **Polümorfism** (*polymorphism*). Samanimelised meetodid võivad erinevatel objektidel teostuda erinevalt.
@ulend

---

## Klass ja objekt

@ul[ul-80]
- Klass kui tarkvaramoodul

 - valmiskomponent
 - saab kasutada, et kokku panna suuremaid süsteeme

- Objekt on OOP keskne komponent

 - objekt on justkui iseseisev terviklik moodul:
 - millel on **olek** (andmed, mida see objekt sisaldab) ja
 - millele saab **sõnumeid saata** (meetodeid välja kutsuda)
@ulend

---

## Klass ja objekt

@ul[ul-80]
- **Klass** kirjeldab ära raamistiku

 - vorm, šabloon
 - klassil puudub sisu

- **Objekt** - vormi (klassi) järgi loodud andmehulk

 - klassile antakse sisu
 - ühest klassist võib luua mitu erinevat objekti

- Javas reeglina on iga klass eraldi failis

 - klass ``Car`` on failis ``Car.java``
@ulend

---

## Klass ja objekt

- Minimaalne klassi kirjeldus

```java
    public class Student {
    }
```

- Objekti loomine:

```java
    Student s = new Student();
```

---

## Klass ja objekt

@ul
- Klassi on see, mille arendaja kirjutab koodi.
- Objekt on see, mille kood loob kirjutatud klassist.
@ulend

---

## Andmetüüp (klass)

@ul[ul-90]
- Klassi nimi kirjeldab ära andmetüübi

 - kui kirjeldada klass ``Student``, siis saab luua vastavat tüüpi muutuja

- **Muutuja deklareerimine ei loo veel objekti**
- @css[red](Javas muutuja ei hoia endas kunagi objekti)
- Muutuja on **viide** (*reference*) objektile
- Objektid paiknevad arvuti mälus erinevatel positsioonidel
- Muutuja hoiab vajalikku infot, et objekt mälust üles leida
@ulend

---

## Objekti loomine

@ul[ul-90 ulw100](false)
- Objekti loomiseks kasutatakse operaatorit **new**

 - loob objekti
 - tagastab **viida** sellele objektile

- Näiteks loome uue ``Student`` tüüpi objekti:
@ulend

```java
    Student s = new Student();
```

@ul[ul-90 ulw100](false)
- Mällu luuakse uus ``Student`` objekt (sõltumatu teistest objektidest)
- Muutuja ``s`` viitab sellele objektile
- Muutuja ``s`` kaudu saab objekti meetodeid kasutada:
@ulend

```java
    s.getName();
```

---

## Null-viit (*null reference*)

@ul[ul-90](false)
- Muutuja, mille andmetüüp on mingi klass, ei pruugi viidata objektile
- Sellisel juhul hoiab muutuja null-viita (*null reference*)
- Null-viit kirjutatakse Javas **null**
@ulend

```java
Student std = null
if (std == null) {
    // ...
}
String name = std.getName();
```
@[1](Null-viida saab määrata muutujasse)
@[2-4](Null-viita saab kontrollida tingimuslauses)
@[5](Kui muutuja hoiab null-viita, ei tohi sellel pärida meetodeid/muutujaid)
@[5](See rida viskab `NullPointerException` erindi.)


---

## Objekti näide

@ul[special](false)
- @css[red](Ärge kasutage ``public`` muutujaid!)
@ulend

```java
    public class Student {
        public String name;  // Student's name.
        public double test1, test2, test3;   // Grades on three tests.
        public double getAverage() {  // compute average test grade
            return (test1 + test2 + test3) / 3;
        }
    }  // end of class Student

    // ...
    
    Student std, std1,      // Declare four variables of
            std2, std3;     // type Student.

    std = new Student();    // Create a new object belonging
                            //   to the class Student, and
                            //   store a reference to that
                            //   object in the variable std.

    std1 = new Student();   // Create a second Student object
                            //   and store a reference to
                            //   it in the variable std1.

    std2 = std1;            // Copy the reference value in std1
                            //   into the variable std2.

    std3 = null;            // Store a null reference in the
                            //   variable std3.

    std.name = "John Smith";  // Set values of some instance variables.
    std1.name = "Mary Jones";
```



@snap[east span-50 image-string-example]
![String example](oop-basic/string_example.png)
@snapend


---

## Objektid ja väärtustamine

@ul[ul-80]
- Kui muutujale antakse väärtuseks muutuja (viide mingile objektile), siis kopeeritakse ainult viide

 - ``std2 = std1``
 - ``Student`` objekt, millele ``std1`` viitab, jääb mälus täpselt samasuguseks
 - ``std2`` viitab nüüd samma kohta
 - objekti ei kopeerita!

- **Primitiivsete** andmetüüpide puhul **väärtus kopeeritakse**
- **Objektide** puhul objekti **ei kopeerita**, ainult **viide kopeeritakse**
- ``std1.name`` ja ``std2.name`` viitavad samale nimele

 - viitavad samale mäluaadrssile
 - kui mälu sisu muutub, muutub see kõikide viitade (muutujate) jaoks
@ulend

---

## Objekti võrdlemine

```java
    Student s1 = new Student("Mati");
    Student s2 = new Student("Mati");

    if (s1 == s2) {
        System.out.println("the same student!");
    } else {
        System.out.println("Not the same");
    }
```
@ul[ul-80]
- Luuakse kaks objekti (kaks tudengit)
- Mõlema nimi on Mati, aga nad on erinevad tudengid
- Võrdlusega ``s1 == s2`` kontrollitakse, kas ``s1`` ja ``s2`` viitavad **samale** tudengile

 - **ei võrrelda objekti väärtusi**

- **equals** meetod sõltub objektist

 - tudengi puhul võiks kontrollida nime, koodi jms.
@ulend

---

## Sõnede võrdlemine

- Sõne on objekt
- Seega kasutame **equals** meetodit, et võrrelda sõnede sisu
- Sõne puhul kontrollitakse sõne tähti/sümboleid

```java
    String s1 = new String("hello");
    String s2 = new String("hello");

    System.out.println(s1 == s2);       // false
    System.out.println(s1.equals(s2));  // true
```

---

## Pärimine (*inheritance*)

@ul
- OOP tsentraalne idee on võimaldada kirjeldada sarnaseid objekte, mis on mingis osas sarnased (jagavad sarnast struktuuri ja/või käitumist)
- Sellist sarnasust väljendatakse pärimise abil
- Pärimine tähendab, et üks klass pärib kas kõik või osa oma struktuurist ja käitumisest mõnelt teiselt klassilt
@ulend

---

## Pärimine (*inheritance*)

@snap[east image-single-inheritance]
![Single inheritance](oop-basic/single_inheritance.jpg)
@snapend

@ul[ul-80 ulw80](false)
- **Alamklass** (*subclass*) on klass, mis pärib struktuuri ja käitumise teiselt klassilt
- Kui klass ``B`` on alamklass klassile ``A``, siis ``A`` on **ülemklass** (*superclass*) klassile ``B``.
- Klassi kirjeldust luues saab määrata, kas see klass on mõne teise klassi alamklass
- Kui klass ``B`` on alamklass klassile ``A``, siis kirjutatakse:
@ulend

```java
    public class B extends A {
        // additions to, or modifications of,
        // stuff inherited from class A.
    }
```

---

## Mitu alamklassi

- Ühel ülemklassil võib olla mitu alamklassi
- Pärimine võib toimuda ka üle mitme "generatsiooni"
- Joonisel klass ``E`` on alamklass klassile ``D``, ``D`` omakorda on alamklass klassile ``A``.

![Multi inheritance](oop-basic/multi_inheritance.png)

---

## Näide: sõidukid

![Vehicle inheritance](oop-basic/vehicle_inheritance.png)

@ul[ul-60]
- Klass ``Vehicle`` kirjeldab üldise sõiduki
- Selle abil saab kirjeldada kõiki sõiduki tüüpe

- **Ühine** kõikide sõidukite peale:

 - ``Vehicle`` klass võib sisaldada instantsi muutujaid nagu ``registrationNumber`` (registrinumber), ``owner`` (omanik) ja instantsi meetodit ``transferOwnership()``.

- **Laiendused**: iga alamklass võib lisada selle tüübi spetsiifilisi muutujaid ja meetodeid:

 - ``Car`` klassis näiteks ``numberOfDoors`` (uste arv)
 - ``Truck`` klassis näiteks ``numberOfAxles`` (telgede arv)
 - ``Motorcycle`` klassis näiteks tõeväärtust ``hasSidecar`` (külgkorviga)
@ulend

---

## Koodinäide

```java
    public class Vehicle {
        private String registrationNumber;
        private Person owner;

        public String getRegistrationNumber() { 
            return registrationNumber; 
        }

        public void setRegistrationNumber(String registrationNumber) {
            this.registrationNumber = registrationNumber;
        }

        public Person getOwner() { return owner; }

        public void setOwner(Person owner) { 
            this.owner = owner; 
        }

        // all subclasses will have this method
        public void transferOwnership(Person newOwner) {
            // change owner here
        }
    }


    public class Car extends Vehicle {
        private int numberOfDoors;

        public int getNumberOfDoors() { 
            return numberOfDoors; 
        }

        public void setNumberOfDoors(int numberOfDoors) { 
            this.numberOfDoors = numberOfDoors; 
        }
    }
```

---

## Vehicle objektid

- Loome uue ``Car`` tüüpi objekti:

```java
    Car myCar = new Car();
```

- kasutades ``Car`` klassi kirjeldust, saame pöörduda:

```java
    myCar.getNumberOfDoors();
```

- Kuna ``Car`` laiendab klassi ``Vehicle``, pärib ta järgmised meetodid:

```java
    myCar.getRegistrationNumber();
    myCar.getOwner();
    myCar.transferOwnership();
```

---

## Tüübid ja alamtüübid

@ul[ul-80](false)
- Pärismaailmas on nii autod, veoautod ja mootorrattad kõik sõidukid

 - sama kehtib tegelikult ka programmis

- Objekt, mille tüüp on ``Car``, ``Truck`` või ``Motorcycle``, on automaatselt ``Vehicle`` tüüpi

- Muutuja, mis saab viidata objektile **tüübiga A**, saab ühtlasi viidata ka objektile, mille tüüp on **A alamklass**
- Seega on korrektsed:
@ulend

```java
    Vehicle myVehicle = myCar;
    Vehicle yourVehicle = new Car();
```

---

## Objekt teab oma klassi

@ul[ul-90](false)
- Objekt teab, et ta on tegelikult ``Car`` tüüpi, mitte ``Vehicle`` tüüpi objekt

 - info klassi kohta salvestatakse koos objektiga

- Selleks, et kontrollida, kas objekt kuulub klassi, saab kasutada:
@ulend

```java
    if (myCar instanceof Car)
```

@ul[ul-90](false)
- Vastupidiselt eelnevale, järgmine kood ei tööta:
 - @css[red](`myCar = myVehicle;`)
 - kuna ``myVehicle`` võib viidata ka teist tüüpi sõidukile (nt mootorratas).
@ulend


---

## Tüübiteisendus (*cast*)

@ul[ul-80](false)
- Kui on teada, et ``myVehicle`` on ``Car`` tüüpi, saab kasutada tüübiteisendust (*cast*):
@ulend

```java
    (Car) myVehicle
```

@ul[ul-80](false)
- Selliselt kasutab arvuti ``myVehicle`` objekti nagu see oleks ``Car`` tüüpi
- **Tüübiteisendusega algne objekt (ja selle tüüp) ei muutu**
- Näiteks saab teha nii (tüübiteisendus muutujasse):
@ulend

```java
    myCar = (Car) myVehicle;
    System.out.println(myCar.getNumberOfDoors());
```

@ul[ul-80](false)
- Või kasutada tüübiteisendust jooksvalt:
@ulend

```java
    System.out.println( ((Car) myVehicle).getNumberOfDoors());
```

---

## Tüübiteisendus ja -kontroll

```java
    System.out.println("Vehicle regnr:" +
            myVehicle.getRegistrationNumber());

    if (myVehicle instanceof Car) {
        System.out.println("Vehicle type: Car");
        Car car = (Car) myVehicle;
        System.out.println(car.getNumberOfDoors());
    } else if (myVehicle instanceof Truck) {
        System.out.println("Vehicle type: Truck");
        Truck truck = (Truck) myVehicle;
        System.out.println(truck.getNumberOfAxles());
    } else if (myVehicle instanceof Motorcycle) {
        System.out.println("Vehicle type: Motorcycle");
        Motorcycle motorcycle = (Motorcycle) myVehicle;
        System.out.println(motorcycle.hasSidecar());
    }
```
---

## Polümorfism (*polymorphism*)

- Samanimeline meetod võib erinevat tüüpi objektil käituda erinevalt

---

## Näide: kujundid

![Shapes](oop-basic/shapes.png)

@ul[ul-60]
- Näiteks on meil programm, mis tegeleb kujundite joonistamisega ekraanile

 - meil on kolme tüüpi kujundeid: ristkülikud, ovaalid ja ümarad ristkülikud
 - kujundid võivad erinevat värvi olla

- Kujundite jaoks võib kasutada kolme klassi: ``Rectangle``, ``Oval`` ja ``RoundRect``
- Kolm klassi võiksid omada ühist ülemklassi ``Shape``, mis sisaldaks ühiseid omadusi

 - väärtused: värv, positsioon, suurus
 - meetodid väärtuste muutmiseks

- Värvi muutmine muudab instantsi muutuja väärtuse ja joonistab kujundi uue värviga.
@ulend

---

## Shape koodinäide

```java
    public class Shape {
        // import javafx.scene.paint.Color for example
        private Color color;

        public void setColor(Color newColor) {
            color = newColor; // change the value of instance variable
            redraw(); // redraw the shape in new color
        }
        public void redraw() {
            // how to draw the shape..
        }
    }
```

---

## Kuidas joonistada kujundit?

@ul
- Erinevad kujundid joonistatakse erinevalt
- ``setColor()`` töötab igasuguse kujundi jaoks
- Kuidas arvuti teab, millist kujundut joonistada, kui ``redraw()`` välja kutsutakse?

- Vastus:

 - Arvuti laseb kujundil **iseennast joonistada**
 - **Iga kujund teab**, kuidas ennast joonistada.
@ulend

---

## Igal klassil oma **redraw()**

```java
    public class Rectangle extends Shape {
        @Override
        public void redraw() {
            // commands for drawing a rectangle
        }
    }

    public class Oval extends Shape {
        @Override
        public void redraw() {
            // commands for drawing an oval
        }
    }

    public class RoundRect extends Shape {
        @Override
        public void redraw() {
            // commands for drawing a rounded rectangle
        }
    }
```

---

## Ülekirjutamine (*override*)

@ul[ul-80]
- Alamklass võib ülemklassi meetodi üle kirjutada
- See tähendab, et alamklassis on kirjeldatud sama nime ja samade parameetritega meetod mis ülemklassis
- Kui koodis pöördutakse objekti meetodi poole, siis kõigepealt otsitakse meetodit objekti tüüpi klassist.

 - Kui sealt meetodit ei leita, otsitakse ülemklassist jne

- Koodis kirjutatakse ``@Override`` annotatsioon meetodi ette

 - see pole koodi käivitamise mõttes oluline, aga loetavuse ja jälgitavuse mõttes vajalik
@ulend

---

## Polümorfism (*polymorphism*)

```java
    Shape shape;
```

@ul[ul-60](false)
- ``shape`` võib viidata ükskõik millisele ``Shape`` alamtüübile (``Rectangle``, ``Oval``, ``RoundRect``)
- Programmi käivitamise ajal võib see muutuja erineval ajahetkel viidata erinevt tüüpi objektile
- Ükskõik milla kutsutakse välja:
@ulend

```java
    shape.redraw();
```

@ul[ul-60](false)
- siis ``redraw()`` meetod käivitatakse selle objekti juures, millele ``shape`` viitab

---

## Polümorfism (*polymorphism*)

```java
for (Shape shape : allTheShapes) {
    shape.redraw();
}
```

- Näiteks käime kõik kujundid ekraanil läbi, ühe tsükli sammu jooksul muutuja ``shape`` viitab ühele kujundile ekraanil, millele rakendame ``redraw()`` meetodit
- Saame öelda, et ``redraw()`` on **polümorfne**
- Meetod on polümorfne, kui käivitatav tegevus sõltub objekti tegelikust tüübist

---

## Polümorfism => sõnumid

@ul[ul-80]
- OOP puhul kasutatakse meetodi väljakutse kohta mõnikord väljendit sõnumi saatmine objektile
- Objekt vastab sõnumile sellega, et käivitab vastava meetodi
- Käsklus ``shape.redraw();`` saadab sõnumi ``shape`` objektile
- Objekt ise teab, mis tüüpi ta on, seega ta teab, kuidas sõnumile vastata

- Selliselt vaadatuna käivitab arvuti ``shape.redraw()`` alati samamoodi: saadab sõnumi
- Vastus sõnumile sõltub sellest, kes selle vastu võtab
- Polümorfism tähendab, et **erinevad** objektid võivad **samale sõnumile** reageerida erinevalt
@ulend

---

## Polümorfism: tüüpide lisamine on lihtne

![Shapes new](oop-basic/beveled_rect.png)

@ul[ul-60]
- Kui peame programmi lisama uut tüüpi kujundi (``BeveledRect``), piisab uue klassi kirjutamisest ja ``redraw()`` meetodi kirjeldamisest

- ``shape.redraw()`` meetod töötab automaatselt ka uue kujundi korral
@ulend

---

## **this** ja **super**

@ul[ul-60](false)
- Käskluse ``shape.redraw();`` puhul saadetakse sõnum ``shape`` objektile

- ``Shape`` klassis on ``setColor`` meetod:
@ulend

```java
    public void setColor(Color newColor) {
        color = newColor; // change the value of instance variable
        redraw(); // redraw the shape in new color
    }
```

@ul[ul-60](false)
- Millisele objektile saadetakse ``redraw()`` sõnum?
- ``setColor()`` on ise sõnum, mis saadeti mingile objektile
- vastus on, et ``redraw()`` sõnum saadetakse samale objektile, mis sai ``setColor()`` sõnumi
- Kui ``setColor()`` kutsutakse välja ristküliku objektil, siis ``redraw()`` kutsutakse välja samal objektil (``Rectangle`` klassis olev ``redraw()`` meetod).
@ulend

---

## **this** ja **super**

@ul[ul-80](false)
- ``redraw()`` meetod ``setColor()`` meetodis ei pruugi välja kutsuda ``Shape`` klassi ``redraw()`` meetodit
- ``redraw()`` meetod, mis käivitatakse, võib olla ükskõik millises ``Shape`` alamklassis
- Javas on kaks spetsiaalset muutujat, mis väärtustatakse, kui mõni meetod on välja kutsutud:

 - **this** - objekt, mis sai sõnumi (millel meetod välja kutsuti)
 - **super** - viitab sama objekti ülemklassile
@ulend

---

## **this**

@ul[ul-60](false)
- Muutuja **this** viitab objektile, mis sai sõnumi
- Seda on vaja kasutada näiteks siis, kui objekti ennast on vaja anda kaasa teise meetodisse:

 - ``Person`` objekti määramine raamatu omanikuks ``Book`` klassis:
@ulend

```java
    book.setOwner(this);
```

@ul[ul-60](false)
- Teine kasutuskoht on *setter* meetodites:
@ulend

```java
    public void setName(String name) {
        this.name = name;
    }
```

@ul[ul-60](false)
- ``name`` viitab kohalikule muutujale (deklareeritud meetodi sees)

 - see peidab ära objekti muutuja ``name`` (mis on sama nimega)

- ``this.name`` viitab sõnumi saanud objekti muutujale
@ulend

---

## **super**

@ul[ul-80]
- **super** viitab sama objekti (instantsi) **ülemklassile**
- Kui ülemklassis on sama nimega meetod kui alamklassis (nt ``redraw()``), siis alamklassi tüüpi objekti puhul meetodit välja kutsudes peidetakse ülemklassi meetod ära

 - kui ``shape`` on ristkülik, siis ``shape.redraw()`` kutsub ``Rectangle`` klassi ``redraw()`` meetodit
 - ``Shape`` klassi ``redraw()`` meetod on peidetud
 - selleks, et kutsuda välja ülemklassi ``redraw()`` meetodit, saab kasutada: ``super.redraw();``
@ulend

---

## **super** näide

@ul[ul-50](false)
- Oletame, et meil on klass ``TextBox``, mis kirjeldab ära tekstilahtri ekraanil, kuhu kasutaja saab teksti sisse kirjutada.
- Olgu sellel klassil instantsi meetod ``key()``, mis kutsutakse välja iga klahvi vajutuse peale

 - Meetodi eesmärk on kasutaja vajutatud klahvi kuvamine tekstilahtris

- Kui tahame luua alamklassi ``NumberBox``, mis lubab kasutajal sisestada vaid numbreid, saame kirjutada:
@ulend

```java
    public class NumberBox extends TextBox {
        @Override
        public void key(char ch) {
            if (ch >= '0' && ch <= '9') {  // show only 0..9
                super.key(ch);
            }
        }
    }
```

@ul[ul-50](false)
- Kui sisestatud sümbol on number, kutsutakse välja ``super.key(ch)``, mis kuvab sümboli (numbri) ekraanil.
- ``super`` viitab siin ``TextBox`` klassis kirjeldatule.
- Muul juhul ei tehta midagi, ehk sümbol ekraanile ei ilmu
@ulend

---

## Nähtavus

![Visibility](oop-basic/visibility.png)

@ul[ul-80](false)
- **public** - kõigile nähtav
- **protected** - paketi sees nähtav, alamklass (ka mujal paketis) näeb
- *puudub* - ainult paketi sees nähtav
- **private** - ainult klass näeb
@ulend

---

## Millal *private*, *public*?

@ul[ul-80]
- Üldine reegel

 - Kasuta kõige rangemat (piiratumat) nähtavust.
 - Seega, kasuta alati ``private``, kui sul pole väga head põhjust midagi muud kasutada.
 - Väldi ``public`` muutujate kasutamist, välja arvatud konstantide puhul

- Objektide puhul tuleks kasutada *getter*/*setter* meetodeid andmete/oleku muutmiseks

 - Annab võimaluse hiljem implementatsiooni muuta
 - Otse väljade kasutamine (``Student.name``) teeb hilisema funktsionaalsuse muutmise keeruliseks

- *getter*/*setter* meetodid on üldiselt ``public`` nähtavusega
@ulend

---

## *getter* / *setter* meetodid

@ul[ul-80]
- Kasutatakse objekti oleku muutmiseks
- *getter* võimaldab objekti olekut lugeda
- *setter* võimaldab objekti olekut muuta
- Tavaliselt ``public`` nähtavusega
- Saab kontrollida, kuidas objekti olekut saab jälgida/juhtida väljaspoolt objekti

 - näiteks kasutaja ``id`` väärtust hiljem enam muuta ei lubata
 - ehk siis *getter* on olemas, *setter* aga puudub
@ulend

---

## *getter* / *setter* näide

```java
    public class Student {
        private int id;
        private String name;

        public int getId() {
            return id;
        }

        public void setName(String name) {
            this.name = name;
        }

        public String getName() {
            return this.name;
        }
    }
```

---

## *getter* / *setter* IntelliJ-s

@ul
- Kirjelda instantsi muutujad ära
- ``alt`` + ``insert`` annab menüü
- vali ``Getter and Setter``
- saad valida väljad, mille kohta genereeritakse meetodid
@ulend

---

## Staatiline muutuja / meetod

@ul[ul-80](false)
- (Instantsi) muutuja / meetod on seotud ühe konkreetse isendiga
- Ühe tudengi (instantsi, objekti) nimi ei ole kuidagi seotud teise tudengi nimega
- Ühe tudengi meetod ``sleep()`` mõjutab ainult seda tudengit
- **Staatilised** muutujad ja meetodid ei ole setud objektiga, vaid on seotud **klassiga**
- Staatilise muutuja väärtus on üle programmi ühine
- Staatiline meetod kutsutakse välja klass nimega:
@ulend

```java
    int a = Math.abs(-12);
```

---

## Staatiline / mittestaatiline näide

```java
    public class Student {
        public static final String STUDENT_CODE_PREFIX = "TALTECH";
        private String name;
        private String code;

        public static String generateCode(String name) {
            // calculate or get code from somewhere
            return STUDENT_CODE_PREFIX + "_" + name.toUpperCase();
        }

        public Student(String name) {
            this.name = name;
            code = Student.generateCode(name);
        }

        public String getCode() {
            return code;
        }

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }
```

---

## Konstruktor

@ul[ul-80]
- Eriline meetod, mis pannakse käima juhul, kui luuakse uus objekt
- Seda ei pea kirjeldama klassi puhul
- Meetodil pole tagastustüüpi
- Nimi on alati sama klassi nimega
- Mõistlik kasutada oleku algväärtustamiseks
- Kui konstruktorit ei kirjelda, siis objekti loomisel ei tule argumente kaasa anda
@ulend

---

## Konstruktori näide

@ul[ul-80](false)
- Kui konstruktorit ei defineeri:
@ulend

```java
    public class Student {
    }
```

@ul[ul-80](false)
- Saab kasutada nii:
@ulend

```java
    Student s = new Student();
```
---

## Konstruktori näide

@ul[ul-80](false)
- Konstruktoriga:
@ulend

```java
    public class Student {
        private String name;
        private int age;

        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }
    }
```

@ul[ul-80](false)
- Saab kasutada nii:
@ulend

```java
    Student s = new Student("Mati", 22);
```

---

## Konstruktori ülelaadimine

```java
    public class Student {
        enum Gender { MALE, FEMALE, UNKNOWN }

        private String name;
        private int age;
        private Gender gender;

        public static final int AGE_UNKNOWN = -1;

        public Student(String name, int age, Gender gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
        }

        public Student(String name) {
            this(name, AGE_UNKNOWN, Gender.UNKNOWN);
        }

        public Student(String name, int age) {
            this(name, age, Gender.UNKNOWN);
        }

        public Student(String name, Gender gender) {
            this(name, AGE_UNKNOWN, gender);
        }
    }
```

---

## **enum**

@ul[ul-80](false)
- **enum** - eriline klass, mis hoiab vaid konstante
@ulend

```java
    public enum Weekday {
        MONDAY, TUESDAY, WEDNESDAY, THURSDAY,
        FRIDAY, SATURDAY, SUNDAY
    }
```

@ul[ul-80](false)
- Kirjeldatakse näiteks eraldi failis Weekday.java

 - võib kirjeldada ka teise klassi sees

- Kasutamine:
@ulend

```java
    if (getWeekday() == Weekday.FRIDAY) {
        System.out.println("Party!");
    }
```

---

## **enum** lisainfoga

```java
    public enum Weekday {
        MONDAY("esmaspäev", true),
        TUESDAY("teisipäev", true),
        WEDNESDAY("kolmapäev", true),
        THURSDAY("neljapäev", true),
        FRIDAY("reede", true),
        SATURDAY("laupäev", false),
        SUNDAY("pühapäev", false);

        private String name;
        private boolean workingDay;

        Weekday(String name, boolean workingDay) {
            this.name = name;
            this.workingDay = workingDay;
        }

        public String getName() {
            return name;
        }

        public boolean getWorkingDay() {
            return workingDay;
        }
    }
```

---

## Küsimused
