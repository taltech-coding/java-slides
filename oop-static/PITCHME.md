## Programmeerimise põhikursus (ITI0202)

Loeng

Staatilised väljad/meetodid (*Static fields/methods*)

Ago Luberg

---

## Terminoloogia


@ul
- Staatiline muutuja, meetod
 - klassi muutuja, meetod
 - ``public static int getValue()``

- Mitte-staatiline muutuja, meetod
 - instantsi muutuja, meetod
 - objekti muutuja, meetod
 - ``public int getValue()``
@ulend

---

## Staatiline meetod/muutuja

@ul
- Staatilised meetodid/muutujad on seotud klassiga
- Väljakutsumine ``Klassinimi.meetod()``
- Staatiline meetod saab kasutada vaid staatilisi muutujaid
- Kogu programmi kohta ühine "olek"
@ulend

---

## Mittestaatiline meetod/muutuja

@ul
- Seotud objektiga
- Igal objektil on erinev olek (näiteks tudengi nimi)
- Väljakutsumine ``objektiMuutuja.meetod()``
- Saab kasutada mittestaatilisi muutujaid (mis on seotud selle objektiga)
@ulend

---

## Koostoimimine

@ul
- Staatilise meetodi sees **ei saa** kasutada mittestaatilisi muutujaid
- Mittestaatilise meetodi sees **saab** kasutada staatilisi muutujaid/meetodeid
- Loomulikult nähtavus (*visibility*) peab seda lubama
@ulend

---

## Näide

```java
    class Student {
        // DONT USE PUBLIC! just here to simplify the code
        public static String nameStatic;
        public String name;

        public static String getNameStatic() {
            // we cannot access non-static name
            // System.out.println("Non-static name is:" + name);
            return nameStatic;
        }

        public String getName() {
            // we can access nameStatic too
            if ("Klaabu".equals(nameStatic)) { }
            return name;
        }
    }

    // static name is accessible without objects
    Student.nameStatic = "Fanstatic";
    System.out.println("Static name:" + Student.getNameStatic());

    // non-static variable is "created" along with an object
    Student mati = new Student();
    mati.name = "Mati";
    Student kati = new Student();
    kati.name = "Kati";
    System.out.format("mati: %s kati: %s Student: %s\n", mati.getName(),
            kati.getName(), Student.getNameStatic());

    Student.nameStatic = "Ofeeliks";
    System.out.println(kati.nameStatic); // works, not recommended!
```

---

## Staatiline muutuja

- Kasutatakse tavaliselt konstantide jaoks:

```java
    class Earth {
        public static final int RADIUS_KM = 6_371;
        public static final double ORBITAL_SPEED_KM_S = 29.78;
    }
```

- Andmete jaoks, mis on üle terve programmi ühised

 - *Singleton* disainimustri puhul luuakse üks instants klassist ja
   seda hoitakse staatilises muutujas.

- ``out`` muutuja ``System`` klassis on staatiline `System.out.println();`

---

## Staatiline meetod

@ul
- Kasutatakse juhul, kui meetod ei pea kasutama konkreetse objekti andmeid
- *Static factory* meetod - objekti oomine läbi staatilise meetodi
- Näiteks matemaatika valemid (trigonomeetria, ``abs`` jms ``Math`` klassist)
- Tihti staatilise meetodi panemine klassi alla on lihtsalt üks viis koodi struktureerimiseks
  - matemaatikaga seonduv ``Math`` klassis
@ulend

---

## *Static factory* meetod

@ul

- Staatiline meetod, mille sisu on uue objekti loomine
- Annab võimaluse teha täiendavat kontrolli enne objekti loomist
- Konstruktor saab tagastada vaid ühte andmetüüpi objekti
- *Static factory* meetod võimaldab tagastaa lisaks ka ``null`` ning alamklassi tüüpi objekti

 - näiteks ``createVehicle()`` meetod võib tagastada ``Car`` või ``Bus`` vms

 - ``public static BankCard createCard()`` EX04-s
@ulend

---

## Küsimused?