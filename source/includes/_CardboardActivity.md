# CardboardActivity

`public class CardboardActivity`

用于与Cardboard进行集成的基础Activity类。

提供了与Cardboard进行交互的事件，并且处理了许多创建VR渲染Activity时的许多细节。

### Public Constructors

[`CardboardActivity()`](#cardboardactivity)

### Public Methods

定义 | 方法名
---- | ------
[CardboardView](cardboardview) | getCardboardView()
synchronized boolean | getConvertTapIntoTrigger()
void | onCardboardTrigger()
void | setCardboardView(CardboardView cardboardView)
synchronized boolean | setConvertTapIntoTrigger(boolean enable)

### Protected Methods

定义 | 方法名
---- | ------
void | updateCardboardDeviceParams(CardboardDeviceParams newParams)

### Inherited Methods

* From class java.long.Object

定义 | 方法名
---- | ------
Object | clone()
boolean | equals(Object arg0)
void | finalize()
final Class<?> | getClass
int | hashCode()
final void | notify()    
final void | notifyAll()
String | toString()
final void | wait(long arg0, int arg1)
final void | wait(long arg0)
final void | wait()

* From interface com.google.vrtoolkit.cardboard.VolumeKeyState.Handler

定义 | 方法名
---- | ------
abstract boolean | areVolumeKeysDisabled()

* From interface com.google.vrtoolkit.cardboard.sensors.SensorConnection.SensorListener

定义 | 方法名
---- | ------
abstract void | onCardboardTrigger()

## Public Constructors

### public CardboardActivity()

## Public Methods

### public CardboardView getCardboardView ()

    返回与该 activity 想关联的 `CardboardView`

#### Returns

    * 返回与该 activity 想关联的 `CardboardView`, 返回值不为 null

### public synchronized boolean getConvertTapIntoTrigger ()

    返回轻触屏幕是否已被转换为 Cardboard 的触发动作

#### Returns
    
    * 是否轻触屏幕动作已被转换为 Cardboard 的触发动作

### public void onCardboardTrigger ()

    重写该方法来检测 Cardboard 的触发动作。当设备在 Cardboard 内时，提供了一种类似于单击的动作。

### public void setCardboardView (CardboardView cardboardView)

    将 Cardboard view 与该 activity 关联。

    该方法不会改变 view 中的内容，仅会将其与 activity 相关联以确保该 `CardboardView` 能接收到需要的有关 activity 生命周期中的消息。

    若使用 `setContentView` 方法直接设置了 `CardboardView` 则该方法会被自动调用。当使用其他方法设置了 `CardboardView`时，需要手动调用该方法（例如，使用布局资源设置时）。

#### Parameters

参数名 | 描述
------ | ----
cardboardView | 要与 activity 关联的 Cardboard view ，不能为 null

### public synchronized void setConvertTapIntoTrigger (boolean enabled)

    设置是否将轻触屏幕动作转换为 Cardboard 的触发动作。

    若为 true，则轻触屏幕动作会触发 `onCardboardTrigger`， 默认为 false

#### Parameters

参数名 | 描述
------ | ----
enabled | 是否将轻触屏幕动作转换为 Cardboard 的触发动作

## Protected Methods

### protected void updateCardboardDeviceParams (CardboardActivity newParams)

    请求为当前的 Cardboard 设备更新参数。

    该方法会对比传入参数与已有设置的异同，并更新不同的参数。

    该方法调用前必须已设置好 `CardboardView`，查看 `setCardboardView`

#### Parameters

参数名 | 描述
------ | ----
newParams | 新的 Cardboard 设备参数
