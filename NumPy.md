# NumPy用于处理数组，数组对象称为ndarray

## 创建——array（）函数 arr=np.array([1,2,3])

ndim属性检查维数 arr.ndim

array()函数中的ndmin参数定义维数，arr=np.array([1,2,3]，ndmin=3)

## 索引

```
arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])

print(arr[0, 1, 2])
```

第一个数字代表第一个维度，其中包含两个数组：

[[1, 2, 3], [4, 5, 6]]

然后：

[[7, 8, 9], [10, 11, 12]]

由于我们选择了 `0`，所以剩下第一个数组：

[[1, 2, 3], [4, 5, 6]]

第二个数字代表第二维，它也包含两个数组：

[1, 2, 3]

然后：

[4, 5, 6]

因为我们选择了 `1`，所以剩下第二个数组：

[4, 5, 6]

第三个数字代表第三维，其中包含三个值：

4
5
6

由于我们选择了 `2`，因此最终得到第三个值：

6

### 负索引

arr[-1]返回倒数第一个元素

## 数组裁切

```
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7])

print(arr[1:5:2])
```

结果：[2,4]

### 裁切2D数组

```python
import numpy as np

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])

print(arr[0:2, 1:4])
```

[[2 3 4]
 [7 8 9]]

## 数据类型

默认情况下，Python 拥有以下数据类型：

- `strings` - 用于表示文本数据，文本用引号引起来。例如 "ABCD"。

- `integer` - 用于表示整数。例如 -1, -2, -3。

- `float` - 用于表示实数。例如 1.2, 42.42。

- `boolean` - 用于表示 True 或 False。

- `complex` - 用于表示复平面中的数字。例如 1.0 + 2.0j，1.5 + 2.5j。

  NumPy 有一些额外的数据类型，并通过一个字符引用数据类型

  以下是 NumPy 中所有数据类型的列表以及用于表示它们的字符。

  - i` - 整数

  - `b` - 布尔

  - `u` - 无符号整数

  - `f` - 浮点

  - `c` - 复合浮点数

  - `m` - timedelta

  - `M` - datetime

  - `O` - 对象

  - `S` - 字符串

  - `U` - unicode 字符串

  - `V` - 固定的其他类型的内存块 ( void )

    dtype属性，返回数组的数据类型

    arr.dtype

    `array()` 函数来创建数组，该函数可以使用可选参数：`dtype`，它允许我们定义数组元素的预期数据类型：arr = np.array([1, 2, 3, 4], dtype='S')

    更改现有数组的数据类型的最佳方法，是使用 `astype()` 方法复制该数组。

    `astype()` 函数创建数组的副本，并允许您将数据类型指定为参数。

    ```python
    arr = np.array([1.1, 2.1, 3.1])
    
    newarr = arr.astype('i')
    ```

## 副本和视图

副本和数组视图之间的主要区别在于副本是一个新数组，而这个视图只是原始数组的视图。

副本拥有数据，而视图不拥有数据

### 检查数组是否拥有数据

每个 NumPy 数组都有一个属性 `base`，如果该数组拥有数据，则这个 base 属性返回 `None`。

否则，`base` 属性将引用原始对象。

```python
x = arr.copy()
y = arr.view()

print(x.base)
print(y.base)
```

None
[1 2 3 4 5]

## 数组的形状

数组的形状是每个维中元素的数量。

## 获取数组的形状

NumPy 数组有一个名为 `shape` 的属性，该属性返回一个**元组**，每个索引具有相应元素的数量。

```python
import numpy as np

arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])

print(arr.shape)
```

(2, 4)

## 数组重塑

重塑意味着更改数组的形状。

数组的形状是每个维中元素的数量。

通过重塑，我们可以添加或删除维度或更改每个维度中的元素数量。

将以下具有 12 个元素的 1-D 数组转换为 2-D 数组。

最外面的维度将有 4 个数组，每个数组包含 3 个元素：

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])

newarr = arr.reshape(4, 3)

print(newarr)
```

