## Programmeerimise põhikursus (ITI0202)

Loeng

Baasklass `Object`

Ago Luberg

----

## Baasklass (``Object``)

@ul
- Baasklass
- Kõik klassid pärinevad sellest klassist
  - seda ei pea erali välja kirjutama (`extends Object`)
- ``Object`` klass defineerib ära päris palju meetodeid, nt:
 - ``String toString()``
 - ``boolean equals(Object o)``
 - ``int hashcode()``
 - ``Object clone()``
 - jne
@ulend

---

## Objekti kasutamine sõnena (``toString()``)

- Objekti sisu presenteerimine sõnena
- Näiteks kui objekti välja printida, kasutatakse seda meetodit:

```java
    System.out.println(student);
```

- Või kutsutakse eraldi välja:

```java
    String myStudent = student.toString();
```

- Vaikimisi implementatsioon:

```java
    return getClass().getName() + '@'
        + Integer.toHexString(hashCode());
```
---

## Objekt sõnena - näide

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

- Vaikimisi toimib nii:

```java
    Student s = new Student("Juurikas", 19);
    System.out.println(s);  // Student@1c53fd30
```

---

## Objekt sõnena - näide 2

```java
    public class Student {
        private String name;
        private int age;
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        @Override
        public String toString() {
            return String.format("%s (%d a)", name, age);
        }
    }
```

- See toimib nii:

```java
    Student s = new Student("Juurikas", 19);
    System.out.println(s);
    // Juurikas (19 a)
```

---

## Objektide võrdlemine

@ul
- Objekte võrreldakse ``equals()`` meetodiga: ``x.equals(y)``
- Iga klass kirjeldab ise ära, millisel juhul objektid võrdsed on
- Vakimisi lahendus ``Object`` klassis tagastab ``true`` kui objektid on samad (viitavad samale objektile) ``x == y``
- Üldiselt aga erineb ``x.equals(y)`` tulemus ``x == y`` omast
- ``equals()`` kirjeldamisel tuleb vastavalt kirjeldada ka ``hashCode()`` meetod
@ulend

---

## hashCode() meetod

@ul
- Tagastab objekti räsikoodi (*hash code*)
- Kasutatakse näiteks ``HashMap`` objekti poolt
- Kui objektid on võrdsed (``x.equals(y)``), peavad nad tagastama sama koodi (``x.hashCode() == y.hashCode()``)

  - kui objektid ei ole võrdsed, ei pea nad tingimata tagastama erinevad koodid
  - kuigi erinevate objektide puhul erineva koodi tagastamine näiteks parandab ``HashMap``'i tööd

- Sama objekt peab läbi programmi töö tagastama alati sama räsikoodi (eeldusel, et andmed, mida ``equals()`` kasutab, ei ole muutunud).
@ulend

---

## ``equals`` ja ``hashCode`` näide

@ul[ul-50](false)
- Kasutasime IntelliJ genereeritud meetodeid
- ``alt + insert -> equals() and hashCode()``
@ulend

```java
    public class Student {
        // ...

        @Override
        public boolean equals(Object o) {
            if (this == o) return true;
            if (o == null || getClass() != o.getClass()) return false;
            Student student = (Student) o;
            return age == student.age &&
                    Objects.equals(name, student.name);
        }

        @Override
        public int hashCode() {
            return Objects.hash(name, age);
        }
    }
```

---

## Küsimused?
