# **Java**

copyright ©️ WHU NCC 2022 Aaron

------



### Java基础

1. 赋值

    - 对象赋值：赋予管理权限
    - 变量赋值：赋予值
    
2. for-each循环

    ```java
    int[] = new data[4];
    for(int k : data)
        if(k = in.nextInt())
            System.out.println("found: " + k);
    ```

    - 每次取出data中的元素赋值给k
    - k是data中元素的拷贝，通过k无法更改data中的元素
    - **若数组为对象数组，则每轮for-each循环k都可以获得对data的管理权限，即可以通过k更改data中的元素**

3. 字符类型char
   - java使用Unicode编码，''内可为汉字/字母/符号等

4. 包裹类型

   | 基础类型 | 包裹类型  |
   | :------: | :-------: |
   | boolean  |  Boolean  |
   |   char   | Character |
   |   int    |  Integer  |
   |  double  |  Double   |

   - 包裹类型可与基础类型相互赋值

       ```java
       int i;
       Interger p;
       p = i;
       ```

   - 包裹类型中提供了一些函数，如

       ```java
       Character.isdigit(char ch);
       Character.toUpperCase(char ch);
       Character.toLowerCase(char ch);
       Integer.MAX_VALUE
       ```

5. Math类

   ```java
   Math.abs(variable);		//取绝对值
   Math.round(variable);	//对小数四舍五入为整数
   Math.random();	//给出0~1之间的随机数
   Math.pow(a, b);
   ```

6. 字符串

   - 一个类，包含操作

   - 创建

      ```java
      //创建的是常量
      String str0 = "abc";
      String str1 = new Sring("abc");
      ```

   - 输入

      ```java
      in.next();	//读一个单词，标准是空格/tab/换行
      in.nextLine();	//读一行
      ```

   - 比较

      ```java
      String s = "yourString";
      s.equals("targetString");	//判断字符串相等
      s.compareTo(string);	//比较Unicode编码的大小
      ```

   - 类操作

      ```java
      str.lenth();	//获取字符串长度
      str.charAt(index);	//获取index位置的字符
      str.substring(n);	//从n号位置到末尾的字串
      str.substring(b, e);	//从b开始到e前的字串
      
      str.indexOf(c);		//c字符所在位置，-1表示不存在
      str.indexOf(c, n);	//从n号位置开始找c
      str.indexOf(t);		//找字符串t
      
      str.lastIndexOf(c);		//从右边找
      str.lastIndexOf(c, n);
      str.lastIndexOf(t);
      
      str.startsWith(t);	//是否以t字符串开始
      str.endsWith(t);
      
      //以下函数不改变原字符串，结果是创建的新字符串
      str.trim();		//删除两端空格
      str.replace(c1, c2);	//将所有字符c1替换为c2
      
      str.toLowerCase();
      str.toUpperCase();
      ```

      ```java
      //寻找字符串中第n个x
      String str = "123x456x789...";
      int loc = 0;
      for(int i = 0; i < n - 1; ++i)
          loc = str.indexOf('x', loc + 1);	//先找前n-1个x
      System.out.println(str.indexOf('x'));	//输出第n个x的位置
      ```

   - switch-case可对字符串使用

7. 函数

    - 创建函数

        ```java
        public static returnType funcName(){
            code;
        }
        ```




## 面向对象编程

### 类

1. 对象与类

    - 对象：实体，需要被创建，能为我们做事情
        - 表达东西或事件
        - 运行时响应消息（提供服务）
        - 对象 = 属性 + 服务
    - 类：规范，根据类的定义创建对象
        1. 定义所有对象的属性
        2. 可以用来定义变量

2. 封装：将数据和对数据操作放在一起

3. this

    - 成员函数的一个特殊固有的本地变量，表达了调用这个函数的哪个对象

4. 函数调用

    - 从成员函数外调用：对象名称.成员函数
    - 从成员函数内部调用：直接调用

5. 构造函数

    - ~~~java
        public class Coin {
            private HashMap<Integer, String> coinName = new HashMap<Integer, String>();
        
            public Coin() {		//构造函数
                coinName.put(11, "penny");
                coinName.put(10, "dime");
                coinName.put(25, "quarter");
                coinName.put(50, "half-dolar");
            }
        }
        ~~~

    - 如果有一个成员函数的名字和类的名字完全相同，则在创建这个类的每一个对象的时候会自动调用这个函数 —> 构造函数

    - 这个函数不能有返回类型

6. 友元函数

    - 不加public的成员函数
    - 在同一个包下可相互访问

