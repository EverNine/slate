# DistortionRenderer

### public class DistortionRenderer

封装了所有用于镜头失真校正的渲染操作。

该类并不保证线程安全。出于性能考虑，该类中暴露出的公有方法假定在互斥环境中运行（如在同一线程或不重叠的多个线程中）。

### Public Constructors

构造函数 |
-------- |
DistortionRenderer() |

### Public Methods

定义 | 函数名
---- | ------
void | afterDrawFrame()
void | beforeDrawFrame()
boolean | haveViewportsChanged()
void | onFovChanged(HeadMountedDisplay hmd, FieldOfView leftFov, FieldOfView rightFov, float virtualEyeToScreenDistance)
void | setRestoreGLStateEnabled(boolean enabled)
void | setVignetteEnabled(boolean enabled)
void | undistortTexture(int textureId)
void | updateViewports(Viewport leftViewport, Viewport rightViewport)    

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### public Distortion ()

## Public Methods

### public void afterDrawFrame ()

执行失真校正。

必须在一帧绘制完成后调用以完成失真校正。需要注意的是，该方法仅能对使用了 GLStateBackup 对象来记录 OpenGL 状态机并恢复了其状态的部分进行校正。

### public void beforeDrawFrame ()

执行失真校正的必要准备工作。

必须在需要进行校正的每一帧绘制前执行。

### public boolean haveViewportsChanged ()

检查自上一次调用 `updateViewports` 后视口的失真校正范围是否有变化。

#### Returns

* 若范围有变化返回 `true`，否则返回 `false`

### public void onFovChanged(HeadMountedDisplay hmd, FieldOfView leftFov, FieldOfView rightFov, float virtualEyeToScreenDistance)

将会在眼镜的观察区域变化时被调用。

该方法在调用 `beforeDrawFrame()` 前至少调用一次。在 `beforeDrawFrame()` 与 `afterDrawFrame()` 之间调用该方法会抛出 `IllegalStateException` 异常。

该方法可能会用于失真校正的网格，但在调用 `beforeDrawFrame()` 前不会对OpenGL的调用产生影响。

参数名 | 描述
------ | -----
hmd | 头戴显示器
leftFov | 左眼观察区域大小
rightFov | 右眼观察区域大小
virtualEyeToScreenDistance | 虚拟的眼镜至屏幕的距离，以米为单位

### public void setRestoreGLStateEnabled (boolean enabled)

开启或关闭后处理后的 GL 状态的恢复。

若启用，框架会保证每一帧开始时与每一帧结束时的状态相同。

默认为开启。

参数名 | 描述
------ | -----
enabled | true 表示开启 GL 状态恢复， false 表示禁用。

### public void setVignetteEnabled (boolean enabled)

开启或禁用帧边缘的虚化效果。

若开启，则失真着色器会在可视区域的边界处应用变暗效果以模拟虚化。

默认开启。

参数名 | 描述
------ | -----
enable | true 表示开启虚化效果，false 表示禁用

### public void undistortTexture (int textureId)

通过渲染当前的出书目标校正目标材质。

该方法不能再使用了 `beforeDrawFrame()` 与 `afterDrawFrame()` 方法时直接调用。

参数名 | 描述
------ | -----
textureId | 要校正的材质

### public void updateViewports (Viewport leftViewport, Viewport rightViewport)

在失真校正后更新眼睛的视口为它们的有效尺寸。

参数名 | 描述
------ | -----
leftViewport | 用于更新左眼的 viewport 对象
rightViewport | 用于更新右眼的 viewport 对象
