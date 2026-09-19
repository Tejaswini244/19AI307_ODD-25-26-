# Ex.No:3(A) INHERITANCE AND AGGREGATION

## QUESTION:
A jewelry store tracks gold rates for different types of customers. The base class is Customer with attributes like customerId, name, and purchaseWeight (in grams). There are two types of customers: RegularCustomer and PremiumCustomer. RegularCustomer gets a fixed discount of 2% on the gold rate per gram. PremiumCustomer gets a 5% discount plus a special cashback. The base gold rate per gram is input at runtime. For each customer, calculate the final price they pay:

       
       
      finalPrice = purchaseWeight * (goldRatePerGram - discount)


For PremiumCustomer, additionally show cashback amount (which is 1% of the final price).

## AIM:
To build an inheritance-based Java program that calculates the final price of gold for different types of customers (Regular and Premium), applying respective discounts and showing cashback for premium customers.

## ALGORITHM :
1. Create a base class Customer with attributes: customerId, name, purchaseWeight, and goldRatePerGram.

2. Create method getDiscountRate() in base class returning 0 (default).

3. Create method calculateFinalPrice() that:

        calculates discount per gram → discountAmount = goldRatePerGram * (discountRate/100)

        calculates effective rate → effectiveRate = goldRatePerGram - discountAmount

  returns → finalPrice = purchaseWeight * effectiveRate

4. Override display() in base class to show general customer details.

5. Create child class RegularCustomer:

       Override getDiscountRate() to return 2%.

       Override display() to show customer type as Regular.

6. Create child class PremiumCustomer:

       Override getDiscountRate() to return 5%.

7.  Add calculateCashback() → returns 1% of final price.

8.  Override display() to show final price + cashback.

9.  Call display() to show the complete bill with discounts.





## PROGRAM:
 ```
/*
Program to implement a Inheritance and Aggregation using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;
import java.text.DecimalFormat;

class Customer {
    String customerId, name;
    double purchaseWeight, goldRatePerGram;

    Customer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        this.customerId = customerId;
        this.name = name;
        this.purchaseWeight = purchaseWeight;
        this.goldRatePerGram = goldRatePerGram;
    }

    double getDiscountRate() {
        return 0;
    }

    double calculateFinalPrice() {
        double discountAmount = goldRatePerGram * getDiscountRate() / 100;
        double effectiveRate = goldRatePerGram - discountAmount;
        return purchaseWeight * effectiveRate;
    }

    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: General");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: " + getDiscountRate() + "%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
        
    }
}

class RegularCustomer extends Customer {

    RegularCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    @Override
    double getDiscountRate() {
        return 2.0;
    }

    @Override
    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: Regular");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: 2%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
       
    }
}

class PremiumCustomer extends Customer {

    PremiumCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    @Override
    double getDiscountRate() {
        return 5.0;
    }

    double calculateCashback() {
        return calculateFinalPrice() * 0.01;
    }

    @Override
    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: Premium");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: 5%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
        System.out.println("Cashback: " + df.format(calculateCashback()));
        
    }
}

public class GoldRateSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input 1
        String type1 = sc.next();
        Customer cust1;
        if (type1.equalsIgnoreCase("Regular")) {
            cust1 = new RegularCustomer(sc.next(), sc.next(), sc.nextDouble(), sc.nextDouble());
        } else {
            cust1 = new PremiumCustomer(sc.next(), sc.next(), sc.nextDouble(), sc.nextDouble());
        }

        
        cust1.display();
     

        sc.close();
    }
}
```




## OUTPUT:
<img width="884" height="700" alt="image" src="https://github.com/user-attachments/assets/bc4bc233-2418-404a-88cc-490c1d83bc24" />



## RESULT:
Therefore the program successfully applies different discount rules for regular and premium customers.

------
# Ex.No:3(b) POLYMORPHISM


## QUESTION:
Write a Java program to create a class Vehicle with a method called speedUp(). Create two subclasses Car and Bicycle. Override the speedUp() method in each subclass to increase the vehicle's speed differently.

## AIM:
To create a Java program demonstrating method overriding by defining a base class Vehicle with a speedUp() method and overriding it in subclasses Car and Bicycle to increase speed differently.

