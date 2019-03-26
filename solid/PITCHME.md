## Programmeerimise põhikursus (ITI0202)

Loeng

S.O.L.I.D. (OOP printsiibid)

Ago Luberg

---

## SOLID

- **S** The Single-Responsibility Principle
- **O** The Open/Closed Principle
- **L** The Liskov Substitution Principle
- **I** The Interface-Segregation Principle
- **D** The Dependency-Inversion Principle

---

## The Single-Responsibility Principle

- *A class should have only one reason to change.*
- Ühel klassil peaks olema üks konkreetne ülesanne

```java
public class Employee {
    private String name;
    private String title;
    private int age;
    private int salary;
    private SalaryDB salaryDB = new SalaryDB();

    public Employee(String name, String title, int age) {
        this.name = name;
        this.title = title;
        this.age = age;
    }

    public String generateReport(String reportType) {
        if (reportType.equals("CSV")) {
            System.out.println("CSV report");
        }
        if (reportType.equals("JSON")) {
            System.out.println("SJON report");
        }
        return "";
    }

    public int calculateSalary() {
        double coefficient = 1.0;
        if (age > 40) coefficient *= 1.2;
        if (title.equals("Manager")) coefficient *= 1.2;
        if (title.equals("CTO")) coefficient *= 1.3;
        salary = (int) (salaryDB.getBaseSalary() * coefficient);
        return salary;
    }
}
```

---

## The Single-Responsibility Principle

- Jagame raporti koostamise eraldi klassi `EmployeeReportGenerator`
- Jagame palgaarvutuse eraldi klassi `SalaryCalculator`
- `Employee` klass hoiab vaid kliendi andmeid

---

## The Open/Closed Principle

- *Entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.*
- Klassid tuleb struktureerida selliselt, et neid saab uue funktsionaalsuse vajadusel mugavalt laiendada (*open for extensions*). 
- Samas seda osa koodist, mis on juba kirjutatud, ei tohiks kunagi muuta (välja arvatud vigade parandamiseks) (*closed for modifications*).

---

## The Open/Closed Principle

```java
public class Canvas {
    private List<Shape> shapes = new ArrayList<>();

    public void draw() {
        for (Shape shape : shapes) {
            if (shape.getClass().equals(Rectangle.class)) {
                // draw rectangle here using x, y, width, height
            } else if (shape.getClass().equals(Circle.class)) {
                // draw circle here using x, y, radius
            }
        }
    }
}
```

---

## The Open/Closed Principle

- Uue kujundi lisamisel peame `Canvas.draw()` meetodit muutma
- Lisame liidesesse `Shape` meetodi `draw()`, mida iga liidest implementeeriv klass peab realiseerima
- `Canvas` tuleb selle võrra lühem - edaspidi ei pea muid klasse muutma, ainult lisatav kujund tuleb realiseerida

---

## The Open/Closed Principle

```java
public class Canvas {
    private List<Shape> shapes = new ArrayList<>();

    public void draw() {
        for (Shape shape : shapes) {
            shape.draw();
        }
    }
}
```

---

## The Liskov Substitution Principle

- *Child classes should never break the parent class type definitions.*
- Alamklassid tuleb kirjeldada nii, et objekti kasutaja jaoks ei ole vahet, kui kasutusse antakse alamklassi tüüpi objekt.
- Kui alamklass teeb midagi sellist, mida ülemklassist ei eeldaks, siis see on selle printsiibi rikkumine.

---

## The Liskov Substitution Principle

```java
public abstract class TransportationDevice {
    private String name;
    private int speed;
    private Engine engine;
    // getters/setters

    public abstract void startEngine();

}

public class Car extends TransportationDevice {
    @Override
    public void startEngine() {
        // start car's engine
    }
}

public class Bicycle extends TransportationDevice {
    // Engine setter/setter <- also a problem

    @Override
    public void startEngine() {
        // what to do here? PROBLEM
    }
}
```

---

## The Liskov Substitution Principle

- Tekivad tühjad meetodid või olukorrad, kus meetodit ei saa üldse implementeerida
- Lahendus on luua parem hierarhia
- Jagame sõidukid mootoriga ja ilma mootorita sõidukiteks

---

## The Liskov Substitution Principle

```java
public abstract class TransportationDevice {
    private String name;
    private int speed;
    // getters/setters
}

public abstract class DeviceWithEngine extends TransportationDevice {
    private Engine engine;
    // getter/setter

    public abstract void startEngine();
}

public class Car extends DeviceWithEngine {
    @Override
    public void startEngine() {
        // start car engine here
    }
}

public abstract class DeviceWithoutEngine extends TransportationDevice {
    public abstract void startMoving();
}

public class Bicycle extends DeviceWithoutEngine {
    @Override
    public void startMoving() {
        // bicycle starts moving, no engine here
    }
}
```

---

## The Interface-Segregation Principle

- *No client should be forced to depend on methods it does not use.*
- Liidese kasutaja ei pea sõltuma meetoditest, mida otseselt vaja ei lähe. 
- Liidesed, kus on palju meetodeid, jagatakse väiksemateks.

---

### The Interface-Segregation Principle

```java
public interface Shape {
    double area();
    double volume();
}

public class Circle implements Shape {
    private double radius;

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }

    @Override
    public double volume() {
        return 0;  // problem here
    }
}
```

---

### The Interface-Segregation Principle

- Jagame liidese kaheks: kahemõõtmelised kujundid, kolmemõõtmelised kujundid

```java
public interface Shape {
    double area();
}

public interface SolidShape {
    double volume();
}

public class Circle implements Shape {
    private double radius;
    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

public class Cube implements Shape, SolidShape {
    private double side;
    public Cube(double side) {
        this.side = side;
    }

    @Override
    public double area() {
        return 6 * side * side;
    }

    @Override
    public double volume() {
        return side * side * side;
    }
}
```

--- 

## The Dependency-Inversion Principle

- *High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend upon details. Details should depend upon abstractions.*
- Tarkvarakomponendid peaksid sõltuma abstraktsioonidest, mitte konkreetsetest klassidest.
- Komponentide implementatsiooni peab olema võimalik vahetada

--- 

### The Dependency-Inversion Principle

```java
public class BackendDeveloper {
    public void writeJava() {
        // do magic here
    }
}

public class FrontendDeveloper {
    public void writeJavascript() {
        // do javascript magic here
    }
}

public class Project {
    private BackendDeveloper backendDeveloper = new BackendDeveloper();
    private FrontendDeveloper frontendDeveloper = new FrontendDeveloper();

    public void implement() {
        backendDeveloper.writeJava();
        frontendDeveloper.writeJavascript();
        // we need another java developer..
    }
}
```

---

### The Dependency-Inversion Principle

- Loome üldisema (abstraktse) andmetüübi: arendaja
- Annab meile võimaluse kasutada arendajate listi

```java
public interface Developer {
    void develop();
}

public class JavaDeveloper implements Developer {
    @Override
    public void develop() {
        // write java
    }
}

public class FrontendDeveloper implements Developer {
    @Override
    public void develop() {
        // write javascript here
    }
}

public class Project {
    List<Developer> developers = new ArrayList<>();

    public void addDeveloper(Developer developer) {
        developers.add(developer);
    }

    public void implement() {
        developers.forEach(Developer::develop);
    }
}
```