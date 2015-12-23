# Eye

### public class Eye

描述3D渲染关于眼睛的渲染细节。

### 内部类

定义 | 类名 | 描述
---- | ---- | ----- 
class | Eye.Type | 定义用于确定眼睛类型的常数

### Public Constructors

构造函数 |
-------- |
Eye(int type) |

### Public Methods

定义 | 函数名
---- | ------
float[] | getEyeView()
FieldOfView | getFov()
float[] | getPerspective(float zNear, float zFar)
boolean | getProjectionChanged()
int | getType()
Viewport | getViewport()
void | setProjectionChanged()

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### public Eye (int type)

创建一组新的关于眼镜的参数。

#### Parameters

参数名 | 描述
-------- |
type | 表示眼睛类型的 Eye.Type 中的常数。关于无效的眼睛类型常数的行为未定义。

## Public Methods

### public float[] getEyeView ()

返回由观察坐标系到当前眼睛坐标系的变换矩阵。

该矩阵应于相机矩阵左乘。

应用于瞳孔间距时需满足 1个世界单位 = 1米 的假设，若不满足，需调用 `android.opengl.Matrix.sacleM` 方法修正该矩阵。

变换中已经包含了头部追踪的旋转、平移以及瞳距平移。若只是想从正常视角获取一只眼睛的视角可以使用此方法。

#### Returns

* 一个表示观察空间到该眼睛的 4x4 的列主序变换矩阵

### public FieldOfView getFov ()

返回当前眼睛的观察区域。

使用 `getFov().toPerspectiveMatrix` 方法生成透视投影变换矩阵。

#### Returns

* 该眼睛的观察区域

### public float getPerspective (float zNear, float zFar)

获取当前眼睛透视投影变换矩阵的简便方法。

该方法会调用 `getFov().toPerspectiveMatrix` 方法来生成矩阵。

#### Parameters

参数名 | 描述
-------- |
zNear | 投影中的近Z平面
zFar | 投影中的远Z平面

#### Returns

* 一个表示该眼睛透视投影的 4x4 的列主序变换矩阵

### public boolean getProjectionChanged ()

投影矩阵是否已失效并应重新计算。

#### Returns

* true 表示矩阵已失效，false 反之

### public int getType ()

返回该眼睛的类型。

#### Returns

* 该眼睛的类型，与 `Eye.Type` 中常数相对应

### public Viewport getViewport ()

返回该眼睛的视口。

#### Returns

* 该眼睛用于渲染的视口

### public void setProjectionChanged ()

强制清除缓存的投影矩阵。

当两帧直接投影参数变化时框架会自动调用该方法。应在该眼睛的 `getFov()` 方法返回的观察大小变化时调用该方法。