## ALGORITHM :
1. Create a parent class Vehicle with an integer variable speed and a method speedUp(int increment) that increases speed normally.

2. Create a subclass Car that overrides speedUp() to increase speed by double the increment.

3. Create a subclass Bicycle that overrides speedUp() to increase speed normally (same as parent but customized message).

4. Read vehicle type and increment value from user.

5. Based on the type, create an object of Car, Bicycle, or Vehicle.

6. Call the speedUp(increment) method to show polymorphic behavior.




## PROGRAM:
 ```
/*
Program to implement a Polymorphism using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

// Parent class
class Vehicle {
    int speed = 0;

    void speedUp(int increment) {
        speed += increment;
        System.out.println("Vehicle speed increased to: " + speed + " km/h");
    }
}


class Car extends Vehicle {
    @Override
    void speedUp(int increment) {
        speed += increment * 2;
        System.out.println("Car speed increased to: " + speed + " km/h");
    }
}


class Bicycle extends Vehicle {
    @Override
    void speedUp(int increment) {
        speed += increment;
        System.out.println("Bicycle speed increased to: " + speed + " km/h");
    }
}


public class TestVehicles {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String type = sc.nextLine().toLowerCase();
        int increment = sc.nextInt();

        Vehicle vehicle;
        if (type.equals("car")) {
            vehicle = new Car();
        } else if (type.equals("bicycle")) {
            vehicle = new Bicycle();
        } else {
            vehicle = new Vehicle();
        }

        vehicle.speedUp(increment);
    }
}
```






## OUTPUT:
<img width="910" height="308" alt="image" src="https://github.com/user-attachments/assets/7931a719-b7f8-43a7-ada3-7c29a6fbf6cd" />



## RESULT:
Therefore the  program successfully demonstrates method overriding by applying different speed increase behaviors for car and bicycle.
-----
# Ex.No:3(C) ABSTRACTION


## QUESTION:
Description:
Create abstract class GameScore with method finalScore().
Subclasses:

ArcadeGame: score = baseScore + (level × 100)

PuzzleGame: score = (attempts ≤ 3) ? 1000 - (attempts × 100) : 500

Input Format:

First line: 1 or 2
Second line: base, level (or attempts)

Output Format:

Final score (int)



## AIM:
To write a Java program using an abstract class GameScore with subclasses ArcadeGame and PuzzleGame, each implementing its own finalScore() method.

## ALGORITHM :
1.	Create an abstract class GameScore with an abstract method finalScore().
2.	Define subclass ArcadeGame where finalScore = baseScore + (level × 100).
3.	Define subclass PuzzleGame where
4.	If attempts ≤ 3, score = 1000 - (attempts × 100)
5.	Else score = 500.
6.	Take user input for game type and relevant values.
7.	Display the final score based on game type.



## PROGRAM:
 ```
/*
Program to implement a Abstraction using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.*;

abstract class GameScore {
    abstract int finalScore();
}

class ArcadeGame extends GameScore {
    int base, level;
    ArcadeGame(int base, int level) {
        this.base = base;
        this.level = level;
    }
    int finalScore() {
        return base + (level * 100);
    }
}

class PuzzleGame extends GameScore {
    int attempts;
    PuzzleGame(int attempts) {
        this.attempts = attempts;
    }
    int finalScore() {
        if (attempts <= 3)
            return 1000 - (attempts * 100);
        else
            return 500;
    }
}

public class prog {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int type = sc.nextInt();
        if (type == 1) {
            int base = sc.nextInt();
            int level = sc.nextInt();
            ArcadeGame game = new ArcadeGame(base, level);
            System.out.println(game.finalScore());
        } else if (type == 2) {
            int attempts = sc.nextInt();
            PuzzleGame game = new PuzzleGame(attempts);
            System.out.println(game.finalScore());
        }
    }
}
```

## OUTPUT:
<img width="605" height="204" alt="image" src="https://github.com/user-attachments/assets/083a97fe-77ab-4994-91f5-74a35a786eb1" />

## RESULT:
The program successfully demonstrates abstraction and inheritance by computing the final score for different game types using subclass-specific logic.
------
# Ex.No:3(D)    INTERFACE 

