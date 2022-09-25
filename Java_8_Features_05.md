# Stream in java 8:

## Collection & Stream:

1. If we want to represents a group of objects as a single entity then we should go for Collection.
2. If want to process objects from the Collection then we can use stream concepts of java 8.
3. Stream s=c.stream();
4. java.util.stream pkg
5. functions:

* stream()
* filter()
* map()
* collect() 
* count()
* sorted()
* sorted(Comparator)
* sorted(Comparable)
* min()
* max()
* forEach()
* toArray()
* Streamof()

        import java.util.ArrayList;
        import java.util.List;
        import java.util.stream.Collectors;

        public class Main{
            public static void main(String[] args) {

                ArrayList<Integer> l1=new ArrayList<Integer>();

                l1.add(0);
                l1.add(3);
                l1.add(6);
                l1.add(8);
                l1.add(7);
                List<Integer> collect = l1.stream().filter(i -> i % 2 == 0).collect(Collectors.toList());
                System.out.println(collect);
                
                List<Integer> collect1 = l1.stream().map(i -> i + 5).collect(Collectors.toList());

                System.out.println(collect1);
            }
        }
        
        [0,6,8]
        [5, 8, 11, 13, 12]
     
-----------------------------------------------------------------------------------------------------------------------------------------     
        
                import java.util.ArrayList;

                public class Main{
                    public static void main(String[] args) {

                        ArrayList<Integer> l1=new ArrayList<Integer>();

                        l1.add(15);
                        l1.add(45);
                        l1.add(68);
                        l1.add(79);
                        l1.add(34);

                        long count = l1.stream().filter(i -> i < 35).count();
                        System.out.println(count);

                    }
                }     
                
                2
                
 ---------------------------------------------------------------------------------------------------------------------------------------------
 
                import java.util.ArrayList;
                import java.util.List;
                import java.util.stream.Collectors;

                public class Main{
                    public static void main(String[] args) {

                        ArrayList<Integer> l1=new ArrayList<Integer>();

                        l1.add(15);
                        l1.add(45);
                        l1.add(68);
                        l1.add(79);
                        l1.add(34);

                        // sorted method sort objects in asc order by default
                        List<Integer> collect = l1.stream().sorted().collect(Collectors.toList());
                        System.out.println(collect);

                        //if we want to sort in desc order then we should go for Comparator
                        List<Integer> collect1 = l1.stream().sorted((i1, i2) -> ((i1 < i2) ? 1 : (i1 > i2) ? -1 : 0)).collect(Collectors.toList());
                        System.out.println(collect1);

                        //using Comparable
                        List<Integer> collect2 = l1.stream().sorted((i1, i2) -> i1.compareTo(i2)).collect(Collectors.toList());
                        System.out.println(collect2);

                        //using Comparable desc
                        List<Integer> collect3 = l1.stream().sorted((i1, i2) -> i2.compareTo(i1)).collect(Collectors.toList());
                        System.out.println(collect3);

                    }
                }
                
                [15, 34, 45, 68, 79]
                [79, 68, 45, 34, 15]
                [15, 34, 45, 68, 79]
                [79, 68, 45, 34, 15]
                
------------------------------------------------------------------------------------------------------------------------------

                import java.util.ArrayList;
                import java.util.Comparator;
                import java.util.List;
                import java.util.stream.Collectors;

                public class Main{
                    public static void main(String[] args) {

                        ArrayList<String> l1=new ArrayList<String>();

                        l1.add("Zahid");
                        l1.add("Walter");
                        l1.add("Jessy");
                        l1.add("Skyler");
                        l1.add("Hank");
                        System.out.println(l1);

                        List<String> collect = l1.stream().sorted().collect(Collectors.toList());
                        System.out.println(collect);

                        List<String> collect1 = l1.stream().sorted((i1,i2)->i1.compareTo(i2)).collect(Collectors.toList());
                        System.out.println(collect1);

                        List<String> collect2 = l1.stream().sorted((i1,i2)->i2.compareTo(i1)).collect(Collectors.toList());
                        System.out.println(collect2);

                        Comparator<String> c=(s1,s2)->{
                            int len1=s1.length();
                            int len2=s2.length();
                            if(len1<len2)
                                return 1;
                            else if (len1>len2) {
                                return -1;
                            }
                            else
                                return 0;
                        };
                        List<String> collect3 = l1.stream().sorted(c).collect(Collectors.toList());
                        System.out.println(collect3);

                    }
                }
                
                [Zahid, Walter, Jessy, Skyler, Hank]
                [Jessy, Walter, Hank, Zahid, Skyler]
                [Jessy, Walter, Hank, Zahid, Skyler]
                [Skyler, Zahid, Hank, Walter, Jessy]
                [Jessy, Zahid, Skyler, Walter, Hank]
                
----------------------------------------------------------------------------------------------------------------------------------------

                import java.util.ArrayList;
                import java.util.Comparator;
                import java.util.List;
                import java.util.stream.Collectors;

                public class Main{
                    public static void main(String[] args) {

                        ArrayList<Integer> l1=new ArrayList<Integer>();

                       l1.add(15);
                       l1.add(0);
                       l1.add(10);
                       l1.add(30);
                       l1.add(5);
                       System.out.println(l1);

                        Integer integer = l1.stream().min((i1, i2) -> i1.compareTo(i2)).get();
                        System.out.println(integer);

                        Integer integer1 = l1.stream().max((i1, i2) -> i1.compareTo(i2)).get();
                        System.out.println(integer1);

                        Integer integer2 = l1.stream().min((i1, i2) -> -i1.compareTo(i2)).get();
                        System.out.println(integer2);

                        Integer integer3 = l1.stream().max((i1, i2) -> -i1.compareTo(i2)).get();
                        System.out.println(integer3);
                    }
                }
                
---------------------------------------------------------------------------------------------------------------------------------------------

                import java.util.ArrayList;

                public class Main{
                    public static void main(String[] args) {

                        ArrayList<Integer> l1=new ArrayList<Integer>();

                       l1.add(15);
                       l1.add(0);
                       l1.add(10);
                       l1.add(30);
                       l1.add(5);
                       System.out.println(l1);

                       l1.stream().forEach(l2->{
                           System.out.println(l2);
                       });
                        System.out.println();
                        System.out.println();
                        Integer[] integers = l1.stream().toArray(Integer[]::new);
                        for(Integer p: integers)
                        {
                            System.out.println(p);
                        }
                    }
                }

                [15, 0, 10, 30, 5]
                15
                0
                10
                30
                5


                15
                0
                10
                30
                5
------------------------------------------------------------------------------------------------------------------------------

                import java.util.stream.Stream;

                public class Main{
                    public static void main(String[] args) {

                        Stream<Integer> integerStream = Stream.of(1, 22, 333, 4444, 55555);

                        integerStream.forEach(System.out::println);
                    }
                }
                
                
                1
                22
                333
                4444
                55555                
