# 小学期实训

**Copyright :copyright: NCC 2022 Aaron**



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
    $ git pull origin
    ```

14. 将分支推送到远端并成为master的分支

    ```bash
    $ git push origin <branch name>
    ```

