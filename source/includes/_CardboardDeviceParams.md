# CardboardDeviceParams

### public class CardboardDeviceParams

定义与 Cardboard 适配设备的物理参数。

该模型假设适配设备：

1. 镜头与设备平行
2. 每个镜头的中心在同一高度（以设备底部为计算基准）
3. 镜头关于设备的中心对称
4. 每个镜头中心的可视区域大小相等

这些参数对于不同的镜头与设备而言都有可能是不同的，为方便起见，可以将这些参数存储在 Cardboard 的 NFC 标签中。

### Nested Classes

定义 | 类名 | 描述
---- | ---- | ----
enum | [CardboardDeviceParams.VerticalAlignmentType]() | 用于指示根据镜头中心的垂直排版方案的枚举

### Public Constructors

构造函数 |
-------- |
CardboardDeviceParams() |
CardboardDeviceParams(CardboardDeviceParams params) |

### Public Methods

定义 | 函数名
---- | ------
static CardboardDeviceParams | createFromInputStream(InputStream inputStream)
static CardboardDeviceParams | createFromNfcContents(NdefMessage tagContents)
static CardboardDeviceParams | createFromUri(Uri uri)
boolean | equals(Object other)
Distortion | getDistortion()
boolean | getHasMagnet()
float | getInterLensDistance()
FieldOfView | getLeftEyeMaxFov()
String | getModel()
float | getScreenToLensDtance()
String | getVendor()
CardboardDeviceParams.VerticalAlignmentType | getVerticalAlignment()
float | getVerticalDistanceToLensCenter()
static boolean | isCardboardUri(Uri uri)
boolean | isDefault()
void | setHasMagnet(boolean magnet)
void | setInterLensDistance(float interLensDistance)
void | setModel(String model)
void | setScreenToLensDistance(float screenToLensDistance)
void | setVendor(String vendor)    
void | setVerticalAlignment(CardboardDeviceParams.VerticalAlignmentType vertiaclAlignment)
void | setVerticalDistanceToLensCenter(float verticalDistanceToLensCenter)    
String | toString()
Uri | toUri()
boolean | writeToOutputStream(OutputStream outputStream)

### Inherited Methods

* From class java.lang.Object

## Public Constructors

### public CardboardDeviceParams ()

使用默认的 Cardboard v1.0.0 的参数对设备进行初始化。

可以使用 [`HeadMountedDisplayManager`]() 来访问 Cardboard 设备参数为听筒进行优化。

### public CardboardDeviceParams (CardboardDeviceParams params)

为已有的设备参数创建一份拷贝。

#### Parameters

参数名 | 描述
------ | ----
params | 要拷贝的设备参数

## Public methods

### public static CardboardDeviceParams createFromInputStream (InputStream inputStream)

从 `InputStream` 中初始化 Cardboard 设备参数，调用者负责关闭流。

#### Parameters

参数名 | 描述
------ | ----
inputStream | 包含设备参数的输入流

#### Returns

* 一个新的设备参数对象，发生错误时返回 `null`

### public static CardboardDeviceParams createFromNfcContents (NdefMessage tagContents)

根据 NFC 标签中的内容初始化设备参数

#### Parameters

参数名 | 描述
------ | ----
inputStream | 包含设备参数的输入流

#### Returns

* 一个新的设备参数对象，发生错误时返回 `null`

### public static CardboardDeviceParams createFromUri (Uri uri)

从 Uri 初始化设备参数。

#### Parameters

参数名 | 描述
------ | ----
uri | 用于读取设备参数的 uri

#### Returns

* 一个新的设备参数对象，发生错误时返回 `null`

### public boolean equals (Object other)

比较当前实例与指定对象是否相同。

#### Parameters

参数名 | 描述
------ | ----
other | 要与当前实例进行比较的对象

#### Returns

* 若两个对象相同则返回 `true`，否则返回 `fasle`

### public Distortion getDistortion()

返回镜头失真模型。

#### Returns

* 镜头失真模型。

### public boolean getHasMagnet()

返回 Cardboard 设备是否有磁铁。

#### Returns

* 若有磁铁返回 `true`，否则返回 `false`

### public float getInterLensDistance ()

返回设备镜头间距。

#### Returns

* 单位为米的镜头间距

### public FieldOfView getLeftEyeMaxFov ()

返回左眼通过镜头的最大可视区域，实际的渲染区域大小将会根据该区域大小以及屏幕大小决定。渲染时，一个同样的大小的区域会被应用于右眼。

#### Returns

* 左眼的最大可视区域

### public String getModel ()

返回表示设备模型的字符串。

#### Returns

* 一串用于表示设备模型的字符串

### public float getScreenToLensDistance ()

返回以米为单位的屏幕到镜头的距离

#### Returns

* 以米为单位的屏幕到镜头的距离

### public String getVendor ()

返回表示设备供应商的字符串

#### Returns

* 一串用于表示设备供应商的字符串

### public CardboardDeviceParams.VerticalAlignmentType getVerticalAlignment ()

获得垂直排版方案。

### public float getVerticalDistanceToLensCenter ()

返回设备到镜头中心的垂直距离。

#### Returns

* 镜头中心到设备底部或顶部边缘的垂直距离，单位为米

### public static boolean isCardboardUri (Uri uri)

若可根据给定的 uri 确定一个 Cardboard 设备则返回 `true`

### public boolean isDefault ()

### public void setHasMagnet (booolean magnet)

设置该 Cardboard 设备是否有磁铁。

### public void setInterLensDistance (float interLensDistance)

设置设备的镜头间距。

#### Parameters

参数名 | 描述
------ | ----
interLensDistance | 以米为单位的两个镜头中心的距离

### public void setModel (String model)

设置表示设备模型的字符串。

#### Parameters

参数名 | 描述
------ | ----
model | 要设置的表示设备模型的字符串

### public void setScreenToLensDistance (float screenToLensDistance)

设置屏幕到镜头光学中心的距离。

该值影响了渲染时的缩放比例。

#### Parameters

参数名 | 描述
------ | ----
screenToLensDistance | 以米为单位的屏幕到镜头的距离

### public void setVendor (String vendor)

设置表示设备供应商的字符串

#### Parameters

参数名 | 描述
------ | ----
vendor | 要设置的表示设备供应商的字符串

### public void setVerticalAlignment (CardboardDeviceParams.VerticalAlignmentType vertiaclAlignment)

设置垂直排版方案。

### public void setVerticalDistanceToLensCenter (float verticalDistanceToLensCenter)

设置到镜头中心的垂直距离。

#### Parameters

参数名 | 描述
------ | ----
verticalDistanceToLensCenter | 要设置的设备顶部或底部到镜头中心的垂直距离，以米为单位

### public String toString ()

返回一串简明、可读的关于对象的描述。

#### Returns

* 关于该对象的文字描述

### public Uri toUri ()

将当前的 Cardboard 设备参数编码为 Uri。

返回的 Uri 可以被写入 NFC 标签中或者文件以及二维码中。

可以通过 `Uri.buildUpon()` 与 `Uri.Builder.appendQueryParameter(key, value)` 方法为返回的 Url 添加额外的参数。参数的键名 URI_KEY_PARAMS 为保留字。

#### Returns

* 将 Cardboard 设备参数编码二生成的 Uri

### public boolean writeToOutputStream (OutputStream OutputStream)

将设备参数写入指定的输出流中。

调用者负责关闭流。

#### Parameters

参数名 | 描述
------ | ----
OutputStream | 用来存储设备参数的输出流

#### Returns

* 设备参数是否写入成功
