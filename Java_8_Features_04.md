# default and static methods in java 8: 

until 1.7 version every method present inside an interface is always public and abstract.

    void m1();

    public void m1();

    abstract void m1();

    public abstract void m1();

 

### Related method :

1.8 V: default methods + static method

1.9 V: private method

### variable :

Every variable present in interface is always public static final

Means no enhancement related to the varaible in any version

# default method | virtual extension method | Defender method :

Without effecting implementation classes if we want to add new method to the interface then we should go for default method.

Example:

        interface I1

        {

            void m1();

            void m2();

        }

        class Test1 implements It

        {

            void m1(){}

            void m2(){}

        }

        class Test2 implements It

        {

            void m1(){}

            void m2(){}

        }

        .

        .

        .

        .

        class Test100 implements It

        {

            void m1(){}

            void m2(){}

        }

        

If we want to add one more method in I1 interface, So it may effect to all implementation classes.Means we need to override that new method in all implemetation classes.if we have 100 implementation classes so we need to implement that new method in all implementation classes.        

        

                    interface I1

                    {

                        default void m1()

                        {

                            System.out.println("Default method m1 of I1");

                        }

                    }

                    interface I2

                    {

                        default void m1()

                        {

                            System.out.println("Default method m1 of I2");

                        }

                    }

                    public class Main implements I1,I2{

                        public void m1()

                        {

                            System.out.println("Default Overriden method");

                            I1.super.m1();

                            I2.super.m1();

                        }

                        public static void main(String[] args) {

                            Main t1=new Main();

                            t1.m1();

                        }

                    }        

------------------------------------------------------------------------------------------------------------------------------------------

        interface I1

        {

            public static void m1()

            {

                System.out.println("Interface static method");

            }

        }

        public class Main{

            public static void main(String[] args) {

                I1.m1();

        //        m1();                 invalid

        //        Test.m1();            invalid

        //        Main t=new Main();

        //        t.m1();               invalid

            }

        }

        

We can also create main method in interface in 1.8 version 

        interface Main

        {

            public static void main(String args[])

            {

                System.out.println("Interface static method");

            }

        }