[[ 1 2 3]
 [ 4 5 6]
 [ 7 8 9]
 [10 11 12]]

将以下具有 12 个元素的 1-D 数组转换为 3-D 数组。

最外面的维度将具有 2 个数组，其中包含 3 个数组，每个数组包含 2 个元素：

```
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])

newarr = arr.reshape(2, 3, 2)

print(newarr)
```

[[[ 1 2]
 [ 3 4]
 [ 5 6]]

 [[ 7 8]
 [ 9 10]
 [11 12]]]

reshape出来的数组是一个视图，因为对他调用base返回的是原来的数组

## 未知的维

您可以使用一个“未知”维度。

这意味着您不必在 reshape 方法中为维度之一指定确切的数字。

传递 `-1` 作为值，NumPy 将为您计算该数字。

## 展平数组

展平数组（Flattening the arrays）是指将多维数组转换为 1D 数组。

我们可以使用 `reshape(-1)` 来做到这一点。

## 数组迭代

迭代意味着逐一遍历元素。

如果我们迭代一个 n-D 数组，它将逐一遍历第 n-1 维。

如需返回实际值、标量，我们必须迭代每个维中的数组。

迭代到标量：

```python
import numpy as np

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])

for x in arr:
  for y in x:
    for z in y:
      print(z)
```

1
2
3
4
5
6
7
8
9
10
11
12

在基本的 `for` 循环中，迭代遍历数组的每个标量，我们需要使用 n 个 `for` 循环，但函数 `nditer()` 是一个辅助函数，从非常基本的迭代到非常高级的迭代都可以使用。

遍历以下 3-D 数组：

```python
import numpy as np

arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])

for x in np.nditer(arr):
  print(x)
```

1
2
3
4
5
6
7
8

## 迭代不同数据类型的数组

我们可以使用 `op_dtypes` 参数，并传递期望的数据类型，以在迭代时更改元素的数据类型。

NumPy 不会就地更改元素的数据类型（元素位于数组中），因此它需要一些其他空间来执行此操作，该额外空间称为 buffer，为了在 `nditer()` 中启用它，我们传参 `flags=['buffered']`。

以字符串形式遍历数组：

```
import numpy as np

arr = np.array([1, 2, 3])

for x in np.nditer(arr, flags=['buffered'], op_dtypes=['S']):
  print(x)
```

## 使用 ndenumerate() 进行枚举迭代

枚举是指逐一提及事物的序号。

有时，我们在迭代时需要元素的相应索引，对于这些用例，可以使用 `ndenumerate()` 方法。

枚举以下 2D 数组元素：

```python
import numpy as np

arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])

for idx, x in np.ndenumerate(arr):
  print(idx, x)
```

(0, 0) 1
(0, 1) 2
(0, 2) 3
(0, 3) 4
(1, 0) 5
(1, 1) 6
(1, 2) 7
(1, 3) 8

## 连接 NumPy 数组

连接意味着将两个或多个数组的内容放在单个数组中。在 NumPy 中，我们按轴连接数组。

我们传递了一系列要与轴一起连接到 `concatenate()` 函数的数组。如果未显式传递轴，则将其视为 0。

沿着行 (axis=1) 连接两个 2-D 数组：

```python
import numpy as np

arr1 = np.array([[1, 2], [3, 4]])

arr2 = np.array([[5, 6], [7, 8]])

arr = np.concatenate((arr1, arr2), axis=1)

print(arr)
```

[[1 2 5 6]
 [3 4 7 8]]

## 使用堆栈函数连接数组

堆栈与级联相同，唯一的不同是堆栈是沿着新轴完成的。

我们可以沿着第二个轴连接两个一维数组，这将导致它们彼此重叠，即，堆叠（stacking）。

我们传递了一系列要与轴一起连接到 `concatenate()` 方法的数组。如果未显式传递轴，则将其视为 0。