7. 函数重载

    - 一个类可以有多个函数，只要它们的参数表不同

    - 创建对象的时候给出不同的参数值，就会自动调用不同的构造函数

    - 通过this()还可以调用其他构造函数

    - 一个类里的同名但参数表不同的函数构成了重载关系

    - ~~~java
        public String getName(int index) {
            if (coinName.containsKey(index))
                return coinName.get(index);
            else
                return "NOT FOUND";
        }
        
        public void getName(String name) {
            System.out.println("hhhhhhhhhhhhhhhhh");
        }
        ~~~

    - 

8. private变量：同类不同对象可相互访问私有成员对象

9. 一个编译单元只能有一个public类，但是可以有多个类，public类名称需要与编译单元名称相同

10. 类变量(static variable)

    - 在类的装载时初始化
    - 属于类，不属于类的任何对象
    - 可以通过 `<类名.变量名>` 访问
    - 多个（含类变量的）类的变量，只有一个static变量

11. 类函数(static function)

       - 类函数中可以调用其他类函数，不能直接访问类的成员变量

       - ```java
            public class test{
                private int a;
                public static f(){
                    
                }
            	public static void main(){
                    test t = new test();
                    test.a++;	//正确
                    a++;	//错误
                    f();	//正确
                    test.f();	//正确
            	}   
            }
            ```

12. 在类中加以下代码可以式println直接将对象的内容打印出来

       - ```java
            public String toString(){
                return ...(fomat);
            }
            ```
    
13. 判断对象是否属于一个类

     ~~~java
     objectNmae instanceof className
     ~~~



### 泛型容器

1. 顺序容器

     - `ArrayList<Type> name`

          ```java
          import java.util.ArrayList;
          
          ArrayList<String> s = new ArrayList<String>();
          ```

     - 基本操作：详见说明文档

2. 对象容器

     - 对象数组中每个元素都是对象的管理者而非对象本身，创建数组并没有创建其中的每一个对象。
     - for-each对对象数组使用时，获得的是对象的管理者，因此可以对其管理的数据进行更改

3. 集合容器（set）

     -  `HashSet<Type> name`

          ```java
          import java.util.HashSet;
          
          HashSet<String> = new HashSet<String>();
          ```

     - 无重复元素

     - 无排序概念

4. 散列表（hashmap）

     - `HashMap<K, V> name`

          ```java
          import java.util.HashMap;
          
          HashMap<Key, Value> name = new HashMap<Key, Value>();
          HashMap<Integer, String> name = new HashMap<Integer, String>();
          ```
          



### 继承和多态

1. 继承

    1. 用法

        ~~~java
        class ThisClass extends SuperClass { 
            ...
        }
        ~~~

        - `ThisClass`: 子类
        - `SuperClasa`: 父类

    2. 特点

        - 父类先初始化，子类再初始化
        - 继承父类所有方法、变量、成员
        - 若子类父类方法重名，调用子类方法(覆盖override)
        - 一个子类仅能继承自一个父类

    3. 访问属性

        | **父类成员访问属性** | **在父类中的含义**                 | **在子类中的含义**                                           |
        | -------------------- | ---------------------------------- | ------------------------------------------------------------ |
        | public               | 对所有人开放                       | 对所有人开放                                                 |
        | protected            | 只有包内其它类、自己和子类可以访问 | 只有包内其它类、自己和子类可以访问                           |
        | 缺省                 | 只有包内其它类可以访问             | 如果子类与父类在同一个包内：只有包内其它类可以访问否则：相当于private，不能访问 |
        | private              | 只有自己可以访问                   | 不能访问                                                     |

    4. 子类参数通过父类构造需要通过 `super(value, ...)` 进行参数传递

    5. 子类调用父类方法通过 `super.methodOfSuperClass()`
    
2. 多态

    1. 子类和父类

        - 子类对象可被当作父类对象使用
            - 赋值给父类
            - 作为参数传入需要父类参数的函数
            - 放入父类对象的容器

    2. 多态变量

        1. 变量在程序运行中管理的变量类型不同（如DataBase中的item可保存cd和dvd）

            - 能够保存声明类型（静态类型）及其子类
            - 动态类型：程序运行中使用的类型
            - 向上造型：将子类赋给父类

        2. 造型cast

            1. 子类赋给父类（本质是两者共同管理同一个对象）

            2. 父类不能赋给子类

                ~~~java
                Vehicle v;
                Car c = new Car();
                v = c;		//	可以
                c = v;		//	不行
                c = (Car)v	//	造型，可以，但若v此时管理的不是c类，则会异常
                ~~~

        3. 函数调用的绑定

            1. 静态绑定：根据变量的声明类型决定
            2. 动态绑定：根据变量的动态类型决定

    3. Object类

        1. java的单根结构![image-20220618231448698](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220618231448698.png)



