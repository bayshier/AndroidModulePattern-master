
### 你知道吗？Github的 “star” 功能就像微信朋友圈中的 **“点赞”** 功能，如果你觉得我的代码对你有帮助，你可以帮我点个赞，随手 “star” 一下。

# AndroidModulePattern
Android项目组件化示例代码

### app组件功能：
1. app组件主要用于管理其他组件；
2. app组件中可以初始化全局的库，例如Lib.init(this);
3. 添加 multiDex 功能

### main组件功能：
1. 声明应用的launcherActivity----->android.intent.category.LAUNCHER；
2. 添加SplashActivity;
3. 添加LoginActivity；
4. 添加MainActivity；

### girls/news组件功能：
1. 这两个组件都是业务组件，根据产品的业务逻辑独立成一个组件；

### common组件功能：
1. common组件是基础库，添加一些公用的类；
2. 例如：网络请求、图片加载、工具类、base类等等；
3. 声明APP需要的uses-permission；
4. 定义全局通用的主题（Theme）；

## License
    400天48国家
    http://www.miaopai.com/show/-YZD4h~cQy0LJukKshT24Q__.htm
    
    https://www.zhihu.com/question/27000882
    
    这一节的内容是Git的组件化部署
    
    建立工程后，如果你是个单人开发项目的大牛，我佩服你，可以跳过这里，然后愉快写你的代码。
    
    但是如果你需要将组件化项目部署为多人开发，并需要使用到Git部署，那么这编文章希望能成为你的刚需。
    
    这里介绍的是完全可以搭建出一个多人的组件化的研发框架。
    
    优势在于
    
    1.用文件系统将代码隔离。
    
    2.可以功能模块独立编译，并且最终聚合编译。
    
    3.可以自由组合自己需要的模块。
    
    4.编译速度加快。
    
    还有更多的妙用会在之后的章节介绍。
    
    
    
    Gank里面新开了一个Sub的分支（https://github.com/cangwang/Gank/tree/sub），欢迎star一波
    
    
    
    一.安装git
    
    我一直以来其实只用傻瓜式的git界面工具，将代码放到GitHub。
    
    
    GitHub
    但是GitHub的UI工具，并不能提供全部的Git的功能，我们需要使用Git Bash来完成我们的操作
    
    然后我们上Git的官网（https://git-scm.com/downloads），下载一个Git
    
    
    
    然后安装客户端，注意一定要安装Git Bash
    
    
    
    然后一路Next安装就可以了，我们最后再桌面可以看到Git Bash的工具，那就安装完成了。
    
    
    
    然后，一些GitHub账号验证和服务器验证的基础，那就需要大家IT服务配置来完成了。这里不做深入介绍
    
    
    
    二.创建子模块
    
    这里用我的GitHub作为例子，如果自身有git服务器，如何创建项目目录，应该对你们来说也很容易。
    
    New创建一个项目
    
    
    
    填写项目名字，然后按create repsository就可以完成
    
    
    
    完成模块创建
    
    
    
    然后我们使用Git Bash工具，打开到我们的目录，git命令，如果有用过linux命令，应该没有太大的入门成本
    
    
    
    然后我们需要使用命令
    
    git submodule add 你想依赖的module的git地址
    例如我的是
    
    git submodule add https://github.com/cangwang/home
    
    那么git将会在我们的Gank文件夹里面，将home里面的内容拷贝下来，并且会创建一个.gitmodules的文件。
    
    
    
    我们用记事本打开，将显示里面的引用内容。
    
    
    
    然后我们已经引用了home子模块到我们的Gank目录里面了。
    
    然后我们下一步，需要将home以子模块引用的方式提交到GitHub上。
    
    我们工程里如果有子模块，是无法使用GitHub的工具来提交到GitHub上的。提示我们需要用GitShell工具
    
    
    
    其实我们用Git Bash工具，也是可以的。
    
    我们使用git commit命令
    
    
    
    如果我们git commit的时候，没有填写任何的描述信息是无法提交的，所以一定要注意提交的时候务必要填写。
    
    
    
    然后使用git push命令就能完成提交了。
    
    
    
    然后我们在GitHub将看到子模块的显示和其他一般的文件夹显示是不同的，然后点进去会跳到我们实际的home的GitHub地址里面。
    
    
    
    
    
    三.子模块编译。
    
    我们新建一个工程
    
    
    
    使用GitHub来下载home子模块的代码到我们的Android 的Home工程里面。
    
    
    
    选定目录到Home里面
    
    
    
    然后我们就能在工程里，看到home了
    
    
    
    然后我们新建一个lib module的代码，然后将基本代码拷贝到home里面
    
    
    
    然后将home作为lib module配置到settings.gradle里面
    
    
    
    home作为lib module配置完成了。
    
    当然我们会组件化运行的时候，功能模块同样需要依赖于base模块的，那么也是非常简单的，重复以上的操作做一个base模块。
    
    
    
    这里因为GitHub工具是同一个电脑是无法clone同一个工程多次，所以需要使用命令git clone可以直接克隆。
    
    
    
    然后这个Home工程里面，就可以作为一个单一的功能模块来开发了。
    
    然后我们将home代码提交到GitHub上，提交就是上面介绍过的git commit和git push的命令。
    
    如果我们想要将最新的代码更新到我们的Gank的总工程里面，需要使用命令
    
    git submodule update
    这里还有一个深坑的地方，因为这句命令不一定能更新子模块的代码，需要使用下面这一句比较保险，直接从远端或者每个子模块的代码，当然相当于全部重新获取，而不是增量获取。
    
    git submodule update --remote
    这时候才能获取到其子模块的最新代码。
    
    
    
    三 总工程代码同步
    
    如果你的其他同事，第一次下载带有子模块的工程，会发现子模块是完全没有任何代码的
    
    
    
    你需要使用命令来拉取子工程的代码
    
    git submodule update --init --recursive
    然而就算你拉取了代码下来，还是无法运行
    
    有可能会提示错误
    
    Plugins Suggestion
    Unknown features (Run Configuration[AndroidRunConfigurationType], Facet[android, android-gradle]) covered by disabled plugin detected. Enable plugins... Ignore Unknown Features
    这是因为android surport没有被勾选导致的，勾选一下重启AS就可以了
    
    方法：左上角File >> Setting >> Plugins >> 把Android Support勾选上，点击Apply，再点OK，会提示重启，重启完就好了。
    
    最终项目完成全部用子模块分层后
    
    
    
    
    
    四.注意事项
    
    1.如果你想要完全删除子模块
    
    你需要运行下面两句代码。
    
    git rm -r --cached 子模块名称
    rm -rf .git/modules/子模块名称
    如果你想完全删除，再重新拉取代码，一定要使用上面两句命令，不然他会拉取缓存中的内容。
    
    
    
    2.使用GitHub是没法提交子模块的，你子模块的代码，他会检测到很多子模块文件夹修改内容的，它会提示你只能使用Git shell命令来提交，然而提交的时候，会发现根本检测不到提交新的提交内容。
    
    
    
    这样如果你总工程是有很多分支的，例如我的Gank有kotlin，java，sub三个分支，我想切换分支，是无法使用GitHub按钮切换的。
    
    只能使用Git Bash命令行来做
    
    切换的命令
    
    git checkout 分支名字
    切换前一定要将其他额外的修改提交了，才能切换成功的。
    
    
    
    3.为何我不方便一点直接子项目，直接就是一个Android工程，而现在只是一个lib module的库呢？
    
    其根本是因为Git的机制。
    
    使用git submodule add 地址 的时候，其会检测一定是一整个项目，无法add指定的某个项目中指定的文件夹。
    
    Android studio 和git的相互制约，我们现在只能使用这样的机制开发。
    
    
    
    4.子模块中，如果引用的额外的xxx.gradle gradle.properties文件。
    
    （1）.代码需要手动提交到总工程
    
    （2）.再做一个子模块，然后让总工程中的引用到这个子模块中，其他子模块研发的时引用这个子模块，并且将这些配置文件全部引用这个子模块，那么修改的时候也可以同步。
    
    
    
    5.Git子模块的更深入的运用还是查看官网中的介绍（https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97）
    
    
    
    五.总结
    
    Android studio 和Git机制的限制，所以现在的开发框架，并非绝对的完善和最优。
    
    如果对Git 子模块更加深入的研究，和更好的部署实践，欢迎提出建议，会尽量完善这个组件化部署的简书文章。
    

    
    大致谈一下我们在使用 submodule 和 repo 的一些经验吧，我们本身工程模块并不多，遇到的任何问题放大到 Android 工程里，都会被成百倍上千倍的放大。微店工程结构改造历程虽然工程结构、版本控制只是日常开发非常小的一块内容，但是在一个现代的大型项目里，如果构建一个更高效地组织形式，是每一个团队都必须正视和解决的问题。从 16 年的四月份微店 Android 开始了平台化改造，为了配合平台化开发，微店的工程结构经历了多次大的调整。调整之后，稳定使用较长的有两个节点，第一次是全部模块插件化之后，工程结构由一个大的 Git 库改造成了 submodule 的形式；第二次是在使用了较长时间submodule 之后，遇到了不少问题，经过权衡，改为了 repo 的形式，一直用到现在，目前业务开发反馈良好。微店工程结构的特点微店工程插件化之后，工程结构呈现这样的形式：一个宿主 module，若干个子 module，最终打包的时候，需要先将子 module 打成一个二进制的文件，然后使用宿主 module 包裹子 module，将宿主 module 打成一个 APK，在运行的时候，动态地去读取二进制的子 module 文件。submodule—踩坑之旅通过对微店工程结构的描述，我们很容易想到使用 submodule 去管理微店工程。在 submodule 里，每个 module 都是一个 Git 库，各个 module 提交代码相互不干扰，同时一个主 module 管理若干个子 module，这样在同一个工程里，不同的 module 既是相互独立的，所有的 module 代码又可以存在同一个工程里。相互独立就意味着我们各个业务并行开发不受干扰，代码共存又让我们在调试的时候可以引用到其他 module 的代码。仿佛 submodule 就是为了并行开发量身定做的，于是我们花了很大力气将工程切到了 submodule 上，然而理想很美好，现实却是残酷的...在 submodule 的主工程里，每个 module 在 Git 库里的表现形式是这个 module 的 name 加上一串数字和字母，这串数字和字母代表的是 Git 提交记录，我们知道每次 Git 提交都会有一个 sha 记录值，这个 sha值记录了我们每一次的 Git 提交记录，通过它，我们可以进行克隆、回滚等操作。举个例子，小王和小刘同时开发 message 这个模块，当前在主 module 里记录的 message 模块的 sha 值是 fc0282f7，也就是message@fc0282f7 ，然后小王提交了代码，假设这次提交记录的sha 是 ab8762f0，这时候小王主 module 管理的 message 版本就是ab8762f0，但是主 module 的 remote 库里管理的 message 版本还是fc0282f7，因此为了保持同步，我们在提交了 message 模块的更新之后，必须要把自己主 module 里的这个更新的 sha 值也提交上去。如果小王忘了提交自己主 module 里的 sha 值，这时候小刘也提交了 message 模块的代码，这时候主 module 的 sha 值就会落后两个版本，这样问题就产生了，如果这时候再更新主 module 代码，这个主 module 的 sha 值就会产生冲突，无法更新、无法回滚、无法合并（Android 组同事印象应该会很深刻）。由此，可以看到，这些问题是由我们一些根深蒂固的使用习惯造成的，尤其是在多人开发的时候，很难要求每个人都对一个新的技能点能够完全掌握。而且，按照我们的初衷，业务开发只需要负责自己模块的代码就可以了，而 submodule 需要把所有模块的代码都下载到自己本地，并且显式地导入 IDE，这样 Gradle 的配置检查、同步以至于代码编译就会很耗时。在使用了近半年之后，这种状况依然没有任何好转，我们只好寻求更好的解决方案。当然，对于 submodule 的使用，如果能注意以下几点，也能用的很顺畅：最最重要的一个原则，也是使用 Git 最基本的一个原则：先更新再提交，先更新再提交，先更新再提交；尽量使用命令行终端，至少要学会基本的 Git 命令，不要太依赖 GUI 工具；在子 module 里 push 了代码之后，一定要提交主 module 里对应的 sha 值；在主 module 里 git pull 之后，一定要执行 git status，要确认 submodule 是否有修改，如有修改，需执行 git submodule update；git submodule update 并不会将子 module 切到任何一个分支，而是一个游离状态的 HEAD state（这一点跟 repo 类似，后面也会讲到），因此在做任何子 module 的操作之前，一定要确认子 module 已经在需要操作的分支上；假如说在游离的 HEAD state 下进行了代码修改，然后又提交了，这时候可以先切到需要提交的分支，然后再用 git cherry-pick xxx，再 push 即可；请尽量使用 git submodule foreach 'pwd && git pull'，这样的组合命令，单引号里的 git pull 可以换成其他的终端命令，而不仅仅是 git 命令（这也和 repo 里的类似）。repo—重新上路针对我们使用 submodule 过程中遇到的问题，我们希望能找到一种既能满足像 submodule 那样，各模块相互独立以便于开发，各模块的组织结构形式能方便调试，又能避免像 submodule 那样，模块提交代码对其他模块造成影响。于是我们又重新上路了。经过长时间的考察，我们发现 repo 正是这样一种方案。repo 引入了一个新角色，这个新角色来管理所有的 module，而不是像 submodule 那样，建立一种主从关系，用主 module 管理子 module。在 repo 里，所有 module 都是平级关系，每个 module 的版本管理完全独立于任何其他 module，不会像 submodule 那样，提交了子 module 代码，也会对主 module 造成影响。实际上，我们在使用过程中，还发现了另外一些好处：剥离了主 module 和子 module 的关系，检出、同步、提交等操作都比 sumodule 要快了好多倍；只需要检出需要开发的模块的代码，代码量减少了很多，正常情况下，本来要检出 30 多个模块代码，现在只需要一个模块代码，考虑到 Gradle 构建生命周期，整个构建时间在我们插件化改造之后又一次大大降低了；模块管理配置由一个陌生的 .gitmodules 变成了所有人都更熟悉的 xml 文件，便于配置管理。在 repo 真正的工程代码同一级，多出了一个 .repo 目录，默认情况下是隐藏目录，这里面存储了整个 repo 工程的信息。针对 repo，也有一些使用建议：最好新建一个空目录，在这个新建的空目录里检出整个 repo 工程，保证 repo 工程与其他目录隔离开来；正常情况下，我们没办法把 repo 的工程配置文件 default.xml 和软链接 manifest.xml 导入到 IDE 里，同步不同模块的代码就不太方便，可以新建一个 default.xml 的软链接放在代码工程里，这样就可以在 IDE 操作；默认情况下只保留必备的几个 git 库，开发需要哪个模块，就将哪个模块 git 库解开注释；请尽量使用 repo forall -c 'pwd && git pull' 这样的组合命令执行代码同步，这一点跟 submodule 类似；类似 submodule，使用 repo 把代码下载下来之后，每个 module 同样是一个游离的 HEAD state，需要手动切换到 master 分支（或需要操作的分支），执行 repo forall -c git checkout master 即可。当然，repo 也并不是就没有坑了，目前发现的主要有这样两点：明明状态已经改变了，但是使用 repo 命令查看，显示的还是原来的状态。进入到对应工程里，用 git 命令查看，就是正常的。repo down 下来代码，跟 submodule 一样，都是一个游离的 HEAD state，第一次切换到 master 分支，有可能并不能把所有项目都切到 master 分支，必须得再次 check，要不然就很有可能出问题。因此在做完一些 repo 操作之后，最好是再次使用 repo forall -c 'pwd && git branch' 类似的命令 check 一下。以后的工作在工程模块化的今天，虽然我们已经踩了很多坑，做了很多优化，现在也逐渐适应了 repo 的工作方式，但是还存在如下一些问题：一些先进的经验往往伴随着一些新技能的引入，如何让使团队里每个开发人员都尽快接受，这个是重中之重；因为权限的问题，我们有非常多的教训，如何对团队里每个人的代码的权限和模块发布权限进行控制，这一点需要不断的完善；非自己开发的模块，由源码依赖改为二进制包之后，如何保证调试效率，这是我们至今尚未完美解决的一个难题。接下来，我们还会对现有的不断地改进，以期能够达到对日常业务开发更加友好的状态。