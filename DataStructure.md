# **数据结构与算法**

**Copyright ©️ NCC 2021 刘蔚峰**

[TOC]



## 第一章	绪论

### 数据结构定义

1. 数据项：具有独立含义的数据的最小单位
2. 数据对象：性质相同的数据元素的集合
3. 数据结构
    1. 逻辑结构：数据间的逻辑关系
    2. 储存结构：数据结构在计算存储器中的存储



### 逻辑结构

1. **表示：**

    1. 图表
    2. 二元组
        - B = { D, R }    一个数据逻辑结构
        - D = { d~i~ |1 &le; i &le; n, n &ge; 0 }    d~i~表示D中第i个元素，n为D中数据元素个数
        - R = { r~j~ | 1 &le; j &le; m, m &ge; 0 }    r~j~表示R中的第j个关系，m为R中的关系个数
        - 序偶：< x, y >
            - 表示xy相邻
            - x是y的前驱元素，y是x的后继元素
            - 开始元素：无前驱元素
            - 终端元素：无后继元素

2. **类型**

    1. 集合

    2. 线性结构

    3. 树形结构：元素之间存在一对多的关系

        - 每个元素有一个前驱元素（除开始元素外），和至少一个后继元素
        - eg：二叉树

    4. 图形结构

        [^注]: 树形结构和图形结构统称非线性结构
        
        

### **储存结构**

1. 顺序储存结构
    - 内存上相邻
    - 优点：储存效率高
    - 缺点：不便于数据修改
    - 主要用于内存的储存
    
    ```c
    typedef struct node {
        int num;
        char name[10];
        int sex;
    } Node;
    ```
    
2. 链式储存结构
    - 优点：便于数据修改
    - 缺点：储存空间利用率低
    - 主要用于内存的储存
    
    ```c
    typedef struct list {
        int num;
        char name[10];
        int sex;
        struct node* next;
    } List;
    ```
    
3. 索引储存结构：储存元素信息同时构建附加索引表
    - 主数据表：存放数据元素信息的表
    - 索引表：
        - 索引项：关键字（有序）+地址
    - 优点：查找效率高
    - 缺点：需要建立索引表，内存开销大
    - 主要用于外存（文件）的储存
    
4. 哈希（散列）表：元素关键字通过哈希函数计算出一个值作为储存地址
    - 优点：查找速度快
    - 只适合要对数据进行快速查找和插入的场合
    - 主要用于外存（文件）的储存
    
    

### **抽象数据类型（Abstract Data Type, ADT）**

1. 基本格式

    ```c
    ADT 抽象数据类型名称 {
    	数据对象：声明;
        	D = {e1, e2 | e1, e2均为实数};
        数据关系：声明;
        	R = {<e1, e2> | e1为实数部分，e2为虚数部分};
        基本运算：声明;	
        	AssignComplex(&z, v1, v2)：构造复数z，实部虚部分别为v1，v2
            DestroyComplex(&z)：销毁z
            //格式：基本运算名(参数表)：运算功能描述
            // 参数表示：
            // 值参数：只为运算提供输入值
            // 引用参数(&参数名)；提供输入值/返回结果
    }
    ```
    
2. 表示：(D, S, P)

    - D：数据对象
    - S：D上的关系集
    - P：D中数据运算的基本运算集

3. 特征（p14）：

    - 数据抽象
    - 数据封装：将数据和操作数据的运算组合在一起的机制



### 算法

1. 特性
   - 有穷性：有穷时间可停止
   - 确定性：无二义性
   - 可行性：可被机械执行
   - 有输入
   - 有输出
   
2. 算法分析
   - 原操作：固有数据类型的操作
   - 问题规模n：求解问题大小的正整数

3. 算法复杂度

- 算法频度

    - 程序算法所有原操作的次数：T(n)

    - T(n) = O(f(n))

    - ![image-20220118175132989](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220118175132989.png)

    - eg:求T(n)

        ```c
        for(int i = 0; i < n; i++)		//语句执行n+1次，最后i=n，但循环执行n次
            for(int j = 0; j < n; j++)	//语句执行n(n+1)次
                a += 1;					//语句执行n^2次
        ```

        T(n) = n + 1 + n(n + 1) + n^2^ = 2n^2^ + 2n + 1

        O(n) = O(n^2^)

- 时间复杂度：O(n)

    - O(1):无循环，与问题规模n无关
    - O(n):1重循环
    - O(n^m^):m重循环
    - 可用最深层内原操作执行的时间×次数作为时间复杂度
    - 求和定理：对于两个并列代码片段，复杂度 = O(MAX(f(n), g(n)))
    - 求积定理：对于两个嵌套代码，复杂度 = O(f(n) × g(n))
    - 最好、最坏时间复杂度
    - 平均时间复杂度：E(n) = Σ(P(I) × T(I))
        - ΣP(I) = 1，P(I)为I出现的频率 

- 空间复杂度：S(n)

    - 程序运行时临时占用的内存大小
    - S(n) = O(g(n))
    - O(1)：原地工作

- 算法复杂度渐进表示法![image-20220122124208660](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220122124208660.png)

  [^Tips]: 遇到O(n^2^)时，尝试将其转为O(nlogn)

- 算法分析窍门![image-20220122124019919](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220122124019919.png)



