# CardboardView.StereoRender

### public static interface CardboardView.StereoRenderer

该接口无需关心3D渲染的细节，渲染由 view 完成。开发者只需提供变换用的参数，渲染的细节与失真校正等都从 renderer 中抽象出来，并由 view 内部进行管理。

### Public Methods

接口定义 | 接口名    
-------- | -------
abstract void | [onDrawEye](#public-abstract-void-ondraweye-eye-eye)(Eye eye)
abstract void | onFinishFrame(Viewport viewport)
abstract void | onNewFrame(HeadTransform headTransfrom)
abstract void | onRendererShutdown()
abstract void | onSurfaceChanged(int width, int height)
abstract void | onSurfaceCreated(EGLConfig config)

## Public Methods

### public abstract void onDrawEye ([Eye]() eye)

    用于绘制在某一视点一直眼镜观察到的内容。

    当失真校正开启时，在调用时 GL 上下文会将绘制结果放入纹理提供的帧缓存中，若要在某些渲染阶段中修改帧缓存，需要通过 `glGetIntegerv(GL_FRAMEBUFFER_BINDING, ...)`方法将帧缓存设为1。

    当 VR 模式开启时，[`onDrawEye`]()方法仅会被调用一次用于绘制单眼系统，且失真校正不会开启。开发者可以不受`FieldOfView`的限制，创建任意大小的透视变换矩阵(可以通过`ScreenParams.getWidth()/ScreenParams.getHeight()`获得宽高比)。查看`setVRModeEnable`以获得更多的信息。

#### Parameters

参数名 | 描述
------ | ------
eye | 要渲染的眼睛的信息，包含要用到的变换信息

### public abstract void onFinishFrame ([Viewport]() viewport)

    该方法会在每一帧绘制完成前调用。

    当该方法被调用时，当前帧的绘制已经完成，且若失真校正开启，则校正也已完成。

    该方法可以覆盖修改已经完成的绘制结果，例如可以为用户绘制标识中心位置的准心。

    在该阶段的渲染会对整个绘制表面起效，而非对单个眼睛的视图起效。传入的[`viewport object`]()描述了绘制面的边界，并会被自动置于 GL 的上下文中。

#### Parameters

参数名 | 描述
------ | ------
viewport | 整个 GL 绘制面的视口，会在调用前被自动设置。

### public abstract void onNewFrame ([HeadTransform]() headTransfrom)

    该方法会在每一帧绘制前被调用。

    可以用于改变不同帧或视点的渲染，所有不是针对特定眼睛的帧的预处理都应在此处处理。

#### Parameters

参数名 | 描述
------ | ------
headTransform | 每一帧绘制是的头部位置的变换信息

### public abstract void onRendererShutdown ()

    当渲染线程结束时被调用。

    用于释放 GL 资源以及进行关闭渲染线程的操作。仅当之前有调用过[`onSurfaceCreated`]()方法的情况下会被调用。

### public abstract void onSurfaceChanged (int width, int height)

    当绘制表面尺寸变化时会被调用。

    所有值均为用于绘制一只眼睛的观察尺寸。当 VR 模式开启时，表示渲染两只眼睛的其中一只用的尺寸；当 VR 模式禁用时，则表示的是整个绘制面的尺寸。

    Viewport，视口的大小以及投影的细节会被自动更新。

    需要注意的是，通过 [`onDrawEye(Eye)`]() 传入的 eye 的参数是基于绘制面尺寸与横置的全屏尺寸相对应的假设下进行计算的，任何其他的配置都有可能产生收敛问题。

    还需要注意的是，3D渲染用到的表面尺寸对应的是单眼的尺寸，即在VR模式开启下整个可视表面宽度的一半。

#### Parameters

参数名 | 描述
------ | ------
width | 新的显示面的宽度，单位为像素
height | 新的显示面的高度，单位为像素

### public abstract void onSurfaceCreated (EGLConfig config)

    该方法会在表面被创建时被调用。

#### Parameters

参数名 | 描述
------ | ------
config | 用于创建表面的EGL选项
