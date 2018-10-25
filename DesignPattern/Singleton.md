## Eager initialization
In eager initialization, the instance of Singleton class is created at the time of class loading, this is the easiest method to create a singleton class but it has a drawback that instance is created even though client application might not be using it.
```
class Singleton {
  private static final Singleton uniqueInstance = new Singleton();
  private Singleton() {
  }
  public static Singleton getInstance() {
    return uniqueInstance;
  }
}
```
## Static block initialization
Static block initialization is similar to eager initialization, expect that the instance of class is crated in the static block that provides option for exception handling. <br>
Both eager initialization and static block initialization creates the instance even before it's being used and that is not the best practice to use.
```
class Singleton {
  private static Singleton uniqueInstance;
  private Singleton() {
  }
  static {
    try {
      uniqueInstance = new Singleton();
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
  public static Singleton getInstance() {
    return uniqueInstance;
  }
}
```
## Lazy initialization
Lazy initialization is not thread-safe.
```
class Singleton {
  private static Singleton uniqueInstance;
  private Singleton() {
  }
  public static Singleton getInstance() {
    if (uniqueInstance == null) {
      uniqueInstance = new Singleton();
    }
    return uniqueInstance;
  }
}
```
## Lazy initialization & synchronized method
Thread-safe but it reduces the performance because of cost associated with the synchronized method.
```
class Singleton {
  private static Singleton uniqueInstance;
  private Singleton() {
  }
  public static synchronized Singleton getInstance() {
    if (uniqueInstance == null) {
      uniqueInstance = new Singleton();
    }
    return uniqueInstance;
  }
}
```
## Lazy initialization & double checked locking
```
class Singleton {
  private static Singleton uniqueInstance;
  private Singleton() {
  }
  public static Singleton getInstance() {
    if (uniqueInstance == null) {
      synchronized (Singleton.class) {
        if (uniqueInstance == null) {
          uniqueInstance = new Singleton();
        }
      }
    }
    return uniqueInstance;
  }
}
```
## Inner static class
When the singleton class is loaded, InstanceHolder class is not loaded into memory and only when someone calls the getInstance method, the class get loaded and creates the Singleton class instance. <br>
This is the most widely used approach for Singleton class as it doesn't require synchronization.
```
class Singleton {
  private Singleton() {
  }
  public static Singleton getInstance() {
    return InstanceHolder.uniqueInstance;
  }
  private static class InstanceHolder {
    private static final Singleton uniqueInstance = new Singleton();
  }
}
```
## Using reflection to destroy singleton pattern
Reflection can be used to destroy all the above implementation approaches.
```
class ReflectionSingletonTest {
  public static void main(String[] args) {
    Singleton instanceOne = Singleton.getInstance();
    Singleton instanceTwo = null;
    try {
      Constructor[] constructors = Singleton.class.getDeclaredConstructors();
      for (Constructor constructor : constructors) {
        constructor.setAccessible(true);
        instanceTwo = (Singleton) constructor.newInstance();
        break;
      }
    } catch (Exception e) {
      e.printStackTrace();
    }
    System.out.println(instanceOne.hashCode());
    System.out.println(instatnceTwo.hashCode());
  }
}
```
## Enum
```
enum Singleton {
  uniqueInstance;
}
```
