1.  分支

   ​     分支与主线平行，不影响主线的运行

2.  查看当前有多少分支         **git branch** 

   ![1542888527053](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542888527053.png)

   以上表示当前只有主线，没有分支，指针指向master主线

    

3.  创建分支             **git branch 分支名**   

   ​                                  ![1542888738474](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542888738474.png)

​        以上表示当前有主线master和分支dev，指针指向master主线



4.  切换分支            **git checkout  分支名**

![1542888947418](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542888947418.png)

​         以上表示当前有主线master和分支dev，指针指向dev分支



5.  创建+切换分支           **git checkout -b 分支名**

![1542889125433](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542889125433.png)

​         以上表示当前有主线master和分支dev  dev1，指针指向dev1分支



6. 合并某分支到某分支或主线         **git merge 分支名**

![1542889810243](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542889810243.png)

​        首先将指针切换到需要合并到的主线上，再合并需要合并的分支

​        备注：  fast-forward为快进模式，就是直接把master指向dev1的当前提交，合并速度非常快



7.  删除分支               **git branch -d 分支名**

   ![1542890270984](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542890270984.png)

​             删除已经合并到主线的分支，只保留主线master



8. 解决冲突

   ​      (1): 创建并切换到分支，然后对文件编辑

​             ![1542892593947](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542892593947.png)

 

​              (2): 切换到主线，然后对文件编辑

![1542892727029](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542892727029.png)



​               (3): 合并分支到主线冲突，此时需打开文件，对文件进行编辑，然后提交此次变更

![1542892819058](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542892819058.png)



![1542893255259](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542893255259.png)



​             (4).   合并分支到主线后删除分支

![1542893391455](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542893391455.png)



9.  分支管理策略

   (1):  通常合并分支时，如果可能，git会用 fast forward 模式，但是有些快速合并并不能成但合并时没有冲突，这个时候会合并之后做一次新的提交

   ![1542895134099](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895134099.png)

   ​    

   ​      对dev分支新建一个文件，对master主线文件修改

   ​      然后git merge dev 合并分支出现下图所示画面

   ​       修改备注后  ctrl+X离开然后按Y保存

   ​      此时dev分支合并到master主线

![1542895179485](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895179485.png)

![1542895390624](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895390624.png)

![1542895607264](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895607264.png)

![1542895643329](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895643329.png)



最后删除dev分支

![1542895762683](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542895762683.png)



(2): 强制禁用fast forward模式，git会在merge时生成一个新的commit

​    

​          首先创建并切换到分支上，修改文件

​          然后切换到master主线，使用 **git merge --no-ff -m 备注 分支名** 将分支合并到主线上

![1542897461454](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542897461454.png)



![1542897621877](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1542897621877.png)



10.  bug分支

     bug可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。

     当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后再git stash pop回到工作现场



​         (1).分支dev上目前在编辑cat3.txt文件，还没有提交，此时有一个bug需要处理，可以使用git stash将分支dev 放入暂存区

![1543319451265](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543319451265.png)



​           (2). 切换回master主线，然后新建一个分支处理bug，将bug修改后的分支合并到主线，然后删除bug分支

![1543320298296](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320298296.png)



![1543320440123](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320440123.png)



![1543320477555](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320477555.png)



​           (3). bug修改OK后再切换回dev分支，使用git stash pop恢复暂存区里的文件

​                  git stash list可以查看暂存区里是否有文件

![1543320700345](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320700345.png)



![1543320746734](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320746734.png)





**总结**

![1543320919662](C:\Users\better\AppData\Roaming\Typora\typora-user-images\1543320919662.png)