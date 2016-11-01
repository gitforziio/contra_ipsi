# 脑电数据合并工具  contra_ipsi

## 概述

对scan导出的dat文件进行合并的工具包。


## 内容

### 通用基础小函数

#### structOverride.m

用法：`a = structOverride( a, b )`

作用：把结构体`b`覆盖到结构体`a`。

如果有相同的字段，会用`b`的字段覆盖`a`的字段。

#### structCombine.m

用法：`c = structCombine( a,b [,tla,tlb] )`

作用：将结构体`a`和`b`合成新的结构体`c`。

如果有相同的字段，会给原本的字段分别加上后缀`tla`和`tlb`，默认`tla='_a'`，`tlb='_b'`。

#### structForMean.m

用法：`c = structForMean( a,b [,choice] )`

作用：将包含dat数据的结构体`a`和`b`中的数据求平均值之后变成新的结构体`c`。

可选参数：`choice`表示将数据投射在左脑还是右脑，`'l'`表示左脑，`'r'`表示右脑，默认为右脑。
~~其实只要输入`'l'`开头的字符串或者输入奇数都会认为是左脑，其他字母开头的字符串或者偶数都会认为是右脑，但是不建议这样恶搞。~~

**前提假设**：结构体`a`和`b`是使用本工具包生成的dat结构体，并且其中的字段名称是正常的脑电channel名称。

#### getNameInfo.m

作用：从文件名中获得信息，写入一个结构体。

**前提假设**：文件是按照[特定格式](#file-name-format)命名的。否则输出的结构体中只有`error(=1)`和`errormsg`字段。

#### getPair.m

作用：获取与输入的脑电channel所对应的channel。



#### datReader.m

用法：`dat = datReader( filepath )`

作用：读取一个`.dat`文件的内容，放进一个结构体中。

#### datCombine.m

用法：`datc = datCombine( data, datb )`

作用：将两个读取自`.dat`文件的结构体通过`structCombine()`函数合并成新的结构体。

#### datMean.m

用法：`[datc,choice] = datMean( data, datb, choice )`

作用：将两个读取自`.dat`文件的结构体通过`structForMean()`函数求均值后成为新的结构体。

#### datPairReader.m

用法：`dat = datPairReader(patha,pathb)`

作用：直接将两个`.dat`文件读取并合并成一个结构体。

#### datMeaner.m

用法：`dat = datMeaner(patha,pathb,choice)`

作用：直接将两个`.dat`文件读取并计算平均值，然后合并成一个结构体。


#### datWriter.m

用法：`[err,exc]=datWriter(dat,filepath)`

作用：将含有dat数据的结构体以`.dat`的格式写入到文件中。

#### datNamer.m

用法：`datname = datNamer(dat,suffix)`

作用：根据含有dat数据的结构体中的信息，生成一个符合[特定格式](#file-name-format)的文件名。

#### script_2file.m

脚本。选择两个要求均值的dat文件，合成一个，投射在右脑。



## File Name Format
> 本工具所采用的特定的`.dat`文件命名格式

格式：`被试编号`+`-avg(`+`Validity或者逗号隔开的code`+`_`+`下划线相连接的条件描述`+`)`+`.dat`

例子：

- 45-avg(Cue-only_Contra).dat
- 22-avg(Invalid_Fast_Ipsi).dat
- 001-avg(Valid_Slow_Contra).dat
- 032-avg(12,13_Fast_Contra).dat
- 15-avg(17,18_Slow_Ipsi).dat
- 21-avg(19_Ipsi).dat


## 授权

随便使用和更改，提及作者更好。作者：roomcar。



