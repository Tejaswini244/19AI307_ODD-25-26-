# Ex.No:4(A) EXCEPTION HANDLING

## QUESTION:
If an Integer object is set to null, and you attempt to call .toString() on it, what happens? How can you prevent your code from throwing an exception in such cases?


## AIM:

To write a Java program to demonstrate NullPointerException when calling .toString() on a null Integer object and to handle the exception using try-catch.

## ALGORITHM :
1.	Start the program.
2.	Import the necessary package 'java.util'
3.	Read an integer value from the user.
4. Assign null if the user enters 0 (or a specific case).
5. Try to call .toString() method on the Integer object.
6. Catch the NullPointerException and display a meaningful message.
7. Display output and end the program.

## PROGRAM:
 ```
/*
Program to implement a Exception Handling using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class NullCheck
{
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
        Integer num = sc.nextInt(); 
        try 
        {
            if (num == 0) 
            {
                num = null;
            }
            System.out.println(num.toString());

        } 
        catch (NullPointerException e) 
        {
            System.out.println("Null Integer");
        }
    }
}
```

## OUTPUT:
<img width="631" height="288" alt="image" src="https://github.com/user-attachments/assets/4d236def-b545-4c78-9554-6e146b0919fb" />


## RESULT:
Thus, the program demonstrates that calling .toString() on a null object causes a NullPointerException, and the exception can be prevented using a try-catch block.
------
# Ex.No:4(B)  IMPLEMENT SOLID PRINCIPLES IN JAVA PROGRAM 

## QUESTION:
In a large office, multiple departments send print jobs to a shared central printer. To manage load and prevent collision, a Print Spooler Manager handles all job submissions.

The IT team insists that there should be only one spooler manager instance in the entire system. Regardless of how many jobs or departments exist, all jobs must pass through this one manager.

Your task is to simulate a singleton print job queue. Each print job submitted increases the queue count.

## AIM:
To write a Java program that demonstrates the Singleton Design Pattern, ensuring only one instance of a Print Spooler Manager exists to handle job queue management.

## ALGORITHM :
1.	Start the program.
2.	Import the necessary package 'java.util'
3.	Create a PrintSpooler class with:

    A private static instance.

    A private constructor.

    A public static getInstance() method to return the single instance.

4. Maintain a counter that represents the number of print jobs.
5. In the main() method, simulate two departments submitting print jobs.
6. Access the same instance of the Print Spooler and increment the job count.
7. Display the print job queue.
8. Stop the program.



## PROGRAM:
 ```
/*
Program to implement a SOLID Principles in Java Program
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.*;

class PrintSpoolerManager {
    private static PrintSpoolerManager instance;
    private int jobCount = 0;

    private PrintSpoolerManager() {}

    public static PrintSpoolerManager getInstance() {
        if (instance == null) {
            instance = new PrintSpoolerManager();
        }
        return instance;
    }

    public int submitJob(String department) {
        jobCount++;
        return jobCount;
    }
}

public class prog {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        sc.nextLine();

        for (int i = 0; i < n; i++) {
            String dept = sc.nextLine();
            PrintSpoolerManager spooler = PrintSpoolerManager.getInstance();
            int total = spooler.submitJob(dept);
            System.out.println(dept + " submitted a print job. Total Jobs in Queue: " + total);
        }
    }
}
```


## OUTPUT:

