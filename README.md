# AndroidCodingStandard

我们在平时编程过程中，并没有对程序中代码进行规范化，对资源规范化。所以我们在此简单的说明一下我们在开发过程的一些规范。希望对大家有用。

### 1. 介绍

首先这篇文档仅供大家参考，并不是Android绝对的规范，有问题大家可以指出。

### 2. Android Studio的标准配置

    我们首先配置我们心爱的开发工具，然后才可以进行我们正常的开发。
   
#### 2.1 Android 环境的配置

##### 2.1.1 Android Studio
(1)下载Android Studio，http://developer.android.com/sdk/index.html

(2)第一次打开Android Studio，点击右下角`Configure - > Project Defaults - > Project Structure`进行SDK和jdk的配置

(3)然后你可以点击Start a new Android Studio project

##### 2.1.2 Git
(1)下载安装，https://git-scm.com/downloads

(2)配置，http://blog.csdn.net/gao_chun/article/details/49817229/

##### 2.1.3 Java
(1)下载安装，http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

(2)在`File - > Project Structure`可以看到配置jdk的路径

##### 2.1.4 Gradle
(1)下载安装，https://www.gradle.org/downloads

(2)然后在Android Studio中project目录下的build.gradle中配置如下
```
dependencies {
        classpath 'com.android.tools.build:gradle:3.0.0'
        ...
}
```

##### 2.1.5 Android SDK
(1)下载安装，http://developer.android.com/sdk/index.html

#### 2.2 Android Studio简单设置

1. Android尽量使用最稳定的版本

2. 编码格式统一为UTF-8(`File - > Settings - > Editor - >F ile Encodings`,然后选择`IDE Encoding`和`Project Encoding`设置为UTF-8,然后在最下面`Default encoding for proterties files`也设置为UTF-8，完成)

3. 显示行号，`File - > Settings –> Editor –> Appearance` ，勾选 `Show line numbers` 。

4. 自动导包，默认的Android Studio不会自动导入这段代码中使用到的类的引用 ，可以如下设置：`Settings –> Editor –> Auto Import`
        
5. 设置自定义注释模板，点击`File - > Settings - > File and Code Templates - > Includes   - > File Header`,然后你可以自己定义了，最后新建一个java类就可以看到了

6. 代码写完需要进行格式化代码处理，( <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>L</kbd>, <kbd>OPTION </kbd> + <kbd>CMD</kbd> + <kbd>L</kbd>)

7. 一些常用的Android开发工具可以参考：[Android 开发工具](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2017/0526/7973.html)

### 3. Android命名规范
- 【强制】代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。

     反例：_name / __name / $name / name_ / name$ / name__
- 【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。
说明：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式
也要避免采用。

    正例：alibaba / taobao / youku / hangzhou 等国际通用的名称，可视同英文。
    
    反例：DaZhePromotion [打折] / getPingfenByName() [评分] / int 某变量 = 3

#### 3.1 包命名
包名全部小写，点分隔符之间有且仅有一个自然语义的英语单词，不使用下划线。包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。
采用反域名命名规则，全部使用小写字母。一级包名为com，二级包名为xx（可以是公司或则个人的随便），三级包名根据应用进行命名，四级包名为模块名或层级名。

例如：com.alibaba.test

| 包名                               | 此包中包含           |
| ---------------------------     |:-------------:      |
|com.xx.应用名称缩写.activity        |页面用到的Activity类 (activitie层级名用户界面层) | 
|com.xx.应用名称缩写.base            |基础共享的类 | 
|com.xx.应用名称缩写.adapter         |页面用到的Adapter类 (适配器的类) | 
|com.xx.应用名称缩写.util            |此包中包含：公共工具方法类（util模块名） | 
|com.xx.应用名称缩写.bean             |下面可分：vo、po、dto 此包中包含：JavaBean类 | 
|com.xx.应用名称缩写.model           |此包中包含：模型类 | 
|com.xx.应用名称缩写.db              |数据库操作类 | 
|com.xx.应用名称缩写.view (或者 com.xx.应用名称缩写.widget )      |自定义的View类等 | 
|com.xx.应用名称缩写.service         |Service服务 | 
|com.xx.应用名称缩写.receiver        |BroadcastReceiver广播 | 

>注意：
 如果项目采用MVP，所有M、V、P抽取出来的接口都放置在相应模块的I包下，所有的实现都放置在相应模块的impl下

#### 3.2 类命名

