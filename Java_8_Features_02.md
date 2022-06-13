# Java 8 features:

* Lambda Expression
* Functional Interface
* Default method and Static method
* Predefine Functional Interface
    
      * Predicate
      * Function
      * Consumer
      * Supplier
      * etc
* Double Colon Operator(::)
* Method Reference
* Constructor Reference
* Streams
* Date and Time Api
* Optional class
* Nashron Javascript Engin
* etc

#  Lambda Expression:

1. The main objective of lambda expression is to bring functional progarmming in java.  
2. It is an anonymous function, means it dont have any name,it dont have any return type ,and it dont have modifires.

##  write a function which print hello world using both ways:

    //Normal java function 
    
    public void m1()
    {
        System.out.println("Hello world");
    }
    
    // Lambda Function
    
    () -> System.out.println("Hello world");
    
    
## Write a function which take 2 arguments and print sum:

    //Normal java function 
    public void sum(int a,int b)
    {
         System.out.println(a+b);
    }
     // Lambda Function
     // some time compiler uess the varibale type automatically we are not required to write explicitly.
     
    (a,b)->System.out.println(a+b);
    
## Write a function which calculate squr:

    //Normal java function 
    
    public int squareIt(int a)
    {
    
        return a*a;
    }

    // Lambda Function
    // return ststmt should be write in curly brases {}.
    1. (int a) -> {return a*a;}
    2. (int a) -> a*a;
    3. (a) -> a*a;
    4. a -> a*a;
    
    
    // Tell which is valid and which is in valid
    
    n-> return n*n;     => Invalid
    n->{return n*n;};   => Valid
    n->{return n*n};    => Invalid
    n->{n*n;};          => Invalid
    n->n*n;             => Valid
    
    
### Note: 

1. Without curly braces we cannot use return keyword. Compiler will conceder return value automatically.
2. Within curly braces if we want to return some values compulsory we should use return statement.



    
## Note: Now we learn how to write Lambda Expression, But if we want to call Lambda expression we should go for Functional Interface.