### 设计原则

1. 耦合
    1. 耦合程度
        - 紧耦合：两个类有相关程度很大
        - 松耦合：两个类有相关程度很小
    2. 使用封装来降低耦合
        1. 将类变量改为 `private`
        2. 对外提供接口
2. `StringBuffer` 类
    1. `String` 类的变量是不可修改的，每次 `+ "..."` 都会产生一个新的字符串，开销较大
    2. `StringBuffer` 产生一个可以修改的字符串，通过 `SringBuffer.append(String)` 方法从后面连接字符串
3. 可扩展性
    1. 框架+数据提升可扩展性
        1. 硬编码(如 `if-else` )转换为框架+数据
        2. 用容器替代私有变量
            - 用 `HashMap` 建立一对一的关系
            - 使用 `HashMap.put(V, K)` 加入关系
            - 对 `HashMap.keySet()` 使用 `for-each` 来调取所有值
    2. 尽量多使用 `Set` `HashSet` `HashMap` 等容器来保存数据
    3. 减少硬编码(如 `System.out.println()` 来直接打印数据)，多使用库函数输出 (如 `toString()`)
4. 业务逻辑和数据分开
    - 数据
        - 数据操作
        - 数据计算
    - 表现
        - 节目
        - 交互
5. 图形界面网格化
6. 责任驱动设计
    - 将需要实现的功能分配到适合的类/对象中实现



### 抽象和接口

1. 抽象 `abstract`

    1. 相关概念
        1. 抽象函数：没有方法体
        2. 抽象类：表达概念且不能产生对象的类
        3. 类似C/C++中的声明，只声明方法的形式，没有实际方法体
        4. 类中若一个及以上的抽象函数，则类必须为抽象类
        5. **抽象类可以定义变量**
            - 任何继承次抽象类的非抽象（子类）类对象都可以赋值给这个变量
            - 抽象类变量可以管理所有子类对象
    2. 实现
        1. 抽象类的子类必须覆盖父类的抽象函数，否则自己成为抽象类

2. 接口 `interface` 

    1. 纯抽象类

        1. 函数为抽象函数
        2. 成员变量为 `public static final` (属于类，常量)

    2. 接口规定了形式，任何继承自接口的类必须实现接口

    3. 接口定义

        ~~~java
        public interface className {
            ...
        }
        ~~~

    4. ~~~java
        public class name (extends superClass) implements className {
            //	name类继承自superClass实现了className接口
        }
        ~~~

        - 一个类可以实现多个接口
        - 接口可以继承接口，不能继承类
        - 接口不能实现接口

    5. 面向接口编程

        1. 设计程序先定义接口再实现类
        2. 任何需要在函数间传入传出的都是接口而非类



### 控制反转

1. swing机制

    1. `JButton` 和 `BorderLayout`

        1. `BorderLayout` 将窗口分为`NORTH`, `SOUTH`, `EAST`, `WEST`, `CENTER`，以此为基准放置部件

        2. GUI

            ~~~java
            JFrame frame = new JFrame();
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);	//设置点按关闭
            frame.setResizable(false);						//	是否可调大小
            frame.setTitle("Title");
            frame.add(Component);				    	    //	加入显示的部件
            JButton btn = new JButton("Text");
            frame.add(btn, BorderLayout.SOUTH);				//	将按钮加入到最下方
            btn.addActionListener(new ActionListener() {	 //	反转控制
                  //定义的一个内部类（匿名类）
            
                @Override
                public void actionPerformed(ActionEvent e) {
            		// Handle action
                }
            
            });
            frame.pack();
            frame.setVisible(true);
            ~~~

        3. 内部类

            1. 定义在外部类内部的类

                ~~~java
                public class Out {
                    private int variable;
                    
                    private class stepActionListener implements ActionListener{
                        //	内部类
                    }
                }
                ~~~

                - 内部类可以访问外部类的成员变量和成员函数

            2. 定义的位置不同

                1. 类的内部
                2. 函数的内部
                    - 当访问变量的时候，只能访问 `final` 类型的变量

            3. 匿名类

                1. 内部类的一种
                2. 在new的时候同时给出类的定义
                3. 可以继承，可以实现接口
                4. swing机制广泛使用匿名类

        4. 反转控制

            1. 按钮提供一个 `ActionListener` 接口和一对注册注销函数`addActionListener()` `removeActionListener()` 来接收按钮被点按消息，在实现此接口的类里重写 `actionPerformed(ActionEvent e)` 方法来执行点按后的操作
            2. 
