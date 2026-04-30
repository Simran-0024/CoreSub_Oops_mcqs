151. What will be the output of the following Java 8 code resolving the "Diamond Problem"?

```
interface A { 
    default void show() { System.out.print("A"); } 
}
interface B { 
    default void show() { System.out.print("B"); } 
}
class C implements A, B {
    public void show() { 
        A.super.show(); 
    }
    public static void main(String[] args) { 
        new C().show(); 
    }
}
```

a) A
b) B
c) AB
d) Compilation Error

Answer: a
Explanation: When a class implements multiple interfaces with the same default method, it must override the method to resolve the ambiguity. Using InterfaceName.super.methodName() allows the class to explicitly call a specific interface's implementation.

---

152. What will be the output of the following try-with-resources snippet?

```
class Resource implements AutoCloseable {
    public void close() { System.out.print("Close "); }
}
public class Main {
    public static void main(String[] args) {
        try (Resource r = new Resource()) {
            System.out.print("Try ");
            throw new Exception();
        } catch (Exception e) {
            System.out.print("Catch ");
        }
    }
}
```

a) Try Catch Close
b) Try Catch
c) Try Close Catch
d) Compilation Error

Answer: c
Explanation: In a try-with-resources block, the resources are closed automatically before the catch or finally blocks are executed.

---

153. Evaluate the output of the following String manipulation:

```
public class StringTest {
    public static void main(String[] args) {
        String s1 = new String("Java");
        String s2 = s1.intern();
        String s3 = "Java";
        System.out.print((s1 == s2) + " " + (s2 == s3));
    }
}
```

a) false false
b) true true
c) false true
d) true false

Answer: c
Explanation: s1 is created in the heap. s1.intern() returns the string from the String Pool, so s2 points to the pool. s3 is a literal, so it also points to the same object in the pool as s2. Thus, s1 == s2 is false, and s2 == s3 is true.

---

154. What is the output of the following Collection snippet?

```
public class MapTest {
    public static void main(String[] args) {
        Map<Integer, String> map = new IdentityHashMap<>();
        Integer a = new Integer(10);
        Integer b = new Integer(10);
        map.put(a, "One");
        map.put(b, "Two");
        System.out.print(map.size());
    }
}
```

a) 1
b) 2
c) 0
d) RuntimeException

Answer: b
Explanation: Unlike HashMap which uses .equals() to compare keys, IdentityHashMap uses reference equality (==). Since a and b are created using new Integer(), they are distinct objects in memory, resulting in two separate entries.

---

155. Which overloaded method is invoked by the compiler?

```
class Test {
    void go(long n) { System.out.print("Long "); }
    void go(Integer n) { System.out.print("Integer "); }
    void go(int... n) { System.out.print("Varargs "); }
    
    public static void main(String[] args) {
        int i = 5;
        new Test().go(i);
    }
}
```

a) Long
b) Integer
c) Varargs
d) Compilation Error

Answer: a
Explanation: In Java method overloading resolution, widening (int to long) beats boxing (int to Integer), and boxing beats varargs.

---

156. What happens when compiling the following inheritance snippet?

```
class Parent {
    static void print() { System.out.print("Parent"); }
}
class Child extends Parent {
    void print() { System.out.print("Child"); }
}
```

a) Compiles and Child hides the Parent method
b) Compilation Error
c) Compiles and Child overrides the Parent method
d) RuntimeException

Answer: b
Explanation: An instance method in a subclass cannot override a static method in a superclass. Attempting to do so results in a compilation error. (Similarly, a static method cannot hide an instance method).

---

157. What is the output of the following Stream operation?

```
public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 3);
        list.stream().peek(System.out::print);
    }
}
```

a) 123
b) Compilation Error
c) 1 2 3
d) Nothing is printed

Answer: d
Explanation: Streams in Java are evaluated lazily. Because there is no terminal operation (like .collect() or .forEach()) at the end of the pipeline, the intermediate operation (peek) is never executed.

---

158. What will be returned by the following method?

```
int testMethod() {
    try { 
        return 1; 
    } catch (Exception e) { 
        return 2; 
    } finally { 
        return 3; 
    }
}
```

a) 1
b) 2
c) 3
d) Compilation Error due to unreachable code

