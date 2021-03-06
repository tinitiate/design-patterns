---
Title: Java Design Patterns Factory Method Pattern
MetaKeywords: Java Design Patterns Factory Method Pattern example code, tutorials
Author: Venkata Bhattaram / tinitiate.com
ContentName: factory-method-pattern
---

# JAVA DESIGN PATTERNS FACTORY METHOD PATTERN
* The **FACTORY METHOD DESIGN PATTERN** is a **CLASS** called as 
  **factory class** It should have a method, that returns Object of an 
  **Abstract Class** or **Interface**
* Also the **Abstract Class** or **Interface** are extended or implemented 
  by many classes.
* The Factory Method Pattern is also known as Virtual Constructor.
* **FACTORY CLASS**
* Creates objects without exposing the instantiation logic to the client 
  (caller class that wants to create an object).
* **FACTORY METHOD**
* Define an interface for creating an object, Define classes to 
  implement the interface, but let the caller class to decide which class
  object to instantiate.
* The Factory empowers the caller class to create the Object it requires.


## JAVA DESIGN PATTERNS FACTORY METHOD PATTERN WITH INTERFACE
* This example demonstrates an interface of **Loans**
* The **objective** of this example is to get interest rates of various 
  Loan types such as Auto Loan, Home Loan and Personal Loan.
* **STEP 1.**
* Create Interface
> Loans.java
```java
package com.tinitiate.designpatterns.factory;

public interface Loans {

    public double getInterestRate();
}
```
>

* **STEP 2.** Create `AutoLoan` Implementation class
> AutoLoan.java
```java
package com.tinitiate.designpatterns.factory;

// Implement the Interface "Loans"
public class AutoLoan implements Loans {

    // Implement getInterestRate method
    @Override
    public double getInterestRate() {
        return 5.5;
    }
}
```

* **STEP 2.** Create `HomeLoan` Implementation class
> HomeLoan.java
```java
package com.tinitiate.designpatterns.factory;

// Implement the Interface "Loans"
public class HomeLoan implements Loans {

    // Implement getInterestRate method
    @Override
    public double getInterestRate() {
        return 7.5;
    }
}
```

* **STEP 3.** Create `PersonalLoan` Implementation class
> PersonalLoan.java
```java
package com.tinitiate.designpatterns.factory;

// Implement the Interface "Loans"
public class PersonalLoan implements Loans {

    // Implement getInterestRate method
    @Override
    public double getInterestRate() {
        return 2.5;
    }
}
```


* **STEP 4.** Create the Factory Class This class will generate Objects of 
  the above implementations `Loans` interface
> LoanInterfaceFactory.java
```
package com.tinitiate.designpatterns.factory;

public class LoanInterfaceFactory {

  //use getPlan method to get object of type Plan   
  public Loans getLoan(String loanType) {

    // Return the Class Object for each of the input provided  
    if(loanType == null) {
      return null;
    }
    if(loanType.equalsIgnoreCase("AUTO-LOAN")) {
      return new AutoLoan();
    }
    else if(loanType.equalsIgnoreCase("HOME-LOAN")) {  
      return new PersonalLoan();
    }   
    else if(loanType.equalsIgnoreCase("PERSONAL-LOAN")) {  
      return new HomeLoan();  
    }
    return null;  
  }
}
```


* **STEP 5.** Create the Class that consumes the Objects
* This is the clas that has the **MAIN** method and running this will 
  demonstrate the **FACTORY PATTERN** using Interface
