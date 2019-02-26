## Programmeerimise põhikursus (ITI0202)

Loeng

Konstruktor (*Constructor*)

Ago Luberg

---

## Konstruktor

@ul
- Eriline meetod, mis pannakse käima juhul, kui luuakse uus objekt
- Seda ei pea kirjeldama klassi puhul
- Meetodil pole tagastustüüpi
- Nimi on alati sama klassi nimega
- Mõistlik kasutada oleku algväärtustamiseks
- Kui konstruktorit ei kirjelda, siis objekti loomisel ei tule argumente kaasa anda
@ulend

---

Konstruktori käivitusahel
=========================

- Kõigepealt käivitatakse ülemklassi konsturktor, seejärel alamklassi konstruktor

```java
public class Vehicle {
    public Vehicle() {
        System.out.println("Vehicle constructor");
    }
}
public class Car extends Vehicle {
    public Car() {
        System.out.println("Car constructor");
    }
}
public class Main {
    public void run() {
        Car c = new Car();
    }
}
```
@[](Sõiduk ja alamklass auto, mõlemal konstruktor print korraldusega)
@[13](Loome uue `Car` objekti)
@[1-100](Prinditakse `Vehicle construtor` ja `Car constructor`.)

---

## Vaike-konstruktor (*default constructor*)

@ul[ul-70](false)
- Kui klass ei defineeri ühtegi konstruktorit, siis öeldakse, et sellel klassil on vaike-konstruktor (*default constructor*)
- *Default constructor* on ilma parameetriteta konstruktor
- ``Student`` klass, millel on vaike-konstruktor:
@ulend

```java
    public class Student { }
```

@ul[ul-70](false)
- ``Student`` klass, mis kirjeldab konstruktori (samaväärne eelmisega, aga enam ei ole tegemist vaike-konstruktoriga)
@ulend

```java
    public class Student {
        public Student() { }
    }
```

---

## Konstruktori käivitusahel

@ul[ul-60]
- Konstruktori puhul käivitatakse **kõigepealt ülemasklassi konstruktor**

 - kui konstruktoris eraldi ülemklassi konstruktori väljakutset pole,
   käivitatakse ilma parameetriteta konstruktor
 - kui ülemklassil selline konstruktor puudub, antakse kompileerimisviga
 - kui klassil ülemklassi pole (st ``Object`` on klassi ülemklass),
   siis sellist viga ei teki, kuna ``Object`` klassis on parameetriteta konstruktor olemas.

- Ülemklassi konstruktorit saab ise välja kutsuda järgmiselt: ``super()``
- ``super()`` peab olema esimene rida konstruktoris!

 - kui ``super()`` väljakutset eraldi pole, siis toimub automaatselt sarnane väljakutse ülemklassi konstruktori poole
 - võib kasutada argumente: ``super(name, 12)`` - kutsutakse välja ülemklassi konstruktor vastavat tüüpi parameetritega
@ulend

---

## Konstruktori näide 1

- ``Car`` konstruktor kutsub välja ilma parameetriteta ``Vehicle`` konstruktori
- Kui ``Vehicle`` klassis konstruktorit pole kirjeldatud, siis vaike-konstruktor on olemas

```java
    public class Vehicle {
    }

    public class Car extends Vehicle {
        public Car(int doors) {
            // Vehicle no-args constructor is called before
        }
    }
```

---

## Konstruktori näide 2

- ``Car`` konstruktor kutsub välja ilma parameetriteta ``Vehicle`` konstruktori
- Kuna ``Vehicle`` klass kirjeldab ära konstruktori, siis parameetriteta (*default*) konstruktorit enam ei ole

```java
    public class Vehicle {
        public Vehicle(int doors) { }
    }

    public class Car extends Vehicle {
        public Car(int doors) {
            // Vehicle no-args constructor is called before
        }
    }
```

- @css[red](See kood ei kompileeru!)

---

## Konstruktori näide 3

- ``Car`` konstruktor kutsub seekord välja spetsiaalselt ülemklassi parameetriga konstruktori - enam parameetriteta konstruktorit ei otsita

```java
    public class Vehicle {
        public Vehicle(int doors) { }
    }

    public class Car extends Vehicle {
        public Car(int doors) {
            super(doors);
        }
    }
```

---

## Konstruktori näide 4

- ``Car`` konstruktor kutsub välja ilma parameetriteta ``Vehicle`` konstruktori
- Kuna ``Vehicle`` klass kirjeldab ära parameetriga (``doors``) konstruktori, siis koodi toimimiseks peame kirjeldama lisaks ka parameetriteta konstruktori:

```java
    public class Vehicle {
        public Vehicle() { }
        public Vehicle(int doors) { }
    }

    public class Car extends Vehicle {
        public Car(int doors) {  }
    }
```

---

## Konstruktori näide 5

- Lisame alamklassi ``RaceCar``:

```java
    public class Vehicle {
        public Vehicle() { }
        public Vehicle(int doors) { }
    }

    public class Car extends Vehicle {
        public Car(int doors) {  }
    }

    public class RaceCar extends Car {
    }
```

- @[css](Kood ei kompileeru!)

---

## Konstruktori näide 6

- Lisame ``RaceCar`` klassi ka konstruktori, mis kutsub oma ülemklassi konstruktorit välja
- Kuna ``Car`` klassis parameetriteta konstruktorit pole, kasutame ainsat ``doors`` parameetriga konstruktorit:

```java
    public class Vehicle {
        public Vehicle() { }
        public Vehicle(int doors) { }
    }

    public class Car extends Vehicle {
        public Car(int doors) {  }
    }

    public class RaceCar extends Car {
        public RaceCar(int doors) {
            super(doors);
        }
    }
```

---

## Küsimused?