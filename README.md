# 脑电数据合并工具`contra_ipsi`

对scan导出的dat文件进行合并的工具包。

## 通用基础小函数

####structOverride.m

用法：`a = structOverride( a, b )`

作用：把结构体`b`覆盖到结构体`a`。

如果有相同的字段，会用`b`的字段覆盖`a`的字段。

####structCombine.m

用法：`c = structCombine( a,b [,tla,tlb] )`

作用：将结构体`a`和`b`合成新的结构体`c`。

如果有相同的字段，会给原本的字段分别加上后缀`tla`和`tlb`，默认`tla='_a'`，`tlb='_b'`。

####structForMean.m

用法：`c = structForMean( a,b [,choice] )`

作用：将包含dat数据的结构体`a`和`b`中的数据求平均值之后变成新的结构体`c`。

可选参数：`choice`表示将数据投射在左脑还是右脑，`'l'`表示左脑，`'r'`表示右脑，默认为右脑。
~~其实只要输入`'l'`开头的字符串或者输入奇数都会认为是左脑，其他字母开头的字符串或者偶数都会认为是右脑，但是不建议这样恶搞。~~

**前提假设**：结构体`a`和`b`是使用本工具包生成的dat结构体，并且其中的字段名称是正常的脑电channel名称。




datCombine.m
datMean.m
datMeaner.m
datNamer.m
datPairMean.m
datPairReader.m
datReader.m
datWriter.m
getNameInfo.m
getPair.m
script_2file.m
script_path.m
writedemo.m



#### script_2file

脚本。选择两个要求均值的dat文件，合成一个，投射在右脑。
