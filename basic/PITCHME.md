
## Programmeerimise põhikursus (ITI0202)


Muutuja, tingimuslause, tsükkel

Ago Luberg

---

## Java programm


@ul[ul-80]
- Programm kirjutatakse faili, mille laiend on java, nt ``Hello.java``
- Failis on alati vähemalt üks klass
- Faili nimi ja klassi nimi peavad olema samad
- Fail võib paikneda kaustas (kaust = pakk, *package*)
- Programm kompileeritakse

  - java-failidest luuakse class-failid
  - class-failid sisaldavad Java baitkoodi

- Kompileeritud Java baitkood pannakse käima

  - programm käivitatakse JVM (Java Virtual Machine) sees
  - JVM käivitab sama kompileeritud programmi sama tulemusega erinevate platvormide (Windows, Linux, Mac) peal
@ulend

---

## Hello world!

IntelliJ's:

- **File** -> **New..** -> **Project**
- Java (peaks olema valitud)
- Midagi muutma ei pea, **Next**
- **Next**
- Project name - projekti nimi, näiteks "Hello"
- **Finish**
- Paremal projekt "Hello", selle all "src" kaust
- Parem klikk "src" kaustal, **New..** -> **Java Class**
- Name: ``HelloWorld``, **OK**

---

## Hello world!

```java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.print("Hello world!");
    }
}

```

---

## Koodi käivitamine

- **Run** -> **Run..** -> **HelloWorld**
- või parem klikk koodiaknal **Run..**
- All paneelil on näha väljund, peaks olema umbes selline:

```
"C:\Program Files\Java\jdk-11.0.2\bin\java.exe" ....
Hello World!
Process finished with exit code 0
```


---

## Programmikoodi osad - klass

- Java kood on alati klassi sees
- Reeglina on ühes failis üks klass
- Failinimi ja klassinimi peavad ühtima

  - kui klassinimi on ``Hello``, peab failinimi olema ``Hello.java``:

```java
public class Hello {
   // class contents
}
```

---

## Programmikoodi osad - *main* meetod

- Kui java-fail käivitada, otsitakse üles ``main`` meetod
- ``main`` meetod kirjeldatakse järgnevalt:

```java
public static void main(String[] args) {
    // statements
}

```

---

## Programmikoodi osad - kokku

- Esialgu te ei pea väga täpselt aru saama, mida kogu järgnev kood teeb
- Võtke aluseks, et järgnev kood on minimaalne, et saaks programmi käima panna

```java
public class HelloWorld {
    public static void main(String[] args) {
        // statements
    }
}
```

---

## *main* meetod

@ul[ul-80]
- ``main`` meetodi definitsioonis:

 - ``public`` - tegemist on avaliku meetodiga (kättesaadav kõikidele)
 - ``static`` - staatiline meetod (vastupidiselt objekti/instantsi meetodile)
 - ``void`` - meetod ei tagasta midagi
 - ``main`` - meetodi nimi
 - ``()`` - sulgudes on parameetrid, mida antud meetod nõuab
 - ``String[] args`` - ``main`` meetodile antakse automaatselt kaasa käsurealt tulevad argumendid. Konkreetsemalt on tegemist sõnede massiiviga, mis on kättesaadav muutuja ``args`` kaudu.
@ulend

---

@snap[north span-100]
## Koodi kompileerimine
@snapend

@snap[west span-50]
@ul[ul-80](false)
- Java lähtekood kompileeritakse Jaba baitkoodiks
- Java baitkood käivitatakse JVM-s (Java Virtal Machine)
- JVM on implementeeritud erinevate operatsioonisüsteemide jaoks
  - sama baitkoodi saab jookustada erinevate platvormide peal
@ulend
@snapend

@snap[east span-50]
![Compiler](basic/java_compiler.png)

