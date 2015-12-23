# Distortion

### public class Distortion

定义了所有需要用于校正透镜造成的失真的参数。

### Public Constructors

构造函数 |
-------- |
Distortion() |
Distortion(Distortion other) |

### Public Methods

定义 | 函数名
---- | ------
float | distort(float radius)
float | distortInverse(float radius)
float | distortionFactor(float radius)
boolean | equals(Object other)
Distortion | getApproximateInverseDistortion(float maxRadiux)
float[] | getCoefficients()
void | setCofficients(float[] coefficients)
String | toString()

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### public Distortion ()

### public Distortion (Distortion other)

拷贝构造函数。

#### Parameters

参数名 | 描述
------ | -----
other | 要拷贝的 distortion 对象

## Public Methods

### public float distort (float radius)

根据失真因子对传入的透镜半径进行变形处理。

#### Parameters

参数名 | 描述
------ | -----
radius | 以透镜中心为圆心的半径

#### Returns

* 失真后的半径

### public float distortInverse (float radius)

根据失真后的半径计算原始半径。

也可以使用 getApproximateInverseDistortion() 方法计算，速度更快但不太精准。

#### Parameters

参数名 | 描述
------ | -----
radius | 失真后的透镜半径

#### Returns

* 未失真的原始半径

### public float distortionFactor (float radius)

返回该店的失真因子。

参数名 | 描述
------ | -----
radius | 该点以透镜中心为圆心的的半径

#### Returns

* 失真因子。乘以该因子对某一点进行失真处理。

### public boolean equals (Object other)

比较该实例与指定对象是否相等。

参数名 | 描述
------ | -----
other | 要与当前实例比较的对象

#### Returns

* 若相等则返回 `true`，否则返回 `false`

### public Distortion getApproximateInverseDistortion (float maxRadiux)

通过最小二乘法构造一个逆失真对象。

该函数是用于实现应用层面的自定义失真。通过对返回的对象使用 `.getCoefficients()` 方法来获得逆失真函数的系数。

这是一种近似求逆，对返回的对象使用  `.distort()` 函数可以获得更快的执行速度但会随时一定的精度。仅当输入值在 0 到 maxRadiux 之间时，能够获得有效的结果。

参数名 | 描述
------ | -----
maxRadiux | 支持的最大半径。应于最大可观察角度保持一致。

#### Returns

* 新的 Distortion 对象

### public float[] getCoefficients ()

返回当前的镜头失真校正系数。

#### Returns

* 一个包含当前失真校正系数的浮点数组

### public void setCofficients (float[] coefficients)

设置镜头的失真校正系数。

系数 Ki 与下式的失真方程对应：

`p' = p ( 1 + K1 r^2 + K2 r^4 + ... + Kn r^(2n) )`

r 表示距光学中心的距离， p 为输入点， p' 为输出结果。
