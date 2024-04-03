# Coding convention

## Table of Contents
- [Coding convention](#coding-convention)
  - [Table of Contents](#table-of-contents)
  - [1. Before we begin](#1-before-we-begin)
      - [What it really is? The reason](#what-it-really-is-the-reason)
    - [1.1 What is coding convention](#11-what-is-coding-convention)
    - [1.2 Why we need coding convention](#12-why-we-need-coding-convention)
  - [2. Coding convention scope](#2-coding-convention-scope)

## 1. Before we begin
In Clean Code Page 3 have written:
> Wrote a killer app. It was very popular, and lots of
professionals bought and used it. But then the
release cycles began to stretch. Bugs were not
repaired from one release to the next. Load times
grew and crashes increased

>  They had rushed the product to
market and had made a huge mess in the code. As they added more and more features, the
code got worse and worse until they simply could not manage it any longer. It was the bad
code that brought the company down

<details>
<summary> Bad code, why did you write it? </summary>

Of course you have been impeded by bad code. So then—why did you write it?

Were you trying to go fast? Were you in a rush? Probably so. Perhaps you felt that 
- You didn’t have time to do a good job; 
- Your boss would be angry with you if you took the time to clean up your code. 
- Perhaps you were just tired of working on this program and wanted it to be over. 
- Or maybe you looked at the backlog of other stuff that you had promised to get done and realized that you needed to slam this module together so you could
move on to the next. 

We’ve all done it.
We’ve all looked at the mess we’ve just made and then have chosen to leave it for
another day

#### What it really is? The reason
Stupid boss? Intolerant customers? Useless marketing types?

The answer is No, it's not their fault. We are deeply compicit in the planning of the project and share great deal of the responsibility for any failures. Esecially if those failures hace to do with bad code.

**<u>It’s your job to defend the code with equal
passion</u>**

Bad code will slow you down.

Question: What is a good code?

Clean code


</details>

### 1.1 What is coding convention
Coding convention is to create a list of rules for our project that everyone in the development team must follow.

### 1.2 Why we need coding convention
Because of all the team members need to quickly get into upgrade the tasks that other people did before, so we need to make the code more readable and a simple way to achive this is clean code.
If everyone in the team have the same way of implement feature, same style of coding, we don't have to worry about who implemented it.

## 2. Coding convention scope
Names are everywhere in software. We name our variables, our functions, our arguments, classes, and packages. We name our source files and the directories that contain them.


<details>
<summary> Use intention-revealing names</summary>
Choosing good names takes time but saves more than it takes. So take care with your names and change them when you find better ones. Everyone who reads your code (including you) will be happier if you do.

```cpp
public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>(); 
    for (int[] x : theList)
        if (x[0] == 4) 
            list1.add(x);
    return list1; 
}
```

1. What kinds of things are in theList?
2. What is the significance of the zeroth subscript of an item in theList?
3. What is the significance of the value 4?
4. How would I use the list being returned?

```cpp
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>(); 
    for (int[] cell : gameBoard)
        if (cell[STATUS_VALUE] == FLAGGED) 
            flaggedCells.add(cell);
    return flaggedCells; 
}
```

More readable
```cpp
public List<Cell> getFlaggedCells() {
    List<Cell> flaggedCells = new ArrayList<Cell>(); 
    for (Cell cell : gameBoard)
        if (cell.isFlagged()) 
            flaggedCells.add(cell);
    return flaggedCells; 
}
```
</details>

<details>
<summary>Avoid Disinformation</summary>

* Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meanings vary from our intended meaning. For example, `hp`, `aix`, and `sco` would be poor variable names because they are the names of Unix plat- forms or variants. Even if you are coding a hypotenuse and `hp` looks like a good abbreviation, it could be disinformative.
<br />
<br />

* Do not refer to a grouping of accounts as an `accountList` unless it’s actually a List. The word list means something specific to programmers. If the container holding the accounts is not actually a List, it may lead to false conclusions. So `accountGroup` or `bunchOfAccounts` or just plain `accounts` would be better.

<br />
<br />

* Beware of using names which vary in small ways. 
<br />

    ```
    XYZControllerForEfficientHandlingOfStrings
    vs
    XYZControllerForEfficientStorageOfStrings
    ```
    The words have frightfully similar shapes.
    Spelling similar concepts similarly is information. Using inconsistent spellings is dis- information.

* Avoid using variable name with lower-case L and uppercase O
    ```cpp
    int a = l; 
    if ( O == l )
        a = O1; 
    else
        l = 01;
    ```

</details>

<details>
<summary>Make Meaningful Distinctions</summary>

* Programmers create problems for themselves when they write code solely to satisfy a compiler or interpreter.
    
    For example, because you can’t use the same name to refer to two different things in the same scope, you might be tempted to change one name in an arbitrary way. Sometimes this is done by misspelling one, leading to the surprising situation where correcting spelling errors leads to an inability to compile
    
    It is not sufficient to add number series or noise words, even though the compiler is satisfied. If names must be different, then they should also mean something different.
    
    Number-series naming (a1, a2, .. aN) is the opposite of intentional naming. Such names are not disinformative—they are noninformative; they provide no clue to the author’s intention
    
    ```cpp
    public static void copyChars(char a1[], char a2[]) {
        for (int i = 0; i < a1.length; i++) {
            a2[i] = a1[i]; 
        }
    }
    ```
    This function reads much better when source and destination are used for the argument
    names.


* If you have another called ProductInfo or ProductData, you have made the names dif- ferent without making them mean anything different. Info and Data are indistinct noise words like a, an, and the.
</details>

<details>
<summary>Use Prnounceable Names</summary>

* Humans are good at words. A significant part of our brains is dedicated to the concept of words. And words are, by definition, pronounceable. It would be a shame not to take advantage of that huge portion of our brains that has evolved to deal with spoken language. So make your names pronounceable.
  

    If you can’t pronounce it, you can’t discuss it without sounding like an idiot. “Well, over here on the bee cee arr three cee enn tee we have a pee ess zee kyew int, see?” This matters because programming is a social activity.

    ```cpp
    class DtaRcrd102 {
        private Date genymdhms;
        private Date modymdhms;
        private final String pszqint = "102"; 
        /* ... */
    };

    // vs

    class Customer {
        private Date generationTimestamp; 
        private Date modificationTimestamp;
        private final String recordId = "102"; 
        /* ... */
    }
    ```


</details>


<details>
<summary>Use Searchable Name</summary>


* Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.
    ```cpp
    for (int j=0; j<34; j++) { 
        s += (t[j]*4)/5;
    }

    //vs

    int realDaysPerIdealDay = 4;
    const int WORK_DAYS_PER_WEEK = 5;
    int sum = 0;
    for (int j=0; j < NUMBER_OF_TASKS; j++) {
        int realTaskDays = taskEstimate[j] * realDaysPerIdealDay; 
        int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
        sum += realTaskWeeks;
    }
    ```
</details>

<details>
<summary>Interfaces and Implementations</summary>

* `IShapeFactory` and `ShapeFactory`? I prefer to leave interfaces unadorned. The preceding I, so common in today’s legacy wads, is a distraction at best and too much information at worst. I don’t want my users knowing that I’m handing them an interface. I just want them to know that it’s a `ShapeFactory`. So if I must encode either the interface or the implementation, I choose the implementation. Calling it `ShapeFactoryImp`, or even the hideous `CShapeFactory`, is pref- erable to encoding the interface.
</details>

<details>
<summary>Avoid Mental Mapping</summary>

* In general programmers are pretty smart people. Smart people sometimes like to show off their smarts by demonstrating their mental juggling abilities. After all, if you can reliably remember that `r` is the lower-cased version of the url with the host and scheme removed, then you must clearly be very smart.

    One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.


</details>

<details>
<summary>Class Names</summary>

* Classes and objects should have ***noun*** or ***noun phrase*** names like `Customer`, `WikiPage`, `Account`, and `AddressParser`. Avoid words like `Manager`, `Processor`, `Data`, or `Info` in the name of a class. A class name **should not** be a **verb**.

    Why?

    ```
    ChatGPT:
    Avoiding words like "Manager," "Processor," "Data," or "Info" in the name of a class is generally advised because it violates the principle of high cohesion and low coupling in object-oriented design.

    High Cohesion: Classes should have a clear and specific purpose. When a class name contains generic terms like "Manager" or "Processor," it often suggests that the class is handling too many responsibilities. It's better to have classes with names that clearly indicate their purpose or domain of responsibility.

    Low Coupling: Classes should be loosely coupled, meaning they should be independent and not overly reliant on each other. Naming a class with terms like "Data" or "Info" can suggest a tight coupling to data handling, which might limit the flexibility and reusability of the class.

    Abstraction and Reusability: Generic terms like "Manager" or "Processor" don't provide much information about what the class actually does. Classes should be named based on the abstraction they represent and what they offer in terms of functionality. This makes the code more readable, maintainable, and reusable.

    Clarity and Understandability: Clear and descriptive class names contribute to the readability and understandability of the codebase. Developers should be able to understand the purpose of a class just by looking at its name. Using vague terms like "Manager" or "Processor" can lead to confusion about the class's responsibilities.

    Instead of using generic terms, consider naming classes based on specific responsibilities or domain concepts. For example, if a class manages employee information, you might name it EmployeeManager. If a class processes data related to sales transactions, you could name it SalesDataProcessor. These names are more descriptive and convey the purpose of the classes more clearly.
    ```

</details>

<details>
<summary>Method Names</summary>

* Methods should have ***verb*** or ***verb phrase*** names like `postPayment`, `deletePage`, or `save`. Accessors, mutators, and predicates should be named for their value and prefixed with `get`, `set`, and `is` according to the javabean standard.
    ```cpp
    string name = employee.getName(); 
    customer.setName("mike");
    if (paycheck.isPosted())...
    ```

    When constructors are overloaded, use static factory methods with names that describe the arguments. For example,
    ```cpp
    Complex fulcrumPoint = Complex.FromRealNumber(23.0);

    // is generally better than
    Complex fulcrumPoint = new Complex(23.0);
    ```
    Consider enforcing their use by making the corresponding constructors private.

</details>

<details>
<summary>Pick One Word per Concept</summary>

* Pick one word for one abstract concept and stick with it. For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes. How do you remember which method name goes with which class? Sadly, you often have to remember which company, group, or individual wrote the library or class in order to remember which term was used. Otherwise, you spend an awful lot of time browsing through headers and previous code samples.

</details>

