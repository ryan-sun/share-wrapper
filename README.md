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
#
FixBugManage的使用
＃
首先，在自定义Application中初始化：
＃
init(versionCode)； 
＃
当versionCode与之前的versionCode不同，会自动清除掉之前addPatch所有的补丁文件 
＃
当versionCode与之前的versionCode相同，会自动加载之前addPatch所有的补丁文件
＃

package cn.coolspan.open.fixbug;

import android.app.Application;

public class MyApplication extends Application {

    public FixBugManage fixBugManage;

    @Override
    public void onCreate() {
        super.onCreate();
        this.fixBugManage = new FixBugManage(this);
        this.fixBugManage.init("1.0");
    }
}
＃
添加新补丁文件接口： 
＃
addPatch(patchPath)；
＃
在要使用的位置添加修复补丁文件的路径
MyApplication myApplication = (MyApplication) getApplication();

                File patch = new File(
                        Environment.getExternalStorageDirectory(), "patch.jar");
                myApplication.fixBugManage.addPatch(patch.getAbsolutePath());
＃
清除所有补丁文件的接口:
＃
removeAllPatch();


















