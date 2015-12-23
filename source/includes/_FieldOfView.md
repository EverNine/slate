# FieldOfView

### public class FieldOfView

封装了用于传给 glFrustum 的由四个半角(左侧，右侧，底部，顶部)组成的的视野。

### Public Constructors

构造函数 |
-------- |
FieldOfView() |
FieldOfView(float left, float right, float bottom, float top) |
FieldOfView(FieldOfView other) |

### Public Methods

定义 | 函数名
---- | ------
void | copy(FieldOfView other)
boolean | equals(Object other)
float | getBottom()
float | getLeft()
float | getRight()
float | getTop()
void | setAngles(float left, float right, float bottom, float top)
void | setBottom(float bottom)
void | setLeft(float left)
void | setRight(float right)
void | setTop(float top)
void | toPerspectiveMatrix(float near, float far, float[] perspective, int offset)
String | toString()

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### public FieldOfView ()

### public FieldOfView (float left, float right, float bottom, float top)

根据提供的参数创建一个新的视野对象。

#### Parameters

参数名 | 描述
------ | -----
left | 左侧视野半角，单位为度
right | 右侧视野半角，单位为度
bottom | 底部视野半角，单位为度
top | 顶部视野半角，单位为度

### public FieldOfView ()

拷贝构造函数。

#### Parameters

参数名 | 描述
------ | -----
other | 要拷贝的 FieldOfView 对象

## Public Methods

### public void copy (FieldOfView other)

将传入的 FieldOfView 对象中的内容拷贝到当前对象中。

#### Parameters

参数名 | 描述
------ | -----
other | 要拷贝的 FieldOfView 对象

### public boolean equals (Object other)

比较当前实例与传入对象是否相同。

#### Parameters

参数名 | 描述
------ | -----
other | 要与当前实例比较的对象

#### Returns

* true 表示相同，false 反之

### public float getBottom ()

返回底部视野的半角角度。

#### Returns

* 底部视野的半角角度。

### public float getLeft ()

返回左侧视野的半角角度。

#### Returns

* 左侧部视野的半角角度。

### public float getRight ()

返回右侧视野的半角角度。

#### Returns

* 右侧部视野的半角角度。

### public float getTop ()

返回顶部视野的半角角度。

#### Returns

* 顶部视野的半角角度。

### public void setAngles (float left, float right, float bottom, float top)

设置视野的半角。

#### Parameters

参数名 | 描述
------ | -----
left | 左侧视野半角，单位为度
right | 右侧视野半角，单位为度
bottom | 底部视野半角，单位为度
top | 顶部视野半角，单位为度

### public void setBottom (float bottom)

设置底部视野半角角度。

#### Parameters

参数名 | 描述
------ | -----
bottom | 底部视野半角，单位为度

### public void setLeft (float left)

设置左侧视野半角角度。

#### Parameters

参数名 | 描述
------ | -----
left | 左侧视野半角，单位为度

### public void setRight (float right)

设置右侧视野半角角度。

#### Parameters

参数名 | 描述
------ | -----
right | 右侧视野半角，单位为度

### public void setTop (float top)

设置顶部视野半角角度。

#### Parameters

参数名 | 描述
------ | -----
top | 顶部视野半角，单位为度

### public void toPerspectiveMatrix (float near, float far, float[] perspective, int offset) 

生成该对象的透视投影矩阵。

#### Parameters

参数名 | 描述
------ | -----
near | 近平面
far | 远平面
perspective | 用于填充的透视矩阵
offset | 写入透视数组时的偏移量

#### Throws

异常名 | 描述
------ | -----
IllegalArgumentException | 若没有足够的空间写入结果时抛出

### public String toString ()

返回一串简明、可读的关于对象的描述。

#### Returns

* 关于该对象的文字描述