Answer: c
Explanation: If a finally block contains a return statement, it will override any return statement executed in the try or catch blocks.

---

159. What happens if a lambda expression accesses a local variable that is modified later?

```
public class Main {
    public static void main(String[] args) {
        int x = 10;
        Runnable r = () -> System.out.print(x);
        x = 20;
        r.run();
    }
}
```

a) 10
b) 20
c) Compilation Error
d) RuntimeException

Answer: c
Explanation: Local variables referenced from a lambda expression must be final or "effectively final" (never modified after initialization). Modifying x to 20 breaks this rule, causing a compilation error at the lambda definition.

---

160. What is the output demonstrating pass-by-value in Java?

```
public class Main {
    static void modify(StringBuilder sb) {
        sb.append("World");
        sb = new StringBuilder("Java");
    }
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");
        modify(sb);
        System.out.print(sb);
    }
}
```

a) Hello
b) HelloWorld
c) Java
d) HelloWorldJava

Answer: b
Explanation: Java is strictly pass-by-value. The reference to the object is passed by value. Modifying the state of the object (sb.append) affects the original object. However, reassigning the reference (sb = new...) only changes the local copy of the reference, not the original.

---

161. Identify the output of the following concurrency code:

```
public class Main {
    public static void main(String[] args) {
        Object obj = new Object();
        try {
            obj.wait();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

a) The thread waits indefinitely
b) Compilation Error
c) IllegalMonitorStateException
d) NullPointerException

Answer: c
Explanation: The wait(), notify(), and notifyAll() methods must be called from within a synchronized context (the current thread must own the object's monitor). Calling them outside throws an IllegalMonitorStateException.

---

162. How does the compiler resolve this overloaded method call with null?

```
public class Test {
    void show(String s) { System.out.print("String"); }
    void show(Object o) { System.out.print("Object"); }
    
    public static void main(String[] args) {
        new Test().show(null);
    }
}
```

a) String
b) Object
c) Compilation Error due to ambiguity
d) NullPointerException

Answer: a
Explanation: When passing null, the compiler selects the most specific method applicable. Since String is a subclass of Object, it is more specific, so show(String) is invoked.

---

163. What will happen in the following finally block scenario?

```
public class Main {
    public static void main(String[] args) {
        try {
            System.out.print("Try ");
            System.exit(0);
        } finally {
            System.out.print("Finally ");
        }
    }
}
```

a) Try Finally
b) Try
c) Compilation Error
d) RuntimeException

Answer: b
Explanation: System.exit(0) terminates the Java Virtual Machine immediately. Therefore, the finally block is bypassed and never executed.

---

164. What is the behavior of static methods inside an interface (Java 8+)?

```
interface MyInterface {
    static void display() { System.out.print("Interface"); }
}
class MyClass implements MyInterface {
    public static void main(String[] args) {
        display();
    }
}
```

a) Interface
b) Compilation Error
c) RuntimeException
d) MyClass

Answer: b
Explanation: Static methods in interfaces are NOT inherited by implementing classes. They can only be called using the interface name itself, i.e., MyInterface.display().

---

165. What does the put method return in a HashMap?

```
public class Main {
    public static void main(String[] args) {
        Map<Integer, String> map = new HashMap<>();
        System.out.print(map.put(1, "A") + " ");
        System.out.print(map.put(1, "B"));
    }
}
```

a) null null
b) true true
c) null A
d) A B

Answer: c
Explanation: The put() method returns the previous value associated with the key. If there was no mapping for the key, it returns null.

---

166. What happens if a switch statement evaluates a null string?

```
public class Main {
    public static void main(String[] args) {
        String str = null;
        switch (str) {
            case "null": System.out.print("String null"); break;
            default: System.out.print("Default");
        }
    }
}
```

a) String null
b) Default
c) Compilation Error
d) NullPointerException

Answer: d
Explanation: The switch statement uses the hashCode() and equals() methods under the hood for Strings. Calling these on a null reference results in a NullPointerException before any cases are evaluated.

---

167. What is true about overriding a method with a different return type?

```
class A { }
class B extends A { }

