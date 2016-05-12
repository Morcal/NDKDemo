# NDKDemo  
Android Studio编写NDK  
## step1  
在AS下配置Android NDK的本地目录  
## step2  
在src下创建一个java类并创建本地native方法  
## step3  
编译应用，使其在\build目录下生成一系列包，命令进入到\build\intermediates\classes\debug，用javah命令对包含native方法的类生成头文件，javah -jni com.moyu.lyqdhgo.myapplication.Test  
## step4  
在src/main下创建jni目录，右键new->folder-JNIFolder  
## step5  
将javah生成的头文件复制到jni目录下  
## step6  
在jni目录下创建执行操作的.c文件，引入头文件，并实现头文件中的方法  
## step7  
配置module下的bulid.gradle文件,s使其生成不同平台下的.so文件;一下代码要配置在defaultConfig {}里
```
        ndk{
            //模块名，该模块名要与测试类中加载library
            moduleName 'test'
            //目标平台
            abiFilters 'armeabi','armeabi-v7a'
            //链接库文件
            ldLibs 'log'
        }
```  
## step8  
配置项目的gradle.properties下添加  
> android.useDeprecatedNdk=true  
## step9  
在测试类中加载ndk模块,此处的名称一定要与  bulid.gradle中的ndk中的modleName一致  
```
static {
        System.loadLibrary("YanboberJniLibName");	//defaultConfig.ndk.moduleName
    }
```  
## step10  
在Activity中运native方法，创建测试类对象调用native方法  










