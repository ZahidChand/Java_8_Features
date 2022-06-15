# Functional Interface:

An interface which contains only One Abstract Method is called functional interface like.  

1. Runnable=>   run()
2. Comparable=> compareTo()
3. Comparator=> compare()
4. ActionListener=> actionPerformed()
5. Callable=> call()

Q) In java 8 we can use default method and static method in interface,so can we use it in functional interface also ?  

ans: Restriction is aplicable only for abstract method,but not for default method and static method you can take any numbers of default method and static method in functional interface .

@FunctionalInterface annotation is used to make functional interface, But it is not compulsory.

### Labmda Functoin with Functional Interface:
        
            //Example 1
            
            package com.zahid;

            @FunctionalInterface
            interface inter {
                public void m1();

            }

            /*class Demo implements inter
            {
                @Override
                public void m1() {
                    System.out.println("hello.......");
                }
            }*/

            public class Main {

                public static void main(String[] args) {

                    /*Demo d1=new Demo();
                    d1.m1();

                    inter d2=new Demo();
                    d2.m1();*/

                    // we are replacing above by lambda function

                    inter i1 = () -> System.out.println("Hello world.........");
                    i1.m1();

                }
            }
            // Hello world.........        
            
            
            
            //Example 2
           
            package com.zahid;

            @FunctionalInterface
            interface inter {
                public void m1(int a, int b);

            }

            public class Main {

                public static void main(String[] args) {
                    inter i1 = (a, b) -> System.out.println("The sum :" + (a + b));
                    i1.m1(10, 20);
                    i1.m1(100,200);
                    i1.m1(1000,2000);

                }
            }
            //The sum :30
            //The sum :300
            //The sum :3000
            
## Runnable Example with lambda expression:

                import java.util.*;

                /*class MyThread implements Runnable
                {
                    @Override
                    public void run() {
                        for(int i=0;i<10;i++)
                        {
                            System.out.println("Child"+i);
                        }
                    }
                }*/
                public class Main {
                    public static void main(String[] args) {
                //        MyThread m=new MyThread();
                //        Thread t1=new Thread(m);
                //        t1.start();

                        Runnable r=()->{
                            for(int i=0;i<10;i++)
                            {
                                System.out.println("Child"+i);
                            }
                        };
                        Thread t1=new Thread(r);
                        t1.start();
                        for(int i=0;i<10;i++)
                        {
                            System.out.println("Main"+i);
                        }
                    }
                }        

## Comparator Example with lambda expression:

                import java.util.ArrayList;
                import java.util.Collections;
                import java.util.Comparator;

                //class MyComparator implements Comparator<Integer>
                //{
                //    @Override
                //    public int compare(Integer i1, Integer i2) {
                //        return (i1<i2)?-1:(i1>i2)?1:0;
                //    }
                //}
                public class Main {
                    public static void main(String[] args) {

                        ArrayList<Integer> l=new ArrayList<>();

                        l.add(10);
                        l.add(4);
                        l.add(12);
                        l.add(16);
                        l.add(8);
                        System.out.println(l);
                //        Collections.sort(l,new MyComparator());
                //        System.out.println(l);

                        Comparator<Integer> c=(i1,i2)->(i1<i2)?-1:(i1>i2)?1:0;
                        Collections.sort(l,c);
                        System.out.println(l);
                        
                        l.stream().forEach(System.out::println);
                        List<Integer> l1=l.stream().filter(i ->i%2==0 ).collect(Collectors.toList());
                        System.out.println(l1);
                    }
                }
                
                
                [10, 4, 12, 16, 8, 7, 3, 13]
                [3, 4, 7, 8, 10, 12, 13, 16]
                3
                4
                7
                8
                10
                12
                13
                16
                [4, 8, 10, 12, 16]
## Anonymous Inner class Vs Lambda Expression:
* Anonymous inner class can extend a normal class.
* Anonymous inner class can extend a an abstract class.
* Anonymous inner class can implement an interface which contains any number of abstract methods

* Lambda expression can implement an interface which contains only one abstract method
* anonymous inner class is different from Lambda Expression

                public class Main {
                    public static void main(String[] args) {

                        Runnable r=new Runnable() {

                            @Override
                            public void run() {
                                for(int i=0;i<10;i++)
                                {
                                    System.out.println("Child");
                                }
                            }
                        };
                        Thread t1=new Thread(r);
                        t1.start();
                        for(int i=0;i<10;i++)
                        {
                            System.out.println("Main");
                        }

                       /* Runnable r=()->{
                            for(int i=0;i<10;i++)
                            {
                                System.out.println("Child");
                            }
                        };
                        Thread t1=new Thread(r);
                        t1.start();
                        for(int i=0;i<10;i++)
                        {
                            System.out.println("Main");
                        }*/
                    }
                }