![java42](https://github.com/ABINAYA-27-76/19AI307_ODD-25-26-/blob/307e4889adff0712306078adcc9b86614a3f814f/19AI307_JAVA(25-26)/Module-04/DAY-2/java42.png)

## RESULT:
Thus, the program to simulate a Singleton Print Spooler Manager using SOLID principles was successfully implemented and executed.
-----
# Ex.No:4(C)  COMPOSITION IN JAVA

## QUESTION:
Create animals from two regions: "Africa" and "Asia". Use Abstract Factory to create families of animals (Herbivore, Carnivore). Print the interaction result.



## AIM:
To write a Java program demonstrating Composition and Abstract Factory Pattern by creating animal families of different regions and displaying interactions between herbivores and carnivores.

## ALGORITHM :
1.	Start the program.
2.	Import the necessary package 'java.util'
3.	Create interfaces Herbivore and Carnivore.
4. Create concrete animal classes (e.g., Wildebeest, Lion, Deer, Tiger) implementing those interfaces.
5. Create an abstract factory class for producing families of animals.
6. Implement region-based factories (AfricaFactory, AsiaFactory).
7. In the main program, instantiate factories and show interactions.
8. Print the result.
9. Stop the program.

## PROGRAM:
 ```
/*
Program to implement a Composition Concepts in Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

interface Herbivore {}
interface Carnivore {
    void eat(Herbivore h);
}

class Wildebeest implements Herbivore {}
class Lion implements Carnivore {
    public void eat(Herbivore h) {
        System.out.println("Lion eats Wildebeest");
    }
}

class Buffalo implements Herbivore {}
class Tiger implements Carnivore {
    public void eat(Herbivore h) {
        System.out.println("Tiger eats Buffalo");
    }
}

interface AnimalFactory {
    Herbivore createHerbivore();
    Carnivore createCarnivore();
}

class AfricaFactory implements AnimalFactory {
    public Herbivore createHerbivore() { return new Wildebeest(); }
    public Carnivore createCarnivore() { return new Lion(); }
}

class AsiaFactory implements AnimalFactory {
    public Herbivore createHerbivore() { return new Buffalo(); }
    public Carnivore createCarnivore() { return new Tiger(); }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String region = sc.nextLine().toLowerCase();
        AnimalFactory factory;

        if (region.equals("africa")) factory = new AfricaFactory();
        else if (region.equals("asia")) factory = new AsiaFactory();
        else {
            System.out.println("Invalid region");
            return;
        }

        Carnivore carn = factory.createCarnivore();
        Herbivore herb = factory.createHerbivore();
        carn.eat(herb);
    }
}
```
## OUTPUT:

![java43](https://github.com/ABINAYA-27-76/19AI307_ODD-25-26-/blob/8b4be1e27b6fb5da0aa68915801ab1e6c9c7174e/19AI307_JAVA(25-26)/Module-04/DAY-3/java43.png)

## RESULT:
Thus, the program using Composition and Abstract Factory Pattern was successfully implemented and executed to create animal interactions for African and Asian regions.
-----
# Ex.No:4(D) DESIGN PATTERN -- ABSTRACT FACTORY

## QUESTION:
You are asked to simulate a simple Shape Drawing Tool using the Factory Design Pattern in Java.

You will implement a Shape interface with concrete classes for different shapes (Circle, Square, Rectangle). Using a ShapeFactory, your program will take shape names from user input and draw them accordingly. If the shape is unknown, print an error message.



## AIM:
To write a Java program that implements the Factory Design Pattern to create and draw shapes dynamically based on user input.

## ALGORITHM :
1.	Start the program.
2.	Import the necessary package 'java.util'
3.	Create a Shape interface containing a draw() method.
4. Create concrete classes Circle, Square, and Rectangle implementing Shape.
5. Create a ShapeFactory class with a method getShape(String shapeType).
6. In the main() method, accept user input for shape type.
7. Call factory method to get the appropriate object.
8. Draw the shape or print error if unknown.
9. Stop the program.


## PROGRAM:
 ```
/*
Program to implement a Abstract Factory Pattern using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

interface Shape {
    void draw();
}

class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing Circle");
    }
}

class Square implements Shape {
    public void draw() {
        System.out.println("Drawing Square");
    }
}

class Rectangle implements Shape {
    public void draw() {
        System.out.println("Drawing Rectangle");
    }
}

class ShapeFactory {
    public Shape getShape(String shapeType) {
        if (shapeType == null) {
            return null;
        }
        switch (shapeType.toLowerCase()) {
            case "circle":
                return new Circle();
            case "square":
                return new Square();
            case "rectangle":
                return new Rectangle();
            default:
                return null;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ShapeFactory factory = new ShapeFactory();
        
        while (true) {
            String input = sc.nextLine().trim();
            if (input.equalsIgnoreCase("exit")) {
                break;
            }
            
            Shape shape = factory.getShape(input);
            if (shape != null) {
                shape.draw();
            } else {
                System.out.println("Invalid shape: " + input);
            }
        }
        sc.close();
    }
}
```
## OUTPUT:

![java44](https://github.com/ABINAYA-27-76/19AI307_ODD-25-26-/blob/b628a27d8352a971924fad5b0adffc7f5f8644ba/19AI307_JAVA(25-26)/Module-04/DAY-4/java44.png)

## RESULT:
Thus, the Java program to simulate Shape Drawing using the Factory Design Pattern was successfully implemented and executed.
-----
# Ex.No:4(E) DESIGN PATTERN  ---- BEHAVIOUR PATTERN

## QUESTION:
Create an Article class where changes to the content are saved as mementos. Let the user view and restore any saved version.

## AIM:
To implement the Memento Design Pattern that allows saving and restoring versions of an Article object.

## ALGORITHM :
1.	Create ArticleMemento to store article content (state).
2.	Create Article (Originator) that can write, save, and restore content.
3.	Create VersionHistory (Caretaker) to store multiple mementos.
4.	Allow the user to:
5.	Write new content
6.	Save current version
7.	View all saved versions
8.	Restore any version
9.	Display restored version content.

## PROGRAM:
 ```
/*
Program to implement a InnerClass using Java
Developed by: R.TEJASWINI
RegisterNumber: 212224230218
*/
```

## SOURCE CODE:
```

import java.util.*;

class Article {
    private String content;

    public Article(String content) {
        this.content = content;
    }

    public void setContent(String content) {
        this.content = content;
    }

    public String getContent() {
        return content;
    }

    // Save current state to memento
    public ArticleMemento save() {
        return new ArticleMemento(content);
    }

    // Restore state from memento
    public void restore(ArticleMemento memento) {
        this.content = memento.getContent();
    }
}

class ArticleMemento {
    private final String content;

    public ArticleMemento(String content) {
        this.content = content;
    }

    public String getContent() {
        return content;
    }
}

class ArticleHistory {
    private List<ArticleMemento> versions = new ArrayList<>();

    public void saveVersion(Article article) {
        versions.add(article.save());
    }

    public ArticleMemento getVersion(int index) {
        if (index >= 0 && index < versions.size()) {
            return versions.get(index);
        }
        return null;
    }

    public List<ArticleMemento> getAllVersions() {
        return versions;
    }
}

public class ArticleManager {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read number of versions
        int n = Integer.parseInt(sc.nextLine());
        ArticleHistory history = new ArticleHistory();
        Article article = new Article("");

        // Read and save each version
        for (int i = 0; i < n; i++) {
            String content = sc.nextLine();
            article.setContent(content);
            history.saveVersion(article);
        }

        // Read version index to restore (0-based)
        int restoreIndex = Integer.parseInt(sc.nextLine());
        ArticleMemento memento = history.getVersion(restoreIndex);
        if (memento != null) {
            article.restore(memento);
            System.out.println(article.getContent());
        } else {
            System.out.println("Invalid version");
        }

        sc.close();
    }
}

```

## OUTPUT:
<img width="1240" height="593" alt="image" src="https://github.com/user-attachments/assets/1011ef9f-2030-4cf0-af05-89f76ddb4b89" />



## RESULT:
The program successfully demonstrates the Memento Pattern, allowing the user to save, view, and restore different versions of an article.



