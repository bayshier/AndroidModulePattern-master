
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