class Parent {
    A get() { return new A(); }
}
class Child extends Parent {
    B get() { return new B(); }
}
```

a) Compilation Error, return types must strictly match
b) It compiles successfully due to covariant return types
c) Compilation Error, overloading occurs instead of overriding
d) RuntimeException

Answer: b
Explanation: Java supports covariant return types. An overriding method in a subclass can return a subtype of the return type declared in the overridden method of the superclass.

---

168. What will be the output regarding the instanceof operator?

```
public class Main {
    public static void main(String[] args) {
        String s = null;
        System.out.print((s instanceof String) + " " + (s instanceof Object));
    }
}
```

a) true true
b) true false
c) false false
d) NullPointerException

Answer: c
Explanation: The instanceof operator always returns false if the object being tested is null, without throwing a NullPointerException.

---

169. Identify the output regarding exception hierarchies:

```
public class Main {
    public static void main(String[] args) {
        try {
            throw new Error();
        } catch (Exception e) {
            System.out.print("Exception ");
        } catch (Throwable t) {
            System.out.print("Throwable ");
        }
    }
}
```

a) Exception
b) Throwable
c) Compilation Error
d) The program crashes

Answer: b
Explanation: Error and Exception are both subclasses of Throwable. Error does not inherit from Exception, so the Exception catch block ignores it, and it is caught by the broader Throwable catch block.

---

170. Which generic declaration correctly implements PECS (Producer Extends, Consumer Super)?
a) List<? extends Number> list = new ArrayList<Integer>(); list.add(10);
b) List<? super Integer> list = new ArrayList<Number>(); list.add(10);
c) List<? extends Integer> list = new ArrayList<Number>();
d) List<? super Number> list = new ArrayList<Integer>();

Answer: b
Explanation: According to PECS, use super when you only need to put values into a collection (Consumer). List<? super Integer> can point to an ArrayList of Number or Object, and it is perfectly safe to add(10) to it. Option A fails because you cannot add() to an extends wildcard.

---

171. What will be the output of this static block initialization?

```
class Parent {
    static { System.out.print("1"); }
}
class Child extends Parent {
    static final int x = 10;
    static { System.out.print("2"); }
}
public class Main {
    public static void main(String[] args) {
        System.out.print(Child.x);
    }
}
```

a) 1210
b) 210
c) 10
d) 110

Answer: c
Explanation: Child.x is a static final primitive variable (a compile-time constant). Accessing it does not trigger class loading or static block execution for either Child or Parent.

---

172. Evaluate the output of Optional behavior:

```
public class Main {
    static String getBackup() {
        System.out.print("Backup");
        return "Guest";
    }
    public static void main(String[] args) {
        String name = "Admin";
        String res = Optional.ofNullable(name).orElse(getBackup());
        System.out.print(res);
    }
}
```

a) Admin
b) BackupAdmin
c) Guest
d) BackupGuest

Answer: b
Explanation: orElse() evaluates its argument eagerly. Even though the Optional contains "Admin" (and won't use the default value), getBackup() is still executed, printing "Backup" before "Admin" is returned and printed. (To prevent eager evaluation, orElseGet() with a supplier should be used).

---

173. What is the output of the array type mismatch?

```
public class Main {
    public static void main(String[] args) {
        Object[] arr = new String[2];
        arr[0] = "Java";
        arr[1] = 10; 
        System.out.print(arr[0]);
    }
}
```

a) Java
b) Compilation Error
c) ArrayStoreException
d) ClassCastException

Answer: c
Explanation: Although an array of String can be assigned to an Object[] reference (array covariance), the runtime type of the array is still String[]. Attempting to put an Integer (10) into it throws an ArrayStoreException at runtime.

---

174. What is true about constructor definitions for Enums?

```
enum Status {
    SUCCESS, FAILED;
    public Status() { }
}
```

a) Compiles successfully
b) Compilation Error
c) RuntimeException
d) SUCCESS will be printed twice

Answer: b
Explanation: Enum constructors are always implicitly private. You cannot explicitly define an enum constructor with a public or protected access modifier, doing so results in a compilation error.

---

175. What is the output of the following serialization code concept?

```
class User implements Serializable {
    transient String password = "123";
    static String role = "Admin";
}
// Assume object is serialized then deserialized into newUser
```

What will be the values of newUser.password and newUser.role after deserialization?
a) "123" and "Admin"
b) null and null
c) null and "Admin"
d) "123" and null

Answer: c
Explanation: transient fields are not serialized, so upon deserialization, they get their default value (null for objects). static fields belong to the class, not the object. They are not serialized with the object, but when the object is deserialized in the JVM, it accesses the current static value present in the loaded class ("Admin").

176. What will be the output of the following exception handling snippet?

```
public class Main {
    @SuppressWarnings("finally")
    public static int compute() {
        try {
            throw new RuntimeException("Try Failed");
        } finally {
            return 10;
        }
    }
    public static void main(String[] args) {
        System.out.print(compute());
    }
}
```

a) RuntimeException is thrown
b) 10
c) Compilation Error
d) 0

Answer: b
Explanation: If a finally block contains a return statement, it abruptly terminates the method. Any exception thrown in the try or catch block is completely suppressed (swallowed) and the value from the finally block is returned.

---

177. Evaluate the following String pooling scenario:

```
public class StringTest {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = "World";
        String s3 = "HelloWorld";
        String s4 = s1 + s2;
        System.out.print(s3 == s4);
    }
}
```

a) true
b) false
c) Compilation Error
d) RuntimeException

Answer: b
Explanation: String concatenation involving variables (s1 + s2) happens at runtime and creates a new String object on the heap. s3 points to the String Pool literal. Therefore, their memory addresses are different.

---

178. What happens when compiling this Java 8+ interface snippet?

```
interface DefaultTest {
    default String toString() {
        return "DefaultTest Interface";
    }
}
```

a) It compiles and can be used by implementing classes.
b) Compilation Error
c) RuntimeException
d) It compiles but cannot be executed.

Answer: b
Explanation: Compilation Error. An interface cannot provide a default implementation for any of the methods belonging to java.lang.Object (like toString, equals, hashCode). This is by design to prevent ambiguity in multiple inheritance.

---

179. What is the output of the following Collections snippet?

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Set<Integer> set = new TreeSet<>();
        set.add(null);
        System.out.print("Added");
    }
}
```

a) Added
b) Compilation Error
c) NullPointerException
d) IllegalArgumentException

Answer: c
Explanation: TreeSet relies on comparing elements to sort them. Because null cannot be compared to other elements (it lacks a compareTo method), attempting to add null to a TreeSet immediately throws a NullPointerException.

---

180. What is the output of this Generics code?

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        List<String> list1 = new ArrayList<>();
        List<Integer> list2 = new ArrayList<>();
        System.out.print(list1.getClass() == list2.getClass());
    }
}
```

a) true
b) false
c) Compilation Error
d) ClassCastException

Answer: a
Explanation: Due to Type Erasure, generic type parameters (<String> and <Integer>) are removed at runtime. Both list1 and list2 are simply instances of java.util.ArrayList.class.

---

181. Evaluate the behavior of the following static block:

```
public class Main {
    static {
        int x = 1 / 0;
    }
    public static void main(String[] args) {
        System.out.print("Hello");
    }
}
```

a) Hello
b) ArithmeticException
c) ExceptionInInitializerError
d) Compilation Error

Answer: c
Explanation: If an unchecked exception (like ArithmeticException here) is thrown inside a static initialization block, the JVM wraps it in an ExceptionInInitializerError and class loading fails. The main method is never reached.

---

182. What is the output of this overloading scenario involving varargs?

```
public class Main {
    void show(int... a) { System.out.print("Varargs "); }
    void show(int[] a) { System.out.print("Array "); }
    
    public static void main(String[] args) {
        new Main().show(1, 2, 3);
    }
}
```

a) Varargs
b) Array
c) Compilation Error
d) Both methods are executed

Answer: c
Explanation: Compilation error due to duplicate methods. In Java, varargs (int... a) and an array (int[] a) are treated as having the exact same method signature by the compiler. You cannot overload methods this way.

---

183. Identify the output of this code with a labeled break:

```
public class Main {
    public static void main(String[] args) {
        http://www.google.com
        System.out.println("Success");
    }
}
```

a) Success
b) Compilation Error (Invalid Syntax)
c) RuntimeException (Unknown Protocol)
d) NetworkException

Answer: a
Explanation: This perfectly valid Java code! http: is parsed as a label identifier. //www.google.com is parsed as a standard single-line comment. The code prints "Success".

---

184. What happens in this inheritance and exception handling code?

```
import java.io.IOException;
class Parent {
    Parent() throws IOException { }
}
class Child extends Parent {
    Child() { }
}
```

a) Compiles successfully
b) Compilation Error
c) IOException at runtime
d) ClassNotFoundException

Answer: b
Explanation: The child class constructor implicitly calls super(). Since the parent constructor throws a checked exception (IOException), the child constructor must also declare to throw IOException (or a broader exception like Exception) to handle it.

---

185. What will the Map size be?

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Map<String, String> map = new HashMap<>();
        map.put("A", "One");
        map.put(new String("A"), "Two");
        System.out.print(map.size() + " " + map.get("A"));
    }
}
```

a) 2 One
b) 2 Two
c) 1 One
d) 1 Two

Answer: d
Explanation: HashMap uses the equals() and hashCode() methods of the keys to determine uniqueness. Since "A".equals(new String("A")) is true, the second put operation simply overwrites the value of the existing key.

---

186. Evaluate the wrapper class behavior:

```
public class Main {
    static void change(Integer x) {
        x = 20;
    }
    public static void main(String[] args) {
        Integer y = 10;
        change(y);
        System.out.print(y);
    }
}
```

a) 20
b) 10
c) Compilation Error
d) NullPointerException

Answer: b
Explanation: Wrapper classes (like Integer, String) are strictly immutable. When x = 20 executes, a new Integer object is created and assigned to the local reference x. The original reference y remains unchanged and still points to 10.

---

187. Identify the output regarding variable hiding vs overriding:

```
class A { static int i = 1; }
class B extends A { static int i = 2; }

public class Main {
    public static void main(String[] args) {
        A obj = new B();
        System.out.print(obj.i);
    }
}
```

a) 1
b) 2
c) Compilation Error
d) 0

Answer: a
Explanation: Variables do not exhibit polymorphism in Java. Variable hiding relies entirely on the reference type (which is A), not the runtime object instance type.

---

188. What is the output of the following Java 8 Stream snippet?

```
import java.util.stream.Stream;
public class Main {
    public static void main(String[] args) {
        boolean match = Stream.empty().allMatch(e -> false);
        System.out.print(match);
    }
}
```

a) false
b) true
c) NullPointerException
d) IllegalArgumentException

Answer: b
Explanation: In logic and mathematics, evaluating "all" on an empty set results in a concept known as vacuous truth. The allMatch method on an empty stream always evaluates to true, regardless of the predicate.

---

189. What happens when calling methods on abstract classes?

```
abstract class AbstractTest {
    AbstractTest() {
        System.out.print("Abstract ");
    }
}
class Concrete extends AbstractTest {
    Concrete() {
        System.out.print("Concrete");
    }
}
public class Main {
    public static void main(String[] args) {
        new Concrete();
    }
}
```

a) Concrete
b) Compilation Error (Abstract classes can't have constructors)
c) Abstract Concrete
d) RuntimeException

Answer: c
Explanation: Even though abstract classes cannot be directly instantiated via new, they absolutely can have constructors. These constructors are called automatically via super() when a concrete subclass is instantiated.

---