```python
import numpy as np

arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.stack((arr1, arr2), axis=1)

print(arr)
```

[[1 4]
 [2 5]
 [3 6]]

## 沿行堆叠

NumPy 提供了一个辅助函数：`hstack()` 沿行堆叠。

### 实例

```python
import numpy as np

arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.hstack((arr1, arr2))

print(arr)
```

[1 2 3 4 5 6]

## 沿列堆叠

NumPy 提供了一个辅助函数：`vstack()` 沿列堆叠。

### 实例

```python
import numpy as np

arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.vstack((arr1, arr2))

print(arr)
```

[[1 2 3]
 [4 5 6]]

## 沿高度堆叠（深度）

NumPy 提供了一个辅助函数：`dstack()` 沿高度堆叠，该高度与深度相同。

### 实例

```python
import numpy as np

arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.dstack((arr1, arr2))

print(arr)
```

[[[1 4]
 [2 5]
 [3 6]]]

## 拆分 NumPy 数组

拆分是连接的反向操作。

连接（Joining）是将多个数组合并为一个，拆分（Spliting）将一个数组拆分为多个。

我们使用 `array_split()` 分割数组，将要分割的数组和分割数传递给它。

`array_split()` 方法的返回值是一个包含每个分割的数组。

如果将一个数组拆分为 3 个数组，则可以像使用任何数组元素一样从结果中访问它们。

## 分割二维数组

拆分二维数组时，请使用相同的语法。

使用 `array_split()` 方法，传入要分割的数组和想要分割的数目。

import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15], [16, 17, 18]])

newarr = np.array_split(arr, 3)

print(newarr)

[array([[1, 2, 3],
    [4, 5, 6]]), array([[ 7, 8, 9],
    [10, 11, 12]]), array([[13, 14, 15],
    [16, 17, 18]])]

沿行把这个 2-D 拆分为三个 2-D 数组。

```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15], [16, 17, 18]])

newarr = np.array_split(arr, 3, axis=1)

print(newarr)
```

[array([[ 1],
    [ 4],
    [ 7],
    [10],
    [13],
    [16]]), array([[ 2],
    [ 5],
    [ 8],
    [11],
    [14],
    [17]]), array([[ 3],
    [ 6],
    [ 9],
    [12],
    [15],
    [18]])]

另一种解决方案是使用与 `hstack()` 相反的 `hsplit()`。

## 搜索数组

您可以在数组中搜索（检索）某个值，然后返回获得匹配的索引。

要搜索数组，请使用 `where()` 方法。

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 4, 4])

x = np.where(arr == 4)

