---
title: Linear Algebra
date: 2018-12-05T09:06:07+08:00
categories: 数学
tags: 
- 线性代数
- 数学
---
## [Essence of Linear Algebra](https://www.bilibili.com/video/av6731067/?p=1)

普适的代价是抽象

Abstractness is the price of generality

### 向量（Vector）

*   计算机学生眼里：向量是数字列表

*   物理学生眼里：向量是箭头

*   数学家认为：向量可以表示任何东西，只要满足两个运算关系——数乘（scalar multiplication）与加法

### 线性组合、张成的空间和基（Linear combination、span and base）

*   将每个坐标看成标量，这些标量与基向量数乘后就可以表示所有向量

*   对于二维空间，只需要两个***基向量***——i-hat and j-hat，就可以用它们的线性组合表示整个二维空间所有的向量

    但是如果这两个基向量是同向或者反向的，则没法表示整个二维空间的所有向量

*   为何叫***线性组合***？

    对于二维空间的基向量，如果把其中一个基向量固定，另一个基向量变化，则合向量的末端会落在一条直线上

*   基向量的全部线性组合构成的向量集合称为“***张成的空间***”

*   对于三维空间，两个向量张成的空间是什么？

    根据三点共面，张成的空间是这两个向量所确定的面

*   对于三维空间，三个向量张成的空间是什么？

    如果三个向量不共面，则张成的空间是整个三维空间，这时这三个向量***线性无关（linearly independent）***

    如果三个向量共面，则引入的第三个向量并不会使空间维数增加，因为这三个向量是***线性相关（linearly dependent）***的，第三个向量已经落在了由前两个向量张成的空间里，可以由前两个向量线性表示