- 例题1:

    ```c
        int i = 1;
        while(i <= n)
            i *= 2;
    ```

    - 循环1次：i=2=2^1^
    - 循环2次：i=4=2^2^
    - 循环3次：i=8=2^3^
    - 循环x次：i=2^x^
    - 2^x^ &le; n => x &le; log~2~n
    - O(log~2~n)

- 例题2：

    ```c
        for(int i = 1; i <= n; i++)
            for(int j = 1; j <= i; j++)
                for(int k = 1; k <= j; k++)
                    x += 1;
    ```

    - $$
        O(n) = \sum^n_{i=1}\sum^i_{j=1}\sum^j_{k=1}1 = \sum^n_{i=1}\sum^i_{j=1}j = \sum^n_{i=1}\frac{i(i+1)}{2} = \frac12\sum^n_{i=1}(i^2+i) = \frac{n(n+1)(n+2)}64
        $$





## 第二章	线性表与广义表

### 线性表

1. 实现方式
    - 链式：单链、双链、循环
    - 顺序：顺序表
2. 举例：保存一元多项式
3. 存储密度 = 结点数据本身占用的空间/结点占用的空间总量



### 顺序表

1. 按逻辑顺序依次储存到一片连续的存储空间

2. 定义

   ```c
   typedef int ELemtype;
   
   typedef struct node {
       ELemtype data[MAX];
       int length;
   } SqList;
   ```



### 单链表

1. 链表中增加头结点作用
    - 首结点的插入和删除和其他结点操作一致
    - 无论链表是否为空都存在头结点，统一空表非空表处理

2. tips：将头结点前后拆成两个部分
3. 插入数据：找第i-1个元素



### 双链表

1. 定义

    ```c
    typedef struct DNode{
        ElemType data;
        DNode* prior;
        DNode* next;
    } DLinkNode;
    ```

2. 建立双链表：连接时改4个指针

3. 插入数据：找第i个元素



### 循环链表

1. 循环单链表：尾结点指向头结点
2. 循环双列表：两个循环
    - 链表中无空指针
    - p指向尾结点：``p->next = l``
    - 找到尾结点：``p->prior``

### 有序表

1. 定义：所有元素按递增/递减顺序排列的线性表



### 广义表

- <img src="C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220122195259257.png" alt="image-20220122195259257" style="zoom:100%;" />

- 广义表中的元素可以是单元素，也可以是另一个广义表（用union实现空间共享）

- 定义：

  ```c
  typedef ElemTag int;		//所需要的数据类型
  typedef enum { ATOM, LIST } ElemTag;	//ATOM＝0，表示原子结点；LIST＝1，表示表结点
  typedef struct GLNode {
      ElemTag tag;			//标志位tag用来区子结点和表结点
      union {
          ElemType data;		//原子结点的值域data
          GList* sub_list;	//表结点指针
      }URegion;				//URegion是原子结点的值域data和表结点的指针域sub_list的联合体域 
  } GList;
  ```
  
  <img src="C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220122200627115.png" alt="image-20220122200627115" style="zoom:100%;" />



### 多重链表 

- 链表中结点可能同时隶属于多条链
- 拥有多个指针域，如广义链表包含next和sub_list两个指针域





## 第三章	栈和队列

### 栈

1. #### 基本

    1. 定义：只能在一端进行插入的线性表，允许插入删除的是栈顶，相对的是栈底
    2. 特点：后进先出LIFO
    3. n个不同元素入栈（可即入即出），能产生$$\frac{1}{n+1}C^n_{2n}$$种出栈顺序（卡特兰数）

2. #### 栈的顺序存储结构

    1. 定义：

        ```c
        typedef struct {
            ElemType data[MaxSize];
            int top;	//栈顶指针，存放栈顶元素的下标
        } SqStack;
        ```

    2. 栈空：``top = -1``

    3. 栈满：``top = MaxSize - 1``

3. #### 栈的链式存储结构

    1. 定义:

        ```c
        typedef struct linknode {
            ElemType data;
            struct linknode* next;
        } LinkStNode;
        ```

    2. 栈空：``s->next = NULL``

    3. 栈满：不考虑

    4. 入栈：头插一个元素



### 队列

1. #### 基本

    - 先进先出FIFO

2. #### 顺序队列

    ```c
    typedef struct {
        ElemType data[MaxSize];
        int front；		//front指向队头元素的前一个位置
        int rear;		//rear指向队尾元素
    } SqQueue;
    ```

    - 队空：``front = rear``
    - 队满：``rear = MaxSize - 1``
    - 入队：``rear++``
    - 出队：``front++``

3. #### 环形队列

    - 不会出现假溢出

    - 队空/初始：``front = rear = 0``

    - 队满：``(rear + 1) % MaxSize = front``，牺牲一个front单元

    - 进队：

        ```c
        rear = (rear + 1) % MaxSize;
        data[rear] = d;
        ```

    - 出队：

        ```c
        front = (front + 1) % MaxSize;
        d = data[front];
        ```

    - 环形队列计算：

        ```c
        //已知front、rear，求元素个数count：
        count = (rear - front + MaxSize) % MaxSize;
        //已知front、count：
        rear = (front + count) % MaxSize;
        //已知rear、count：
        front = (rear - count + MaxSize) % MaxSize;
        ```

4. #### 链式队列（不带头结点）

    1. 定义

        ```c
        //数据结点
        typedef struct qnode {
            ElemType date;
            qnode* next;
        } DataNode;
        
        //队列结点
        typedef struct {
            DataNode* front;
            DataNode* rear;
        } LinkQuNode;
        ```

        - 队空：front = rear = NULL
        - 队满：不考虑
        - 进队：无头结点，需要分情况讨论
            - 队空
            - 队满

        - 出队：删front->data，front后移





## 第四章	串

### 基本特点

- 特殊线性表（顺序表）
- 真子串：不包含自身的所有子串



### 顺序串

- 存储方式

    - 非紧缩格式
        - 一个字存放一个字符
        - 浪费存储空间
        - 处理一个或一组连续字符方便

    - 紧缩格式：
        - 一个字存放多个字符
        - 节省空间
        - 处理单个字符不方便

- 定义

    ```c++
    typedef struct {
        char data[MaxSize];
        int length;
    } SqString;
    ```



### 链串

- 带头结点的单链表

- 一个结点存储多个字符，每个结点存储字符的个数叫结点大小

- 定义

    ```c
    typedef struct node{
        char data;
        struct node* next;
    } LinkStrNode;
    ```

- 基本运算集

    ```c++
    void strAssign(LinkStrNode*& s, char cstr[]);
    void destroyStr(LinkStrNode*& s);
    void strCopy(LinkStrNode*& s, LinkStrNode* t);
    bool strEqual(LinkStrNode* s, LinkStrNode* t);
    int strLength(LinkStrNode*& s);
    LinkStrNode* concat(LinkStrNode* s, LinkStrNode* t);
    LinkStrNode* subStr(LinkStrNode* s, int i, int j);
    LinkStrNode* insStr(LinkStrNode* s, LinkStrNode* t);
    LinkStrNode* delStr(LinkStrNode* s, int i, int j);
    LinkStrNode* replaceStr(LinkStrNode* s, int i, int j, LinkStrNode* t);
    ```

    

### 模式匹配