print(x)
```

上例会返回一个元组：`(array([3, 5, 6],)`

意思就是值 4 出现在索引 3、5 和 6。

## 搜索排序

有一个名为 `searchsorted()` 的方法，该方法在数组中执行二进制搜索，并返回将在其中插入指定值以维持搜索顺序的索引。

假定 `searchsorted()` 方法用于排序数组。

从右边开始查找应该插入值 7 的索引：

```python
import numpy as np

arr = np.array([6, 7, 8, 9])

x = np.searchsorted(arr, 7, side='right')

print(x)
```

2

查找应在其中插入值 2、4 和 6 的索引：

```python
import numpy as np

arr = np.array([1, 3, 5, 7])

x = np.searchsorted(arr, [2, 4, 6])

print(x)
```

返回值是一个数组：`[1 2 3]` 包含三个索引，其中将在原始数组中插入 2、4、6 以维持顺序。

## 数组排序

排序是指将元素按有序顺序排列。

有序序列是拥有与元素相对应的顺序的任何序列，例如数字或字母、升序或降序。

NumPy ndarray 对象有一个名为 `sort()` 的函数，该函数将对指定的数组进行排序。

**注释：**此方法返回数组的副本，而原始数组保持不变。

## 对 2-D 数组排序

如果在二维数组上使用 sort() 方法，则将对两个数组进行排序：

### 实例

对 2-D 数组排序

```python
import numpy as np

arr = np.array([[3, 2, 4], [5, 0, 1]])

print(np.sort(arr))
```

[[2 3 4]
 [0 1 5]]

## 数组过滤

**从现有数组中取出一些元素并从中创建新数组称为过滤（filtering）。**

在 NumPy 中，我们使用布尔索引列表来过滤数组。

布尔索引列表是与数组中的索引相对应的布尔值列表。

如果索引处的值为 `True`，则该元素包含在过滤后的数组中；如果索引处的值为 `False`，则该元素将从过滤后的数组中排除。

```python
import numpy as np

arr = np.array([61, 62, 63, 64, 65])

x = [True, False, True, False, True]

newarr = arr[x]

print(newarr)
```

## 创建过滤器数组——即创建布尔索引列表

### 实例

创建一个过滤器数组，该数组仅返回原始数组中的偶数元素：

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7])

# 创建一个空列表
filter_arr = []

# 遍历 arr 中的每个元素
for element in arr:
  # 如果元素可以被 2 整除，则将值设置为 True，否则设置为 False
  if element % 2 == 0:
    filter_arr.append(True)
  else:
    filter_arr.append(False)

newarr = arr[filter_arr]

print(filter_arr)
print(newarr)
```

[False, True, False, True, False, True, False]
[2 4 6]

## 直接从数组创建过滤器

我们可以在条件中直接替换数组而不是 iterable 变量

### 实例

创建一个仅返回大于 62 的值的过滤器数组：

```python
import numpy as np

arr = np.array([61, 62, 63, 64, 65])

filter_arr = arr > 62

newarr = arr[filter_arr]

print(filter_arr)
print(newarr)
```

[False False True True True]
[63 64 65]

## 生成随机数

NumPy 提供了 random 模块来处理随机数。

### 实例

生成一个 0 到 100 之间的随机整数：

```python
from numpy import random

x = random.randint(100)

print(x)
```

## 生成随机浮点

random 模块的 `rand()` 方法返回 **0 到 1** 之间的随机浮点数。

## 生成随机数组

### 实例

生成有 3 行的 2-D 数组，每行包含 5 个从 0 到 100 之间的随机整数：

```python
from numpy import random

x = random.randint(100, size=(3, 5))

print(x)
```

[[35 76 81 51 22]
 [85 17 60 22 27]
 [56 53 75 94 16]]

浮点数利用rand（）即可

## 从数组生成随机数

`choice()` 方法使您可以基于值数组生成随机值。

`choice()` 方法将数组作为参数，并随

### choice()` 方法还允许您返回一个值数组。

请添加一个 `size` 参数以指定数组的形状。

### 实例

生成由数组参数（3、5、7 和 9）中的值组成的二维数组：

```
from numpy import random

x = random.choice([3, 5, 7, 9], size=(3, 5))

print(x)
```

机返回其中一个值。

# NumPy ufuncs

ufuncs 指的是“通用函数”（Universal Functions），它们是对 ndarray 对象进行操作的 NumPy 函数。

## 为什么要使用 ufuncs？

ufunc 用于在 NumPy 中实现矢量化，这比迭代元素要快得多。

它们还提供广播和其他方法，例如减少、累加等，它们对计算非常有帮助。

ufuncs 还接受其他参数，比如：

`where` 布尔值数组或条件，用于定义应在何处进行操作。

`dtype` 定义元素的返回类型。

`out` 返回值应被复制到的输出数组。

## 什么是向量化？

将迭代语句转换为基于向量的操作称为向量化。

通过 ufunc，我们可以使用 `add()` 函数：

```python
import numpy as np

x = [1, 2, 3, 4]
y = [4, 5, 6, 7]
z = np.add(x, y)

print(z)
```

[ 5 7 9 11]