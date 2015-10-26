# CardboardView

### public class CardboardView

为简化 VR 渲染而对 GLSurfaceView 进行的扩展。

被设计为在全屏模式下且处于横置状态使用。

该 view 可以被当做普通的 `GLSurfaceView` 使用，但需要实现以下两个渲染接口中的一个:

* [`CardboardView.StereoRenderer`](#cardboardview-stereorenderer): 分离了所有3D渲染的细节。
* [`CardboardView.Renderer`](#cardboardview-renderer): 为需要自己实现所有3D渲染细节的复杂工程提供的接口。

推荐使用 [`CardboardView.StereoRenderer`](#cardboardview-stereorenderer) 接口，仅当真的需要时再使用 [`CardboardView.Renderer`](#cardboardview-renderer) 接口。

该 view 支持在 VR 模式与普通模式间的切换，可以通过调用 [`setVRModeEnable`]() 方法在任何时间进行切换。

### Nested Classes

定义 | 类名 | 描述
---- | ---- | ----
interface | [`CardboardView.Renderer`](#cardboardview-renderer) | 为需要自己实现所有3D渲染细节的复杂工程提供的接口
interface | [`CardboardView.StereoRenderer`](#cardboardview-stereorenderer) | 分离了3D渲染细节的接口

### Public Methods

定义 | 函数名
---- | ------
boolean | getAlignmentMarkerEnabled()
CardboardDeviceParams | getCardboardDeviceParams()
boolean | getDistortionCorrentionEnabled()
boolean | getElectronicDisplayStabilizationEnabled()
boolean | getGyroBiasEstimationEnabled()
HeadMountedDisplay | getHeadMountedDisplay()
float | getInterpupillaryDistance()
float | getNeckModelFactor()
boolean | getRestoreGLstateEnabled()
ScreenParams | getScreenParams()
boolean | getSettingsButtonEnabled()
boolean | getVRmode()
boolean | getVignetteEnabled()
void | onPause()
void | onResume()
void | resetHeadTracker()
void | setAlignmentMarkerEnbled(boolean enabled)
void | setDistortionCorrentionEnabled(boolean enabled)
void | setElectronicDisplayStabilizat5ionEnabled(boolean enabled)    
void | setGyroBiasEstimationEnabled(boolean enabled)
void | setNeckModelEnabled(boolean enabled)
void | setNeckModelFactor(float factor)
void | setOnCardboardTriggerListener(Runnable listener)
void | setRenderer(CardboardView.Renderer renderer)
void | setRenderer(CardboardView.StereoRenderer renderer)
void | setRestoreGLStateEnabled(boolean enabled)
void | setSettingsButtonEnabled(boolean enabled)
void | setVRModeEnable(boolean enabled)
void | setVignetteEnabled(boolean enabled)
void | undistortTexture(int inputTexture)
void | updateCardboardDeviceParams(CardboardDeviceParams cardboardDeviceParams)    
void | updateScreenParams(ScreenParams screenParams)    

### Inherited Methods

* From class java.lang.Object    

## Public Constructors

### public CardboardView (Context context)

### public CardboardView (Context context, AttributeSet attrs)

## public Methods

### public boolean getAlignmentMarkerEnabled ()

返回排版准线是否绘制。

#### Returns

* 若排版准线开启则返回 `true` ，否则返回 `false` ，默认为开启 

### public CardboardDeviceParams getCardboardDeviceParams ()

返回当前 Cardboard 设备的物理参数。

该方法等同于 [`getHeadMountedDisplay().getCardboardDeviceParams()`]()。

修改返回的对象不会影响渲染，若要修改的参数生效需调用 [`updateCardboardDeviceParams`]() 方法。

#### Returns

* 当前 Cardboard 设备的物理参数

### public boolean getDistortionCorrentionEnabled ()

返回失真校正是否开启。

#### Returns

* 若失真校正开启返回 `true`，否则返回 `false`

### publice boolean getElectronicDisplayStabilizationEnabled ()

(实验性质) 返回电子显示稳定(EDS)是否开启。

#### Returns

* 若 EDS 开启返回 `true`，否则返回 `false`

### public boolean getGyroBiasEstimationEnabled ()

返回陀螺仪偏差估计是否开启。

#### Returns

* 若陀螺仪偏差估计开启则返回 `true`

### public float getInterpupillaryDistance ()

获得瞳距看，Cardboard 框架目前假设用户的 IPD 与观察设备的镜头间距相同。

#### Returns

* 当前瞳距，单位为米

### public float getNeckModelFactor ()

获得用于进行头部跟踪颈部模型。

参考 [`setNeckModelEnabled()`]() 与 [`setNeckModelFactor()`]() 以获取更详细的信息。

#### Returns

* 颈部模型因子

### public boolean getRestoreGLstateEnabled ()

返回应用的 GL 状态经过后处理后是否被恢复。

#### Returns

* 若 GL 状态复原开启则返回 `true` ，否则返回 `false` ，默认开启

### public ScreenParams getScreenParams ()

返回插入的设备的屏幕参数。

该方法等同于 [`getHeadMountedDisplay().getScreenParams()`]()。

修改返回的对象不会影响渲染，若要修改的参数生效需调用 [`updateScreenParams`]() 方法。

#### Returns

* 当前插入设备的屏幕参数

### public boolean getSettingsButtonEnabled ()

返回设置按钮是否绘制。

#### Returns

* 若设置按钮启用则返回 `true` ， 否则返回 `false` ，默认为开启

### public boolean getVRmode ()

返回当前 VR 模式是否开启

#### Returns

* 若 VR 模式开启则返回 `true`，否则返回 `false`

### public boolean getVignetteEnabled ()

返回渐晕效果是否开启。

#### Returns

* 若渐晕效果开启则返回 `true` ，否则返回 `false` ，默认为开启

### public void onPause ()

通知 view ， activity 已被暂停。

### public void onResume ()

通知 view ， activity 已被恢复。

### public void resetHeadTracker ()

使头部追踪器重置。

除其他事，该方法会将场景的Z轴与手机当前的朝向对齐。

### public void setAlignmentMarkerEnbled (boolean enabled)

启用或禁用绘制竖直将屏幕分为两半的标记线。该标记是用来帮助用户校正 Cardboard 与手机的位置的。

仅当 VR 模式开启时有效。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启绘制标记线，false表示禁用

### public void setDistortionCorrentionEnabled (boolean enabled)

设置是否开启失真校正。

默认开启，会从调用后的下一帧绘制开始生效。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启失真校正，false表示禁用

### public void setElectronicDisplayStabilizat5ionEnabled (boolean enabled)

(实验性质) 开启或禁用电子显示稳定(EDS)。

电子显示稳定会在失真校正过程中完成（故仅当失真校正开启时有效）。通过读取传感器最近的输入，判断若在当前帧绘制完成后仍有头部转动，则根据转动角度扭曲已经绘制好的画面。该功能可以用来降低延时。

该功能仍处于实验性质，默认禁用。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启EDS，false表示禁用

### public void setGyroBiasEstimationEnabled (boolean enabled)

开启或禁用用于头部追踪的陀螺仪偏差估计。

陀螺仪经常会产生偏移，即在不工作的状态下返回值不为零。这将会使头部追踪产生错误的偏移。当陀螺仪偏差估计开启时， Cardboard 框架会持续地估计陀螺仪的偏差，并据此对原始的陀螺仪返回数据进行校正，借此来降低头部追踪中产生的错误偏差。陀螺仪偏差估计默认开启。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启陀螺仪偏差估计，false表示禁用

### public void setNeckModelEnabled 9)

完全开启或禁用用于头部追踪的颈部模型。

颈部模型是用来模拟基于颈部的自然的头部转动，而非基于双眼中点的会对旋转产生额外平移的模拟。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启颈部模型，false表示禁用。等价于调用 setNeckModelFactor(enabled ? 1.0 : 0.0)

### public void setNeckModelFactor (float factor)

设置用于头部追踪的颈部模型因子。

参考 [`setNeckModelEnabled()`](#public-void-setNeckModelEnabled) 以获取更多信息。

#### Parameters

参数名 | 描述
------ | -----
factor | 颈部模型因子介于 0.0f 与 1.0f 之间。设置为 0.0f 会完全禁用颈部模型，设置为 1.0f 则会完全启用颈部模型。介于 0.0f 与 1.0f 间的值则会根据颈部因子的大小对完全颈部模型与无颈部模型的结果进行线性插值。

### public void setOnCardboardTriggerListener (Runnable listener)

为 Cardboard 触发动作设置监听器。

仅当你没有使用 [`CardboardActivity`](#CardboardActibity) 并且希望在 [`CardboardView`](#CardboardView) 层处理触发动作是使用该函数。如果你在使用 [`CardboardActivity`](#CardboardActibity) ，推荐使用 [`CardboardActivity`](#CardboardActibity) 的 onCardboardTrigger 方法来替代此函数。

#### Parameters

参数名 | 描述
------ | -----
listener | Cardboard 触发动作发生时的回调函数

### public void setRenderer ([CardboardView.Renderer](#cardboardview-renderer) renderer)

设置用来处理所有3D渲染细节的渲染器。

在该对象的整个生命周期内仅能设置一个渲染器，查看 [`Renderer`](#cardboardview-renderer) 接口以获取更多信息。

#### Parameters

参数名 | 描述
------ | -----
renderer | 要设置的渲染器，不能为 null

### public void setRenderer ([CardboardView.StereoRenderer](#cardboardview-renderer) renderer)

设置以分离3D渲染细节的渲染 view 的渲染器。

在该对象的整个生命周期内仅能设置一个渲染器，查看 [`StereoRenderer`](#cardboardview-stereorenderer) 接口以获取更多信息。

#### Parameters

参数名 | 描述
------ | -----
renderer | 要设置的3D渲染器

### public void setRestoreGLStateEnabled (boolean enabled)

启用或禁用后处理后的应用的 GL 状态恢复。

CardboardView 可能会在每一帧的绘制中加入后处理步骤。例如，应用的图像可能会被渲染进材质中而非屏幕上。若该开关开启，则 Cardboard 框架确保下一帧开始时的 GL 状态与上一帧结束时的 GL 状态相同。默认开启。

若禁用，则应用的运行表现会得到改善，但在每一帧的绘制开始时以下关于 GL 状态机的假设不能得到保证：

* 视口
* 清除用色
* 已启用的材质单元
* 正在使用的着色器程序
* 顶点属性（指针以及是否启用）
* GL_CULL_FACE 与 GL_SCISSOR_TEST 是否启用
* GL_ARRAY_BUFFER 与 GL_ELEMENT_ARRAY_BUFFER 的绑定关系
* GL_TEXTURE_2D 与0号材质单元的绑定关系

有两项例外：

1. 无论该开关是否开启，当前的边界帧缓存都会被恢复
2. 顶点属性的绑定永远不会恢复。任何在上一帧结束时对 glVertexAttribPointer 的调用都不会对下一帧开始时的绘制产生任何影响

####　Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启 GL 状态恢复， false 表示禁用

### public void setVRModeEnable (boolean enabled)

开启或关闭 VR 渲染模式。

控制3D渲染与失真校正，默认开启。会在调用后的下一帧开始生效。

若禁用，瞳距不会被应用于针对眼睛的变换，自动失真校正也不会生效，透视投影的可视区域也有可能发生偏转，尤其是在没有设置为全屏模式时。

参考 [`Renderer`](#cardboardview-renderer) 与 [`StereoRenderer`](#cardboardview-stereorenderer) 的文档以获得更多的细节。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启 VR 模式， false 表示禁用

### public void setVignetteEnabled (boolean enabled)

开启或禁用帧边缘的渐晕效果。

若该开关开启，则失真着色器会对可视边缘施加变暗效果以模拟渐晕效果。

默认开启。

#### Parameters

参数名 | 描述
------ | -----
enabled | true 表示开启渐晕效果， false 表示禁用

### public void undistortTexture (int inputTexture)

对提供的纹理进行变形矫正并将渲染结果写入输出缓存中。

该方法为那些使用自己的渲染循环的并无法使用 [`Renderer`](#cardboardview-renderer) 与 [`StereoRenderer`](#cardboardview-stereorenderer) 接口的用户提供。不推荐因其他原因而使用。

若渲染器已设置，纹理变性矫正会在渲染线程中完成。否则该操作会在调用线程中完成。调用者负责确保使用的线程中的 GL 上下文中材质的可用性。

#### Parameters

参数名 | 描述
------ | -----
inputTexture | 要进行变形矫正的纹理

### public void updateCardboardDeviceParams ([`CardboardDeviceParams`](#cardboarddeviceparams) cardboarddeviceparams)

更新用于渲染的 Cardboard 设备的物理参数。

将会在调用后的第一帧开始生效。

#### Parameters

参数名 | 描述
------ | -----
cardboardDeviceParams | 要设置的 Cardboard 适配设备的物理参数。若传入对象为 null 或与原本的参数相同，则请求会被忽略。

### public void updateScreenParams ([ScreenParams screenParams] screenParams)

更新用于渲染的屏幕参数。

更新插入的 Cardboard 设备的屏幕参数，改动会在调用后的下一帧生效。

#### Parameters

参数名 | 描述
------ | -----
screenParams | 要更新的参数，若为 null 则会被忽略
