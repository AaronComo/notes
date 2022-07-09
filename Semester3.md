# 小学期实训

**Copyright :copyright: NCC 2022 Aaron**

------



### Git

1. 创建仓库

    ```bash
    $ git init
    ```

2. 将更改加入提交缓存区

    ```bash
    $ git add <file name> 
    ```

3. 提交更改

    ```bash
    $ git commit -m "comment"				
    $ git commit -m "comment" --amend	//	合并到最后一次提交
    ```

4. 查看提交记录

    ~~~bash
    $ git log
    ~~~

5. 查看文件状态

    ```bash
    $ git status
    ```

6. 查看所有分支

    ```bash
    $ git branch
    ```

7. 创建并切换到新分支

    ~~~bash
    $ git branch -b <new branch name>
    ~~~

8. 删除分支

    ```bash
    $ git branch -d <branch name>
    ```

9. 回退到n个版本前

    ~~~bash
    $ git reset --hard HEAD~n
    ~~~

10. 切换到分支

    ~~~bash
    $ git checkout <branch name>
    ~~~

11. 合并分支(可能需要处理冲突)

    ```bash
    $ git merge <branch name>
    ```

    - 冲突：不同分支修改了同一行

        ~~~shell
        ~ some text here
        ~ some text here.
        ~ some text here.
        ~ <<<<<< Head
        ~ # 以下为主分支里的内容
        ~ Hello world!
        ~ I have a nice day!
        ~ =======
        ~ # 以下为分支里的内容
        ~ Hell world!
        ~ I want to remake!
        ~ >>>>>> branch name
        ~ some text here.
        ~ some text here.
        ~~~

    - 处理方式：保留一个内容

        ```shell
        ~ some text here
        ~ some text here.
        ~ some text here.
        ~ Hell world!
        ~ I want to remake!
        ~ some text here.
        ~ some text here.
        ```

    - 修改完后执行 `git add` 和 `git commit`，然后即可 `git merge`

12. 从远端主分支克隆仓库

    ```bash
    $ git clone "url"
    ```

13. 从远端拉取分支(主)

    ```bash
    $ git pull origin master
    ```

14. 将分支推送到远端并成为master的分支

    ```bash
    $ git push origin <branch name>
    ```



### 贪心算法

1. 多步算法时，每一步取出最优解，即可得到全局最优解

2. 局部最优 -> 全局最优

3. 先排序

4. 按升序/降序取，最先取的个数取最多

5. 打怪游戏

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <stdbool.h>
    
    typedef struct zombie {
        int x;
        int y;
    } Zombie;
    int m, h, b;
    
    int cmp(const void* a, const void* b) {
        Zombie* aa = (Zombie*)a;
        Zombie* bb = (Zombie*)b;
        return (aa->x * aa->y > bb->x * bb->y) ? 1 : -1;
    }
    
    bool killIt(Zombie z) {
        while (z.y > 0) {
            if (m == 0 && z.y != 0)
                return false;
            --m;
            --z.y;
        }
        return true;
    }
    
    void attack(Zombie z, int* cnt) {
        if ((h + b) >= z.x)
            if (killIt(z))
                ++(*cnt);
    }
    
    int main(int argc, char** argv) {
        int n;
        scanf("%d %d %d %d", &n, &m, &h, &b);
        Zombie zombies[n];
        for (int i = 0; i < n; i++) {
            scanf("%d %d", &zombies[i].x, &zombies[i].y);
        }
    
        qsort(zombies, n, sizeof(Zombie), cmp); //按闪避排序
        int cnt = 0;
        for (int i = 0; i < n; i++) {
            attack(zombies[i], &cnt);
            if (m == 0) {
                break;
            }
        }
        printf("%d", cnt);
        return 0;
    }
    ```



### 图

1. 方向数组

    ```c
    int dir = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    
    for (int i = 0; i < 4; i++) {
        int nextx = x + dir[i][0];
        int nexty = y + dir[i][1];
    }
    ```

2. 求连通块个数

    1. 从一个结点调用dfs，遇到的结点标记已访问
    2. 从下一个没有访问的结点调用dfs
    3. 重复以上过程直到所有点被访问
    4. 调用dfs的次数即为连通块个数

3. 并查集【[CSDN](https://blog.csdn.net/the_ZED/article/details/105126583?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165735179016780366596299%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165735179016780366596299&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-105126583-null-null.142^v32^new_blog_fixed_pos,185^v2^control&utm_term=%E5%B9%B6%E6%9F%A5%E9%9B%86&spm=1018.2226.3001.4187)】

    1. 结构

        - 每个集合是一颗以代表元为根的树
        - `pre[]` 用来存放每个结点的父亲
            - `pre[b] = a`：b的双亲结点是a
            - `pre[a] = a`： a是当前集合的代表元

    2. 实现

        ```c
        const int  N=1005					//指定并查集所能包含元素的个数（由题意决定）
        int pre[N];     					//存储每个结点的前驱结点 
        int rank[N];    					//树的高度 
        void init(int n) {    				//初始化函数，对录入的 n个结点进行初始化 
            for(int i = 0; i < n; i++) {
                pre[i] = i;     			//每个结点的上级都是自己 
                rank[i] = 1;    			//每个结点构成的树的高度为 1 
            } 
        }
        int find(int x) {    	 		    //查找结点 x的根结点 
            if(pre[x] == x) return x;  		//递归出口：x的上级为 x本身，则 x为根结点 
            return find(pre[x]); 			//递归查找 
        } 
         
        int find(int x) {    				//改进查找算法：完成路径压缩，将 x的上级直接变为根结点，那么树的高度就会大大降低 
            if(pre[x] == x) return x;		//递归出口：x的上级为 x本身，即 x为根结点 
            return pre[x] = find(pre[x]);   //此代码相当于先找到根结点 rootx，然后 pre[x]=rootx 
        } 
        
        bool isSame(int x, int y) {    		//判断两个结点是否连通 
            return find(x) == find(y);  	//判断两个结点的根结点（即代表元）是否相同 
        }
        
        bool merge(int x, int y) {			//未改进的合并算法，可能导致最终成为单根树，进而性能下降
            int fx = find(x);
            int fy = find(y);
            if (fx != fy) 
                pre[fx] = fy;
        }
        
        bool merge(int x,int y) {
            x = find(x);						//寻找 x的代表元
            y = find(y);						//寻找 y的代表元
            if(x == y) return false;			//如果 x和 y的代表元一致，说明他们共属同一集合，则不需要合并，返回 false，表示合并失败；否则，执行下面的逻辑
            if(rank[x] > rank[y]) pre[y]=x;		//如果 x的高度大于 y，则令 y的上级为 x
            else {								//否则
                if(rank[x]==rank[y]) rank[y]++;	//如果 x的高度和 y的高度相同，则令 y的高度加1
                pre[x]=y;						//让 x的上级为 y
        	}
        	return true;						//返回 true，表示合并成功
        }
        
        ```

    3. 
