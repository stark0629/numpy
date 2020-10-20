# numpy
数据类型
常见数据类型
Python 原生的数据类型相对较少， bool、int、float、str等。这在不需要关心数据在计算机中表示的所有方式的应用中是方便的。然而，对于科学计算，通常需要更多的控制。为了加以区分 numpy 在这些类型名称末尾都加了“_”。

下表列举了常用 numpy 基本类型。

类型	备注	说明
bool_ = bool8	8位	布尔类型
int8 = byte	8位	整型
int16 = short	16位	整型
int32 = intc	32位	整型
int_ = int64 = long = int0 = intp	64位	整型
uint8 = ubyte	8位	无符号整型
uint16 = ushort	16位	无符号整型
uint32 = uintc	32位	无符号整型
uint64 = uintp = uint0 = uint	64位	无符号整型
float16 = half	16位	浮点型
float32 = single	32位	浮点型
float_ = float64 = double	64位	浮点型
str = unicode = str0 = unicode		Unicode 字符串
datetime64		日期时间类型
timedelta64		表示两个时间之间的间隔
创建数据类型
numpy 的数值类型实际上是 dtype 对象的实例。

class dtype(object):
    def __init__(self, obj, align=False, copy=False):
        pass
每个内建类型都有一个唯一定义它的字符代码，如下：

字符	对应类型	备注
b	boolean	'b1'
i	signed integer	'i1', 'i2', 'i4', 'i8'
u	unsigned integer	'u1', 'u2' ,'u4' ,'u8'
f	floating-point	'f2', 'f4', 'f8'
c	complex floating-point	
m	timedelta64	表示两个时间之间的间隔
M	datetime64	日期时间类型
O	object	
S	(byte-)string	S3表示长度为3的字符串
U	Unicode	Unicode 字符串
V	void
【例】

import numpy as np

a = np.dtype('b1')
print(a.type)  # <class 'numpy.bool_'>
print(a.itemsize)  # 1

a = np.dtype('i1')
print(a.type)  # <class 'numpy.int8'>
print(a.itemsize)  # 1
a = np.dtype('i2')
print(a.type)  # <class 'numpy.int16'>
print(a.itemsize)  # 2
a = np.dtype('i4')
print(a.type)  # <class 'numpy.int32'>
print(a.itemsize)  # 4
a = np.dtype('i8')
print(a.type)  # <class 'numpy.int64'>
print(a.itemsize)  # 8

a = np.dtype('u1')
print(a.type)  # <class 'numpy.uint8'>
print(a.itemsize)  # 1
a = np.dtype('u2')
print(a.type)  # <class 'numpy.uint16'>
print(a.itemsize)  # 2
a = np.dtype('u4')
print(a.type)  # <class 'numpy.uint32'>
print(a.itemsize)  # 4
a = np.dtype('u8')
print(a.type)  # <class 'numpy.uint64'>
print(a.itemsize)  # 8

a = np.dtype('f2')
print(a.type)  # <class 'numpy.float16'>
print(a.itemsize)  # 2
a = np.dtype('f4')
print(a.type)  # <class 'numpy.float32'>
print(a.itemsize)  # 4
a = np.dtype('f8')
print(a.type)  # <class 'numpy.float64'>
print(a.itemsize)  # 8

a = np.dtype('S')
print(a.type)  # <class 'numpy.bytes_'>
print(a.itemsize)  # 0
a = np.dtype('S3')
print(a.type)  # <class 'numpy.bytes_'>
print(a.itemsize)  # 3

a = np.dtype('U3')
print(a.type)  # <class 'numpy.str_'>
print(a.itemsize)  # 12
数据类型信息
Python 的浮点数通常是64位浮点数，几乎等同于 np.float64。

NumPy和Python整数类型的行为在整数溢出方面存在显着差异，与 NumPy 不同，Python 的int 是灵活的。这意味着Python整数可以扩展以容纳任何整数并且不会溢出。

Machine limits for integer types.

class iinfo(object):
    def __init__(self, int_type):
        pass
    def min(self):
        pass
    def max(self):
        pass
【例】

import numpy as np

ii16 = np.iinfo(np.int16)
print(ii16.min)  # -32768
print(ii16.max)  # 32767

ii32 = np.iinfo(np.int32)
print(ii32.min)  # -2147483648
print(ii32.max)  # 2147483647
Machine limits for floating point types.

class finfo(object):
    def _init(self, dtype):
【例】

import numpy as np

ff16 = np.finfo(np.float16)
print(ff16.bits)  # 16
print(ff16.min)  # -65500.0
print(ff16.max)  # 65500.0
print(ff16.eps)  # 0.000977

ff32 = np.finfo(np.float32)
print(ff32.bits)  # 32
print(ff32.min)  # -3.4028235e+38
print(ff32.max)  # 3.4028235e+38
print(ff32.eps)  # 1.1920929e-07
In [ ]:
