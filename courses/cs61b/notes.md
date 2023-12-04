# Testing
### Debug
<a href="https://sp21.datastructur.es/materials/guides/debugging-guide.html" target="_blank">Debugging Guide</a><br>
- 断点的Condition使用

### JUnit
When writing JUnit tests, it is good practice to write ‘@Test’ above the function that is testing. This allows for all your test methods to be run non statically.
- Change all test methods to non-static.单例测试要为非静态的，尽管测试并不使用实例变量，而且我可能也不会实例化类。但是，JUnit 的设计者认为测试应该这样写，所以我们就这样做了。

- Annotations(注解)

    - Annotations (like org.junit.Test) don’t do anything on their own. 
    - Runner uses reflections library to iterate through all methods with “Test” annotation. 
    - Pseudocode
    ```
    List<Method> L = getMethodsWithAnnotation(TestSort.class, org.junit Test);
    int numTests = L.size();
    int numPassed = 0;
    for (Method m : L) {
        result r = m.execute();
        if (r.passed == true) { numPassed += 1; }
        if (r.passed == false) { System.out.println(r.message); }
    }
    System.out.println(numPassed + “/” + numTests + “ passed!”);

    ```
- JUnit 测试是短路的--只要方法中的一个断言失败，它就会输出失败信息，然后进入下一个测试。


<https://stackoverflow.com/questions/513832/how-do-i-compare-strings-in-java>

# References, Recursion, and Lists

### The golden rule:
There are 9 types of variables in Java:<br>
- 8 primitive types (byte, short, int, long, float, double, boolean, char).
- The 9th type is references to Objects (an arrow). References may be null.

In box-and-pointer notation, each variable is drawn as a labeled box and values are shown in the box. 
- Addresses are represented by arrows to object instances.

The golden rule:
- b = a copies the bits from a into b.
- Passing parameters copies the bits.



### References

`new`关键字，返回一个内存中的位置

当声明一个任意引用类型的变量

- ①Java allocates exactly a box of size 64 bits, no matter what type of object.<br>
- ②These bits can be either set to:<br>
    - Null (all zeros).<br>
    - The 64 bit “address” of a specific instance of that class (returned by new).<br>

Java 方法中，是值传递（这个变量64bit的值）

我们只需要关注Java变量里（这个64bit）的内容。这可能是我们想要的值（primitive），也可能是引用的地址（references ）

### Instantiation of Arrays
Declaration, instantiation, and assignment.
```
int[] x = new int[]{0, 1, 2, 95, 4};
```
If we were to reassign a to something else, we’d never be able to get the original Object back!



### IntList and Linked Data Structures
```
public class IntList {
    public int first;
    public IntList rest;

    public IntList(int f, IntList r){
        this.first = f;
        this.rest = r;
    }

    public static void main(String[] args) {
        IntList L = new IntList(15, null);
        L = new IntList(10, L);
        L = new IntList(5, L);

        System.out.println(L.size());
        System.out.println(L.iterativeSize());

        System.out.println(L.get(1));
        System.out.println(L.get(2));
        System.out.println(L.get(3));
    }

    /**
     * Return the size of list using recursion
     */
    public int size(){
        if(this.rest == null){
            return 1;
        }
        return 1 + this.rest.size();
    }

    /**
     * Return the size of list using iterative method
     */
    public int iterativeSize(){
        int size = 0;
        IntList p = this;
        while(p != null){
            size ++;
            p = p.rest;
        }
        return size;
    }

    /**
     * Return the ith item of this IntList using recursion
     */
    public int get(int i){
        if(i == 1){
            return this.first;
        }
        return this.rest.get(i - 1);
    }

    /**
     * Return the ith item of this IntList
     */
    public int iterativeGet(int i){
        IntList p = this;
        int t = 0;
        while (t < i-1){
            p = p.rest;
            t++;
        }
        return p.first;
    }
}

```
# Lecture 5: Node Based Lists
## From IntList to SLList

private

reflection反射的影响？？