- 类名、接口名、枚举名等首字母大写，若由多个单词组成，则其后每个单词首字母大写，简明扼要，见名知意原则；

    正例：
    ```
    class ActivityManager{}
    ```
    反例：
     ```
     class activityManager{}
     ```

> 具体事例

| 类                 | 具体描述                       |              例如             |
| ------------------|:-------------:              |:---------------------------:|
|Activity 类	|     Activity为后缀标识              |欢迎页面类WelcomeActivity|
|Adapter类	         |Adapter 为后缀标识	          |新闻详情适配器 NewDetailAdapter|
|adapter中的ViewHolder类|以Holder为后缀标识          |新闻详情holder类NewDetailHolder|
|解析类	             |Parser为后缀标识	              |首页解析类HomePosterParser|
|工具方法类	         |Util或Manager为后缀标识（与系统或第三方的Utils区分）或功能+Util	|线程池管理类：ThreadPoolManager <p> 日志工具类：LogUtil（Logger也可）<p> 打印工具类：PrinterUtil|
|数据库类	         |以DBHelper后缀标识	         |新闻数据库：NewDBHelper|
|Service类	        | 以Service为后缀标识	        |时间服务TimeService|
|Receiver类	        |以Receiver为后缀标识	         |推送接收JPushReceiver|
|ContentProvider	|以Provider为后缀标识	        |手机联系人PhoneContactsProvider |
|自定义的共享基础类	|以Base开头	                    |BaseActivity,BaseFragment|
|Application类      |以Application为后缀标识        |正常MyApplication|
|自定义View类      | 以Custom + 功能或者View为后缀标识|标题栏TitleBarView|
|实体类           | 以Bean、Model、Entity为后缀标识   | TimeEntity,TimeBean,TimeModel|

 - 抽象类命名使用 Abstract 或 Base 开头；异常类命名使用 Exception 结尾；测试类
  命名以它要测试的类名开始，以 Test 结尾,如MainTest.
 - 接口（interface）：命名规则与类一样采用大驼峰命名法，多以 able 或 ible 结尾，如 interface Runnable、interface Accessible。
>注意：
如果项目采用MVP，所有Model、View、Presenter的接口都以I为前缀，不加后缀，其他的接口采用上述命名规则。

#### 3.3 方法命名
方法名使用 lowerCamelCase 风格，必须遵从驼峰形式。方法名通常是动词或动词短语。

| 方法                          | 说明                                       |
| :-------------------------- | ---------------------------------------- |
| `initXX()`                  | 初始化相关方法，使用 init 为前缀标识，如初始化布局 `initView()` |
| `isXX()`, `checkXX()`       | 方法返回值为 boolean 型的请使用 is/check 为前缀标识      |
| `getXX()`                   | 返回某个值的方法，使用 get 为前缀标识                    |
| `setXX()`                   | 设置某个属性值 ,使用 set为前缀标识           |
| `handleXX()`, `processXX()` | 对数据进行处理的方法                               |
| `displayXX()`, `showXX()`   | 弹出提示框和提示信息，使用 display/show 为前缀标识         |
| `updateXX()`                | 更新数据                                     |
| `saveXX()`, `insertXX()`    | 保存或插入数据                                  |
| `resetXX()`                 | 重置数据                                     |
| `clearXX()`                 | 清除数据                                     |
| `removeXX()`, `deleteXX()`  | 移除数据或者视图等，如 `removeView()`               |
| `drawXX()`                  | 绘制数据或效果相关的，使用 draw 前缀标识                  |
| `createXX()`               | 创建数据，使用create前缀标识                  |
| `onXX()`                   | 在某某动作的过程中，使用on前缀标识 ,如`onCreate()`(在页面创建的时候)                 |

下划线可能出现在JUnit测试方法名称中用以分隔名称的逻辑组件。一个典型的模式是：test_，例如testPop_emptyStack。
并不存在唯一正确的方式来命名测试方法。

#### 3.4 常量命名

常量名命名模式为`CONSTANT_CASE`，全部字母大写，用下划线分隔单词。力求语义表达完整清楚，不要嫌名字长。那，到底什么算是一个常量？
每个常量都是一个静态`final`字段，但不是所有静态`final`字段都是常量。在决定一个字段是否是一个常量时，考虑它是否真的感觉像是一个常量。
例如，如果任何一个该实例的观测状态是可变的，则它几乎肯定不会是一个常量。只是永远不打算改变对象一般是不够的，它要真的一直不变才能将它示为常量。

