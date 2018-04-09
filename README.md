# FirstCode
郭神的《第一行代码》（第二版）个笔记
## 第1章 开始启程---你的第一行Android代码
对应的项目demo为[HelloWorld](./HelloWorld)
 - 分析了目录结构，如何使用`Android Studio`创建第一个项目。
 - `AndroidManifest.xml`是整个项目的配置文件，四大组件都需要在这里注册，还可以添加权限声明。这个文件以后会经常用到
 - Android程序的设计讲究逻辑与视图分离，布局文件在res/layout目录下,逻辑在java中的活动中。（感觉这个有点像前端的html和js分离）
 - 日志打印：`Log.v()`、`Log.d()`、`Log.i()`、`Log.w()`、`Log.e()`，第一个参数tag可以在方法外输入`logt`，自动生成一个TAG常量。不用`System.out`。日志可以添加过滤器
 - control+R：运行项目
## 第2章 先从看得到的入手---探究活动
对应的项目demo为[ActvityTest](./ActvityTest)和[ActivityLifeCycleTest](./ActivityLifeCycleTest)
- `android:id`给当前元素定义一个唯一标识符，之后就可以对他进行操作了（类似前端的id），语法为：`@+id:id_name`。`match_parent`表示当前元素和父元素一样宽，`wrap_content`表示当前元素的高度刚好能包含里面的内容（类似于前端的标签）
- 在`AndroidManifest.xml`中加入<intent-filter>T标签，并且在这个标签里面添加`<action android:name="android.intent.action.MAIN"/>`和 `<category android:name="android.intent.category.LAUNCHER"/>`来配置主活动。
- `findViewById()`获取布局文件中定义的元素，`setOnClickListener()`注册监听器，监听`onClick()`方法。
- ` Toast.makeText(FirstActivity.this, "You clicked Button 1", Toast.LENGTH_SHORT).show();`
- 重写方法快捷键：`control+O`
- 在活动中使用Menu（右上角三个点），个人感觉这个功能有点鸡肋，应该用不到吧。。
- 销毁活动：`finish()`，效果和按下back键一样。
- Intent：活动之间的桥梁，用于跳转界面。和iOS 有点不一样。显式Intent：`Intent intent = new Intent(FirstActivity.this, SecondActivity.class);`。启动一个Intent:`                startActivity(intent);`。隐式Intent：在`AndroidManifest.xml`中配置action和category。还可以调起浏览器，显示地理位置，拨打电话等
- 活动之间传递数据：`putExtra()`，key-value的形式。去出去取数据：`getStringExtra()`
- 返回数据给上一个活动`startActivityForResult()`，接收数据也还要重写`onActivityResult()`这个方法。假如是点击back返回，那么重写`onBackPressed()`方法
- 活动的生命周期:`onCreate()`、`onStart()`、`onResume()`、`onPause()`、`onStop()`、`onDestroy()`、`onRestart()`
- 活动回收时防止丢失数据`onSaveInstanceState()`
- 活动的启动模式：`standard(默认)`、`singleTop`、`singleTask`、`singleInstance`。通过修改`AndroidManifest.xml`中的`android:launchMode`属性选择启动模式
- 小技巧：
  - 打印当前界面是哪一个活动：创建一个基类:BaseActivity，继承AppCompatActivity,重写onCreate()方法，打印`Log.d(TAG, getClass().getSimpleName());`然后让其他类都继承这个类
  - 随时随地退出程序：用一个集合类来处理（ActivityCollector），配合BaseActivity使用
  - 杀掉当前进程：`android.os.Process.killProcess(android.os.Process.myPid())`
  - 启动活动的最佳写法：在后一个活动中国年暴露一个方法，这样写比较规范，提高效率

## 第3章 软件也要拼脸蛋---UI开发的点点滴滴
对应的项目demo为[UIWidgeTest](./UIWidgeTest)、[UILayoutTest](./UILayoutTest)、[UICustomViews](./UICustomViews)、[ListViewTest](./ListViewTest)、[RecyclerViewTest](./RecyclerViewTest)、[UIBestPractice](./UIBestPractice)
- TextView:`match_parent`表示让当前控件的大小和父布局的大小一样，也就是由父布局来决定当前控件的大小。`wrap_content`表示让当前控件的大小能够刚好包含住里面的内容，也就是由控件内容决定当前控件的大小
- Button:默认英文转大写，`android:textAllCaps="false""`禁用这个特性
- EditText:`android:hint`=placeholder,`android:maxLines`=最大行数
- ImageView:`android:src`指定图片
- ProgressBar:`visible`、`invisible`、`gone`
- AlertDialog:AlertDialog.Builder
- ProgressDialog:`setCancelable()`
- 4种布局
    - 线性布局LinearLayout
    - 相对布局RelativeLayout
    - 帧布局FrameLayout
    - 百分比布局PercentFrameLayout、PercentRelativeLayout
- 引入布局`<include layout="@layout/name" />`
- ListView和RecyclerView
- 
## 第4章 手机平板要兼顾---探究碎片