*   由此引出基的严格定义（From维基百科）：

    A basis *B* of a [vector space](https://en.wikipedia.org/wiki/Vector_space)  *V* over a [field](https://en.wikipedia.org/wiki/Field_(mathematics))  *F* (such as the [real numbers](https://en.wikipedia.org/wiki/Real_numbers) R or the [complex numbers](https://en.wikipedia.org/wiki/Complex_number) C) is a [linearly independent](https://en.wikipedia.org/wiki/Linear_independence) subset of *V* that [spans](https://en.wikipedia.org/wiki/Linear_span)  *V*.

    **向量空间的一个基是张成该空间的一个线性无关V的子集**

    This means that, a subset B of *V* is a basis if it satisfies the two following conditions:

    *   the *linear independence* property:

        for every finite subset {*b*1, ..., *bn*} of B and every *a*1, ..., *an* in **F**, if *a*1*b*1 + ⋅⋅⋅ + *anbn* = 0, then necessarily *a*1 = ⋅⋅⋅ = *an* = 0;

    *   the *spanning* property:

        for every (vector) *v* in *V*, it is possible to choose *v*1, ..., *vn* in **F** and *b*1, ..., *bn* in B such that *v* = *v*1*b*1 + ⋅⋅⋅ + *vnbn*.

    The [scalars](https://en.wikipedia.org/wiki/Scalar_(mathematics))  *vi* are called the coordinates of the vector *v* with respect to the basis *B*, and by the first property they are uniquely determined.

    标量vi是向量v关于基B的坐标，根据第一个性质，vi是唯一确定的

### **矩阵与线性变换（Matrices and Linear transformations）**

*   线性变换其实只是函数（function）的另一种说法

    用“线性变换”而不是“线性函数”，是为了表示“移动”的概念，因为线性变换可以让向量移动到另一个位置

*   线性变换

    （二维平面）直线仍然是直线、保持原点不动、保持网格线平行且等距

*   矩阵的积

    对应的两个线性变换相继作用

    从右向左读，就像函数一样

    Matrix: A×B×X，X先与B相乘，再与A相乘 / X先做关于B的线性变化，再做关于A的线性变换

    Function: f(g(x))，g是关于变量x的函数，而f是关于g的函数

*   矩阵不具有交换律（Commutative property）：

    A×B≠B×A

    但是从右往左读的，具有结合律（Associative property）：

    (A×B)×C=A×(B×C)

*   线性变换，其实就是矩阵相乘，AX=Y，其中X为输入向量（nx1矩阵），Y为输出向量（nx1矩阵），A为与某线性变换对应的mxn矩阵

### 行列式（Determinant）

*   线性变换有时会使空间延伸，有时会压缩空间，所以需要探讨空间（面积/体积/...）变化了多少倍

    考虑如下矩阵

        1 0
        0 1

*   线性变化的行列式（The determinant of a transformation）

    行列式就是用来表示线性变换对空间的扩张/压缩程度的度量

    记作det(A)

*   但是行列式有负值，怎么理解?

    定向（Orientation）如果不变，则为正值，如果变化，行列式为负值，其绝对值是扩张/压缩的倍数

    对于二维空间，i-hat本来在j-hat的顺时针90度方向，线性变换后，i-hat-landed在j-hat-landed的逆时针方向，这时定向（Orientation）改变了，所以行列式取负值

    对于三维空间，i-hat、j-hat、z-hat的方向符合右手定则，如果线性变换后仍满足右手定则，则定向（Orientation）不变，行列式为正值

### 逆矩阵、列空间、秩、零空间（Inverse matrices, Column space, Rank, Null space）

*   计算方法在Essence of Linear Algebra中不会重点讲解，可以自行搜索高斯消元法和行阶梯形

*   考虑一个线性方程组（linear system of equations ）：

    AX=Y

    对于向量X^T=(x1, x2, x3, ..., xn)，乘以系数矩阵A后得到向量Y^T

    别忘了矩阵的乘法就是对向量进行线性变换，所以通过线性变换（A）可以把X“变换”到Y

    那么如何把Y“变换”到X？这就相当于**线性变换的逆变换**：

    X=A^(-1)×Y

*   单位矩阵

    两个线性变换相继作用相当于矩阵的乘法，所以一个矩阵的逆（矩阵）乘以这个矩阵本身，相当于“什么也不做”

    这时把它们的积称为**单位矩阵**：

    A^(-1)×A=E

*   逆矩阵恒存在吗？

    显然不是，当det(A)=0时，线性变换把原空间压缩（降维）了，没法把压缩的空间解压缩

    对于二维：如果det(A)=0，则线性变换把平面压缩成了一条线（或一个点），你无法将一条线“解压缩”为一个平面，因为平面是无数线的集合，没法用这一条线去表示这无数的、方向各异的线，线性变换使得二维平面的度量——面积压缩为0

    对于三维：如果det(A)=0，则线性变换把三维空间压缩成了一个面（或一条线甚至一个点），你也无法将一个面“解压缩”为一个三维空间，因为线性变换使得三维空间的度量——体积压缩为0

*   行列式为0（即det(A)=0）时，线性方程组一定无解？

    不一定，有可能Y正好落在线性变换压缩后的空间中

    对于二维：det(A)=0，线性变换把空间从平面压缩为线，有可能Y正好在这条线上，所以有解

    对于三维：det(A)=0，线性变换把空间从三维空间压缩为面，有可能Y正好在这个面上，所以有解

*   对于同维向量空间，不同的det(A)=0，产生线性变换的效果一样吗？

    不一样，比如对于三维空间，有可能线性变换使三维空间压缩为二维空间（即平面），也有可能压缩得更厉害，成了一维空间（即直线）

*   如何度量呢？——————**用秩来度量**

    如果线性变换使所有向量都落在同一条线上，则说这个线性变换的秩为1

    如果线性变换使所有向量都落在同一平面上，则说这个线性变换的秩为2

    如果线性变换使所有向量都落在同一三维空间上，则说这个线性变换的秩为3

    ...

    所以，**秩（Rank）代表着线性变换后空间的维数（Number of dimensions in the output）**

    如果det(A)≠0：

    对于2x2矩阵，线性变换最多只能从平面变换到平面，所以最大的秩为2

    对于3x3矩阵，线性变换最多只能从空间变换到空间，所以最大的秩为3

    如果det(A)=0：

    线性变换一定会使原空间**降维**

*   列空间：所有可能的输出向量构成的集合

    线性变换使基向量发生变换，变换后的基向量张成的空间就是所有可能的变换结果

    **列空间就是矩阵的列所张成的空间**

    于是，**秩就是列空间的维数**

    > 列空间可以告诉我们线性方程组何时有解何时无解

*   当秩达到最大值时，意味着秩与列数相等，这时成为满秩（Full rank）

*   零空间（Null space）/ 核（Kernel）

    零向量一定在列空间中，因为线性变换必须保持原点不变

    对于满秩变换，唯一能在变换后落在原点的就是零向量本身

    对于非满秩变换，会有一系列向量在变换后成为零向量

    *   对于平面，非满秩变换，意味着det(A)=0，变换后成为一条直线，在原来的平面一定存在一条直线，该直线上的所有向量变换后的向量为零向量（用动画想象一下如何从平面压缩到直线就知道了）

    *   对于三维空间，非满秩变换，意味着det(A)=0，变换后成为一个平面（或一条直线），在原来的三维空间中一定存在一个平面（或一条直线），该平面（或一条直线）上的所有向量变换后的向量为零向量

    **这些变换后为零向量的向量，称为矩阵的零空间或核**

    > 对于线性方程组，如果Y为零向量，则系数矩阵A的零空间就是这个线性方程组的所有可行解，或者说这个线性方程组的所有可行解构成了系数矩阵A的零空间

### 非方阵

*   3x2矩阵的几何意义就是把二维空间映射到三维空间上

    矩阵有两列，表明输入空间有两个基向量

    矩阵有三行，表明每一个基向量在变换后都用三个独立的坐标来描述

    其列空间的维数为2，如果满秩的话也为2

*   2x3矩阵的几何意义就是把三维空间映射到二维空间上

    矩阵有三列，表明输入空间有三个基向量

    矩阵有二行，表明每一个基向量在变换后都用二个独立的坐标来描述

    其列空间的维数为2，如果满秩的话也为2

### 点积与对偶性（Dot product and duality）

*   两个向量的点积，就是对应坐标的积之和

    两个向量的方向在同一侧时，点积为正

    两个向量的方向在相反侧时，点积为负

    两个向量的方向垂直时，点积为0

*   点积在几何上的解释就是一个向量在另一个向量方向上的投影（projection），再乘以另一个向量，得到一个标量（scalar）

*   如何理解点积具有交换性呢？

    假设两个向量共线，那么投影就是本身，这时就是普通的乘法，具有交换性：

    |v||w|=|w||v|

    假设两个向量不共线，再假设两个向量是同等长度，那么可以找到一条对称线，无论是哪个向量“主动”投影过去，点积肯定是相同的：

    v·v=v·v

    假定其中一个向量缩放了n倍，点积的结果也是原来的n倍：

    (nv)·v=n(v·v)

    因为n可取任意值，推广到任意长度的向量，于是点积具有交换性：

    v·w=w·v

*   为何对应坐标的积之和可以和投影联系起来?

    回想矩阵的知识，1x2矩阵（线性变换）乘以2x1矩阵（某向量有两个坐标），得到1x1矩阵，也就是标量，这不就是向量的点积吗？

    两个向量点积，就是把其中一个向量转化为线性变换

    很巧妙地用到了对偶性的知识，笔记不好做，看视频吧

*   一个向量的对偶是由它定义的线性变换

*   一个多维空间到一维空间的线性变换的对偶是多维空间中某个特定向量

*   **向量不仅仅是空间中的箭头，还是线性变换的物质载体**

### 叉积（Cross product）

叉积的标准介绍：

*   两个向量的叉积可以生成另一个向量，记作：

    v×w=p

    新生成的向量满足：

    p=det(k;v;w)=平行四边形，其中v、w是列向量在各个维度的坐标（不带方向），k为一组基向量（带方向，如i-hat、j-hat、k-hat），p的方向垂直于平行四边形，用右手定则确定

    对于三维空间，行列式det(k;v;w)如下类似：

        i-hat    v1    w1
        j-hat    v2    w2
        k-hat    v3    w3

    故

          det(k;v;w)=(v2w3-v3w2)i-hat + (v1w3+v3w1)j-hat + (v1w2+v2w1)z-hat

*   叉积何时为正，何时为负？

    巧妙记忆：xoy直角坐标系，v为x，w为y，这时叉积为正v×w>0；否则叉积为负v×w<0

    于是有，v×w=-w×v

从线性变换的角度看叉积：

*   考虑三维空间，我们已经知道vxw=p，得到的新向量p可以用如下行列式描述：

          |p|=det(k;v;w)=(v2w3-v3w2)i-hat + (v1w3-v3w1)j-hat + (v1w2-v2w1)z-hat

    **为什么要引入三个基向量呢**？

*   先不着急回答这个问题，先用三个变量xyz代替三个基变量，考虑函数：f([x,y,z]^T)=det([ [x,y,z]^T, [v1,v2,v3]^T, [w1,w2,w3]^T]) ，这个函数描述了任意一个向量，通过向量v与w的组合后，所输出的新向量，**本质上是三维空间到一维空间的线性变换**

    明显，这个函数是线性的，所以可以使用对偶性——线性变换与其对偶向量是一一对应的

*   接下来的任务就是寻找这个对偶向量，首先观察函数，输入是三维向量，输出是一维，于是可以构造一个从三维到一维的线性变换，根据前面的知识，这个线性变换和一个1x3矩阵对应：

        [?,?,?][x,y,z]^T = det([ [x,y,z]^T, [v1,v2,v3]^T, [w1,w2,w3]^T])

    而根据点积的对偶性——两个（列）向量的点积等价于其中一个向量“躺下来”变为线性变换乘以另一个向量所构成的矩阵，于是，我们可以把1x3矩阵“立起来”变成一个向量，再与[x,y,z]^T进行点积运算：

         [?,?,?]^T﹒[x,y,z]^T = det([ [x,y,z]^T, [v1,v2,v3]^T, [w1,w2,w3]^T])

    ”立起来“的向量设为p=(p1,p2,p3)^T，于是上式可改写为：

          [p1,p2,p3]^T﹒[x,y,z]^T = det([ [x,y,z]^T, [v1,v2,v3]^T, [w1,w2,w3]^T])
    根据简单的计算，易知：

           p1=v2w3-v3w2
          p2=v1w3-v3w1
          p3=v1w2-v2w1

于是可以回答之前的问题：**叉积中引入三个基变量是为了表示叉积的结果是一个（三维）向量**

### 基变换

*   永远别忘了线性变换可以用矩阵描述，基变换也是一种线性变换，*而且是不降维的线性变换*

*   从一种基变换到另一种基，可用唯一的矩阵描述，相反，如果要反过来，则用这个矩阵的逆即可

*   假设用甲的基向量表示某个向量为[x0,y0]^T，用乙的基向量表示这个向量为[xj,yj]^T，那么如果用甲的**坐标**来表示这个向量为A矩阵，则有如下基变换公式

          A[xj,yj]^T = [x0,y0]^T

*   那如果甲做了某种线性变换，甲的基向量也会变化，如果甲乙对应的基变换不变，那么对应的乙的基向量如何变化呢？假设在甲的线性变换之前，用乙的基向量描述某个向量为j-hat，在甲的线性变换之后，用乙的基向量描述这个向量为j'-hat

           		基变换			线性变换			逆线性变换
          j-hat --------> i-hat --------> i'-hat --------> j'-hat

    计算方法很简单，每经历一个变换都左乘变换所对应的矩阵即可

### 特征向量与特征值（Eigenvectors and Eigenvalues）

*   前提知识：线性变换（对应矩阵）、行列式（线性变换/矩阵的面积变化倍数）、线性方程组、基变换

*   经过线性变换后，某些向量***仍***留在它们所张成的空间里，这些特殊的向量就称为变换的“**特征向量**”，而每个特征向量都有一个对应的值，称为”**特征值**“，用来表示特征向量在变换中拉伸或压缩的比例因子，对于不同的特征向量，特征值有可能相同有可能不同

*   特征向量有啥用？

    举个例子，在三维空间里面，不同的（满秩）线性变换具有不同的特征向量，根据特征向量的定义——仍留在它们所张成的空间里，所以这些向量并没有动，**也就是对称轴**！

    再举个例子，三维空间的旋转，显然用作图的方法要比矩阵的表示更加清晰，而旋转也是一种线性变换，对称轴上的向量并没有被拉伸或压缩，所以**旋转对应的特征值为1**！

*   如何求解特征值？

    假设变换矩阵为A，特征向量为V，对应的特征值为𝞴，根据特征向量、特征值的含义，不难理解以下等式：

            AV = 𝞴V

    等式左边是矩阵相乘，右边是向量数乘（𝞴是一个常数），看起来怪怪的，为了理解，可以将𝞴看作如下的矩阵：

            𝞴 0 0
            0 𝞴 0
            0 0 𝞴

    又可写成𝞴与单位矩阵I（或者叫做E）的乘积：

                ⎡1 0 0⎤ 
            𝞴 * ⎢0 1 0⎥
                ⎣0 0 1⎦

    于是等式可变形为：

            (A-𝞴I)V=0

    ok，现在的认为就是寻找非零向量V，使上式成立

    对于非零向量V而言，**(A-𝞴I)相当于是一个降维的线性变换**，把向量V从n维降到了0维（零向量），这就意味着：

             det(A-𝞴I) = 0

    这里可以得到一个关于𝞴的多项式，称为***特征多项式***！

    > 这里没理解的话，复习行列式那节！

*   当然，有可能不存在特征向量与特征值，比如二维线性变换的旋转，这个时候没有实数意义上的特征值

*   **如果基向量恰好是特征向量，那么线性变换对应的矩阵一定是一个对角矩阵，对角元就是特征值！**

    所以，对角矩阵的连乘，可以很容易计算，比如求如下矩阵的2018次幂与向量(x,y)^T的乘积：

          3 0
          0 2

    易知𝞴=3、𝞴=2，于是最后答案是(3^2018×x, 2^2018×y)

*   对于某种线性变换，能否通过基变换，使得新基向量是特征向量呢？

    假设线性变换矩阵为A，基变换矩阵为P，逆基变换矩阵自然为P^(-1)，

    则必有：

            P^(-1)AP = 对角矩阵

    一组基向量（同样是特征向量）构成的集合被称为一组**特征基（Eigenbasis）**

    所以，如果要计算非对角矩阵的2018次幂，一个个去计算是难以想象的，但是可以先把非对角矩阵A化为对角矩阵，对角矩阵求2018次幂很容易，再反推回原来的非对角矩阵A的2018次幂

    即，在原基向量中做n次重复的线性变换很麻烦，但是如果通过基变换后，新基向量是这个线性变换的特征向量，就可以做到快速求解，最后再逆基变换就得到原来的答案

    这里有个前提，因为全空间是基向量所张成的空间，这就意味着这种线性变换的特征向量一定要足够多，并不是所有线性变换都可以**相似对角化**的

### 抽象向量空间

*   把“向量”的概念抽象出来，看看哪些东西符合“向量”的特征？

    根据向量的加法和向量的数乘，不难想象函数符合“向量”的特征

    比如导数，就是把一个函数“变换”为另一个函数，可以理解为把向量线性变换到另一个向量上去，**而且求导是线性运算**

    线性算子和线性变换是同一个东西！

*   线性变换保持向量加法运算和数乘运算

    Linear transformations preserve addition and scalar multiplication

*   多项式空间，基函数是1、x、x2、x3、...，这个基函数集是无穷大的，任何一个多项式空间中的元素（即某个确定的多项式）可以由基函数线性组合表示，并且维数是无穷大的

    导数的矩阵描述：

          0 1 0 0 0 ...
          0 0 2 0 0 ...
          0 0 0 3 0 ...
          ...

*   所以线性代数和函数是有很大联系的：

    线性变换--线性算子

    点积--内积

    特征向量--特征函数

*   向量空间，公理满足八个条件（矩阵分析ch1有讲到），只有定义满足这8个条件，就符合了向量空间的特征

    所以，向量到底是什么，它的形式并不重要，主要看它构成的向量空间

## [理解矩阵——孟岩](https://blog.csdn.net/myan/article/details/647511)

### 矩阵是什么？

*   容纳运动是空间的本质特征，“空间”是容纳运动的一个对象集合，而变换则规定了对应空间的运动

*   在线性空间中选定基之后，向量刻画对象，矩阵刻画对象的运动，用矩阵与向量的乘法施加运动。

*   **矩阵的本质是运动的描述**

### 矩阵与变换有什么关系

*   矩阵是线性空间里“跃迁”的描述

*   所谓变换，其实就是空间里从一个点（元素/对象）到另一个点（元素/对象）的跃迁，用“跃迁”这个词太物理了，换成正牌的数学术语——变换

*   **矩阵是线性空间里的变换的描述**，在一个线性空间中，只要我们选定一组基，那么对于任何一个线性变换，都能够用一个确定的矩阵来加以描述

*   既然一个线性变换可以在不同基下有不同的描述（即不同矩阵），那怎么知道这是同一个线性变换？

    只要满足A与B相似即可！

    A = P-1BP

    #### **本质：把P看成基变换，B看成线性变换，P-1看成逆基变换，所以线性变换A是线性变换B的另一种表示！**

### 矩阵与坐标系有什么关系？

*   矩阵是由一组向量组成的，如果矩阵非奇异（可逆），那么组成这个矩阵的那一组向量也就是线性无关的了，也就可以成为度量线性空间的一个坐标系，所以，**矩阵描述了一个坐标系**

*   固定坐标系下一个对象的变换等价于固定对象所处的坐标系变换

*   **因为运动是相对的！**

*   考虑 Ma=b ，有以下两种理解：

    *   向量a经过矩阵M所描述的变换，变成了向量b

    *   向量a在坐标系M的度量下得到的度量结果为a，在另一个坐标系I（单位矩阵）的度量下度量结果为b

*   在M为坐标系的意义下，如果把M放在一个向量a的前面，形成Ma的样式，我们可以认为这是对向量a的一个环境声明

    > “注意了！这里有一个向量，它在坐标系M中度量，得到的度量结果可以表达为a。可是它在别的坐标系里度量的话，就会得到不同的结果。为了明确，我把M放在前面，让你明白，这是该向量在坐标系M中度量的结果。”

*   再看 Ma=b，其中的b并不是孤零零的，可以看成 Ma=Ib，在单位坐标系，也就是我们通常说的直角坐标系I中，有一个向量，度量的结果是b

    > “在M坐标系里量出来的向量a，跟在I坐标系里量出来的向量b，其实根本就是一个向量啊！”

*   我们平时说一个向量是[2 3 5 7 ]T，隐含了这个向量在I坐标系中的度量结果是[2 3 5 7 ]T

*   同样地，M矩阵所描述的坐标系，也是由一个基构成的，而这个基也是由向量组成的，同样存在这组向量在哪个向量下度量的问题。也就是说，表述一个矩阵的一般方法，也应该要指明其所处的基准坐标系。所谓M，其实是 IM，也就是说，M中那组基的度量是在 I 坐标系中得出的。从这个视角来看，M×N也不是什么矩阵乘法了，而是声明了一个在M坐标系中量出的另一个坐标系N，其中M本身是在I坐标系中度量出来的。

*   **对坐标系施加变换的方法，就是让表示那个坐标系的矩阵与表示那个变化的矩阵相乘**

### 矩阵的乘法

1\. 从变换的观点看，对坐标系N施加M变换，就是把组成坐标系N的每一个向量施加M变换。
​
 2\. 从坐标系的观点看，在M坐标系中表现为N的另一个坐标系，这也归结为，对N坐标系基的每一个向量，把它在I坐标系中的坐标找出来，然后汇成一个新的矩阵。
​
 3\. 至于矩阵乘以向量为什么要那样规定，那是因为一个在M中度量为a的向量，如果想要恢复在I中的真像，就必须分别与M中的每一个向量进行內积运算。</pre>

* * *

作者：myan 来源：CSDN 原文：[https://blog.csdn.net/myan/article/details/1865397](https://blog.csdn.net/myan/article/details/1865397)  版权声明：本文为博主原创文章，转载请附上博文链接！

> 原文发表于 https://www.jianshu.com/p/80218dbc9f8b, by 2018.12.05 09:06:07