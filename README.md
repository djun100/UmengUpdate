# UmengUpdate
base on umeng-update-v2.6.0.1.jar

usage

 1、添加APPKEY和渠道到<application>标签下： 

    <meta-data android:value="YOUR APP KEY" android:name="UMENG_APPKEY"/>
    <meta-data android:value="Channel ID" android:name="UMENG_CHANNEL"/>
UMENG_APPKEY：用来定位该应用的唯一性，用您该应用的UMENG APPKEY，替换value中的"YOUR APP KEY"。
UMENG_CHANNEL：用来标注应用推广渠道，不同渠道可以上传不同更新包，您可以使用20位以内的英文和数字为渠道定名，替换value中的"Channel ID"。如果不改动，将代表默认渠道。（特别提示：如果需要使用友盟自动更新多渠道更新，必须先集成友盟统计SDK）

2、调用更新接口

主要应用场景：最常见的自动更新模式，当用户进入应用首页后，如果处于wifi环境则检测更新，如果有更新，弹出对话框提示有新版本，用户点选更新开始下载更新。
在应用程序入口Activity里的OnCreate() 方法中调用

    public void onCreate(Bundle  savedInstanceState) {
    super.onCreate(savedInstanceState);
    UmengUpdateAgent.update(this);


注意

考虑到用户流量的限制，目前我们默认在Wi-Fi接入情况下才进行自动提醒。如需要在任意网络环境下都进行更新自动提醒，则请在update调用之前添加以下代码：UmengUpdateAgent.setUpdateOnlyWifi(false)。 特别提示：针对机顶盒等可能不支持或者没有无线网络的设备， 请同样添加上述代码。
API：
public static void update(Context context)

v2.4版本之后的SDK中，您可以传入当前Activity的Context，也可以传入Application的Context。
引用

      repositories {
        // ...
        maven { url "https://jitpack.io" }
    }

    compile 'com.github.djun100:UmengUpdate:81d4b7126cd19260bf13a30ac80b6eba6de83e5e'