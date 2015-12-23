# HeadMountedDisplay

### public class HeadMountedDisplay

封装了关于头戴3D显示器的关于屏幕与 Cardboard 适配装置的参数。

### Public Constructors

构造函数 |
-------- |
HeadMountedDisplay(ScreenParams screenParams, CardboardDeviceParams cardboardDevice) |
HeadMountedDisplay(HeadMountedDisplay hmd) |

### Public Methods

定义 | 函数名
---- | ------
boolean | equals(Object other)
CardboardDeviceParams | getCardboardDeviceParams()
ScreenParams | getScreenParams()
void | setCardboardDeviceParams(CardboardDeviceParams cardboardDeviceParams)
void | setScreenParams(ScreenParams screen)

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### HeadMountedDisplay(ScreenParams screenParams, CardboardDeviceParams cardboardDevice) |

根据提供的对象创建一个新的头戴显示器对象。

#### Parameters

参数名 | 描述
------ | -----
screenParams | 屏幕参数
cardboardDevice | Cardboard 设备参数

### HeadMountedDisplay(HeadMountedDisplay hmd) |

拷贝构造函数。

#### Parameters

参数名 | 描述
------ | -----
hmd | 要拷贝的头戴显示器对象

## Public Methods

### public boolean equals (Object other)

比较当前实例与传入对象是否相同。

#### Parameters

参数名 | 描述
------ | -----
other | 要与当前实例比较的对象

#### Returns

* true 表示相同，false 反之

### public CardboardDeviceParams getCardboardDeviceParams ()

返回描述 Cardboard 设备的参数。

#### Returns

* 描述 Cardboard 设备的参数

### public ScreenParams getScreenParams ()

返回描述屏幕的参数。

#### Returns

* 描述屏幕的参数

### public void setCardboardDeviceParams (CardboardDeviceParams cardboardDeviceParams)

设置描述 Cardboard 设备的参数。

#### Parameters

参数名 | 描述
------ | -----
cardboardDeviceParams | 描述 Cardboard 设备的参数

### public void setScreenParams ()

设置描述屏幕的参数

#### Parameters

参数名 | 描述
------ | -----
screen | 描述屏幕设备的参数
