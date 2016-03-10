# share-wrapper
#
用来作为封装的jar包所支持的maven仓库
#
把jar文件转换成dex文件
#
dx --dex --output patch.jar fixbug.jar
#
异常：bad class file magic (cafebabe) or version (0033.0000) 
#
解决方法：在build.gradle中jdk的版本修改为1.6
#
compileOptions {

        sourceCompatibility JavaVersion.VERSION_1_6
        targetCompatibility JavaVersion.VERSION_1_6
        
    }
