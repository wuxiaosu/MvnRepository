# MvnRepository
自己用github搭建的mvn仓库。

# 已有项目  
- [AMapLocation](https://github.com/wuxiaosu/AMapLocation)  
  高德定位的基础library（主要是用来做例子的）；  

---

# 附录 
## 如何引用此仓库内的代码  
配置仓库地址，在项目 **build.gradle** 文件中添加
```
repositories {
    maven {
        url 'https://raw.githubusercontent.com/wuxiaosu/MvnRepository/master'
    }
}
```
然后跟依赖其他仓库一样
```
dependencies {
    ...
    compile 'com.github.wuxiaosu:AMapLocation:0.1@aar'
}
```
## 如何添加项目到此仓库 
### 1.生成项目的.jar/.aar包
在项目目录下运行 **build** 命令（当然需要本机配置好Gradle环境）
```
gradle build
```
### 2.部署.jar/.aar文件到本地Maven仓库  
在.jar/.aar文件目录下运行命令,以  **AMapLocation-0.1.aar** 为例（当然需要本机配置好Maven环境）  
```
mvn install:install-file -Dfile=AMapLocation-0.1.aar  -DgroupId=com.github.wuxiaosu -DartifactId=AMapLocation -Dversion=0.1 -Dpackaging=aar
```  
### 3.将生成的文件提交到仓库
打开本机中的maven本地仓库 **.m2/repository** ，将整个文件目录上传到github，然后就可以在项目中使用此依赖了，目录结构应该是这样子的  
```
com/github/wuxiaosu
```  
# 其他  
两篇利用github搭建个人maven仓库的文章参考  
[利用github搭建个人maven仓库](http://blog.csdn.net/hengyunabc/article/details/47308913)  
[用GitHub构建个人Maven仓库](http://blog.csdn.net/xiaolyuh123/article/details/50358383)