```
// Constants
static final int NUMBER = 5;
static final ImmutableListNAMES = ImmutableList.of("Ed", "Ann");
static final Joiner COMMA_JOINER = Joiner.on(','); // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};
enum SomeEnum { ENUM_CONSTANT }
// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final SetmutableCollection = new HashSet();
static final ImmutableSetmutableElements = ImmutableSet.of(mutable);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = {"these", "can", "change"};

```

#### 3.4 非常量命名

非常量字段名以`LowerCamelCase`风格的基础上改造为如下风格：
基本结构为`scopeVariableNameType`，

#### 3.4.1 scope：范围
非公有，非静态字段命名以m(member)开头。
静态字段命名以s(static)开头。
公有非静态字段命名以p(private)开头。
公有静态字段（全局变量）命名以g(global)开头。
`public static final` 字段(常量) 全部大写，并用下划线连起来。
例子：
````
 public class MyClass {  
        public static final int SOME_CONSTANT = 42;  
        public int pField;  
        private static MyClass sSingleton;  
        int mPackagePrivate;  
        private int mPrivate;  
        protected int mProtected; 
        public static int gField; 
  }
````
使用1个字符前缀来表示作用范围，1个字符的前缀必须小写，前缀后面是由表意性强的一个单词或多个单词组成的名字，而且每个单词的首写字母大写，其它字母小写，这样保证了对变量名能够进行正确的断句。

#### 3.4.1 Type：类型
考虑到Android中使用很多UI控件，为避免控件和普通成员变量混淆以及更好达意，所有用来表示控件的成员变量统一加上控件缩写作为后缀（文末附有缩写表）。
对于普通变量一般不添加类型后缀，如果统一添加类型后缀，请参考文末的缩写表。
用统一的量词通过在结尾处放置一个量词，就可创建更加统一的变量，它们更容易理解，也更容易搜索。

>注意：如果项目中使用`ButterKnife`，则不添加m前缀，以`LowerCamelCase`风格命名。

例如，请使用 `mCustomerStrFirst` 和 `mCustomerStrLast`，而不要使用`mFirstCustomerStr`和`mLastCustomerStr`。

| 量词列表    | 量词后缀说明     |
| -------    |:------------------:|
| First       | 一组变量中的第一个  |
| Last        | 一组变量中的最后一个 |
| Next        | 一组变量中的下一个  |
| Pre         | 一组变量中的上一个  |
| Cur         | 一组变量中的当前变量 |

说明：
集合添加如下后缀：`List`、`Map`、`Set`
数组添加如下后缀：`Arr`

>注意：所有的VO（Value Object值对象）统一采用标准的`lowerCamelCase`风格编写，所有的DTO（Data Transfer Object数据传输对象）就按照接口文档中定义的字段名编写。

#### 3.6 参数名
参数名以`LowerCamelCase`风格编写

#### 3.7 局部变量名
局部变量名以`LowerCamelCase`风格编写，比起其它类型的名称，局部变量名可以有更为宽松的缩写。
虽然缩写更宽松，但还是要避免用单字符进行命名，除了临时变量和循环变量。
即使局部变量是final和不可改变的，也不应该把它示为常量，自然也不能用常量的规则去命名它。
临时变量
临时变量通常被取名为i，j，k，m和n，它们一般用于整型；c，d，e，它们一般用于字符型。 如： 
`for (int i = 0; i < len ; i++)`，并且它和第一个单词间没有空格。

#### 3.8 类型变量名
类型变量可用以下两种风格之一进行命名：

单个的大写字母，后面可以跟一个数字(如：E,T,X,T2)。
以类命名方式(3.2节)，后面加个大写的T(如：`RequestT`,`FooBarT`)。

#### 3.9 构造方法命名

构造方法的命名规则和类名的命名规则一致
采用递增方式（参数多的写在后面）
例如：
```
public class AdressEntity {
        public AdressEntity(String message) {
            this.message = message;
        }

        public AdressEntity(String timestamp, String message) {
            this.timestamp = timestamp;
            this.message = message;
        }
}
```

### 4.资源文件规范

在资源文件res文件夹中有很多资源，有`Animation Resources`、`Color State List Resource`、`Drawable Resources`、`Layout Resource`、`Menu Resource`、`String Resources`、`Style Resource`、`Font Resources`等相关资源。

