---
Title: Java Design Patterns Singleton Pattern
MetaKeywords: Java Design Patterns Singleton Pattern example code, tutorials
Author: Venkata Bhattaram | github.com/tinitiate
ContentName: singleton-pattern
---

# Java Design Patterns Singleton Pattern
* Singleton design pattern is intended to create only **ONE INSTANCE OF A CLASS**
* This is useful in situations where the requirement demands to create 
  only a SINGLE POINT of access of a resource or class.
* Some practical use cases of singleton pattern are creating a Global Logger,
  a caching mechanism, reading configuration and settings data.

## Demonstration of Singleton Cache
> ClassicSingletonCache.java
```java
package com.tinitiate.designpatterns.singleton;

import java.util.LinkedList;
import java.util.List;

public class ClassicSingletonCache {

    // Cache resource
    private List<String> TinitiateCache = new LinkedList<String>();

    // Getter Method for TinitiateCache
    public List<String> getTinitiateCache() {
        return TinitiateCache;
    }

    // Setter Method for TinitiateCache
    public void setTinitiateCache(String tinitiateCacheData) {
        
        TinitiateCache.add(tinitiateCacheData);
    }

    // SINGLETON CREATION MEMBERS
    // ==========================
    
    // A Null Static Object of type "ClassicSingletonCache" 
    private static ClassicSingletonCache instance = null;

    // Private Constructor Exists only deny instantiation.
    private ClassicSingletonCache() {  }

    // Standard Name to get SingleTon Instance
    public static ClassicSingletonCache getInstance() {

       if(instance == null) {
          instance = new ClassicSingletonCache();
       }

       return instance;
    }

 }
```

## SingleTon Caller
* This class demonstrates the SingleTon being called,
* No matter how many instances are created all Objects share the same values.
> ClassicSingleonCacheCaller.java
```java
package com.tinitiate.designpatterns.singleton;

public class ClassicSingleonCacheCaller {
    
    public static void main(String[] args) {

        // Create an Object of ClassicSingletonCache and add values
        ClassicSingletonCache Object1 = ClassicSingletonCache.getInstance();
        Object1.setTinitiateCache("Data From Object1");
        
        // Create another Object of ClassicSingletonCache and add values
        ClassicSingletonCache Object2 = ClassicSingletonCache.getInstance();
        Object2.setTinitiateCache("Data From Object2");
        
        // Print values of Object2,
        // Here we see Data from both the objects proving the SingleTon create 
        // ONLY A SINGLE INSTANCE
        for (String s : Object2.getTinitiateCache()) {
            System.out.println(s);
        }
    }
}
```
