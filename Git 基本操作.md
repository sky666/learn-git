Git 学习手册：

1. **git init**   初始化 ，在目标文件夹使用此命令，文件夹内会新增一个.git隐藏文件

   ![1539698692543](C:\Users\better\AppData\Local\Temp\1539698692543.png)

   ​



2. **git add** 后跟着需要上传的文件上传文件

   **git commit -m** ‘注释’  确认上传文件

​                                          ![1539611612234](C:\Users\better\AppData\Local\Temp\1539611612234.png)



3. **git log** 查询所有已上传的版本记录

![1539612725079](C:\Users\better\AppData\Local\Temp\1539612725079.png)



![1542889627186](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542889627186.png)

4. **git reset --hard  HEAD^**      版本回退到上一个版本  git reset --hard  HEAD^^      版本回退到上上一个版本

​       **git reset --hard  HEAD~1**    版本回退到上一个版本 git reset --hard  HEAD~2    版本回退到上上一个版本

![1539615016922](C:\Users\better\AppData\Local\Temp\1539615016922.png)

![1539615095001](C:\Users\better\AppData\Local\Temp\1539615095001.png)

​        **git reset --hard** 后跟着版本的文件编码前几位可以回退到那个版本

![1539615222184](C:\Users\better\AppData\Local\Temp\1539615222184.png)



5. **git reflog**  查询之前的操作记录   

    注意：每个记录前有文件的编码，可以使用git rest --hard 命令回退到想退回的版本文件

​    ![1539615448089](C:\Users\better\AppData\Local\Temp\1539615448089.png)



6. 工作区和暂存区

    工作区： 电脑中的目录文件夹

     版本库： 工作区内有一个隐藏目录.git，这个不是工作区，而是git的版本库 

   ![1539699387853](C:\Users\better\AppData\Local\Temp\1539699387853.png)

​      **git status**   查看当前工作树的状态（新增一个cat1.txt文件，修改cat.txt文件)

![1539699636131](C:\Users\better\AppData\Local\Temp\1539699636131.png)



​       git add  可以一次上传多个文件，也可以上传一个文件夹里的所有文件

​       此时文件放在暂存区中

![1539699845730](C:\Users\better\AppData\Local\Temp\1539699845730.png)

​      git commit  将文件上传到版本库中

​      此时工作区内无文件需要提交

![1539700025147](C:\Users\better\AppData\Local\Temp\1539700025147.png)



7.  git 管理文件的修改，它只会提交暂存区的修改来创建版本

     比如一个文件修改后git add到暂存区，然后对文件再次修改，但是没有git add到暂存区，此时git commit只会将之前暂存区的文件上传，而再次修改的文件没有上传，而是留在工作区

   ![1539700818526](C:\Users\better\AppData\Local\Temp\1539700818526.png)

  

8. 撤销修改

   ​    a.工作区里的文件撤销修改：   **git checkout --** 要撤销的文件

   ![1539701211359](C:\Users\better\AppData\Local\Temp\1539701211359.png)

​                 

​             b.暂存区里的文件撤销修改:   首先  **git reset HEAD** 要撤销的文件     到工作区，然后  **git checkout --** 要撤销的文件    将文件撤销

![1539701478777](C:\Users\better\AppData\Local\Temp\1539701478777.png)



​                c.版本库里的文件撤销修改：  **git reset --hard**  到需要返回的版本



9. 对比文件的不同

   ​        a.对比工作区中的文件和版本库中的文件的不同

   ​                    **git diff HEAD -- 要对比的文件**

   ​                    其中文件前有---的表示为版本库HEAD里的文件，+++的表示工作区里的文件

   ​                    以下对比表示工作区里的文件比版本库HEAD里的文件多了一行，多了一行‘a new line;’前面有加了一个‘+’号,白色文字表示两个文件都有的内容

   ![1539785559848](C:\Users\better\AppData\Local\Temp\1539785559848.png)



​                b.对比版本库中的不同版本的文件的不同

​                    **git diff  <u>HEAD  HEAD^</u>  -- 要对比的文件(不同版本可以用不同方式表示)**

​                    其中文件前有---的表示为当前HEAD文件，+++的表示版本库里的HEAD前一个版本的文件

​                    以下对比表示当前版本里的文件比前一个版本库里的文件多了一行，多了一行‘this is the forth line;’前面有加了一个‘-’号，白色文字表示两个文件都有的内容

![1539785940053](C:\Users\better\AppData\Local\Temp\1539785940053.png)





10.  删除文件

    ​             使用**rm** 命令删除文件后，可以使用**git  checkout -- 文件名**恢复文件

    ​             ![1539786921302](C:\Users\better\AppData\Local\Temp\1539786921302.png)

    ​            

    ​             使用**rm** 命令删除文件后，可以使用**git  add/rm 文件名**将文件放入暂存区，此时可以使用**git reset HEAD 文件名**取消暂存，文件重回工作区删除状态

![1539787230294](C:\Users\better\AppData\Local\Temp\1539787230294.png)



​                最后**git commit -m ’注释‘**将此次删除文件放入版本库中

![1539787475080](C:\Users\better\AppData\Local\Temp\1539787475080.png)

​              

​                   如果一个文件不在暂存区也没有在版本库，那么文件删除后无法恢复

​                   ![1539788890781](C:\Users\better\AppData\Local\Temp\1539788890781.png)



​                **如果一个文件已经被提交到版本库，那么永远不用担心误删，但是要小心，只能恢复到最新版本，你会丢失最近一次提交后你修改的内容**

11.  总结：git基本操作

    ![1539788561430](C:\Users\better\AppData\Local\Temp\1539788561430.png)

    ​