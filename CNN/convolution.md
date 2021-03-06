# 卷积
#### 一、定义

卷积，和加减乘除一样，是一种数学运算。下面给出它的定义：f，g的卷积记为(f\*g)，其中：

* **连续情形：** <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{{\color{Blue}&space;(f*g)(t)&space;=&space;\int_{a}^{b}&space;f(\tau)&space;g(t&space;-&space;\tau&space;)\mathit{d}\tau&space;}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{{\color{Blue}&space;(f*g)(t)&space;=&space;\int_{a}^{b}&space;f(\tau)&space;g(t&space;-&space;\tau&space;)\mathit{d}\tau&space;}}" title="\mathbf{{\color{Blue} (f*g)(t) = \int_{a}^{b} f(\tau) g(t - \tau )\mathit{d}\tau }}" /></a>

* **离散情形：** <a href="https://www.codecogs.com/eqnedit.php?latex={\color{Red}&space;(f&space;*&space;g)(x)&space;=&space;\sum_{\tau&space;=&space;a}^{b}&space;f(\tau)g(x-\tau)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{Red}&space;(f&space;*&space;g)(x)&space;=&space;\sum_{\tau&space;=&space;a}^{b}&space;f(\tau)g(x-\tau)}" title="{\color{Red} (f * g)(x) = \sum_{\tau = a}^{b} f(\tau)g(x-\tau)}" /></a>

其中[a, b]为函数的定义域，连续情形下f(x), g(x)在定义域区间内是可积的。

#### 二、示例：高利贷利息

  
  假设賴某每月都向某机构贷款f(t)元，贷款的利息是按复利计算，月利率3%。计算N个月月底賴某需要付出的利息**P(N)**？
  
  
  ![复利](https://github.com/Anfany/Machine-Learning-for-Beginner-by-Python3/blob/master/CNN/c1.png)
  
  
  利息
  
  <a href="https://www.codecogs.com/eqnedit.php?latex=\\&space;\mathbf{P(N)}&space;=&space;{\color{DarkOrange}&space;f(N)*3\%&space;}&plus;&space;\mathbf{f(N-1)*(1&plus;3\%)*3\%&space;}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*(1&plus;3\%)^{(N-1)}*3\%}&space;\\&space;\\&space;=&space;{\color{DarkOrange}&space;f(N)*&space;g(0))}&plus;&space;\mathbf{f(N-1)*g(1)}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*g(N-1)}&space;\\&space;\\&space;=&space;{\color{DarkOrange}&space;f(N)*&space;g(N&space;-&space;N))}&plus;&space;\mathbf{f(N-1)*g(N&space;-&space;(N-1))}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*g(N-1)}&space;\\" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\\&space;\mathbf{P(N)}&space;=&space;{\color{DarkOrange}&space;f(N)*3\%&space;}&plus;&space;\mathbf{f(N-1)*(1&plus;3\%)*3\%&space;}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*(1&plus;3\%)^{(N-1)}*3\%}&space;\\&space;\\&space;=&space;{\color{DarkOrange}&space;f(N)*&space;g(0))}&plus;&space;\mathbf{f(N-1)*g(1)}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*g(N-1)}&space;\\&space;\\&space;=&space;{\color{DarkOrange}&space;f(N)*&space;g(N&space;-&space;N))}&plus;&space;\mathbf{f(N-1)*g(N&space;-&space;(N-1))}&plus;&space;\cdots&space;&plus;&space;{\color{Red}&space;\mathbf{f(1)}*g(N-1)}&space;\\" title="\\ \mathbf{P(N)} = {\color{DarkOrange} f(N)*3\% }+ \mathbf{f(N-1)*(1+3\%)*3\% }+ \cdots + {\color{Red} \mathbf{f(1)}*(1+3\%)^{(N-1)}*3\%} \\ \\ = {\color{DarkOrange} f(N)* g(0))}+ \mathbf{f(N-1)*g(1)}+ \cdots + {\color{Red} \mathbf{f(1)}*g(N-1)} \\ \\ = {\color{DarkOrange} f(N)* g(N - N))}+ \mathbf{f(N-1)*g(N - (N-1))}+ \cdots + {\color{Red} \mathbf{f(1)}*g(N-1)} \\" /></a>
  
  其中<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{g(x)&space;=&space;(1&plus;3\%)^{x}*3\%}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{g(x)&space;=&space;(1&plus;3\%)^{x}*3\%}" title="\mathbf{g(x) = (1+3\%)^{x}*3\%}" /></a>
  
  * **离散情形：**
  
  此时利息的公式为：<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{P(N)}&space;=&space;\mathbf{\sum_{\tau&space;=&space;1}^{N}f(\tau)*g(N-\tau&space;)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{P(N)}&space;=&space;\mathbf{\sum_{\tau&space;=&space;1}^{N}f(\tau)*g(N-\tau&space;)}" title="\mathbf{P(N)} = \mathbf{\sum_{\tau = 1}^{N}f(\tau)*g(N-\tau )}" /></a>
  

  * **连续情形：**
  
  将借款的时间间隔无限缩小，利息的计算尺度也相应的缩小。问题就可以转变为连续情形，此时利息的公式为：<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{P(N)}&space;=&space;\mathbf{\int_{\tau&space;=&space;1}^{N}f(\tau)*g(N-\tau&space;)}\mathit{\mathbf{d}\tau}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{P(N)}&space;=&space;\mathbf{\int_{\tau&space;=&space;1}^{N}f(\tau)*g(N-\tau&space;)}\mathit{\mathbf{d}\tau}" title="\mathbf{P(N)} = \mathbf{\int_{\tau = 1}^{N}f(\tau)*g(N-\tau )}\mathit{\mathbf{d}\tau}" /></a>
  
将上面的示例抽象表示，借款好比输入，计算利息的方式可看作一个系统，利息的多少可看作输出。也就是输出等于输入与系统的卷积。系统决定了输出与输入的关系，设置不要同系统，就可以得到不同的输出。 卷积的应用很多，下面主要介绍在图像方面的应用。

#### 三、图像卷积

图像可以看成一个三维矩阵，通过卷积的方式就可以得到图像中的信息。图像是输入，不同的卷积核可看作不同的系统，图像和卷积核卷积得到的结果就可看作图像中的信息。设置不同的卷积核，可以对图像进行不同的处理，也就是获得不同的图像的信息。

  + **卷积操作**
  
  
  
  
  + **不同卷积核的对比**


      * **图像平滑**


      * **平行边缘识别**
  
      * **竖直边缘识别**
  
      * **图像锐化**
  
  
  
  
  
  
  
  
  
  
  
  
  
