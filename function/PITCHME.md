
## Programmeerimise põhikursus (ITI0202)

Loeng

Funktsioon (meetod)

Ago Luberg

---

## Koodi grupeerimine ja korduvkasutamine

- Sarnased osad koodis on mõistlik grupeerida, et neid oleks hiljem hea kasutada
- Selleks kasutatakse funktsioone
- Javas on funktsioonidena kasutuses staatilsed meetodid (hiljem räägime täpsemalt)
- Koodi grupeerimiseks kasutatakse ka klassidesse jagamist.

---

## Funktsioonid

- Osad meetodid tagastavad mingi väärtuse, neid nimetatakse ka funktsioonideks.
- Näiteks matemaatika funktsioonid:

```java
    Math.sqrt(9);
    Math.random();
```

- Meetodit kirjeldades tuleb öelda, mis tüübi andmeid see tagastab:

```java
    public static boolean lessThan(double x, double y)
```

- Eelnev defineerib meetodi (ehk funktsiooni) `lessThan`, mis tagastab tõeväärtuse (`boolean`).


---

## Funktsiooni tagastusväärtus


- Funktsioon peab tagastama seda tüüpi andmeid, nagu on funktsiooni definitsioonis märgitud
- Tagastamiseks kasutatakse `return` korraldust

- Näiteks:

```java
    static double pythagoras(double a, double b) {
        // computes the length of the hypotenuse of a right
        // triangle, the sides of the triangle are a and b
        return Math.sqrt(a * a + b * b);
    }
```

---

## Tagastusväärtus

- Arvutame 3N+1 järjestuse järgmise elemendi
  - 3N+1 puhul kui liige jagub kahega, jagatakse see kahega ning järgmine liige on saadud jagatis.
  - kui liige ei jagu kahega, korrutatakse liige 3-ga ja liidetakse 1 (tulemuseks on paarisarv)

```java
    static int nextN(int currentN) {
        if (currentN % 2 == 1) // test if current N is odd
            return 3 * currentN + 1; // if so, return this value
        else
            return currentN / 2; // if not, return this instead
    }
```
@[1-6](Täpselt üks `return` saab käivituda)
@[1-6](`return` võib paikneda kusiganes)
@[1-6](pärast `return` käivitamist funktsioon lõpetab)

---

## Dokumenteerimine

- JavaDoc on dokumentatsiooni genereerimise tööriist, millega saab lähtekoodist koostada "juhendi"

```java
    /**
     * Calculates the length of the hypotenuse for the right triangle
     * with the side lengths a and b.
     * @param a The length of one side
     * @param b The length of other side
     * @return The length of the hypotenuse
     */
    double pythagoras(double a, double b) {
        // code here
    }
```

---

## Dokumenteerimine

@ul[ul-70]
- JavaDoc koosneb:

  - Algab `/**`
  - Iga järgmine rida algab `*` (tärniga)
  - Esimene lause on lühike kirjeldus.
  - Sellele võib järgneda pikem kirjeldus (võib olla mitu peatükki).
  - Parameetrid kirjeldatakse `@param` sildiga:
   - `@param variable-name description`
  - Tagastatav väärtus kirjeldatakse eraldi `@return` sildiga:
   - `@return description`
  - Lisaks mainitule on teisigi märksõnu, mida saab kasutada
  - Lõppeb `*/` eraldi real

- Täpsem info: http://www.oracle.com/technetwork/java/javase/documentation/index-137868.html
@ulend

---

## Funktsiooni parameetrid

- Funktsioonil võib olla 0 või rohkem parameetreid
- Iga parameeter on määratud konkreetse tüübiga
- Funktsiooni välja kutsudes peab argumendina antud andmetüüp kattuma parameetrites vastaval kohal oleva andmetüübiga.
```java
    static void doTask(int N, double x, boolean test) {
        // statements to perform the task go here
    }
```

- Kutsume välja:

```java
    doTask(17, Math.sqrt(z + 1), z >= 10);
```

---

## Ülelaadimine (*overloading*)

- Javas võib klassis mitu samanimelist funktsiooni esineda, kui nende parameetrid on erinevad

  - st kas parameetrite arv on erinev
  - või andmetüübid on erinevad

```java
public static double calculatePrice(int count, double pricePerPiece) { }
public static double calculatePrice(int count) { }
public static double calculatePrice(double totalPrice, double discount) { }
```

- Aga selline pole lubatud:

```java
public static int calculatePrice(int count, double pricePerPiece) { }
```

---

## Ülelaadimine (*overloading*)

- Vastavalt sellele, mida koodis välja kutsutakse, pannakse õige funktsioon käima:

```java
    double price = calculatePrice(10, 1.2); // calls the first one

    double price2 = calculatePrice(10); // calls the second one

    double price3 = calculatePrice(99.90, 20); // calls the third one
```
@[1](Kutsub välja `int, double` parameetritega funktsiooni)
@[3](Kutsub välja `int` parameetritega funktsiooni)
@[5](Kutsub välja `double, double` parameetritega funktsiooni)
---

## Ülelaadimine (*overloading*)

- Saab kasutada näiteks vaikeväärtustega parameetrite asemel:

```java
public static double calculatePrice(int count, double pricePerPiece) {
    return count * pricePerPiece;
}

public static double calculatePrice(int count) {
    // default price = 1.00
    return calculatePrice(count, 1.00);
}

public static double calculatePrice(double pricePerPiece) {
    // default count = 1
    return calculatePrice(1, pricePerPiece);
}
```
@[7,12](Mõlemad abifunktsioonid kutsuvad välja põhifunktsiooni)
@[7,12](ühel juhul on tüki hind määratud `1.00`, teisel juhul kogus `1`.)

---

## Küsimused?