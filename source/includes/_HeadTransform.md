# HeadTransform

### public class HeadTransform

描述根据眼睛参数的独立头部转换。

### Public Constructors

构造函数 |
-------- |
HeadTransform() |

### Public Methods

定义 | 函数名
---- | ------
void | getEulerAngles(float[] eulerAngles, int offset)
void | getForwardVector(float[] forward, int offset)    
void | getHeadView(float[] headView, int offset)
void | getQuaternion(float[] quaternion, int offset)
void | getRightVector(float[] right, int offset)
void | getTranslation(float[] translation, int offset)
void | getUpVector(float[] up, int offset)

### Inherited Methods
* From class java.lang.Object

## Public Constructors

### HeadTransform () |

## Public Methods

### public void getEulerAngles (float[] eulerAngles, int offset)

提供表示头部转动角度的欧拉角。

由于可能产生万向节死锁，不推荐使用欧拉角，应尽可能使用四元数或旋转矩阵。

提供的代表视口旋转的值分别为 pitch、 yaw、 roll，矩阵 R = Rz(roll) * Rx(pitch) * Ry(yaw) 代表了一个完整的旋转。该旋转矩阵的顺序保证了 yaw 与 roll 在 [-pi, pi] 区间中。

单位为弧度，按照如下的顺序与区间：

* Pitch (X axis): [-pi/2, pi/2]
* Yaw (Y axis): [-pi, pi]
* Roll (Z axis): [-pi, pi]

X-Y-Z 坐标轴按照 OpenGL 风格的右手系。当出现万向节死锁时，yaw 强制为0并提供有效的 roll 角度。

#### Parameters

参数名 | 描述
------ | -----
eulerAngles | 要写入了3个角度的数组
offset | 在数组中的写入位置的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

### public void getForwardVector (float[] forward, int offset)

提供表示头朝向的 3x1 的单位向量。

需要注意在 OpenGL 中的朝向向量是基于相反方向的 Z 轴的，若使用了右手坐标系需要确保对其进行了转换。

#### Parameters

参数名 | 描述
------ | -----
forward | 要写入向量的数组
offset | 写入位置在数组中的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

### public void getHeadView (float[] headView, int offset)

表示相机到头部视角的转换矩阵。

头部的原点定义为两眼的中点位置。

#### Parameters

参数名 | 描述
------ | -----
headView | 要写入4x4列主序转换矩阵的数组
offset | 写入位置在数组中的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

public void getQuaternion (float[] quaternion, int offset)

提供表示头部转向的四元数。    

#### Parameters

参数名 | 描述
------ | -----
quaternion | 要写入了四元数(x,y,z,w)的数组
offset | 在数组中的写入位置的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

### public void getRightVector (float[] right, int offset)

提供表示向右方向的3x1的单位向量。

#### Parameters

参数名 | 描述
------ | -----
right | 要写入了向量的数组
offset | 在数组中的写入位置的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

### public getTranslation (float[] translation, int offset)

提供表示头部相对平移的3x1的向量。

#### Parameters

参数名 | 描述
------ | -----
translation | 要写入了向量的数组
offset | 在数组中的写入位置的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出

### public void getTopVector (float[] top, int offset)

提供表示向上方向的3x1的单位向量。

#### Parameters

参数名 | 描述
------ | -----
top | 要写入了向量的数组
offset | 在数组中的写入位置的偏移量

#### Throws

参数名 | 描述
------ | -----
IllegalArgumentException | 当没有足够的空间写入结果时抛出
