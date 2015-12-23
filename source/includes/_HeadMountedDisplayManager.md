# HeadMountedDisplayManager

### public class HeadMountedDisplayManager

用于管理 `HeadMountedDisplay` 的初始化、更新与访问。

它会根据应用的资源文件夹或外部存储中的配置文件初始化一个 `HeadMountedDisplay`

它会确保 `CardboardDeviceParams` 正确的保留在外部存储的配置文件中让其他 VR 工具包可以访问。

### Public Constructors

构造函数 |
-------- |
HeadMountedDisplay(Context context) |

### Public Methods

定义 | 函数名
---- | ------
HeadMountedDisplay | getHeadMountedDisplay()
void | onPause()
void | onResume()
boolean | updateCardboardDeviceParams(CardboardDeviceParams cardboardDeviceParams)
boolean | updateScreenParams(ScreenParams screenParams)    

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### HeadMountedDisplayManager (Context context) |

根据提供的 context 创建一个新的头戴显示器管理器对象。

#### Parameters

参数名 | 描述
------ | -----
context | 当前 context

## Public Methods

### public HeadMountedDisplay getHeadMountedDisplay ()

返回当前头戴显示器。

不建议对返回的对象进行更新操作，应当使用 `updateCardboardDeviceParams` 与 `updateScreenParams` 方法以确保可以正确的持久化。客户端应避免储存返回的 `HeadMountedDisplay` 对象，应通过调用该函数来确保获取到的对象是最新的。

#### Returns

* 当前头戴显示器

### public void onPause ()

通知管理器当前活动已被暂停。

参考 `onResume()` 获取更多信息。

### public void onResume ()

通知管理器当前活动已恢复。

管理器会在 `HeadMountedDisplay` 需要被更新时调用该方法，若该方法被使用，对应的 `onPause()` 方法也必须被调用用以通知管理器该活动已暂停。

### public boolean updateCardboardDeviceParams (CardboardDeviceParams cardboardDeviceParams)

更新用于渲染的 cardboard 设备参数。

若给定的参数不同，则：
* 当前参数会被给定的参数更新
* 新的参数会被持久化进外部存储中的配置文件中
* 返回 true

关于外部存储中的配置文件可以参考 getConfigFile。

若给定的 `cardboardDeviceParams` 为空或与当前参数相同，则更新操作不会执行，且返回 false。

#### Parameters

参数名 | 描述
------ | -----
cardboardDeviceParams | 新的 cardboard 设备参数

#### Returns

*  参数是否被更新

### public boolean updateScreenParams (ScreenParams screenParams)

更新用于渲染的屏幕参数。

#### Parameters

参数名 | 描述
------ | -----
ScreenParams | 用于更新的参数，若为空则忽略

#### Returns

* 屏幕参数是否被更新
