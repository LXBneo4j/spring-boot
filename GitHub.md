## GitHub团队协同开发流程(LXB)
##### author：刘小波
##### source:[来源](https://github.com/livoras/blog/issues/7);
####1、仓库AND分支
![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/centr-decentr@2x.png)

####2、基本概念
    仓库（Repository）
      在项目的开始到结束，我们会有两种仓库。一种是源仓库（origin），一种是开发者
      仓库。上图中的每个矩形都表示一个仓库，正中间的是我们的源仓库，而其他围绕着
      源仓库的则是开发者仓库。
      
    源仓库：源仓库
        在项目的开始，项目的发起者构建起一个项目的最原始的仓库，我们把它称为origin，
        例如我们的PingHackers网站，origin就是这个PingHackers/blog了。
        
        源仓库有两个作用：
            汇总参与该项目的各个开发者的代码
            存放趋于稳定和可发布的代码
        源仓库应该是受保护的，开发者不应该直接对其进行开发工作。只有项目管理者
        (通常是项目发起人)能对其进行较高权限的操作。
        
        开发者仓库
        上面说过，任何开发者都不会对源仓库进行直接的操作，源仓库建立以后，每个开
        发者需要做的事情就是把源仓库的“复制”一份，作为自己日常开发的仓库。这个复
        制，也就是github上面的fork。每个开发者所fork的仓库是完全独立的，互不干
        扰，甚至与源仓库都无关。每个开发者仓库相当于一个源仓库实体的影像，开发者在
        这个影像中进行编码，提交到自己的仓库中，这样就可以轻易地实现团队成员之间的
        并行开发工作。而开发工作完成以后，开发者可以向源仓库发送pull request，
        请求管理员把自己的代码合并到源仓库中，这样就实现了分布式开发工作，和最后的
        集中式的管理。
        
        
    分支（Branch）
        永久性分支
        master branch：主分支
        develop branch：开发分支
        临时性分支
        feature branch：功能分支
        release branch：预发布分支
        hotfix branch：bug修复分支
    永久性分支
        永久性分支是寿命无限的分支，存在于整个项目的开始、开发、迭代、终止过程中。永久性
        分支只有两个master和develop。
        所有开发者开发好的功能会在源仓库的develop分支中进行汇总，当develop中的代码经过
        不断的测试，已经逐渐趋于稳定了，接近产品目标了。这时候，我们就可以把develop分支
        合并到master分支中，发布一个新版本。所以，一个产品不断完善和发布过程就正如下图：
   ![image](https://raw.githubusercontent.com/livoras/blog-images/master/git/main-branches@2x.png);
   
    注意，任何人不应该向master直接进行无意义的合并、提交操作。正常情况下，master只应该
    接受develop的合并，也就是说，master所有代码更新应该源于合并develop的代码。
    
    暂时性分支
        暂时性分支和永久性分支不同，暂时性分支在开发过程中是一定会被删除的。所有暂时性分支，
        一般源于develop，最终也一定会回归合并到develop。
        
        feature：功能性分支，是用于开发项目的功能的分支，是开发者主要战斗阵地。开发者在本
        地仓库从develop分支分出功能分支，在该分支上进行功能的开发，开发完成以后再合并到
        develop分支上，这时候功能性分支已经完成任务，可以删除。功能性分支的命名一般为
        feature-*，*为需要开发的功能的名称。
   ![](https://raw.githubusercontent.com/livoras/blog-images/master/git/fb@2x.png);
    

#### 3、工作流（worklow）
    Step 1：源仓库的构建
        这一步通常由项目发起人来操作，我们这里把管理员设为LXBneo4j，假设LXBneo4j已经为
        我们建立起了一个源仓库LXBneo4j/git-demo，并且已经初始化了两个永久性分支master和
        develop;
    Step 2:开发者fork源仓库
        源仓库建立以后，每个开发就可以去复制一份源仓库到自己的github账号中，然后作为自己开
        发所用的仓库。假设我是一个项目中的开发者，我就到PingHackers/git-demo项目主页上
        去fork：
        fork完以后，我就可以在我自己的仓库列表中看到一个和源仓库一模一样的复制品。这时就应
        该感叹，你以后要和它相依为命了
    Step 3：把自己开发者仓库clone到本地
    Step 4：构建功能分支进行开发（）
    Step 5：向管理员提交pull request
        假设我完成了“讨论”功能（当然，你还可能对自己的develop进行了多次合并，完成了多个功
        能），经过测试以后，觉得没问题，就可以请求管理员把自己仓库的develop分支合并到源仓库
        的develop分支中，这就是传说中的pull request。





