190. What is the output of this collection removal trick?

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3));
        list.remove(new Integer(2));
        System.out.print(list);
    }
}
```

a) [1, 2, 3]
b) [1, 3]
c) [1, 2]
d) IndexOutOfBoundsException

Answer: b
Explanation: List has two overloaded remove methods: remove(int index) and remove(Object o). Passing new Integer(2) explicitly calls the remove(Object o) method, removing the value 2, not the element at index 2.

---

191. Identify the output related to Unboxing edge cases:

```
public class Main {
    public static void main(String[] args) {
        Integer x = null;
        switch (x) {
            case 1: System.out.print("One"); break;
            default: System.out.print("Default");
        }
    }
}
```

a) Default
b) Compilation Error
c) One
d) NullPointerException

Answer: d
Explanation: When passing a wrapper class (Integer) to a switch statement, Java implicitly unboxes it by calling x.intValue(). Since x is null, calling intValue() throws a NullPointerException.

---

192. What will be the output of the following math operation?

```
public class Main {
    public static void main(String[] args) {
        System.out.print(Math.abs(Integer.MIN_VALUE));
    }
}
```

a) 2147483648
b) 2147483647
c) -2147483648
d) Compilation Error

Answer: c
Explanation: The range of an int is -2,147,483,648 to 2,147,483,647. Because of Two's Complement representation, the absolute value of Integer.MIN_VALUE cannot be represented as a positive int. It overflows and remains -2147483648.

---

193. What is the output demonstrating array initialization behaviors?

```
public class Main {
    public static void main(String[] args) {
        String[] arr = new String[5];
        System.out.print(arr[0].length());
    }
}
```

a) 0
b) 5
c) Compilation Error
d) NullPointerException

Answer: d
Explanation: When an array of Objects (like String) is initialized, all slots are populated with null by default. Attempting to call .length() on arr[0] invokes a method on a null reference.

---

194. What is the output of the following nested exception scenario?

```
public class Main {
    public static void main(String[] args) {
        try {
            throw new Error();
        } catch (Exception e) {
            System.out.print("Caught Exception");
        } finally {
            System.out.print("Finally ");
        }
    }
}
```

a) Caught Exception Finally
b) Finally (followed by StackTrace for Error)
c) Compilation Error
d) Caught Exception

Answer: b
Explanation: Error does not inherit from Exception. Therefore, the catch (Exception e) block ignores it. The finally block executes, printing "Finally", and then the unhandled Error crashes the thread.

---

195. Identify the behavior of daemon threads:

```
public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(() -> {
            while (true) { }
        });
        t.setDaemon(true);
        t.start();
        System.out.print("Done");
    }
}
```

a) Program prints "Done" and hangs indefinitely.
b) Program prints "Done" and terminates.
c) IllegalThreadStateException
d) Compilation Error

Answer: b
Explanation: Daemon threads run in the background. The JVM automatically exits when the only threads running are daemon threads. Because the main (user) thread finishes immediately after printing "Done", the JVM terminates, killing the infinite loop in the daemon thread.

---

196. What happens if a lambda attempts to alter an outer variable?

```
import java.util.function.*;
public class Main {
    public static void main(String[] args) {
        int counter = 0;
        Supplier<Integer> increment = () -> ++counter;
        System.out.print(increment.get());
    }
}
```

a) 1
b) 0
c) Compilation Error
d) RuntimeException

Answer: c
Explanation: Local variables referenced inside a lambda expression must be final or "effectively final". Attempting to modify counter inside the lambda (++counter) breaks this rule and causes a compilation error.

---

197. Evaluate the following Double Brace Initialization syntax:

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<String>() {{
            add("A");
            add("B");
        }};
        System.out.print(list.size() + " " + list.getClass().getSimpleName());
    }
}
```

a) 2 ArrayList
b) Compilation Error
c) 2 (empty string because it's an anonymous class)
d) 0 ArrayList

Answer: c
Explanation: Double brace initialization actually creates an anonymous subclass of ArrayList and uses an instance initializer block to add items. Because it is an anonymous class, .getSimpleName() returns an empty string.

---

198. What is the output involving method references?

```
import java.util.function.*;
public class Main {
    public static void main(String[] args) {
        Supplier<String> s = String::new;
        System.out.print(s.get().length());
    }
}
```

a) 0
b) 1
c) Compilation Error
d) NullPointerException

Answer: a
Explanation: String::new refers to the no-args constructor of the String class, which creates an empty string "". The length of an empty string is 0.

---

199. What will be the output regarding loop labels?

```
public class Main {
    public static void main(String[] args) {
        outer: for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (i == 1) continue outer;
                System.out.print(i + "" + j + " ");
            }
        }
    }
}
```

a) 00 01 02 10 11 12 20 21 22
b) 00 01 02 20 21 22
c) 00 11 22
d) Compilation Error

Answer: b
Explanation: The continue outer; statement immediately halts the inner loop when i == 1 and pushes control to the next iteration of the outer loop. Therefore, no prints happen when i is 1.

---

200. Identify the output related to Java variable arguments (varargs):

```
public class Main {
    static void test(Integer... args) { System.out.print("A"); }
    static void test(int... args) { System.out.print("B"); }
    
    public static void main(String[] args) {
        test();
    }
}
```

a) A
b) B
c) Compilation Error
d) RuntimeException

Answer: c
Explanation: A call to test() passes zero arguments. The compiler cannot decide whether to invoke the empty Integer... array or the empty int... array. It throws a compilation error due to an ambiguous method call.