- 匹配字串
    - Brute-Force（BF）算法
        - target字串从待匹配串头开始匹配，不匹配则向后滑动
        
    - KMP算法[【csdn】](https://blog.csdn.net/weixin_46007276/article/details/104372119?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165208393216782391845514%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165208393216782391845514&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-104372119-null-null.142^v9^control,157^v4^control&utm_term=kmp%E7%AE%97%E6%B3%95&spm=1018.2226.3001.4187)
      
        - next数组保存加速信息
            $$
            next[j]=
            \begin{cases}
            -1,&\text{j = 0 时}\\
            k,&\text{j 前 k 个字符和开头 k 个字符相同}\\
            0,&\text{其他}
            \end{cases}
            $$
        
        - `k = next[j]`: 模式串j位置前有k个字符和开头的k个字符相同
        
        - 主串s指针为i，模式串t为j时失配，则模式串向右滑动 `j - next[j]` 个位置，下次从 $s_i$ 和 $t_{next[j]}$ 开始匹配





## 第五章	递归

### 尾递归

- 递归调用的是最后一条语句
- 可借助循环实现



### 其他递归

- 可借助栈实现



### 何时使用递归

- **问题及其子问题解法相同**
- 结构的递归：如不带头结点的单链表
- 定义是递归的



### 递归出口

1. f(n) = m



### 汉诺塔

1. 盘子移动次数

- m(n) = 1	n = 1;
- m(n) = 2m(n - 1) + 1    n > 1;





## 第七章	树和二叉树

### 树

1. 定义

    - n个元素组成的有限集合（T）
    - n = 0：空树
    - n > 0：仅有一个结点作为树的根结点（根），其余结点可分为m个互不相交的有限集T~1~,T~2~....T~m~，其中每个子集本身也是一颗子树

2. 术语
    - 结点的度：某结点的子树个数
    - 树的度：所有结点的度中的最大值m，m次树4
    - 路径长度：路径结点数 - 1
    - 结点层次（深度）：根结点为1层
    - 树的高度（深度）：结点最大层次

3. 性质

    1. $$n_{总结点数}=所有结点度数之和+1=分支数+1=n_{0}+n_{1}+n_{2}+...+n_{m}$$ (m次树)
    1. $$度之和=n-1=n_1+2n_2+...+mn_m$$
    2. 度为m的树，第i层最多有 $$m^{i-1}$$ 个结点（i&ge;1）
    3. 高度为h的树最多有 $$\frac{m^h-1}{m-1}$$ 个结点
    4. 有n个结点的m次树最小高度为 $$h_{min}=\lceil log_m(n(m-1)+1 \rceil$$

4. 树的遍历

    - 先根遍历
        - 访问根结点
        - 从左到右先根遍历根结点的每一棵子树
    - 后根遍历
        - 从左到右后根遍历根结点的每一棵子树
        - 访问根结点
    - 层次遍历
        - 从根结点开始，从上到下，从左到右

5. 树的存储结构

    - 双亲存储结构

        ~~~c
        typedef struct{
            ElemType data;
            int parent;
        } PTree[MaxSize];
        ~~~

    - 孩子链存储结构

        ~~~c
        typedef struct node{
        	ElemType data;
        	struct node* sons[MaxSons];
        } TSonNode;
        ~~~

    - 孩子兄弟链存储结构

        ~~~c
        typedef struct tnode{
            ElemType data;
            struct tnode* hp;	//指向兄弟结点
            struct tnode* vp;	//指向左边第一个孩子结点
        } TSBNode;
        ~~~
    
        



### 二叉树

1. 定义
    1. 满二叉树
        - 概念
            - 每层都满
        - 特点
            - 高度为h，含 $$2^{h-1}$$ 个结点
            - 叶子结点都在最下层
            - 只有度为0/2的结点
    2. 完全二叉树（满二叉树的特例）
        - 概念
            - 最多只有下面两层的结点度数可以<2，且最下面一层的叶子结点都排列在该层的最左边
        - 特点
            - 叶子结点只可能出现在最下面两层
            - 最大层次中的叶子结点都在左边
            - 最多1个含度为1的结点，此结点只有左孩子
            - 按层序编号式，一旦出现编号为i的结点是叶子结点或只有左孩子，则编号>i的结点均为叶子结点
            - n~总~ = 奇数，n~1~ = 0；n~总~ = 偶数，n~1~ = 1
    
2. 性质
    1. 非空二叉树叶子结点树 = 双分支结点数 + 1
    2. 非空二叉树第i层最多有 $$2^{i-1}$$ 个结点
    3. 高度为h，最多含 $$2^{h-1}$$ 个结点（满二叉树）
    4. 完全二叉树，n个结点，编号为i的结点
        1. $$i\le\frac{n}2$$：i结点为分支结点
        2. $$i\ge\frac{n}2$$：i结点为叶子结点
        3. n为奇数：每个结点有左孩子和右孩子
        4. n为偶数：编号最大的分支结点（$$i=\frac{n}2$$）只有左孩子
        5. i结点有左孩子编号 $$2i$$，右孩子编号 $$2i+1$$
        6. 除根结点，i结点的双亲结点编号 $$\frac{i}2$$
    5. n个结点的完全二叉树高度为 $$\lceil log_2(n+1) \rceil$$ 或 $$\lfloor log_2n \rfloor+1$$
    
3. 二叉树与数、森林的转换

    1. 森林、树 -> 二叉树
        - 树的所有兄弟结点加连线
        - 每个结点只保留与左孩子的连线
    2. 二叉树 -> 森林
        - 若结点j为i的左孩子，则在i的所有右孩子，右孩子的右孩子与i加连线
        - 删除右孩子连线

4. 存储结构

    - 循序存储

        - 定义

            ```c
            typedef struct {
                ElemType data[MaxSize];
            } SqBinTree;
            ```

        - 按照满二叉树存储，没有的位置设为#

        - 空间浪费

        - 完全二叉树时推荐使用

        - 左孩子 $$\frac{i}{2}$$ 右孩子 $$\frac{i+1}{2}$$ 

    - 二叉链存储

        - 定义

            ```c
            typedef struct node{
                ElemType data;
                struct node* lchild, * rchild;
            } BTNode;
            ```

        - n个结点，2n个指针域

        - 分支数n - 1，非空指针域n - 1个

        - 空指针域个数 = n + 1

5. 遍历

    1. 先序遍历
        - 从根结点沿着二叉树外沿，逆时针走一圈回到根节点，路上遇到的元素顺序，就是先序遍历的结果
        - **先根 再左 再右**
        - ![](https://img-blog.csdnimg.cn/202012091634524.gif#pic_center)
    2. 中序遍历
        - 二叉树每个节点，垂直方向投影下来（可以理解为每个节点从最左边开始垂直掉到地上），然后从左往右数，得出的结果便是中序遍历的结果
        - **先左 再根 再右**
        - ![](https://img-blog.csdnimg.cn/20201209164211397.gif#pic_center)
    3. 后序遍历
        - 就是围着树的外围绕一圈，如果发现一剪刀就能剪下的葡萄（必须是一颗葡萄）（也就是葡萄要一个一个掉下来，不能一口气掉超过1个这样），就把它剪下来，组成的就是后序遍历了。
        - **先左 再右 再根**
        - ![](https://img-blog.csdnimg.cn/2020120916532175.gif#pic_center)

6. 二叉树的构造

    - 给定中序序列+前序/后序序列其中之一，可以确定二叉树
    - ![image-20220405154819014](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405154819014.png)
    - ![image-20220405155307247](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405155307247.png)
    - ![image-20220405155324644](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405155324644.png)
    - ![image-20220405160203885](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405160203885.png)
    - ![image-20220405160412226](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405160412226.png)
    - ![image-20220405160431739](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220405160431739.png)

7. 线索二叉树



### 哈夫曼树

1. 定义：n个结点构成的WPL最小的二叉树

    - 权：树中的结点被赋予的一个有意义的值
    - 带权路径长度WPL
        - 对于某结点i：从根结点到该结点的路径长度与该结点的权的乘积
        - 对于整个树：$$WPL=\sum^{n_0}_{i=1}w_il_i$$

2. 构造

    1. 原则

        - 权值越大的结点越靠近根结点
        - 权值越小的结点越远离根结点

    2. 构造方法

        1. 给定n~0~个权值，对应的结点构成n~0~棵二叉树的森林F，其中每棵树都只含有一个权值为w~i~的根结点，其左右子树均为空
        2. 森林F中选取权值最小和次小的两个子树分别作为左右子树构造一棵新的二叉树，新二叉树的根结点权值为左右子树的根结点的权值之和
        3. 在F中删去2中使用的两个子树，将这棵新二叉树放入F
        4. 重复2、3直到F中只含一棵树（哈夫曼树）

    3. 特点

        - 含有n~0~个叶子结点的哈夫曼树，共有2n~0~-1个结点

    4. 结点类型定义

        ```c
        typedef struct{
            ElemType data;  //结点数据
            double weight;	//权值
            int parent, lchild, rchild;
        } HTNode;
        ```

3. 哈夫曼编码

    1. 使用频率越高的字符编码越短





## 第八章	图

### 定义

1. 顶点的集合加边的集合，记作G



### 基本术语

1. 顶点的度
    - 无向图：顶点的边数
    - 有向图
        - 顶点的入度：指向该顶点的边
        - 顶点的出度：指出顶点的边
    - 一个图中有n个顶点，e条边，每个顶点的度为d~i~，则有 $e=\frac12\sum^{n-1}_{i=0}d_i$
2. 完全图
    - 无向图：含 $C_n^2=\frac{n(n-1)}2$ 条边
    - 有向图：含 $A_n^2=n(n-1)$ 条边
3. 子图：G2是G1的子集
4. 路径长度
    - 一条路径上的边数
5. 简单路径：一条路径上除了开始点和结束点可以相同外，其余点均不相同
6. 回路：一个环
    - 简单回路：简单路径构成的环
7. 连通
    - 连通：从顶点i到j有路径
    - 连通图：图中任意两个顶点均连通
    - 连通分量：极大连通子图
    - 强连通图：任意两个顶点i->j/j->i都存在路径
    - 非强连通图中找强连通分量（P255）
        - 先找一个环
        - **$找一个顶点包含\begin{cases}含有指向环的箭头\\含有环指向此顶点的箭头\end{cases}$**
        - 将此点加入环
8. 权
    - 每个边可以可以附带一个数值
    - 表示从一个顶点到另一个顶点的距离或花费的代价
    - 带权图（网）：含权的图



### 储存结构

1. 邻接矩阵：二维矩阵，有边（权）为1（权），无边为0，

    1. 不带权无向图(沿矩阵对角线对称)
        $$
        A[i][j]=\begin{cases}
        1 & \text(i, j) \in E(G)\\
        0 & \text other
        \end{cases}
        $$
        
    2. 不带权有向图
        $$
        A[i][j]=\begin{cases}
        1 & \text<i, j>\in E(G)\\
        0 & \text other
        \end{cases}
        $$
        
    3. 带权无向图
        $$
        A[i][j]=\begin{cases}
        \omega_{ij} & \text i\neq j且(i, j) \in E(G)，该边权为\omega_{ij}\\
        0 & \text i=j\\
        \infty&\text other
        \end{cases}
        $$
        
    4. 带权有向图
        $$
        A[i][j]=\begin{cases}
        \omega_{ij} & \text i\neq j且<i, j> \in E(G)，该边权为\omega_{ij}\\
        0 & \text i=j\\
        \infty&\text other
        \end{cases}
        $$
    
    3. 定义

        ```c
        #define MAXVEX 12					//定义最大顶点个数
        #define INF 32767					//定义无穷
        typedef struct{
        	int no;							//顶点编号
            InfoType info;					//顶点其他信息
        } VertexType;						//顶点类型
        
        typedef struct{
            int edges[MAXVEX][MAXVEX];		//邻接矩阵
            int n, e;						//顶点数，边数
            VertexType vexs[MAXVEX];		//存放顶点信息
        } MatGraph;							//完整的图邻接矩阵类型
        ```
        
    6. 特点
    
        - 空间复杂度O(n^2^)
        - 适合储存边较多的稠密图
    
2. 邻接表存储（顺序与链式的结合）

    1. 表示方法

        - 将每个顶点的所有邻接点构成单链表

        - 构建头结点保存顶点信息

        - 所有头结点构成一个头结点数组adjlist

            - adjlist[i]表示顶点i的单链表头结点
            - 通过i快速找到对应单链表

        - 头结点

            | data(顶点的名称/其他信息) | firstare(指向首结点) |
            | :-----------------------: | :------------------: |

        - 边结点

            | adjvex(与顶点i邻接的顶点编号) | nextarc(指向下一边结点) | weight(相关信息) |
            | :---------------------------: | :---------------------: | :--------------: |

    2. 边结点是与头结点有关的点

    2. 特点

        - 邻接表表示不唯一
        - 适合稀疏图

    4. 定义

        ```c
        //边结点
        typedef struct ANode{
        	int adjvex;					//该边邻接点编号
            struct ANode* nextarc;		//指向下一条边
            ElemType weight;			//该边的相关信息（如权值）
        } ArcNode;						
        
        //头结点
        typedef struct Vnode{
            InfoType info;				//顶点的信息
            ArcNode* firstarc;			//指向第一个边结点
        } VNode;						
        
        //完整图邻接表
        typedef struct{
            VNode adjlist[MAXVEX];		//邻接表头结点数组
            int n, e;					//顶点数n，边数e
        } AdjGraph;						
        ```

    5. 逆邻接表：头结点链接指向顶点的所有点

        - 特点
            - 表示不唯一
            - n个结点e条边的无向图，其邻接表有n个头结点，2e个边结点
            - n个结点e条边的有向图，其邻接表有n个头结点，e个边结点
            - 适合稀疏图
            - 无向图第i个结点对应的第i条链表的边结点个数=顶点i的度
            - 有向图第i个结点对应的第i条链表的边结点个数=顶点i的出度，入度为 所有adjvex值域为i的边结点个数、

3. 十字链表

4. 邻接多重表



### 遍历

1. 深度优先DFS
    - 距离第一个结点越远越先访问
    - 可以找到所有路径
2. 广度优先BFS
    - 距离第一个结点越近越先访问
    - 可以找到最短路径



### 生成树和最小生成树

1. 生成树
    1. 定义
        - 一个极小连通子图，含有图中全部n个顶点和n-1条边
        - 在生成树中添一条边一定产生一个环

    2. 通过BFS和DFS产生
2. 最小生成树
    1. 带全连通图G所有的生成树中权值最小的一个
    2. 构造方法：
        1. Prim算法
            - 算法生成的最小生成图不唯一
            - 步骤
                1. 先取一个顶点i放在u（最小生成树的过程）中
                2. 将u到外界的所有边作为侯选边
                3. 选取权值最小的侯选边输出，并把其连接的外部节点k加入u
                4. 重复2，3（若在3时发现所有侯选边权值相等，则输出最先加入的侯选边），直到u中包含所有顶点
            - 思路
                - 局部最优+调整=全局最优
            - 适合稠密图
            - 时间复杂度：O(n^2^)
        2. Kruskal算法
            - 适合稀疏图
            - 步骤
                - 把边组成集合按权排序（插入）
                - 按权递增取顶点连线
                - 若构成了环，则舍去此条边
            - 时间复杂度
                - 插入排序：O(N^2^)
                - 堆排序+并查集：O(nlogn)
3. 最短路径
    1. 路径长度：简单路径权值之和
    2. Dijkstra算法（单源最短路径）
        1. 步骤
            1. 将图G=(V, E)的顶点集合V分为S(已经求出最短路径的顶点集合)，和U(未求得的顶点集合)
            2. 开始时S只包含源点v(S={v})，v到自己的距离为0
            3. 取源点到U的最短路径长度的顶点u(权最小的，因为v是源点)，将u放入S
            4. 以u为中间点，进行路径调整，从v到U中的j的最短路径长变为min{c~vu~ + w~uj~, c~vj~}
            5. 重复34直到S包含所有顶点
4. 一对顶点间的最短路径
    1. Floyd算法
        - 时间复杂度O(n^3^)



### 拓扑排序

1. 步骤
    - 有向图中选择入度为0的顶点输出
    - 删去此顶点，并删去从此顶点发出的所有边
    - 重复上述步骤直到没有顶点为止



### AOE网与关键路径  

1. AOE网
    1. 定义：用边表示活动且只有一个源点和汇点的有向无环图成为边表示的活动的网
    2. 术语
        - 用有向无环图表示包含多项活动的工程计划
        - 活动：一条有向边
        - 活动需要时间：权
        - 源点：入度为0，表示活动开始事件
        - 汇点：出度为0，表示结束
    
2. 关键路径
    - 从源点到汇点的有最大路径长度的路径
    
    - 由关键活动构成
    
    - 可能不唯一
    
    - 求解过程
    
        - 最早开始时间：从右往左推
            $$
            ve(v)=
            \begin{cases}
            0\\
            max(ve(v)+c(<v,w>))
            \end{cases}
            $$
    
        - 最迟开始时间
        $$
            vl(v)
        $$
        
    - 求关键活动：不存在富裕时间





## 第九章	查找

### 概念

1. 动态查找：边查边改

2. 静态查找：只查找

3. 平均查找长度（关键字平均比较个数）
    $$
    ASL=\sum_{i=1}^{n}p_ic_i
    $$

    - p~i~：查找第i个元素的概率，通常为 $\frac1n$
    - c~i~：找到第i个元素所需要的关键字比较次数



### 线性表查找

1. 顺序查找
2. 二分查找
    1. 查找过程可以构建一颗二叉树（判定树/比较树）
    2. 成功二分查找：比较次数=被查数据在判定树的层数
3. 索引存储结构和分块查找
    1. 索引表
        - <关键字，地址>
        - 有序
    2. 数据块
        - 无序
        - 将数据分块，以数据块的最大/最小值和数据块的首地址建立索引表
    3. 分块查找
        1. 将数据块分为b块，每块有s个数据
        2. 最佳元素个数 $s=(n)^{\frac12}$
        3. 索引可以使用二分/顺序查找
        4. 数据块内用顺序
        5. 成功时平均查找长度
            1. 分块
                - $ASL_{blk}=ASL_{bn}+ASL_{sq}=log_2(b+1)+\frac{s}2$
            2. 顺序
                - $ASL_{blk}=ASL_{bn}+ASL_{sq}=\frac{s+b}2+1$



### 树表的查找

1. 二叉排序树
    1. 特点
        - 左子树非空，则左子树所有结点关键字小于根结点
        - 右子树非空，则右子树所有结点关键字大于根结点
        - 根结点左右子树也是一颗二叉排序树
        - 中序遍历序列为递增排序序列 
        
    2. 结点类型
    
        ~~~c
        typedef struct node{
            KeyType key;
            infoType val;
            struct node* lchild, rchild;
        } BSTNode;
        ~~~
    
    3. 生成、查找、插入
    
        ~~~c
        if (k < p->key)
            走左子树
        else if (k > p->key)
            走右子树
        ~~~
    
    4. 删除结点（本质是替换）
    
        1. 删叶子结点：直接删
        2. 有左子树/右子树：用左子树/右子树替换结点
        3. 左右子树都有
            1. 找到左子树中最大的结点，用其值替换要删结点的值，并删去左子树最大的结点
    
2. 平衡二叉树（AVL）

    1. 平衡因子：左子树高度-右子树高度
    2. 定义：所有结点的平衡因子绝对值&le;1
    3. 构建调整
        - 类型LL、RR、LR、RL型调整
        - 方法
            - 先插入一个结点
            - 从下到上找到第一个平衡因子绝对值>1的结点
            - 对此结点及以下的两个结点进行调整

3. B树
    1. B树又叫多路平衡查找树，适用于外存查找
    
    2. 一个m阶B树满足以下要求
        1. 每个结点至多含有m个孩子结点（最多含有m-1个关键字，MAX=m-1）
        2. 除了根结点，非叶子节点最少有 $\lceil \frac m2 \rceil$ 棵子树（即最少含有 $\lceil \frac m2 \rceil-1$ 个关键字，$MIN=\lceil \frac m2 \rceil-1$
        3. 若根结点不是叶子结点，则至少含有2个孩子结点
        4. 所有外部结点在同一层，B树是所有结点的平衡因子均为0的树（计算B树高度时，要计入最底层的外部结点）
    
    3. ~~~c
        #define MAX_M 10			//定义B树的最大的阶数
        typedef int KeyType;       	 //KeyType为关键字类型
        typedef struct node {      
            int keynum;				//结点当前拥有的关键字的个数
            KeyType key[MAX_M];      //[1..keynum]存放关键字
            struct node *parent;	 //双亲结点指针
            struct node *ptr[MAXM];   //孩子结点指针数组[0..keynum]
        } BTNode;
        ~~~
    
4. B+树

    1. 一个m阶B+树满足
        1. 每个分支结点至多有m棵子树
        2. 根结点或者没有子树，或者至少有两棵子树
        3. 除根结点外，其他每个分支结点至少有 $\lceil \frac m2 \rceil$ 棵子树
        4. 有n棵子树的结点恰好有n个关键字
        5. 所有叶子结点包含全部关键字及指向相应记录的指针，而且叶子结点按关键字大小顺序链接。并将所有叶子结点链接起来。
        6. 所有分支结点（可看成是索引的索引）中仅包含它的各个子结点（即下级索引的索引块）中最大关键字及指向子结点的指针。


### 哈希表

1. 哈希冲突：k~i~!=k~j~, h(k~i~)=h(k~j~)

2. 哈希函数构造方法

    1. 直接定址法
        $$
        h(k)=k+c
        $$

    2. 除留余数法
        $$
        h(k)=k mod p, p\le m
        $$
        p最好是素数

        m是哈希表表长

    3. 数字分析法





## 第十章	内排序

### 排序的特点

1. 所有可能的初始序列共有n!个
2. 所有可能的初始序列的排序过程构成一个决策树（n!个叶结点的二叉树）
3. 稳定性
    1. 稳定：排序后相同关键词的相对顺序不变


### 插入排序

1. 直接插入排序
    1. 思路
        - 正序找到一对反序元素 <b, a>，取 `temp = a`
        - 从b开始向前查找，每次比较当前元素与a的大小，若大于则将其后移
        - 直到找到插入位置，将反序元素放入挪出来的位置
    2. 最好情况（关键字正序）
        - 比较次数：$\sum_{i=1}^{n-1}1=n-1$
        - 移动次数：0
        - O(n)
    3. 最坏情况（关键字反序）
        - 比较次数：$\sum_{i=1}^{n-1}i=\frac{n(n-1)}2$
        - 移动次数：$\sum_{i=1}^{n-1}(i+2)=\frac{(n-1)(n+4)}2$
        - O(n^2^)
    4. 平均O(n^2^)
2. 二分插入排序
    1. 思路：先正序找反序元素，在前面的有序区二分法查找插入位置，大元素后移
    2. 算法分析
        - 平均比较次数：$log_2(i+!)-1$
        - 平均移动次数：$\frac{i}2+2$
        - O(n^2^)
3. 希尔排序
    1. 思路：分成d个组，组内直接插入，每次d /= 2
    2. 时间复杂度O(n^1.3^)



### 交换排序

1. 冒泡排序
    1. 思路：跑n-1趟，每趟将最后的最小元素移到前面（或将最大元素移到最后）
    2. 改进：当某一趟没有交换元素时即可结束
    3. 算法分析
        1. 最好情况（关键字正序）
            - 比较：$n-1$
            - 移动：0
            - O(n)
        2. 最坏情况（记录反序）
            - 比较：$\sum_{i=0}^{n-1}(n-i-1)=\frac{n(n-1)}2$
            - 移动：$\sum_{i=0}^{n-2}3(n-i-1)=\frac{3n(n-1)}2$
            - O(n^2^)
    
2. 快速排序
   
    1. 冒泡排序的改进
    
    2. 思路
    
        - 归位：每趟使表的第1个元素 `temp = nums[0]` 放入适当位置
            - 两端采取双指针进行多次交换
            - 一趟归位后temp左侧元素均小于temp，右侧均大于temp
    
        - 将表一分为二，对子表按递归方式继续这种划分
        - 递归出口：划分的子表长为0或1
    
    3. 算法
    
        ~~~c
        void quickSort(int nums[], int front, int back) {
            int i = front, j = back, temp;
            if (i < j) {
                temp = nums[i];
                while (i != j) {
                    while (i < j && nums[j] >= temp)
                        --j;
                    nums[i] = nums[j];
                    while (i < j && nums[i] <= temp)
                        ++i;
                    nums[j] = nums[i];
                }
                nums[i] = temp;
                quickSort(nums, front, i - 1);
                quickSort(nums, i + 1, back);
            }
        } 
        ~~~
    
    4. ![快速排序算法分析1](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220507204028731.png)
    
    5. ![快速排序算法分析2](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220507204111768.png)
    
        ![快速排序算法分析3](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220507205144352.png)
    
        ![image-20220507205433790](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220507205433790.png)
    



### 选择排序

1. 简单（直接）选择排序
    1. 思路
    
        - 共跑n-1趟
        - 每趟从第i个以后的元素中选出小于 `nums[i]` 的最小的元素和i处元素交换
        - ++i
    
    2. 算法
    
        ~~~c++
        void swap(int& a, int& b) {
            int temp = a;
            a = b;
            b = temp;
        }
        
        int findMin(int nums[], int i, int numsSize) {
            int k = i;
            for (int j = i + 1; j < numsSize; j++)
                if (nums[j] < nums[k])
                    k = j;
            return k;
        }
        
        void selectSort(int nums[], int numsSize) {
            for (int i = 0; i < numsSize - 1; i++) {    //n-1趟
                int k = findMin(nums, i, numsSize);     //k保存最小元素的下标
                if (k != i)                             //k=i后续元素均大于nums[i]，不用交换
                    swap(nums[i], nums[k]);
            }
        }
        ~~~
    
    3. ![简单排序算法分析](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220507211849496.png)

### 堆排序

1. 堆
    1. 一个序列，关键字从k~1~-k~n~，满足以下之一
        1. k~i~ &le; k~2i~, k~i~ &le; k~2i+1~ : 小根堆
        2. k~i~ &ge; k~2i~, k~i~ &ge; k~2i+1~ : 大根堆
    2. 构建大根堆（筛选算法：不是堆->堆）
        1. 对左右子树均为堆的完全二叉树调整根结点
        2. 取出根结点放入temp，比较左右孩子结点，取大值同temp比较，若大于temp则两者互换（表现为大数上升）
    3. 排序模式
        1. 升序：大根堆
        2. 降序：小根堆
    4. 步骤（以升序为例）
        - 将无序数组构造成一个大根堆（新插入的数据与其父结点比较）
        - 固定一个最大值，将剩余的数重新构造成一个大根堆，重复n-1次
    5. ![image-20220508140143307](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220508140143307.png)



### 归并排序

1. 将两个及以上的有序链表合并成一个

2. 思路：从长度为1开始，合并相邻单链表，每次长度加1

3. 二路归并

    ​	<u>3 2</u> <u>5 8</u> <u>9 1</u> <u>6 0</u> <u>7 4</u> 

    1:  <u>2 3</u> <u>5 8</u> <u>1 9</u> <u>0 6</u> <u>4 7</u> 

    ​	<u>2 3 5 8</u> <u>1 9 0 6</u> <u>4 7</u> 

    2:  <u>2 3 5 8</u> <u>0 1 6 9</u> <u>4 7</u> 

    ​	<u>2 3 5 8 0 1 6 9</u> <u>4 7</u> 

    3:  <u>0 1 2 3 5 6 8 9</u> <u>4 7</u> 

    ​	<u>0 1 2 3 5 6 8 9 4 7</u>

    4:  <u>0 1 2 3 4 5 6 7 8 9</u>

4. ![image-20220508145157236](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220508145157236.png)



### 基数排序

1. 基数r
    1. 基数=进制数
    2. 此进制下所有位均不超过基数
2. 分类（根据数据特点选择）
    1. 最低位优先：如正序递增排序（越重要的位放在后面）
    2. 最高位优先
3. 思路：按位比较，分配到n个队列中，然后从低到高收集整个队列连起来，再按下一位比较
4. 由于数据需要放入队列，又要从队列取出来，需要大
    量元素移动。所以排序数据和队列均采用链表存储更好。
5. 通过分配和收集实现排序，关键字比较
6. ![image-20220508154801050](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220508154801050.png)



### 内排序比较

1. ![image-20220508154909622](C:\Users\刘蔚峰\AppData\Roaming\Typora\typora-user-images\image-20220508154909622.png)
2. 按时间复杂度
    1. O(n^2^)：简单排序方法
        - 直接插入
        - 直接选择排序
        - 冒泡排序
    2. O(nlogn)
        - 快速排序
        - 堆排序
        - 归并排序
    3. O(n)
        - 基数排序（假设r、d为常量)
3. 按空间复杂度
    1. O(n)
        - 归并排序
        - 基数排序
    2. O(logn)
        - 快速排序
    3. O(1)
        - 其他排序方法
4. 按稳定性
    1. 不稳定排序
        - 希尔排序
        - 快速排序
        - 堆排序
        - 直接选择排序
    2. 稳定排序
        - 其他
5. 按是否全局有序
    1. 全局有序
        - 冒泡排序
        - 直接选择排序
        - 堆排序
    2. 非全局有序
        - 其他