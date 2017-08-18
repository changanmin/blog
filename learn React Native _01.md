### React Native 本地环境搭建
> 本文为React Native 在windows和mac平台下的搭建方法 和第一次运行 

1. 安装node.js([node.js](https://nodejs.org/en/download/)) .node 版本要在4或更新的版本  
2. 安装jdk([jdk](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)) .jdk版本要在8或更高  
3. >执行下面的两条命令，使用管理员权限  （甭问为什么，just do it ）  
    > npm install -g yarn       //使用yarn 构建速度更快点  
    yarn global add react-native-cli   //安装react-native-cli  

4. window平台用户下载android studio(就因为你用的不是mac，所以你只有选择android studio )，装这个软件是使用Android SDK 来生成一个AVD (android virtual device)or adb tools.有没有windows平台下的ios虚拟机，不知道，我也不知道，没找到过,但是react native 搞出来一个云一样的应用，同时可以在android 和ios设备上预览，也就是不需要mac 你可以也可以开发 ios 和android 的应用，这个暂且不提。下载
（[android studio](https://developer.android.com/studio/index.html)）  
    1. android studio 下载后默认是安装最新的android sdk,但是牛逼的react native 需要 android 6.0(Marshmallow)版本的SDK.所以呢：我们这些叼毛程序员就要去android studio中的sdk manager中安装 6.0 的 android sdk.(木办法，谁知道？我才不会去深究，爱咋咋地)
    2. 怎么装android sdk 6.0 ? 装那些? 看下边的美图
    ![android studio 启动页](https://facebook.github.io/react-native/img/AndroidStudioWelcomeWindows.png)
    步骤一: 启动android studio后，在这个页面点击右下角的configure,然后选择 SDK Manager.(当然还有其他方法，估计不说你知道)  
    步骤二: 在SDKManager 弹出的界面中 ,选中 ”SDK Platforms“ 选项卡，然后呢，选中右下角 ”Show Package Details“ 这个复选框。 你就可以看到的Android 6.0 （Marshmallow），展开这个鬼树，根据下图来选则相应的项目。选完后 别急保存，继续步骤三。
     ![SDK Manager](https://facebook.github.io/react-native/img/AndroidSDKManagerWindows.png)  
    步骤三: 在SDKManager 弹出的界面中,选中 ”SDK Tools“ 选项卡。在这个卡页中 ，选择下图中的23.0.1 
    ![SDK Manager for SDK Tools](https://facebook.github.io/react-native/img/AndroidSDKManagerSDKToolsWindows.png)
    点击 ”Apply“ 下载并安装android sdk和相关的工具。 

        

        开始的时候 我们下载了 react-native-cli ，这个东东 就是生成RN（react-native）项目的,具体命令行：  
            > react-native init AwesomeProject

        项目生成后，要运行看下（小激动）：两种方法，

        1. 使用物理设备（就是你的android手机）
            1. 打开USB调试
            2. 插入设备
            3. adb devices //可以查看连接上的设备
            4. cd AwesomeProject //进入到项目文件夹下
            5. react-native run-android //通过react-native 运行刚才生成的项目
        2. 虚拟机(android virtual device)
            1. 在Android studio 中打开AVD管理器，查看可用的虚拟设备列表。
            2. 如果你刚安装android 则需要创建一个新的AVD,选择移动设备，点击下一步。
            ![AVD Create](https://facebook.github.io/react-native/img/CreateAVDWindows.png)    
            3. 选择”x86 Images“选项卡，在卡页内找到 Target列为android 6.0(Google Api)，Name 为Marshmallow ,API 为level 23 ，x86_64 ABI 的镜像。
            ![AVD Create 02](https://facebook.github.io/react-native/img/CreateAVDx86Windows.png)
            "如果没有安装HAXM 请点击”install Haxm“,完事后，点击下一步，点击”Finish“ 完成AVD的创建。此时 你可以点击AVD旁边的绿色三角形启动这个虚拟机。
            4. 运行刚才生成的项目 
                > cd AwesomeProject  //进入这个目录  
                react-native run-android //运行android 

        佛祖保佑，一切正常，你将会在你的设备上或者虚拟机上看到第一次运行的画面。

    你已经成功运行了应用程序，可以尝试修改 index.android.js中的文本。
    然后按两次R键，或者通过开发菜单的Reload 看到修改后的变化。
5. mac平台 肯定需要 xcode 程序啦。
    1. 打开Xcode 在Xcode 菜单中选择Preferences
    2. 选择locations 卡页，在卡页里找到Command Line Tools:选择最新的版本
    ![xcode](https://facebook.github.io/react-native/img/XcodeCommandLineTools.png)  
    3. > react-native init AwesomeProject //生成项目  
    cd AwesomeProject     //进入项目  
    react-native run-ios // 运行项目

