---
Title: Java Design Patterns Builder Method Pattern
MetaKeywords: Java Design Patterns Builder Method Pattern example code, tutorials
Author: Venkata Bhattaram | github.com/tinitiate
ContentName: builder-method-pattern
---

# JAVA DESIGN PATTERNS BUILDER METHOD PATTERN
* The Builder design pattern primarily addresses the following:
 * Class (the same construction process) creates different representations 
   of a complex object.
 * Class creating a complex object is simplified.
* Builder Pattern is the process to create a complex object from underlying 
  simple objects using a step-by-step approach.
* A simple example would be, Consider a Class with Setter and Getter Methods,
  Instead of regular Setters with a Void return Type, imagine a Setter which
  returns the whole Object itself.
* This pattern is useful when object cannot be created in single step 
  such as object de-serialization.
* **Advantages of Builder Pattern**
* It provides clear separation between object construction and representation.
* It provides control over steps of construction process.
* It enables varying object's internal representation.


## JAVA DESIGN PATTERNS BUILDER METHOD PATTERN EXAMPLE
* **STEP 1.**
* Create EmployeeData Class with Setter Methods and Constructor
* Here we have a controlled mechanism in creating an object with specific 
  attributes, user choice of attributes are limited in Object created.
* Only All attributes Constructor and empty Constructor, where Attributes 
  are assigned after object creation.
>EmployeeDataBuilder.java
```java
package com.tinitiate.designpatterns.builder;

public class EmployeeData {

    int EmpID;
    String EmpName;
    double Salary;
    
    // Setter Methods
    public void setEmpID(int empID) {
        EmpID = empID;
    }

    public void setEmpName(String empName) {
        EmpName = empName;
    }

    public void setSalary(double salary) {
        Salary = salary;
    }

    // Constructors
    public EmployeeData () {
        
    }

    // Constructor
    public EmployeeData(int EmpID, String EmpName, double Salary) {
        this.EmpID = EmpID;
        this.EmpName = EmpName;
        this.Salary = Salary;
    }
    
}
```
>
* **STEP 2.**
* Create a **Builder Pattern** Class with **Setter Methods** that return 
  the Current Class Instance as Obect.
* This will enable to create an Object with the desired fields, rather than 
  creating an Object and assigning attributes after Object Creation.
```java
package com.tinitiate.designpatterns.builder;

public class EmployeeDataBuilder {

    int EmpID;
    String EmpName;
    double Salary;
    
    // Setter Methods, Returning the Current Class Object
    public EmployeeDataBuilder setEmpID(int empID) {
        this.EmpID = empID;
        return this;
    }
    
    public EmployeeDataBuilder setEmpName(String empName) {
        this.EmpName = empName;
        return this;
    }

    public EmployeeDataBuilder setSalary(double salary) {
        this.Salary = salary;
        return this;
    }
    
    // Constructor
    public EmployeeDataBuilder() {
        
    }

    public EmployeeDataBuilder(int EmpID, String EmpName, double Salary) {
        this.EmpID = EmpID;
        this.EmpName = EmpName;
        this.Salary = Salary;
    }
}
```
>
* **Step 3.**
* Here we demonstrate a Caller that creates Objects for Classes 
  EmployeeData and EmployeeDataBuilder, which have same attributes.
```java
package com.tinitiate.designpatterns.builder;

public class EmployeeDataTester {

    public static void main(String[] args) {

        // Create Employee Data using NON Builder Class
        // ===========================================
        // 1. Create Employee Data using the Setters
        EmployeeData ED1 = new EmployeeData();
        ED1.setEmpID(1);
        ED1.setEmpName("ABC");
        ED1.setSalary(10000.00);
        
        // 2. Create Employee Data using Constructor
        EmployeeData ED2 = new EmployeeData(2,"XYZ",5000.00);


        // Create Employee Data using Builder Class
        // =========================================
        // 1. Create Employee Data using the Constructor
        EmployeeDataBuilder EDB1 = new EmployeeDataBuilder(2,"XYZ",5000.00);

        // 2. Create Employee Data using The Builder, Add values as needed
        EmployeeDataBuilder EDB2 = new EmployeeDataBuilder();
        EDB2.setEmpID(1).setEmpName("ABC").setSalary(10000.00);
        
        // 3. Create another Object without Salary
        //    This way using the Builder we have the control to
        //    create objects with the elements we want to populate
        EmployeeDataBuilder EDB3 = new EmployeeDataBuilder();
        EDB3.setEmpID(1).setEmpName("ABC");
    }
}
```