> FactoryInterfaceTester.java
```java
package com.tinitiate.designpatterns.factory;

// This is the Class that Uses the Factory
public class FactoryInterfaceTester {

    // Class main method
    public static void main(String[] args) {

        // Step 1.
        // Create the "LoansFactory" Object
        LoanInterfaceFactory ObjLIF = new LoanInterfaceFactory();
        
        // Step 2.
        // Get Objects of Different classes that the Factory Provides
        // By using different inputs
        
        // Step 3.
        // Objects of Interface Loans, To get various implementations of 
        // that Interface Object

        // * Get Auto Loan Implementation object
        Loans ObjAutoLoan = ObjLIF.getLoan("AUTO-LOAN");
        System.out.println("Auto Loan Rate: " + ObjAutoLoan.getInterestRate());


        // * Get Auto Loan Implementation object
        Loans ObjHomeLoan = ObjLIF.getLoan("HOME-LOAN");
        System.out.println("Home Loan Rate: " + ObjHomeLoan.getInterestRate());


        // * Get Auto Loan Implementation object
        Loans ObjPersonalLoan = ObjLIF.getLoan("PERSONAL-LOAN");
        System.out.println("Personal Loan Rate: " + ObjPersonalLoan.getInterestRate());
    }
}
```


## JAVA DESIGN PATTERNS FACTORY METHOD PATTERN WITH ABSTRACT CLASS
* This example demonstrates an abstract of **MinimumAge**
* The **objective** of this example is to get minimum age for various 
  activities, Such as Minimum Age for driving, Minimum Age for voting
* **STEP 1.** Create Abstract Class
> MinimumAge.java
```java
package com.tinitiate.designpatterns.factory;

abstract class MinimumAge {

    abstract int getMinimumAge();
}
```
>

* **STEP 2.** Create `MinimumDrivingAge` class, This Class that Extends 
  the Abstract Class
> MinimumDrivingAge.java
```java
package com.tinitiate.designpatterns.factory;

public class MinimumDrivingAge extends MinimumAge {

    public int getMinimumAge() {

        return 16;
   }
}
```


* **STEP 3.** Create `MinimumVotingAge` class, This Class that Extends 
  the Abstract Class
> MinimumVotingAge.java
```java
package com.tinitiate.designpatterns.factory;

public class MinimumVotingAge {

    public int getMinimumAge() {

        return 18;
   }
}
```


* **STEP 4.** Create the Factory Class This class will generate Objects of 
  the above implementations `MinimumAge` Abstract Class
> MinimumAgeFactory.java
```java
package com.tinitiate.designpatterns.factory;

// This is the Class that Uses the Factory
public class MinimumAgeFactory {

  //use getPlan method to get object of type Plan   
  public MinimumAge getMinimumAge(String Activity) {

    // Return the Class Object for each of the input provided  
    if(Activity == null) {
      return null;
    }
    if(Activity.equalsIgnoreCase("DRIVING")) {
      return new MinimumDrivingAge();
    }
    else if(Activity.equalsIgnoreCase("VOTING")) {  
      return new MinimumVotingAge();
    }   

    return null;  
  }
}
```


* **STEP 5.** Create the Class that consumes the Objects
* This is the clas that has the **MAIN** method and running this will 
  demonstrate the **FACTORY PATTERN** using Abstract Class
> FactoryAbstractClassTester.java
```java
package com.tinitiate.designpatterns.factory;

public class FactoryAbstractClassTester {

    // Class main method
    public static void main(String[] args) {

        // Step 1.
        // Create the "MinimumAgeFactory" Object
        MinimumAgeFactory ObjMAF = new MinimumAgeFactory();
        
        // Step 2.
        // Get Objects of Different classes that the Factory Provides
        // By using different inputs
        
        // Step 3.
        // Objects of Abstract Class MinimumAge, To get various implementations 
        // of that Interface Object

        // * Get Auto Loan Implementation object
        MinimumAge ObjDrivingAge = ObjMAF.getMinimumAge("DRIVING");
        System.out.println("Minimum Driving Age: " + ObjDrivingAge.getMinimumAge());


        // * Get Auto Loan Implementation object
        MinimumAge ObjVotingAge = ObjMAF.getMinimumAge("VOTING");
        System.out.println("Minimum voting Age: " + ObjVotingAge.getMinimumAge());
    }
}
```
