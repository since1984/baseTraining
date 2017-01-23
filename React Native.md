# React Native
## 实现动画的几种方式
* requestAnimationFrame
* setNativeProps
* LayoutAnimation
* Animated

## animated

### 基本组件

* Animated.View
* Animated.Image
* Animated.Text

### 动画步骤

1. 添加基本组件
2. 给Animated.Value设定一个或多个初始值（透明度，位置等）
3. 将初始值绑定到动画目标的属性上（style）
4. 通过Animated.timing 等函数设定动画参数
5. 调用start启用动画

### 创建动画的方式

1. Animated.timing 
	* 推动一个值按照一个过渡曲线而随时间变化
	* Easing 定义了很多缓冲曲线函数 
		* linear, ease, quad, cubic, sin, elastic, bounce, back, bezier, in, out, inout 
2. Animated.decay
	* 推动一个值按照一个初始速度和一个衰减系数逐渐变为零
3. Animated.spring
	* 产生一个基于Rebound和Origami实现的spring动画
	* 它会在toValue的值更新的同时跟踪当前的速度状态，以确保动画连贯 
	* 可配置对象的属性可以是下列的任何值：
		* **toValue (number)**, 
		* overshootClamping (boolean), 
		* restDisplacementThreshold (number), 
		* restSpeedThreshold (number), 
		* velocity (number), 
		* bounciness (number), 
		* speed (number), 
		* tension(number), 
		* friction (number)。

	> 除了 toValue 是必须的，其他值都是可选的，但 friction 和 tension 能帮你更好地控制 spring 动画。

### 流程控制（对于每个独立的方法都有三种调用该动画的方式）
 * **parallel**
 	* 同时开始一个动画数组里的全部动画
 	* 默认情况下，任何一个动画停止，其余的也会被停止
 	* 可以通过stopTogger选项来改变这个效果 

	`Animated.parallel`

* **sequence** 
	* 接受一系列动画数组为参数，并依次执行
	* 按顺序执行一个动画数组里的全部动画
	* 等待一个完成后再执行下一个
	* 如果当前动画被中止，后面的动画不会被执行
* **stagger** 
	* 接受一系列动画数组和一个 **延迟时间** ，
	* 按照序列，每隔一个延迟时间后执行下一个动画（尤其是插入了delay的parallel）å
* delay 生成一个延迟时间（基于timing的delay参数生成）

### interpolate 差值函数

> 实现数值大小，单位的映射转换，用于多个动画共用一个Animated.Value,只需要在每个属性里面映射好对应的值，就可以用一个变量控制多个动画。

`this.state.rotation.interpolate`

~~~
constructor () {
  super()
  this.animatedValue = new Animated.Value(0)
}
componentDidMount () {
  this.animate()
}
animate () {
  this.animatedValue.setValue(0)
  Animated.timing(
    this.animatedValue,
    {
      toValue: 1,
      duration: 2000,
      easing: Easing.linear
    }
  ).start(() => this.animate())
}
render () { 
  const marginLeft = this.animatedValue.interpolate({
    inputRange: [0, 1],
    outputRange: [0, 300]
  })
  const opacity = this.animatedValue.interpolate({
    inputRange: [0, 0.5, 1],
    outputRange: [0, 1, 0]
  })
  const movingMargin = this.animatedValue.interpolate({
    inputRange: [0, 0.5, 1],
    outputRange: [0, 300, 0]
  })
  const textSize = this.animatedValue.interpolate({
    inputRange: [0, 0.5, 1],
    outputRange: [18, 32, 18]
  })
  const rotateX = this.animatedValue.interpolate({
    inputRange: [0, 0.5, 1],
    outputRange: ['0deg', '180deg', '0deg']
  })
...
}
~~~

### 弹簧效果

Spring 弹簧效果

* friction 摩擦系数 默认40
* tension 张力系数 默认7
* bounciness 跳跃
* speed

Decay 衰变效果

* velocity 初速率
* deceleration 衰减系数 默认0.997

### Animated.event 事件接口
### 动画循环
Animated的start方法是支持回调函数的，在动画或某个流程结束的时候执行，这样子就可以很简单地实现循环动画了。

~~~
startAnimation() {
    this.state.rotateValue.setValue(0);
    Animated.timing(this.state.rotateValue, {
        toValue: 1,
        duration: 800,
        easing: Easing.linear
    }).start(() => this.startAnimation());
}
~~~ 