@size[10](http://math.hws.edu/javanotes/c1/s3.html)
@snapend

---

## Baitkoodi käivitamine

![Architecture](basic/jvm_architecture.png)

@css[image-caption](https://dzone.com/articles/jvm-architecture-explained)

---

## Kommentaar

- Kommentaar on osa koodist, mida kompilaator ignoreerib
- Kommentaar mitmel real `/*` ja `*/` vahel:

```
/*
 comment
 on
 several
 lines
*/
```

- Üherealine, kõik alates `//` kuni rea lõpuni:

```java
    a = 1; // comment here
```

---

## Programmi struktuur

Eelnevalt vaatasime ``HelloWorld`` klassi näidet

Üldisemalt võib klass välja näha järgnevalt:

```
public class ClassName {
    public static void main(String[] args) {
        // statements
    }
    
    // optional variable declarations and subroutines
}
```

---

## Muutuja

- Muutuja abil saab arvu mällu kirjutada ja sealt lugeda andmeid
- Muutuja nimetamine Javas: ``camelCase``, ``hellowWorld``, ``interestRate``, ``speed``.
- Sõnad kirjutatakse kokku, esimene sõna väikese tähega, edasi suure algustähega.

```java
rate = 0.07;
interest = rate * principal;
```

---

## Andmetüüp

@ul
- Javas on igal muutujal kindel andmetüüp
- Muutuja andmetüüpi ei saa muuta
- Muutujasse saab "salvestada" vaid andmeid määratud andmetüübiga
- Java andmetüübid jagatakse kaheks:

  - primitiivsed - hoiavad vaid ühte väärtust
  - objektid - väärtuste kogum, mis sisaldab primitiive ja teisi objekte
@ulend

---

## Primitiivne andmetüüp

| Data Type | Default Value | Min value                               | Max value                                              |
| ---- | --- | --- | --- |
| byte      | 0             | -128                                    | 127                                                    |
| short     | 0             | -32768                                  | 32767                                                  |
| int       | 0             | -2<sup>31</sup>                     | 2<sup>31</sup>`-1                                         |
| long      | 0L            | -2<sup>63</sup>    | 2<sup>63</sup> - 1  |
| float     | 0.0f          | 64-bit                                  | 64-bit                                                 |
| double    | 0.0d          | 64-bit                                  | 64-bit                                                 |
| char      | "\\u0000"     | \\u0000 või 0                           | \\uffff või 65535                                      |
| boolean   | false         | puudub                                  | puudub                                                 |


---

## Muutuja andmetüübiga

- `type-name variable-name;`

```java
int count;
double speed;
```

- `type-name variable-name = expression;`

```java
double rate = 0.03;
char space = ' ';
```

- Sama tüüpi muutujad ühel real:

```java
    double speed, distance;
    char first = 'A', middle = 'K', last = 'Z';
    int i, j = 42;
```

---

## Muutuja nimetamine

@ul[ul-80]
Java konventsioon:

- muutuja nimi peab olema tähenduslik (``temperature``, ``speed``, mitte :red-code:`a`, :red-code:`b`)
- nimi algab väikese tähega
- kasuta tervet sõna mitte lühendeid (``temperature`` vs :red-code:`temp`)
- kui nimi koosneb ühest sõnast, kasuta vaid väikeseid tähti (``weight``)
- kui nimi koosneb mitmest sõnast, kirjuta sõnad kokku ja alates teisest sõnast kirjuta sõna esimene täht suurtähega (``playAgain``, ``currentSpeed``)

- Konstandid kirjutatakse läbiva suurtähega (``PI``, ``SPEED``)
- sõnad eraldatakse alakriipsuga (``SPEED_OF_LIGHT``, ``NUMBER_OF_GEARS``)
@ulend

---

## Muutuja deklareerimine

Muutuja tuleb deklareerida enne kasutamist

```java
{
    int x;
    int y;
    x = 5;
    y = x + 2;

    int a;
    a = 5;
    int b;
    b = a + 2;
}
```

@css[red](Vale:)
```java
{
    x = 5;
    int x;
}
```

---

## Tehete järjekord

- ``exp++, exp--`` - *postfix*
- ``++exp, --exp, +exp, -exp, !``
- ``*`` - korrutamine
- ``/`` - jagamine
- ``%`` - jääk
- ``+, -`` - liitmine, lahutamine
- ``<, >, <=, >=`` - võrdlus
- ``==, !=`` - võrdsus
- ``&&`` - loogiline JA
- ``||`` - loogiline VÕI
- ``=, +=, -=, *=, /=, %=`` - omistamine

---

## Operaatorid

- Suurendamine/vähendamine

  - `y = x++` (``x`` suurendatakse **peale** omistamist)

    - ``y = x``
    - ``x = x + 1``

  - `y = ++x` (``x`` suurendatakse **enne** omistamist)

    - ``x = x + 1``
    - ``y = x``

- ``x += y``

  - ``x = x + y``

---

## Operaatorid

- Jagamine

  - kui jagatav ja jagaja on täisarvud, on tulemus täisarv (täisosa):

    - ``6 / 5 => 1``
    - ``9 / 5 => 1``
    - ``10 / 5 => 2``

  - kui jagatav või jagaja on komaga arv, on tulemus ka komaga arv (*double*):

    - ``6.0 / 5 => 1.2``
    - ``9 / 5.0 => 1.8``
    - ``10.0 / 5.0 => 2.0``

- Jääk

  - ``22 % 5 => 2`` (``22 / 5 => 4``, üle jääb ``2``)
  - ``5 % 5 => 0``

---

## Tüübiteisendus (*Casting*)

- Selleks, et kasutada väärtust teise andmetüübina, saab kasutada *cast*'imist
- Saan näiteks kasutada juhul, kui täisarvudega on vaja täpset tulemust
- Tüübiteisendus **ei muuda** (muutuja) väärtust

`(new-type)variable-name-of-value`

Näiteks:

```
    (double)8 / 5;    // 1.6
    int x = 5, y = 2;
    x / y;            // 5 / 2 => 2
    (double)x / y;    // 5.0 / 2 => 2.5
    x / y;            // 5 / 2 => 2
    (int)5.5 / 3;     // 5 / 3 => 1
```

---

## Koodiplokk

Koodiplokk grupeerib mitu käsklust üheks plokiks.

Süntaks:

```javas
{
    // statements
}
```

Näiteks:

```java
{
    System.out.print("Hello ");
    System.out.println("world!");
}

{ // this block changes values of x and y
    int tmp = x; // temporary variable tmp, store x in it
    x = y;       // copy value of y into x
    y = tmp;     // copy value tmp (original x) into y
}
```

---

## Muutuja skoop

Muutuja kehtib alates selle deklareerimisest kuni ploki lõpuni.

```
{
    int a = 1;
    System.out.println(a); // OK
}
System.out.println(a); // a is not declared here
```

Muutuja on kättesaadav sisemises plokis:

```java
{
    int a = 1;
    {
        System.out.println(a); // OK
    }
}
```

---

## Tingimuslause

Korraldus käivitatakse, kui tingimus on tõene:

```
if (boolean-expression)
    // statement
```

Kui tingimus on tõene, käivitatakse ``statement1``, muul juhul ``statement2``:

```
if (boolean-expression)
    // statement1
else
    // statement2
```

---

## Tingimuslause plokiga

Korraldused käivitatakse, kui tingimus on tõene:

```
if (boolean-expression) {
    // statements
}
```

Kui tingimus on tõene, käivitatakse ``statements1``, muul juhul ``statements2``:

```
if (boolean-expression) {
    // statements1
} else {
    // statements2
}

```

---

## *if-else* ahel

- Mitme tingimuse puhul võib kasutada ``if-else`` ahelat
- **Ainult üks** ahela lüli (korralduste plokk) käivitatakse

```
if (boolean-expression-1) {
    // statements-1
} else if (boolean-expression-2) {
    // statements-2
} else if (boolean-expression-N) {
    // statements-N
} else {
    // statements-N+1
}
```


---

## Tingimusavaldis

- Tingimusavaldis annab tulemuseks kas ``true`` või ``false``
- Näiteks:

  - ``if (true)``
  - ``if (false)``
  - ``if (5 > 2)`` (true)
  - ``if (4 == 4)`` (true)
  - ``if (!true)`` (false)

- Avaldisi võib kombineerida

  - ``exp1 && exp2`` **AND** - mõlead tingimused peavad tõesed olema
  - ``exp1 || exp2`` **OR** - vähemalt üks tingius peab olema tõene
  - ``(exp1 || exp2) && exp3`` grupeerimine sulgudega
  - ``if (4 > 2 || true && false)``
  - ``if (!(2 > 2 + 1) && !(4 == 3 || 2 <= 2))``

---

## Tingimuslause näide

```java
if (temperature <= 10) {
    System.out.println("It is cold");
} else if (temperature <= 25) {
    System.out.println("It is nice");
} else {
    System.out.println("It is hot");
}
```

---

## Segane ``if-else``

```java
if (x > 0)
    if (y > 0)
        System.out.println("y is positive");
else
    System.out.printn("x isn't positive");
```

Soovitus: **kasuta alati plokke!**

---

## Segane ``if-else`` parandatud

Kasutame plokke:

```java
if (x > 0) {
    if (y > 0) {
        System.out.println("y is positive");
    }
} else {
    System.out.println("x isn't positive");
}
```

---

## ``switch``

``switch`` konstruktsiooni saab kasutada diskreetsete väärtuste puhul
```
switch (expression) {
    case constant-1:
        // statements-1
        break;
    case constant-2:
        // statements-2
        break;
    // ...
    case constant-N:
        // statements-N
        break;
    default:
        // statements-N+1
}
```

---