## QUESTION:
You are programming bots that analyze weather data. Each bot must implement a common interface and give a prediction.


 Bot Types:

SunBot: Predicts "HOT" if temperature > 30, else "MODERATE".

RainBot: Predicts "COLD" if temperature < 20, else "WARM".

Input:

temperature
botType (1 for SunBot, 2 for RainBot)Output:
Prediction as a string.

## AIM:
To implement weather prediction using interfaces with two bots — SunBot and RainBot.

## ALGORITHM :
1.	Create WeatherBot interface with predict() method.
2.	Implement SunBot and RainBot classes with different prediction logic.
3.	Take temperature and botType as input.
4.	Use the chosen bot to call predict().
5.	Display the prediction.

## PROGRAM:
 ```
/*
Program to implement a Interface using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

interface WeatherBot {
    String predict(int temperature);
}

class SunBot implements WeatherBot {
    public String predict(int temperature) {
        if (temperature > 30) {
            return "HOT";
        } else {
            return "MODERATE";
        }
    }
}

class RainBot implements WeatherBot {
    public String predict(int temperature) {
        if (temperature < 20) {
            return "COLD";
        } else {
            return "WARM";
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int temperature = sc.nextInt();
        int botType = sc.nextInt();
        WeatherBot bot;

        if (botType == 1) {
            bot = new SunBot();
        } else {
            bot = new RainBot();
        }

        System.out.println(bot.predict(temperature));
        sc.close();
    }
}
```

## OUTPUT:
<img width="532" height="165" alt="image" src="https://github.com/user-attachments/assets/0fade79d-3a7c-4877-a1c4-85f505bff6b0" />


## RESULT:
The program predicts weather conditions using interface implementation and method overriding.
------
# Ex.No:3(E) INNER CLASS


## QUESTION:
Write a Java program to create an inner class and access it from the outer class.

## AIM:
To demonstrate accessing an inner class from an outer class in Java.

## ALGORITHM :
1.	Create an outer class with a private variable.
2.	Define an inner class inside it with a method to access the outer variable.
3.	In main(), create an object of the outer class.
4.	Use it to create an object of the inner class.
5.	Call the inner class method.

## PROGRAM:
 ```
/*
Program to implement a InnerClass using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

class OuterClass {
    String name;

    OuterClass(String name) {
        this.name = name;
    }

    void display() {
        InnerClass inner = new InnerClass();
        inner.showMessage();
    }

    class InnerClass {
        void showMessage() {
            System.out.println("Hello, " + name + "! This message is from the Inner Class.");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("");
        String input = scanner.next();
        scanner.close();

        OuterClass outer = new OuterClass(input);
        outer.display();
    }
}
```

## OUTPUT:
<img width="1151" height="235" alt="image" src="https://github.com/user-attachments/assets/420f7586-a32e-4a77-88ad-2b8630fa14f6" />

## RESULT:
The program successfully accesses and prints data from the inner class using the outer class.
------
# Ex.No:3(F) WRAPPER CLASS


## QUESTION:
Write a Java program to convert a string to an integer using a wrapper class and perform addition.

## AIM:
To convert string inputs into integers using the wrapper class and perform addition.

## ALGORITHM :
1.	Read two numbers as strings.
2.	Convert them to integers using Integer.parseInt().
3.	Add the two integers.
4.	Display the sum.

## PROGRAM:
 ```
/*
Program to implement a Wrapper Class using Java
Developed by: R.TEJASWINI
Register Number: 212224230218
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String str1 = scanner.next();

        String str2 = scanner.next();

        scanner.close();

        try {
            int num1 = Integer.parseInt(str1);
            int num2 = Integer.parseInt(str2);


            int sum = num1 + num2;
            System.out.println("Sum = " + sum);
        } catch (NumberFormatException e) {
            System.out.println("Invalid input. Please enter a valid number.");
        }
    }
}
```
## OUTPUT:
<img width="670" height="285" alt="image" src="https://github.com/user-attachments/assets/d89aa3ae-ff45-48d0-b3cb-7bd8997c675e" />

## RESULT:
The program successfully converts strings to integers and displays their sum.
