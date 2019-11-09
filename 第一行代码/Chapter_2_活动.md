# 活动

## 活动是什么

+ 活动（Activity）：是一种可以包含用户界面的组件，是要用于和用户交互

### 在AndroidManifest.xml文件中注册

+ 在程序中定义的四大组件，都需要在这个文件中注册
+ 还可以在这个文件中给应用程序 **添加权限声明**
+ 所有的活动都要在`AndroidManifest.xml`中注册才能生效
+ 在`<activity>`标签中使用`android:name`来指明具体注册哪一个活动
+ `<action android:name="android.intent.action.MAIN"/>`和`<category android:name="android.intent.category.LAUNCHER"/>`当前的Activity是这个项目的主活动，在手机上点击图标是，首先出现的就是这个活动
+ `android:label`指定活动中标题栏的内容，其内容也会称为启动器（launcher）中应用程序显示的名称

### 在活动中使用Toast

+ 在程序中可以用来将一些短小的信息通知给用户，这些信息会在一段时间后自动消失
+ 通过静态方法`Toast.makeText()`创建一个Toast对象，调用`show()`将Toast显示出来：
    1. 第一个参数`Context`：Toast要求的上下文，且活动Activity本身就是一个Context对象
    2. 第二个参数：显示Toast的内容
    3. 第三个参数：显示Toast的显示时长

### 在活动中使用Menu

+ 在res目录下新建一个menu文件夹，接着在文件夹下面新建一个main的菜单文件（创建的文件名称为`main.xml`）
+ 在`MainActivity.java`中重写方法：
    1. `onCreateOptionsMenu()`
    2. `onOptionsItemSelected()`
+ 运行结果是在标题栏处会出现三个竖列的点，是菜单栏选项

### 销毁一个活动

+ 使用Activity类提供的`finish()`方法，销毁活动

## 使用Intent在活动之间切换

+ Intent是Android程序中各组件之间交互的一种方式
+ Intent一般用于启动活动、启动服务以及发送广播等场景

### 使用显示Intent

+ 使用Intent一个构造函数`Intent(Context packageContext, Class<?> cls)`：第一个参数是启动活动的上下文，第二个参数Class指定想要启动的目标活动
+ 调用Activity的`startActivity()`方法，传入Intent对象，以启动活动

### 使用隐式Intent

+ 调用系统浏览器来打开网页：

    ```java
    Intent intent = new Intent(Intent.ACTION_VIEW);
    intent.setData(Uri.parse("https://www.youtube.com"));
    startActivity(intent);
    ```

    `ACTION_VIEW`是Android系统内置的动作</br>
    `Uri.parse()`方法，将一个网址字符串解析成一个Uri对象
+ 与此对应，可以在`<intent-filter>`标签中配置一个`<data>`标签，用于更精确地指定当前活动能够相应什么类型地数据：配置内容如下：
    1. `android:schema`：指定数据的协议
    2. `android:host`：指定数据的主机名
    3. `android:port`：指定数据的端口
    4. `android:path`：指定主机名和端口之后的部分，如一段网址中跟在域名之后的内容
    5. `android:mimeType`：指定处理的数据类型，允许使用通配符

### 向下一个活动传递数据

+ Intent提供的`putExtra()`方法，可以将想要传递的数据暂存在Intent中，启动另一个活动后，再取出

### 返回数据给上一个活动

+ `startActivityForResult()`方法，接受两个参数，第一个是Intent，第二个是请求码，用于在之后的回调中判断数据的来源

## 活动的生命周期
