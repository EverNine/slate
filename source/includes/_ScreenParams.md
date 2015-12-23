# ScreenParams

### public class ScreenParams

定义了用于适配 Cardboard 设备的屏幕参数。

### Public Constructors

构造函数 |
-------- |
ScreenParams(Display display) |

### Public Methods

定义 | 函数名
---- | ------
static ScreenParams | creatFromInputStream(Display display, InputStream inputStream)
boolean | equals(Object other)
float | getBorderSizeMeters()
int | getHeight()
float | getHeightMeters()
int | getWidth()
float | getWidthMeters()
void | setBorderSizeMeters(float screenBorderSize)
void | setHeight(int height)
void | setWidth(int width)
String | toString()

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### ScreenParams (Display display) |

初始化参数的默认值。

## Public Methods

### public static ScreenParams creatFromInputStream (Display display, InputStream inputStream)

根据 `InputStream` 初始化屏幕参数。

调用者负责关闭流。

#### Parameters

参数名 | 描述
------ | -----
inputStream | 包含手机参数的输入流

#### Returns

* 一个新的 ScreenParams 对象，若发生错误返回 `null`
