- 准备步骤（win）
  collapsed:: true
	- 环境部署
	  collapsed:: true
		- 可以直接下载python.exe安装，
		- 环境变量
		  collapsed:: true
			- 设置中搜索“环境”，进入“编辑系统的环境变量”，
			- 在path中加入python解释器的位置，然后重启powershell，就可以在powershell里直接使用python，
		- Linux一般自带了python，可以直接在终端输入python3运行，
	- 编辑器
	  collapsed:: true
		- IDLE（python自带的编辑器）
		- jupyter notebook
		  collapsed:: true
			- 在anaconda prompt中输入'jupyter lab'可以打开jupyter notebook,
			- 打开后，可以使用'http://localhost:8888/lab' 打开新的一页，
	- anaconda的使用
	  collapsed:: true
		- 官方指南https://conda.io/projects/conda/en/latest/index.html，
		- 更换镜像
		  collapsed:: true
			- anaconda navigator → environments → channels，更换至https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/，
		- 更换根目录`cd C:\Users` ，
		- 在cmd中输入`.../anaconda3/Scripts/activate`可以激活anaconda prompt，
			- （在powershell中输入不成功，原因未知），
- python程序的基本组成
  collapsed:: true
	- 解释器
	  collapsed:: true
		- 可以使用`python3`命令打开python解释器，
		- 可以直接输入代码并运行，
		- `ctrl + z`可以退出python解释器，
	- 代码编写
	  collapsed:: true
		- 编写代码，并保存为.py扩展名的文件，
		- 脚本模式与交互模式
		  collapsed:: true
			- 交互模式：作为解释型语言，可以在python解释器中直接输入代码并运行，
			- 脚本模式：将代码保存到文件内，运行解释器并执行脚本，
			- 脚本模式不会展示结果，而是需要利用print函数等语句才会显示结果，
	- 代码执行
	  collapsed:: true
		- python没有代码编译过程，
		- 可以直接使用python3 file.py执行对应的文件，
		- 脚本模式运行
		  collapsed:: true
			- 可以使用`if __name__ == '__main__':`语句设置条件；
				- 若程序以脚本的形式运行，则if语句返回True，语句后的代码将被执行；
				- 当程序作为模块被导入时，if语句返回False（此时`__name__`的值为模块的名称，不再为main），从而语句后的代码会被跳过，
		- 接受命令行参数
		  collapsed:: true
			- sys模块中的sys.argv方法可以接受命令行中传入的参数（一个或多个），并将其存储为一个字符串组成的列表['file.py', 'arg1', 'arg2'...] ，
			- （输入，输出的重定向）
			- （argparse模块，fileinput模块），
	- 程序（py文件）
	  collapsed:: true
		- 临时程序与长期程序
		  collapsed:: true
			- 临时程序：运行一段时间并输出结果，运行结束后不保存数据；再次运行时仍以全新状态开始，
			- 长期程序：维持运行状态，将部分数据记录在存储设备中（例如对硬盘上的文件进行读写）；再次运行时从上次中断的地方继续，
	- 中断程序运行
	  collapsed:: true
		- 采用Ctrl+C快捷键可以强制终止程序执行，显示为“KeyboardInterrupt”，且不会关闭shell，
		- 也可以尝试直接关闭shell进程，
- 基本编程语法
  collapsed:: true
	- 基本语法
	  collapsed:: true
		- 不同于Java，C，python不用大括号和分号来标识每个语句，而是利用缩进（空格数量）来标识，
		- 应有缩进的语句没有缩进会报错，不需要缩进的语句的额外缩进也会报错，
		- python也支持用分号区分多个语句，但不常用，
		- python中，定义函数与控制语句需要使用冒号标识，
		- 一般语句只能写在一整行（即换行符会导致报错），但可以利用反斜杠\ 来拆分语句，
		- python区分大小写，
		- 类似C语言，python的代码也为从上到下执行；即对变量，函数等的使用语句需要写在声明语句的后方，
	- 变量命名
	  collapsed:: true
		- python区分大小写，可以包含字母、数字和下划线，
		  collapsed:: true
			- 变量名称不能为纯数字，也不能包含其他字符（如*、&等），关键字也不能被用作变量名，
		- 模块名一般不包含下划线，函数名和变量名一般用下划线来增加可读性，
		- 模块、函数、变量一般全小写，只有类的单词的首字母一般用大写，
		- 需要的部分常量（如PI、E等）一般字母全大写，
		- 在类中，一般使用一个空行来分隔方法；而在模块中，可使用两个空行来分隔类，
		- （python关键字）
	- 注释
	  collapsed:: true
		- `#` 符号和`'''`标识出来的语句会被python当作注释，不会被执行，
		- 由于注释会被编译器忽略，因此理论上注释*可以*写在代码的*任何位置*，
		- 一般将注释写在函数代码的下方（需要缩进），说明使用函数时应该了解的关键信息；如函数的作用，不同实参的含义等，即
		- ```def countpi(n):
		  def countpi(n):
		      ''' use arctan's taylor series to count pi '''
		  	statements
		  ```
		- 代码所实现的行为一般较容易理解，因此注释应注重描写代码所表达的隐含意思，如变量的含义或与上下文的联系，
		- 设计良好的函数应该是容易解释的，反之，若函数的作用难以解释，则说明函数还有一定的改进空间，
- 数据类型
  collapsed:: true
	- 基本数据类型
	  collapsed:: true
		- 变量声明
		  collapsed:: true
			- 不同于C语言，python变量在使用前无序“声明”，也不用显式指定类型，
			- 可以直接给变量赋值并使用，
		- 数值
		  collapsed:: true
			- 整型数int，浮点数float
			  collapsed:: true
				- 整数的位数理论上没有限制（只受限于计算机的内存），
				- 浮点数只能有16位小数（多余的位数可以输入，但在赋值时会被舍去），
				- python中可以由整数算得浮点数，但浮点数间的运算只会产生浮点数，
			- 复数complex
			  collapsed:: true
				- python中内置了复数类（complex），
				- 由实部和虚部组成，虚部带有符号j；应注意j为未定义变量，而1j才是复数单位i，
				- 复数间的运算只会产生复数，如1j *1j会得到-1 + 0j，而不是整数-1，
				- 可以用x.real 获得实部，x.imag获得虚部（都为浮点数类型），
				- 示例
				- ```
				  num = 1 + 1j
				  type(num)
				  #<class 'complex'>
				  numr = num.real
				  print(numr)
				  ```
		- 布尔值bool
		  collapsed:: true
			- 只有True和False两种结果，
			- True类似数值1，False类似数值0，即可以对布尔值进行数值运算，
			- 反之，0可以被用作条件False，其它数值则可以被用作条件True，
		- （字符）
		  collapsed:: true
			- python中没有字符类型，一个字符也是字符串，
		- 类型转换
		  collapsed:: true
			- 可以使用int，float，str函数转换数据类型，
			- 前提为数据可以转换，如字符串'2'可以转换为整数2，
			- int函数可以接受第二个可选参数， 用来指定转换输入的字符串时采用的数值进制，
	- 高阶数据类型
		- 列表list
			- 概述
			  collapsed:: true
				- 类似C中的数组类型，但实际上更类似一个链表，
				  collapsed:: true
					- 其实现位于python/Cpython/Objects/listObject.c中，
					- 接口位于python/Cpython/Include/listObject.h中，
					- list类的定义位于/stdlib/builtins.pyi中，
				- python中的列表无需预先分配空间，
				- 其变量可以为任何（基本）变量类型，也可以为列表，
			- 列表的应用
			  collapsed:: true
				- 列表是最常用的python数据结构之一，
				- 大部分常用列表操作可以归为映射，筛选和归并三类，（一般需要通过遍历列表中的元素来实现）
					- 映射：将给定列表中的每个元素用函数转化为另一个元素，并生成新的列表，
					- 筛选：根据给定特征选出给定列表中的部分元素，并生成新的列表，
					- 归并：将列表中的元素根据给定规则整合为单一的输出值，
			- 声明
			  collapsed:: true
				- 声明和赋值`list1 = [1, 2, "str"]`，
				  collapsed:: true
					- 由方括号[]括起来的输入会被解释为列表，
					- 用逗号，连接的不同数据会被解释为列表的元素，
					- 数据可以是各种类型（数值；字符串、列表、字典等），
				- 空列表的声明`list1 = []`，
				  collapsed:: true
					- 该语句声明了一个列表变量list1，后续可以对其进行列表操作，
				- （列表解析）
					- 可以利用for循环创建列表的元素，
					- 示例：`[i for i in range(1,6)]`等同于列表`[1, 2, 3, 4, 5]`，
			- 基本操作
				- index
				  collapsed:: true
					- 索引
					  collapsed:: true
						- list1[n]*返回*列表中的第n - 1个元素，
						- 索引从0开始而并非从1，即[0]表示第一个字母，
						- 索引也可以为反方向，即负数索引[-1]，代表最后一个字符，
						- 对于嵌套列表，也可以嵌套使用下标，如(list1[1])[1]或list[1][1]，但应注意对象是否为仍为列表，
					- 切片
					  collapsed:: true
						- [x: y]*返回*从第x个字符到第y个字符的*列表*片段（*不包括*第y个），
						- 切片也可以为负方向，
						- 下标x/y可以省略，省略时表示从头部/尾部开始；
						- 两个都省略时则会返回原列表，
					- 修改
					  collapsed:: true
						- 可以通过下标方法修改已有的元素，
						- 示例：`list1[n] = arg1`可以将列表中的第n + 1个元素替换为arg1，
						- 虽然列表的长度可变，但*不能*通过*下标*操作添加超过列表长度的元素（对空列表也一样），
						  collapsed:: true
							- 即对于列表`list1 = []`，赋值操作`list1[0] = 1`会报错，
				- 数学符号运算
				  collapsed:: true
					- 加号可以将两个列表拼接为一个列表（而不是将每个对应值相加），
					- 乘号可以形成新的重复几次的列表（并非将列表中的每个值相乘），
					- 运算符号不会改变原列表，而是会返回新的列表，
					- 列表不能进行减法、除法运算，
				- 布尔运算
				  collapsed:: true
					- in运算符
					  collapsed:: true
						- 可以判断元素是否在列表中，但不能识别嵌套列表中的元素，
						- 可以利用下标进一步识别嵌套列表中的元素，
			- 函数与方法
			  collapsed:: true
				- 函数
				  collapsed:: true
					- 基本使用方法为func(list)，一般有返回值，
					- len函数
					  collapsed:: true
						- 返回列表的元素数量，
						- 列表中嵌套的一整个列表会被视为一个“元素”，
					- sum函数
					  collapsed:: true
						- 可以对数值型列表进行求和，不能用于复合元素列表，
					- max、min函数
					  collapsed:: true
						- 返回列表中的最大，最小值，一般用于数值列表，
						- 但字符串列表也可以应用，比较按照字典顺序进行，
						- 复合元素列表不能进行比较，即max、min函数会报TypeError，
					- sorted函数
					  collapsed:: true
						- 可以将列表中的元素进行排序，返回排序后的列表，
						- （相比之下，sort方法则是直接对原列表排序），
						- 复合元素列表不能进行比较，即sorted函数会报TypeError，
						- 设置reverse = True，可以按照逆序排序列表，
					- del函数
						- `del(list1[n])`可以删除n索引位置的元素，
						- del不能作为方法使用，
				- 方法
				  collapsed:: true
					- 方法的基本使用方式为点标记法，即`list1.method()`，
					  collapsed:: true
						- python中的数据类型（list，str等）都以类的形式存在，
						- 因此对数据的操作类似于对类中的元素的操作，
						- 方法可能不需要参数，但仍需要加上空括号来表示对方法的调用，
					- 注意事项
					  collapsed:: true
						- python中列表为可修改的对象，
						- 所以大部分方法都是*直接修改*原列表，不产生*返回值*（即返回None），
						- 为了保险起见，可以创造关于原列表的副本，
					- 元素修改
					  collapsed:: true
						- append方法
						  collapsed:: true
							- `list1.append(arg1)`，会将arg1作为一个元素添加到列表*末尾*，即列表对象arg1也会被当作一个元素，
							- append只能接受*一个*参数，
						- extend方法
						  collapsed:: true
							- `list1.extend(list2)`将*一个*列表list2（仅接受列表）中的元素按原列表中的顺序添加到list1末尾，
							- extend只能接受*一个*参数，
						- insert方法
						  collapsed:: true
							- `list1.insert(n, arg1)`，将元素arg1插入到列表的 n 索引位置*前方*，
						- remove方法
						  collapsed:: true
							- `list1.remove(arg1)`会从第一个元素开始搜索列表，并删除列表中的*第一个*arg1元素（只删除第一个），
							- 列表中不存在arg1则会引发错误，
						- pop方法
						  collapsed:: true
							- `list1.pop(n)`会删除列表 n 索引位置的元素，并*返回*该元素，
							- 不输入参数 n 时会删除最后一个对象，
						- （del函数）
						- （copy方法）
							- `lista.copy()`返回列表lista的浅副本，
					- 元素搜索
					  collapsed:: true
						- index方法
						  collapsed:: true
							- `list1.index(arg1)`，查找列表中是否有arg1，并*返回*arg1的位置（int值）；
							- 若有多个arg1则会返回第一个arg1的位置，
							- 列表中不存在arg1则会引发错误，
						- count方法
						  collapsed:: true
							- `list1.count(arg1)`查找列表中是否有arg1，并*返回*arg1的数量（int值）；
							- 列表中不存在arg1则会引发错误，
					- 排序
					  collapsed:: true
						- sort方法
							- `list1.sort()`可以对列表进行排序，
							- 可选参数
							  collapsed:: true
								- 参数key
									- 可以用于“自定义”排序规则，
								- 参数reverse
									- 设置reverse = True，可以按照逆序排序列表，
							- 嵌套列表排序
							  collapsed:: true
								- python规定的排序规则为先升序比较第一个元素， 再升序比较第二个元素，以此类推，
							- sort只能对列表进行排序，字符串、元组、字典没有sort方法，
						- reverse方法
							- `list1.reverse()`可以将列表按逆序重新排列，
							- 也可使用sort方法的附带参数reverse = True来实现，
			- 列表的“复制”
			  collapsed:: true
				- 赋值
				  collapsed:: true
					- 直接赋值`listb = lista`只是将名称listb作为了lista的别名，
					- 即修改lista会导致listb的同步变化，
				- 浅复制
					- 操作`lista[:]`，`lista + []`，`lista * 1`，`lista.copy()`都会返回原列表lista，这样得到的数据称为浅（shallow）副本，
					- 修改浅副本中的元素不会影响原列表lista，
					- 然而，若lista中有*嵌套列表*，则修改浅副本会导致原列表的嵌套列表的同步变化，
				- 深复制
				  collapsed:: true
					- copy模块的deepcopy函数可以得到列表的深副本，
					- 修改深副本中的嵌套列表的值对原列表没有影响，
		- 元组tuple
			- 概述
			  collapsed:: true
				- 有顺序的多个值组成的序列，由括号()括起来，元素间用逗号连接，
				- 类似列表，但元组的元素不可修改，
				- 不同于列表，元组中的值是不可变的，因此可用作字典的键，
				  collapsed:: true
					- 然而，元组中的元素可以为可变对象（列表等），
					- 包含了可变对象的元组不能用作字典的键，
			- 声明
				- 声明和赋值`tuple1 = (1, 2, "str")`，
				  collapsed:: true
					- 由括号()括起来的输入会被解释为元组，
					- 用逗号，连接的不同数据会被解释为元组的元素，
					- 然而，直接用逗号隔开各个取值的输入也会被python识别为元组；即应将多个用逗号隔开的值看成一个元组，而非离散的各个元素，
				- 空元组的声明`tuple1 = ()`，
				  collapsed:: true
					- 该语句声明了一个元组变量list1，后续可以对其进行操作，
			- 基本操作
				- index
				  collapsed:: true
					- 索引，切片等操作类似列表，
					- 元组中的元素*不能*通过下标方法修改，
				- 布尔运算
			- 函数与方法
			  collapsed:: true
				- 函数
				  collapsed:: true
					- 可以用list(), tuple()函数在列表和元组间转换对象，
					- zip函数
				- 方法
				  collapsed:: true
					- 元组方法的使用类似列表，
					- 然而， 由于元组不可更改，所以修改列表的方法都无法使用，
					- 元素搜索
						- index方法
						  collapsed:: true
							- `list1.index(arg1)`，查找列表中是否有arg1，并*返回*arg1的位置（int值）；
							- 若有多个arg1则会返回第一个arg1的位置，
							- 列表中不存在arg1则会引发错误，
						- count方法
						  collapsed:: true
							- `list1.count(arg1)`查找列表中是否有arg1，并*返回*arg1的数量（int值）；
							- 列表中不存在arg1则会引发错误，
		- 字符串str
			- 概述
			  collapsed:: true
				- python中的字符串类似C中的字符串，但同python的列表相同，使用时无需预先分配空间，
				- python字符串的结尾不需要空字符，因为字符串的长度是在声明时确定的，
				- 字符串的基本操作也类似列表，但字符串的元素不能直接修改，
			- 声明
			  collapsed:: true
				- 基本语法`str1 = "Hello."`，
				- 由双引号标记的一段字符会被解释为一个字符串，
				  collapsed:: true
					- 引号中的所有字符（包括空格、字母、数字等）会被看作一个整体，
					- 单引号和三引号标记的字符也会被识别为字符串，但一般使用双引号，
				- 单引号和双引号标记的字符串不能换行，但可以利用反斜杠\ 来拆分语句，
				  collapsed:: true
					- 即`"He \\n llo"`会被拼接为"Hello"，
					- 三引号标记的字符串可以换行，但一般只用于注释，
			- 转义字符
			  collapsed:: true
				- \ 符号可以将后边的字符变为其他含义，
				  collapsed:: true
					- `\t`代表缩进，`\n`代表换行；
					- `\ "`，`\ \`则分别代表"（不会被当作字符串的结束符）和\本身，
				- 字符串存储是转义字符，只有使用print函数打印出字符串时，转义字符才会变为对应含义，
				  collapsed:: true
					- print函数默认会在字符串末尾添加换行符，若字符串已经以换行符`\n`结尾则会导致两次换行，
					- 可以将print函数的end参数设为""来使print函数不再添加换行符，
				- Unicode字符
				  collapsed:: true
					- \ 也可以将后面的字符转为八进制、十六进制的数字，
			- 基本操作
				- index
				  collapsed:: true
					- 索引
					  collapsed:: true
						- str1[n]返回字符串中的第n + 1个字符（仍然为字符串类型），
						- 索引从0开始而并非从1，即[0]表示第一个字符，
						- 索引也可以为反方向，即负数索引[-1]，代表最后一个字符，
					- 切片
					  collapsed:: true
						- [x: y]返回从第x个字符到第y个字符的字符串片段（不包括第y个），
						- 切片也可以为负方向，
						- 下标x/y可以省略，省略时表示从头部/尾部开始；
						- 两个都省略时则会复制原字符串，
					- 不同于列表，字符串中的元素*不能*通过下标方法修改，
				- 数学符号运算
				  collapsed:: true
					- + 可以连接多个字符串变量，返回组合成的字符串，
					- * 可以按指定次数重复某个字符串，返回重复后的字符串，
				- 布尔运算
				  collapsed:: true
					- in运算符
					  collapsed:: true
						- 可以判断字符是否在字符串中，
						- 示例`"H" in "Hello"`会返回True，
			- 函数与方法
			  collapsed:: true
				- 函数
					- 基本使用方法为func(str)，一般有返回值，
					- len函数：返回字符串中字符的数量，
					- str函数
						- 可以将对象转换为字符串，
						- 示例：`str([2, 3, 5])`会返回字符串`"[2, 3, 5]"`，
						- 即str函数会将整个列表当作一个字符串，而不会返回一个字符串列表，
					- list函数
					  collapsed:: true
						- 可以将字符串转换为*每个单字符*组成的列表，并应用列表方法修改，
						- 即`list[2, 3, 5]`会返回列表`['[', '2', ',', ' ', '3', ',', ' ', '5', ']']`，
						- 可以使用join方法将列表转换回字符串，
				- 方法
					- 注意事项
						- 不同于列表，字符串被声明后，*不能*修改字符串中的*元素*，
						  collapsed:: true
							- 然而，被赋值为字符串的变量名可以用新的字符串重新赋值；
							- 即`str1 = "abc"`和`str1 = "bcd"`不冲突，
						- 因此字符串方法一般不会修改原字符串，而是会*返回新的字符串*，
					- 分割与组合
						- split方法
						  collapsed:: true
							- 以所有空白符号（空格、\ t和\ n等）为界，将字符串分割为子字符串，
							- *返回*一个子字符串组成的*列表*，
							- 示例：`"a pp le".split()`会返回字符串列表`['a', 'pp', 'le']`，
							- 可选参数
							  collapsed:: true
								- 参数sep = 'c'可以以字符c作为分界符，
								- 参数maxsplit = 3可以设置最大分割次数为3，剩余的字符串会被当作一个整体，
						- join方法
						  collapsed:: true
							- 以字符串为分隔符，将字符串列表中的字符连在一起形成一个新字符串，
							- 分隔符可以为空字符串，即""，
							- *返回*一个*字符串*，
							- 示例：`"".join(['a', 'pp', 'le'])`会返回字符串`"apple"`，
					- 修改
						- strip方法
							- 移除原字符串首尾的空白字符，并*返回*新字符串，
							- 可选参数
							  collapsed:: true
								- str2：所有既在字符串中又在str2中的字符都会被移除，不受str2中字符的顺序影响，
								- strip只接受一个*字符串*参数str2，而并非多个字符参数，或字符列表，
							- lstrip和rstrip方法
							  collapsed:: true
								- 功能类似， 只不过分别移除的是原字符串左边或右边的空白符，
						- format方法
							- 类似C中的格式化字符串sprintf函数，
							- `"..{0}..{1}..".format(arg1, arg2...)`会按照将字符串中由{n}表示的对象按数字顺序逐个替换为arg1, arg2，返回新的字符串，
							  collapsed:: true
								- 数字需要从0开始，
					- 字符方法
						- title方法以空格为分界，将每个单词的首字母大写，
						- upper和lower方法将所有字符转变为大写（小写），
					- 查找
					  collapsed:: true
						- find方法
						  collapsed:: true
							- 需要参数arg1，返回第一个arg1在字符串对象中的位置，如果未找到则返回-1，
						- rfind方法
						  collapsed:: true
							- 类似find方法，但是从字符串的末尾开始搜索， 返回的也是arg1在字符串中最后一次出现时的位置，
						- index（rindex）方法
						  collapsed:: true
							- 类似find、rfind方法，但在字符串中找不到arg1时不会返回-1， 而是会引发ValueError，
						- startswith和endswith方法
						  collapsed:: true
							- 检查字符串的开头或结尾是否为arg1，
							- 返回布尔值True或False，
						- count方法
						  collapsed:: true
							- 查找字符串中是否有arg1，并返回arg1的数量，
							- 不存在arg1则会返回0，
			- （bytes对象）
			  collapsed:: true
				- 处理二进制数据（如从二进制数据文件中读取数据等）会用到bytes对象；bytes对象在处理国际字符集时也会有应用，
				- encode方法可以将字符串转换为bytes对象，bytes对象的decode方法可以将其转换为字符串，
		- 字典dict
		  collapsed:: true
			- 概述
			  collapsed:: true
				- 类似于一个复杂的列表，
				- 多组“键值对”组成的序列，由大括号{}括起来，元素间用逗号连接，
				- 每组元素间用：对应，冒号左侧的值称为“键”，右侧的值称为“值”，
			- 声明
				- 声明和赋值`dict1 = {key:value}`，
				  collapsed:: true
					- 由花括号{}括起来，且用冒号分隔开的输入会被解释为字典，
						- 只用逗号分隔的元素会被解释为集合，
					- 用逗号，连接的不同键值对会被解释为字典的元素，
				- 空字典的声明`dict1 = {}`，
				  collapsed:: true
					- 该语句声明了一个字典变量dict1（而不是集合），后续可以对其进行操作，
				- 键值对`{key:value}`
				  collapsed:: true
					- 一个值（value）可以对应多个键，
					- 一个键（key）只能对应一个值——若输入了多个，则python默认只保留最后输入的键值对，
					- “键”必须是“可哈希的”，即为不可变的变量，如元组和字符串；而不能为列表，字典，
					  collapsed:: true
						- 哈希函数接受一个值（任意类型）并返回一个整数，字典使用这些整数存储和查找键值对，
						- 可变的变量可能会对应多个哈希值，从而阻碍字典的工作，
					- “值”的数据结构没有限制，即可以为数值、字符串、列表、元组、字典等，
			- 基本操作
				- 下标
				  collapsed:: true
					- 索引
					  collapsed:: true
						- 不同于列表和元组，字典利用关键字来查找对应值，
						- 所以只能使用键来查找对应的值，即`dict1[key1]`会返回key1对应的值value1，
						- 字典*不能使用*整数索引，
					- 字典不能进行切片操作，
					- 赋值与修改
					  collapsed:: true
						- 不同于列表，可以通过下标操作*增加*字典中的键值对，
						- 可以通过dict[key1] = value1的方式对字典赋值，
						  collapsed:: true
							- 若键值对key1不存在，则操作会*新建*键值对，
							- 若键值对key1存在，则新的值value1会覆盖原来的值，
						- 当key1为整数时，此方法类似列表的下标操作，但实际上字典只是存储了键值对key1 : value1；而不是按下标顺序添加了元素，
				- 查找键
				  collapsed:: true
					- 一般而言，字典不能直接进行逆向查找，即较难以通过值寻找到对应的键；
					- 可以通过for循环遍历字典来寻找，且应注意一个值可能对应多个键，
				- 布尔运算
				  collapsed:: true
					- in函数可以检查字典中是否存在某个键（不能检查值），
			- 函数与方法
				- 函数
					- len函数：返回键值对的个数，
					- sorted函数
					  collapsed:: true
						- 重排字典，返回键的*列表*，
					- del函数
					  collapsed:: true
						- `del(dict1[key1])`可以删除字典中的键值对key1:values1，
				- 方法
					- keys, values, items方法
						- 分别*返回*字典中的*键*，字典中的*值*，字典的*键值对元组*组成的序列的集合，分别为dict_keys、dict_values、dict_items类型；
						- 修改字典时，dict_keys、dict_values、dict_items对象会“同步”变化，
						  collapsed:: true
							- 示例
							- ```
							  dict1 = {'d': 'D', 'e': 'E'}
							  var1 = dict1.keys()
							  
							  del(dict1['d'])
							  
							  print(dict1)
							  print(var1)
							  ```
						- dict_keys、dict_values、dict_items对象可以用for循环遍历，也可以用in操作符来判断键、值是否在字典中，但可执行的操作不同于列表，而更类似于集合，
						- 可以使用list函数将其转换为列表，转换后的列表*不会*再与字典*同步*变化，
					- get方法
					  collapsed:: true
						- `dict1.get(key1, key2)`在字典中存在键key1时返回对应的值values1，不存在键key1时则返回key2，
						- 不指定key2时则会返回None，
					- update方法
					  collapsed:: true
						- `dict1.update(dict2)`会用dict2的所有键/值对*更新*dict1，
						- 如果键在两个字典中都存在， 则第二个字典中的值会覆盖第一个字典的值，
					- zip方法
					  collapsed:: true
						- 可以利用dict和zip方法将两个元组组合在一起，创建一个简单的字典，
				- 复制
				  collapsed:: true
					- 浅复制
					  collapsed:: true
						- copy方法可以得到字典的浅副本，
						- 类似列表，若字典中有*嵌套列表*，则修改浅副本中的嵌套列表的值会导致原字典的同步变化，其他元素的修改则不会产生影响，
					- 深复制
					  collapsed:: true
						- copy模块的deepcopy函数可以得到字典的深副本，
			- 字典应用
			  collapsed:: true
				- 判断出现频率
				  collapsed:: true
					- 利用字典的键值对应和值的可更新性，可以综合利用for循环和字典，来判断某一对象的出现频率；
				- 稀疏矩阵
				  collapsed:: true
					- 一般的m*n矩阵可以利用嵌套列表来表示为向量的形式，即[[m11, m12...], [m21, m22...]...]，但对于较庞大的，且多个元素为0的矩阵，这种表示方式会较为冗余，
					- 可以利用字典和元组索引只存储不为0的元素及其位置，如{(mi, ni) : ki, (mj, nj) : kj...}的形式，可以减少冗余度，
				- 字典缓存
				  collapsed:: true
					- 函数默认不会记录已计算的参数；因此，迭代函数可能会进行很多次重复的从头开始的计算，
					- 可以通过让函数记录已经计算的值，并利用字典保存，综合if-else语句，在函数需要计算值时先从字典中查找值是否已经算得，从而直接取值并简化运算，
		- 集合set
		  collapsed:: true
			- 概述
			  collapsed:: true
				- 无序的多个值组成的序列，
				- 类似数学中的集合，即*重复*的元素只会被计算*一次*，
					- 即`set1 = {1, 1, 2, 2}`等同于`set1 = {1, 2}`，
			- 声明
			  collapsed:: true
				- 基本语法：`set1 = {1, 2}`会声明一个集合，
					- 由花括号{}括起来，且元素不是用冒号连接的键值对，元素间用逗号连接的输入会被识别为集合，
					- 由于空花括号{}会被识别为字典，因此不能这样直接声明空的集合，
				- 集合中的项必须是不可变的，可哈希的，
			- 基本操作
			  collapsed:: true
				- 逻辑运算符
				  collapsed:: true
					- 类似数学中的集合运算，
					- &为且（AND），| 为或（OR），^为异或（XOR），
					- 集合不能使用非（NOT）运算，
				- 布尔运算
					- in运算符可以判断元素是否在集合中，
			- 函数与方法
			  collapsed:: true
				- 函数
				  collapsed:: true
					- 类似列表，可以使用len、min、max等函数，
					- set函数
					  collapsed:: true
						- 接受一个列表、元组、字典等序列变量，返回一个集合；
						- 列表、元组中的重复变量只会被计数一次——但set函数不会计算嵌套列表中的变量，即嵌套列表会被算作一整个元素，
						- 对于字典，set函数只会将字典的*键*组合为集合，*值*会被*舍弃*，
					- forzenset函数
					  collapsed:: true
						- 类似set函数，但返回的集合的元素不可变，
				- 方法
					- 虽然集合可变，但具体方法并不完全等同于列表；
					- 集合需要使用add方法来附加元素，而不是append，
					- 集合同样使用remove方法来删除元素，
	- 其它
	  collapsed:: true
		- None值
		  collapsed:: true
			- 部分计算过程不会产生返回值，这些过程默认的返回值为None，
	- @数据特性
	  collapsed:: true
		- 命名空间
		  collapsed:: true
			- 命名空间
			  collapsed:: true
				- Python的命名空间分为三类，局部（如函数中定义的变量）、全局（如直接在交互模式中定义的变量）和内置（即python内部的关键词），
				- 在运行中遇到特定字符时，Python的查找顺序为局部命名空间→全局命名空间→内置命名空间，若仍未发现特定字符，python就会引发NameError，
				- 由于python会首先查找全局命名空间，因此应避免将部分关键词用作变量，
				  collapsed:: true
					- python没有将所有的内置函数都设置为不能用于命名的关键词，即使用print,tuple,max等函数名称来命名变量是合法的，
					- 然而，这样的命名规则会导致对应的内置函数无法使用，
					- 在交互模式下，使用del函数删除对应的变量就可以重新使用对应函数；但仍应避免这样的命名方式，可以在关键词后加入数字和下划线以进行区分，
			- 全局（global）变量与局部（local）变量
			  collapsed:: true
				- 定义
					- 全局变量，属于`__main__`，可以被任何函数访问，在进行过函数运算后也不会消失，但变量的值可能会发生改变；
					- 局部变量，一般在定义函数时引入，仅在函数内部出现，函数运行结束后就会消失，无法被再次调用，
				- 变量声明
					- 可以在函数内部使用global函数global arg1，告知函数调用全局变量，
					- 对于不可变对象（如元组、 字符串和数值），声明全局变量后，函数内部形参的操作会改变实参的取值，
						- 如果只是要访问函数外的变量， 则不需要将其声明为nonlocal或global，
				- 其它
					- 参数命名
						- python默认函数内定义的变量为局部变量，因此理论上局部变量可以与已定义的全局变量重名，
						- 函数内声明了全局变量时，定义函数时命名的形参与已定义的全局变量不能重名，
					- 过多的全局变量可能会增加函数调试的难度，应注意变量的合理命名与使用，
		- 数据类型与对象相关联
		  collapsed:: true
			- python的数据类型与对象相关联，即变量可以为任何数据结构，
			- 优点在于，变量无需声明即可使用，
			- 缺点在于，同一变量在代码的不同部分可能会变为不同的数据结构，从而导致错误，
		- 数据类型即对象
		  collapsed:: true
			- Python的类型是动态确定的，即同一变量的数据类型会随着程序运行而变化，而不需要事先声明，
			- python的一个思想为“所有”变量均为“对象”，即所有的变量都由对应的类定义，
				- 例如，字符串属于str类，布尔值属于bool类，而str和bool则属于type类，
			- “鸭子类型”
				- 相比于Java等对数据结构和类有严格的要求的语言，python更希望强调“实用性”，即通过灵活的应用数据结构和类达到编程的目的，而不是必须遵循严格的定义，执行严格的检查，
				- 因此，python中引入了很多异常类型，以保证程序出现错误时解释器可以发现并中断程序；相比之下，Java、C等语言则没有规定这样多的异常，因此在编写时就需要尽量保证程序不出错误，
		- type函数可以判断值的类型，del函数可以删除变量，
- 数据操作
	- 基本操作
		- 赋值（assignment）
		  collapsed:: true
			- =表示赋值运算符，而不是数学意义上的相等，
			- 重复赋值
			  collapsed:: true
				- 对同一变量进行多次赋值是合法的，
				- 例如x = x + 1的含义为：获得 x 的当前值，与 1 做加法求和，将 x 的值更新为所求的和，结束，
			- 元组赋值
			  collapsed:: true
				- 元组可以出现在赋值操作符的左侧，
				- 可以将右侧*可迭代对象*中的数值，依次赋予赋值操作符左侧元组中的元素，
				  collapsed:: true
					- 即右侧对象可以为元组，列表，字符串等；也可以为字典（会将字典的键赋值给左侧），
				- 左侧元组中的元素数量需要与右侧可迭代对象中的元素数量*相同*，
				- 示例：`(a, b, c) = "str"`会分别将's'，'t'，'r'赋值给a，b，c，
			- 赋值顺序
			  collapsed:: true
				- 基本顺序为从右到左，从上到下，
				- 连续赋值运算`a = b = c = 123`是合法的，其含义为将123赋值给c，将c（123）赋值给b，将b赋值给a，
				- 然而这样的写法可能导致程序不易理解，实际编程时应避免，
			- 简化赋值运算符
			  collapsed:: true
				- 对于单变量的赋值和运算操作，可以简化赋值运算符，
				- 对于基本运算+、-、*、/、%，赋值运算`var = var + n`都可以简写为`var += n`，
				- python中*不能使用*复合赋值运算符，即递增运算`++`和递减运算`--`
		- 基本运算（operator）
			- 算术运算符
				- 在python中，`*`代表乘法，`**`代表乘方，
				- 字符串一般不能执行运算，但可被理解的加法、乘法运算（如连接两个字符串）是合法的，
			- 除法运算
				- 整除运算//：丢弃小数返回整数，
					- 不同于C，python中的除法`/`更接近于数学除法，且返回的总为浮点数（与进行运算的变量类型无关），
					- 如果希望进行整除运算，则需要使用`//`；
					- 整除运算也可以用于浮点数，但返回的也为浮点数，
				- 求余运算%：只返回余数（不返回除尽的整数），便于查看能否整除，
			- math包提供了额外的数学运算；
			- cmath包可以对复数进行运算，返回的结果也为复数，
			- 运算顺序：括号、指数、乘法/除法、加法/减法，
		- 布尔运算
		  collapsed:: true
			- 仅返回True或False两个结果之一，
			- 真值
				- 任意的非0数值都会被当作True，
				- 0会被当做False，
				- 空列表[]，空元组()等也会被当做False，但含有0元素的列表[0]会被当作True，
			- 基本关系运算符
			  collapsed:: true
				- <（小于）>（大于）<=（小于等于）>=（大于等于）
				- ==（等于）!=（不等于）
				  collapsed:: true
					- python中的等于和不等于可以用于比较字符串，列表，字典等数据结构，
					- 对于赋值运算符=，表达式`n = var1`是不合法的，因为不能给常量赋值；
					- 但对于比较运算符==，表达式`n == var1`是合法的；为了避免将比较错写为赋值，可以在比较时将常量写在左侧，
			- 逻辑运算符
			  collapsed:: true
				- 可以直接使用not，and，or，
				- 也可使用运算符：&为且（AND），| 为或（OR），^为异或（XOR），
				  collapsed:: true
					- ~为非（NOT）运算，但不完全等同于not运算符，
			- any，all函数
			  collapsed:: true
				- 类似数学中的存在\exist和任意\forall，
				- 接受*一个*布尔值*序列*（列表、元组等）作为参数，
				  collapsed:: true
					- 并非需要直接输入布尔值，也可以输入会输出布尔值的特定语句，
				- any：序列中任意一个值为True时返回True，
				  collapsed:: true
					- 示例`any([1, 0, 0])`会返回True，
				- all：序列中所有的值都为True时返回True，
				  collapsed:: true
					- 示例`all([1, 0, 0])`会返回False，
			- is运算符
			  collapsed:: true
				- 接受字符串、列表；若两个字符串、列表“相等”，则返回True，
				- 两个相同的字符串在python中为同一对象，即`is`和`==`都会返回True；但两个“相同”的列表在python中则不是同一对象，虽然`==`会返回True，但`is`会返回False
				- 这里的“相同”被理解为两个列表的每个对应元素相同， 但仍然分属于两个不同的列表，
				- 列表是可变的，除非赋值a = b，这样a、b会同步改变，否则对a的改变不会影响b；相比之下，字符串是不变的，
			- 运算优先级
			  collapsed:: true
				- 高优先级：<（小于）>（大于）<=（小于等于）>=（大于等于）
				- 低优先级：==（等于）!=（不等于），
				- 对于逻辑运算符，顺序（从高到低）为not，and，or，
		- 运算顺序
		  collapsed:: true
			- 由高到低：算数运算，布尔运算，赋值运算，
			- 例如，`x = y > 2`的含义为`x = (y > 2)`，
			- 若`y > 2`为真，则x会被赋值True，否则x会被赋值False；y的值不会被赋值给x，
			- 大部分的运算符都是从左往右计算，
			- 类似数学运算，括号（）可以改变优先级，
	- 控制语句
	  collapsed:: true
		- 基本语法
		  collapsed:: true
			- python中的复合语句通过冒号和缩进来标识，而不是括号和分号，
		- 复合条件
		  collapsed:: true
			- if和while语句只能接受一个“条件”，但条件可以为多个布尔表达式的复合，
			- 对于复杂的任务，可以利用逻辑运算符等方式在一个语句中嵌套多个条件，
			- 应注意嵌套条件可能难以理解，最好附加一定的注释，
		- 循环
		  collapsed:: true
			- while循环
				- 基本语法
				  collapsed:: true
					- ```
					  while condition:
					  	statement
					  ```
				- 循环条件
				  collapsed:: true
					- 条件为假→退出while语句，执行接下来的语句；
					- 条件为真→执行while语句，完成循环后返回，再次判断真假，
				- 主体语句
				  collapsed:: true
					- while语句需要有可被执行的主体部分，否则会报错；
					- 可以利用pass语句作为主体，无论条件真假都不会执行操作，
			- for循环
				- 概述
				  collapsed:: true
					- 类似while循环，其功能也是重复执行某些语句；但for循环一般比while语句更加简约，
					  collapsed:: true
						- 然而，for循环简化了while的条件判断语句，所以可能需要与if共同使用，
					- 遍历任何可以迭代（iterable）的对象（包括列表，字典（键），元组，字符串；不包括整数和浮点数），对序列中的对象逐个执行对应语句，
					- 基本顺序为序列中的第一、第二、第三个元素，以此类推，
				- 基本语法
					- ```
					  for i in sequence：
					  	func(i)
					  ```
					- 不同于while循环和if语句，for循环中的循环变量更类似函数的形参，
					- 因此循环变量的命名没有限制，也不需要事先声明，
				- 多个对象循环
					- for可以对多个对象进行遍历，但前提是给定的序列中的对象可以拆分为对应的几组，
					  collapsed:: true
						- 示例：可以对字典的items对象进行遍历（不能直接遍历字典），并对键，值进行操作，
						- ```
						  for key, value in dicta.items():
						  	func(key)
						      func(value)
						  ```
					- for循环不能识别嵌套列表，即对嵌套列表进行遍历时，嵌套列表中的元素会被视为一个对象，
				- range函数
				  collapsed:: true
					- `range(a, b, c)`返回以c为差值，由a到*b-1*的range对象，
					- 默认a = 0，c = 1，即range(n)返回range(0, n)，
					- range(0, n)类似于正整数列表[0, 1…, n-1]，但所占用的资源更少，
					- 也可以使用list函数将range对象转换为列表，
					- 示例
					  collapsed:: true
						- ```
						  i = k
						  while i < n:
						  	statement
						      i = i + 1
						  
						  等同于
						  
						  for i in range(k, n):
						  	statement
						  ```
				- enumerate函数
				  collapsed:: true
					- 接受一个列表作为参数，返回一个类似字典的enumerate对象；
					- 其中“字典的值”为0，1...正整数索引，“字典的键”为列表中的逐个对象，
					- enumerate对象可以作为for循环需要遍历的序列，
			- continue语句
			  collapsed:: true
				- 可以跳过循环内接下来的语句，重新返回while语句的条件判定，
			- break语句
			  collapsed:: true
				- 可以立即终止循环，循环内的语句不会再被执行，
		- 选择
		  collapsed:: true
			- if-elif-else语句
			  collapsed:: true
				- 基本语法
				  collapsed:: true
					- ```
					  if boolean:
					  	statement
					  elif boolean:
					  	statement
					  else:
					  	statement
					  ```
				- 组成
					- 中间的条件可以用elif指示，elif语句的数目没有限制，也可以没有elif语句，
					- 解释器会逐个检测条件，检测到语句为真后就会执行语句，然后结束任务，不会再检查剩余的语句，
					- 可以没有else语句，即if的条件为False时不执行操作；但else语句（如果有）必须在末尾，
					- 除了条件，if语句需要有可被执行的主体部分，否则会报错；
					- 可以利用pass语句作为主体，无论条件真假都不会执行操作，
		- 其它
		  collapsed:: true
			- 条件表达式
			  collapsed:: true
				- 将语句写在一整行中，不换行和加入冒号；一般在条件语句（if语句）的分支表达式均比较简单时使用，可以简化代码，
			- 列表推导式
			  collapsed:: true
				- 利用for语句，直接在方括号中构造新列表，不新建额外的空白列表；对于简单的表达式，可以简化代码并加快for循环的运行速度，
			- 字典推导式
			  collapsed:: true
				- 类似列表推导式，将括号改为大括号即可构造新字典）
			- 生成器函数（generator）
			  collapsed:: true
				- 函数内部定义了while或for循环时，可以用yield关键字*逐个返回*每次迭代的值，
				  collapsed:: true
				- 当没有可迭代值或函数结束时，生成器函数将停止输出返回值，
				- 生成器函数中的局部变量值会被保留至下一次调用，
	- 函数（function）
	  collapsed:: true
		- 概述
		  collapsed:: true
			- 有命名的，执行某个计算的语句序列,
			- 一般而言，函数解决同一问题的解法和路径可能是多样的，但是输入和输出则一般比较固定；因此，明确输入和输出可以帮助理清逻辑，
		- 函数思想
		  collapsed:: true
			- 算法中可能存在很多重复或类似的操作，而计算机擅长重复执行类似的行为，
			- 因此，应该尝试将算法中的重复操作定义为一个函数，用函数去描述这一系列操作，
			- 利用函数去描述操作可以辅助思考如何提升算法，从而改善程序，
			- 然而，对于复杂问题，最好首先想出一个可行（但可能较复杂）的算法，再尝试利用函数去改进，而不是直接从函数的角度去思考问题，
		- 自定义函数
			- 组成
			  collapsed:: true
				- 基本语法`def func(arg1, arg2...): statement`，
				- python函数利用缩进来判断语句，因此不需要特定符号（如大括号）来表示结尾，
				- 应注意def关键字后的冒号，以及语句间的准确缩进，
			- 参数
			  collapsed:: true
				- 形参（parameter）与实参（argument）
				  collapsed:: true
					- 定义
					  collapsed:: true
						- 形参是计算机存储的环境中的变量（可以是变量，也可以是函数），而实参则是具体的（如人为输入的）数据，
						- 示例：定义函数时输入的def add(t)中的t为形参，而调用时输入的add(3)中的3为实参，
					- 运算规则
					  collapsed:: true
						- 函数运算时先将实参转化为形参，再调用函数根据形参运算，最后输出结果，
						- 若定义函数时没有指定形参，调用时输入形参就会导致报错，
					- 变量实参
					  collapsed:: true
						- 除了具体的数值，python环境中的变量也可以被用作实参，
						- 对于不可变对象（如元组、 字符串和数值），形参的操作不会影响函数外部的实参的取值，
						- 对于可变对象（如列表、 字典），函数内部对形参做出的改动会改变该实参的具体值，但函数内部对形参的重新赋值不会影响实参，
				- 局部变量
				  collapsed:: true
					- 函数内定义的参数为局部变量，即不会与函数外定义的相同名称的参数产生冲突，
				- 参数输入
					- 参数位置
					  collapsed:: true
						- Python默认按定义时形参的位置接受实参，
						- 即对于函数`def func(arg1, arg2...):`，
						- 调用时使用的`func(a, b...)`中的a，b…会分别赋值给arg1，arg2…，
						- 若没有设定默认值，则输入的实参与函数的形参*数量不符合*时会报错，
					- 参数默认值
					  collapsed:: true
						- 可以为参数设定默认值，如`def func_name(arg1, arg2= default2...):`，
						- 对于设定默认值的形参，若没有外界输入的对应实参，python会按照默认值对函数进行运算，
						- 设置函数时，带有默认值的形参必须在*末尾*，
						- 如果没有合适的默认值，可以将空字符串指定为参数的默认值，以避免参数数量不符导致的错误，
					- 关键字实参
					  collapsed:: true
						- 对于具有多个实参的函数，可以在*调用函数*时加入实参的名称，
						- 如`func(a, arg2 = b...)，`
						- 若输入的实参*都指定*了关键字，则此时可以不按照设定函数的实参顺序输入，
						- 若希望混合输入位置参数和关键字参数，则关键字参数必须在最后，
					- 传递多个参数
					  collapsed:: true
						- `*`符号可以汇集多个参数，使函数可以接受任意数量的参数，
						  collapsed:: true
							- 示例：`def func(*tuple1):`会将接收到的实参a，b，c…组成一个*元组*`tuple1 = (a, b, c…)`传递给函数，
							- 因此，函数语句中也需要使用元组对应的操作，
						- `**`符号可以汇集多个*关键字参数*，使函数可以接受任意数量的关键字参数，
						  collapsed:: true
							- 示例：`def func_name(**dict1):`会将输入的关键字和参数`first = "tom", last = "john", age = 30`组成一个字典`dict1 = {first : "tom", last : "john", age : 30}`传递给函数，
							- 字典的键为关键字（即形参名称），字典的值为实参，
							- 因此，函数语句中也需要使用字典对应的操作，
						- 可变数量参数必须在函数定义*参数的最后*，
						- 两者不能互相代替，若输入的参数两类都有，则需要同时定义两种方法，
						- 此外，也可以将多个数据先汇总为列表（或元组），再将列表传递给函数，
						- 由于函数可能修改列表，所以可以将函数的形参设置为列表的副本，如`lista[:]`，
					- 参数设置
						- 一般情况下，不建议对输入对象的原始属性进行修改；
						- 可以试着寻找需要使用修改对象的原因，并尝试用其他方式解决，
						- 也可以考虑将函数的形参设置为对象的副本，但对象较大时，创建一个副本会占用很大内存， 导致程序运行缓慢，
			- 返回值
			  collapsed:: true
				- 类型
				  collapsed:: true
					- 输出一般包括三种：返回数值，显示数值，执行其它行为（不返回值），
					- 在交互模式下，解释器会显示函数的输出；但脚本模式下，返回数值不一定会输出，
					- 特定的函数内部运算也会返回None，由于None无法进一步运算，因此在设置函数时应注意避免返回None的操作，
				- return函数
				  collapsed:: true
					- `return`函数表示函数的返回值，只能
					- 一般而言，return函数只能接受一个参数（即返回一个值）；但可以将返回值设置为元组（或列表、字典），其效果类似于返回多个值，
					- 应尽量保证需要的语句最终以return函数结尾，否则没有以return函数结尾的语句就会输出None（一般不符合设计函数的本来目的），
				- 显示输出
				  collapsed:: true
					- printf函数可以显示函数运算得到的结果，但不产生返回值（返回None），
					- 在程序较为复杂时，可以先使用print函数打印出结果，待确认无误后再使用return函数输出结果，
		- main函数
		  collapsed:: true
			- python程序可以没有main函数，
			- 然而，一般仍习惯将较复杂的程序写为多个函数和main函数的组合，
			- 因为main函数所包含的主要为其他函数，所以一般将main函数写在末尾 ，
		- lambda表达式
		  collapsed:: true
			- 若函数的语句较少，则可以利用lambda表达式在行内完成函数定义，
			- 基本语法为：`lambda arg1, arg2, …: expression`，
			  collapsed:: true
				- lambda不需要def语句和后续缩进，
				- lambda表达式会自动产生返回值，所以不需要return语句，
				- 然而，仍需要对lambda表达式命名以使用表达式，
			- 示例
			- ```
			  def FtoC(degf):
			  	degc = (degf - 32) * 5 / 9
			      return degc
			  #等同于
			  FtoC = lambda degf : (degf - 32) * 5 / 9
			  
			  #使用方式类似
			  degc = FtoC(44)
			  ```
		- 函数赋值给变量
		  collapsed:: true
			- 可以将函数“赋值”给变量，即arg1 = function（不带括号），
			- 其作用之一为简化函数的名称，即引用函数时可以直接使用arg1(a，b…)，用法等同于使用原来的函数，
			- 可以结合字典使用，在需要调用多个函数时会有帮助，
		- （装饰器函数，decorate）
		  collapsed:: true
			- 函数可以作为实参传递给其他函数，
			- 装饰器可以简化将一个函数包装到另一个函数内的过程，
- 数据交互
  collapsed:: true
	- 基本输入/输出
	  collapsed:: true
		- 基本输入函数
			- input函数可以接受用户输入，
			- input函数附带可选的字符串参数，用于提供关于输入信息的提示，
			- 函数以换行符`\n`结束，将换行符*之前*的所有输入赋值给*一个字符串*并返回；
			  collapsed:: true
				- 对于特定输入，可以使用int或float函数来转换为数值，或者使用list和tuple函数将其转换为列表，元组，
			- 示例`name = input("What's your name: ")`会将命令行输入"tom"作为字符串赋值给变量name，
		- 基本输出函数
		  collapsed:: true
			- print函数可以将输入的对象转换为字符串后显示出来，
			- print函数可以接收多个参数和关键字参数，
			- 如print("a", "b", "c", sep="|", end="\t")会输出a|b|c ，
	- 文件输入/输出
		- 路径选择
		  collapsed:: true
			- os模块
			  collapsed:: true
				- 查看路径：`os.getcwd()`函数返回一个字符串变量，表示当前的绝对路径，
					- 相对（relative）路径：一般指当前运行环境的路径，
					- 绝对（absolute）路径：电脑中文件的路径（从根目录`/`开始），
					-
				- 改变路径：`os.chdir("/home/Code")`函数接受一个字符串（表示具体路径），将解释器的运行目录改为对应路径，
				  collapsed:: true
					- Windows的目录不区分大小写，且用反斜杠表示，
					- Linux的目录区分大小写，且用斜杠表示，
				- 新建文件夹：`os.makedirs("folder")` 函数接受一个字符串，在当前目录新建空文件夹folder，
				- 遍历文件：os.walk("/home/Code")函数接受一个字符串（表示具体路径），遍历给定目录下的所有文件，返回一个*生成器*变量，
			- pathlib模块
			  collapsed:: true
				- 查看路径：pathlib.Path()函数可以返回当前（相对）路径，
		- 文件操作
		  collapsed:: true
			- open函数
			  collapsed:: true
				- `open('file.txt', mode = 'r')`可以打开文件，
				  collapsed:: true
					- 返回一个*file变量*，可以赋值给一个变量file1，并对变量进行操作，
					- 可选参数mode
					  collapsed:: true
						- 默认为'r'，即只读模式，
						- mode = 'w'可以写入文件（如果文件不存在，那么将创建一个新的文件；若文件已经存在，用写入模式打开它将会*清空原来的数据*，并从新开始），
						- mode = 'a'可以将需要写入的数据附加到原文件后，而不会清空原来的数据，
					- 可选参数errors
						- 用于处理非ASCII字符，
					- 可选参数encoding
			- with关键字
			  collapsed:: true
				- 语句`with open('file.txt', 'r') as file1: statement`综合了三种操作，
				  collapsed:: true
					- 打开file.txt并将其赋值给变量file1，
					- 执行冒号后的语句statement，
					  collapsed:: true
						- 可以输入多条语句，以换行符分隔，
						- 两次输入换行符会结束with语句，
					- 关闭文件，
				- 注意事项
				  collapsed:: true
					- with关键字后的open语句同样可以接受可选参数，
					- 若不存在file.txt，则with语句会新生成file.txt文件，
					- with关键字在执行完语句后会关闭文件，若需要进一步的编辑，则需要重新打开文件，
					- with位于contextlib模块中，
			- 文件对象方法
			  collapsed:: true
				- 对文件对象的操作基本都是方法，即点标记法操作，
				- 读取
				  collapsed:: true
					- file1.readlines()可以将文件转换为列表，
					  collapsed:: true
						- readlines以换行符`\n`为界，划分列表的每个元素，
					- file1.readline()会读取文件的第一行，返回一个字符串，下次调用则会读取第二行，以此类推，
					- file1.read()可以将文件转换为一个字符串，
				- 写入
					- file1.write('string')接受一个字符串（只能为字符串），将'string'附加到文件末尾，返回被写入字符的个数（int值），
					  collapsed:: true
						- write方法只能用于写入模式('w'或'a')打开的文件，
						- write方法默认将字符串添加到文件最后一个字符后，而不会添加换行负；如果需要，可以主动附加换行符`'\n'`，
						- 可以用str函数将其它值转换为字符串，
					- file1.writelines()接受一个字符串列表（列表中的元素必须*都为字符串*）按字符串逐个输入至文件中，不产生返回值，
						- 默认字符串之间没有分隔符，
				- 关闭
				  collapsed:: true
					- file1.close()方法可以关闭文件；若不关闭，则文件直到程序结束时才会关闭，
			- 其它操作
			  collapsed:: true
				- struct模块可以用于读取二进制数据，
				- pickle模块和shelve模块可以用于保存对象，
			- json模块
			  collapsed:: true
				- json.dump(var1, file1)将var1中的数据写入file1中，不产生返回值，
				- json.load(file1)可以读取并返回file1中的数据，根据字符的形式返回*对应的数据类型*，
- 面向对象编程
  collapsed:: true
	- 类（class）
	  collapsed:: true
		- 引入
		  collapsed:: true
			- 类指现实世界的“一类”物体，这一“类”中的“实例”在个性上存在差异，但拥有相同的一些共性，因此可以抽象为同一类拥有不同“属性”的总体，
			- 例如2，3，4都可以进行+、-运算，都不能除以0；所以可以将其归为整数“类”；2、3、4就是具体的“实例”，
			- python中的数据结构（包括整数、字符串、列表、字典等）本质上就是不同的类，
			  collapsed:: true
				- 因此，指定的每一个具体的列表都拥有列表类所有的“属性”，且都可应用列表类所能使用的“方法”，
			- 根据类来创建对象被称为实例化（instantiation），手动赋值的具体变量则称为类的实例（instance），
		- 类的组成
		  collapsed:: true
			- class函数
			  collapsed:: true
				- class函数`class Class1():`会创建类Class1，
			- 注释
			  collapsed:: true
				- 用于对类型进行说明的字符串，
				- 一般写在最开始的位置（需要缩进），并用三引号'''括起来；这样写出的注释可以使用doc方法访问，即`Class1.__doc__`会返回注释字符串，
				- 对类型进行详细的说明有助于他人的理解，也有助于后期的调试，
			- 类变量
			  collapsed:: true
				- 部分类可能需要多次调用某个常量，如“圆”类可能需要经常调用\pi的值，
				- 可以在类中定义对应的常量，即var1 = num1，
				- 类中的方法或是类外应用变量时，*都需要*用点标记法声明Class1.var1，
				- 不能通过对实例使用点标记法更改类变量，即object1.var1 = str1只会给object1增加一个新的属性var1，并不会对类变量产生影响；
				- 但可以通过对类使用点标记法更改类变量，即使用Class1.var1 = str2，
			- init方法与属性
				- 定义`def __init__(self, attr1, attr2...):`，
				  collapsed:: true
					- 一般的类都以init方法开始，
					- 调用类创造示例时，init方法会首先运行，
				- self参数
				  collapsed:: true
					- 一般第一个形参命名为self，即指代具体对象本身，
				- 属性
				  collapsed:: true
					- 概述
					  collapsed:: true
						- 类中的实例所具有的“基本性质”被称为“属性”，即实例所具有的那些共性，
						- 属性类似C语言中的结构，即组成类的实例的数据类型的一个集合，
					- init中的其余形参规定了对象的属性（attribute），
					- 同自定义函数一样，也可以在init方法中指定属性（参数）的默认值；指定了默认值的属性必须在最后，
				- 其它属性
				  collapsed:: true
					- 一般在init函数中设置完所有属性，
					- 也可以在方法中设置init中没有的新属性，但不调用对应方法时，实例就不会有对应的属性，
					- 不同于C中的结构，在声明类之后，也可以通过点标记法给类（或实例）附加新的属性；但可能会导致代码难以阅读，
				- 主体语句
				  collapsed:: true
					- init函数的主体语句一般为对属性的指定，即`self.attr1 = attr1, self.attr2 = attr2...`，
					- 指定属性与参数的对应后，就可以在其他方法中用点标记法使用实例的属性，即使用self.attr1会返回初始化实例时规定的具体属性值，
					- 可以只在init函数的组成中设置属性`self.attr_n = attr_n`，而不写为init的形参；
					- 这样设置的属性可以通过点标记法和类中的方法更改，但不能在初始化实例时更改，
					- init函数会自动返回一个对象，因此不需要使用return语句，
				- 示例
				  collapsed:: true
					- C中的“student”结构由四个变量：姓名（字符串），年龄（整数），身高（浮点数），体重（浮点数）组成，
					- 语法为
					- ```
					  //声明结构
					  struct Student
					  {
					  	char name[20];
					      int age;
					      float height;
					      float weight;
					  };
					  
					  //创造一个实例并赋值
					  struct Student studenta = {.name = "Tom"};
					  
					  //输出示例的属性（姓名）
					  puts(studenta.name);
					  ```
					- 作为对比，python中的“student”类则有四个属性：姓名（字符串），年龄（整数），身高（浮点数），体重（浮点数），
					- 语法为
					- ```
					  class Student():
					      '''a class to simulate student'''
					  
					  //python中的数据不需要声明类型
					      def __init__(self, name, age, weight, height):
					  		'''attribute of student, include name, age, weight, height'''
					  		self.name = name
					          self.age = age
					          self.weight = weight
					          self.height = height
					  
					  //创造一个实例并赋值（必须对所有属性赋值）
					  studenta = Student('Tom', 27, 171.7, 61.6)
					  
					  //输出示例的属性（姓名）
					  print(studenta.name)
					  ```
			- 方法
			  collapsed:: true
				- 概念
				  collapsed:: true
					- 定义在类中的函数被称为“方法”，
					- 方法可以理解为现实世界中物体“交互”的方式，即物体能做出的行为，
					- 方法与其它python函数并没有实质上的区别；但为了与类中的对象相配合，方法会有一些特有的命名、参数和使用规则，
				- 定义`def func1(self, attr1, attr2...)：`，
				  collapsed:: true
					- 类中的方法的第一个形参一般也为self，即指代具体对象本身；同理，在函数语句中调用实例时也需要用名称self，
					- 除此之外，方法与其它python函数并没有实质上的区别，
					- 方法的参数可以为实例的属性，也可以为外部输入的参数，
					- 不同于init函数，自定义方法不会主动产生返回值，设置时应注意，
			- 特殊方法
			  collapsed:: true
				- 定义
				  collapsed:: true
					- 可以理解为在类中对python原有的“方法”进行*重新定义*，
					- 当对类中的实例应用一些内置方法时，python就会首先调用类中重新定义的方法，
				- 字符串方法的重新定义
				  collapsed:: true
					- 可以在类中定义`__str__`函数，当Python请求该类的实例的可读字符串形式时，类就会调用`__str__`方法，并将其返回值用作请求的字符串，
					- 示例：在类中定义了`def __str__(self): return(attr1...)`后，使用print(object1)时，python就会调用`__str__`函数，返回由该函数定义的字符串，
				- 运算符的重新定义
				  collapsed:: true
					- 可以对基本运算符（+、-、*等）和关系运算符（<、>、==等）的功能进行重新定义，
					- 一般目的为使其更符合类中的元素的形式，并非对运算符的功能进行彻底的重新规划，
					- 示例：`def __add__(self, attr1):`可以重新定义加号的作用；重新定义后，对类中的实例，+运算符就会按照自定义的函数起作用，
					- 直接替换原有运算符的功能，可能导致需要利用基本运算符时出错，应全面考虑不同的情况，并分别规定不同的运算方式，
			- 其它
			  collapsed:: true
				- 引用其它文件
				  collapsed:: true
					- 编写方法时可能需要引入其它的文件（或未引入的库）中的函数，
					- 一般不在方法中加入引入语句import，而是在库的外部先写出引用语句，
				- 私有变量和私有方法
				  collapsed:: true
					- 在名称前加入双下划线`__`（但结尾不加入）的方法和变量会被定义为类私有的，
					- 这些变量和方法只能在类中使用，不能通过类的点标记法访问，
				- 代码重构
				  collapsed:: true
					- 类并不一定必须是现实世界中已有的具体物体，也可能为部分重复代码的抽象总体；
					- 某些程序可能会有多个函数对部分变量（一般为全局变量）进行多次调用，而重复的调用可能会导致输出混乱，
					- 可以将这些变量封装到一个类中，并将函数转化为方法；这是简化代码的一种方式，
					- 也可以将类的一部分作为一个独立的类提取出来，并用作类的一个属性，
		- 类的使用
		  collapsed:: true
			- 实例的创建
			  collapsed:: true
				- 语句`object1 = class1(attr1, attr2...)`会创建class1类的一个实例object1，
				- 创建实例时可以不指定属性，此时init会返回设置的默认值；
				- 但没有设定默认值时必须指定所有属性，否则init方法会报错，
			- 属性的访问
			  collapsed:: true
				- 类似访问C中的结构，可以使用点标记法访问实例的属性，
				- 即`object1.attr1`会返回属性attr1的值，
				- 可以直接通过点标记法更改属性，即`object1.attr1 = str1`，但对于复杂的类， 这样的代码不容易理解，
				- 一般通过类中的方法接受外界参数，对实例的属性进行修改，
			- 方法的使用
			  collapsed:: true
				- 类似属性，可以使用点标记法访问类中的方法，
				- 即`object1.func1(attr1, attr2...)`会对实例object1调用方法func1，
				  collapsed:: true
					- 由于方法需要通过实例调用，因此不需要输入第一个参数self，
				- 可以不指定形参，此时方法会返回设置的形参的默认值（但没有设定默认值时方法会报错），
				- 调用时不能忽略括号（括号代表对方法的使用，不加括号则代表方法本身），
				- 不同于外部的自定义函数，定义在类中的方法不能直接调用，只能由类的实例通过方法调用，
				  collapsed:: true
					- 换言之，定义在类外部的函数可以与类中的方法重名，但不合适的命名可能会导致误解，
		- 继承（Inheritance）
		  collapsed:: true
			- 引入
			  collapsed:: true
				- 有时，部分类可能会共用某些信息，
				- 例如电动车和燃油车都有价格信息，座位数量信息，车企名称信息等，
				- 然而，续航里程信息是电动车特有的，耗油量信息是燃油车特有的，
				- 可以分别创建两个类来表示电动车和燃油车，但两个类会有三个信息重复，
				- 为了简化代码，可以创建一个汽车类，包含两类车都有的价格信息，座位数量信息，车企名称信息，
				- 在创建电动车和燃油车类时，可以让汽车类包括在这两个类中，避免重复创建，
			- 定义：在现有类的基础上定义新的类，原有的类称为父类，而新类称为子类，
			- 子类的设置
				- class函数
				  collapsed:: true
					- `class Class2(Class1):`语句可以将Class2设置为Class1的子类，
				- 注释
				  collapsed:: true
					- 继承可能会使得程序更加难读，即与一个方法相关的代码可能被分散在几个模块之中 ，
					- 应对每个类和属性做出完整的注释；
					- 可以在方法的开始处使用print函数`print(object1.func1)`追踪具体执行的方法来自于哪一个类，
				- 类变量
				  collapsed:: true
					- 子类可以直接继承父类中定义的所有变量，应注意变量的合理命名，
				- 方法与属性
					- init方法
						- 定义`def __init__(self, attr1, attr2, attr3):`，
						- super方法`super().__init__(attr1, attr2)`，可以继承父类中对属性的定义，而无需重新定义属性，
						- 定义子类的特有属性`self.attr3 = attr3`，
					- 方法
						- 子类可以直接继承父类的所有方法（即不需要额外的函数语句）；
						- 然而，若不在init中继承属性，则依赖于父类中的属性的方法仍然不能使用，
						- 除此之外，设置子类的方法与父类中的方法也没有实质上的区别，
						- 继承了父类的属性后，就可以在子类的方法中对父类属性进行修改，
					- 方法覆盖
						- 在子类中重新定义的同样名称的方法，新的定义会*覆盖*父类中的方法的定义，
						- 如果需要覆盖方法，应当使新方法的“接口”与旧方法保持一致，包括接受相同的参数、返回相同的类型等；这可以使能够用于父类的对象的方法，一定可以用于子类，
		- 调试
		  collapsed:: true
			- 类的检查
			  collapsed:: true
				- class属性
				  collapsed:: true
					- `object1.__class__`返回一个type对象type1，描述object1所属的类，
					  id:: 624ae404-2956-4020-a1f4-9e68a8858cbc
					- `type1.__name__`返回一个字符串，描述object1的类；
					- `type1.__bases__`返回一个元组，描述object1所属的类继承的父类，
				- isinstance函数
				  collapsed:: true
					- 函数`isinstance(arg1, Class1)`返回一个布尔值，描述arg1是否为Class1中的实例，
					- python中的“类”的含义十分广泛，即int、list、tuple等数据结构也为一个“类”，
				- issubclass函数
				  collapsed:: true
					- 函数`isinstance(Class1, Class2)`返回一个布尔值，描述Class1是否为Class2的子类，
			- 属性检查
			  collapsed:: true
				- `hasattr(object1, attr1)`返回一个布尔值，可以用于检测对象是否拥有某个属性，
				- `vars(object1)`返回一个字典（属性名称：属性取值），可用于查看对象的所有属性；
				- `vars(Class1)`返回一个mappingproxy对象（类似字典），包括了类中定义的所有函数，
	- 模块（module）
	  collapsed:: true
		- 定义
		  collapsed:: true
			- 相互关联的函数，类和变量的组合，一般以*单个文件*file.py的形式储存，
			- 若需要在新的程序中使用这些函数，可以直接利用import函数导入文件，而无需再次编写函数代码，
		- 基本操作
			- 导入
			  collapsed:: true
				- import函数
					- 可以利用`import file`语句，导入python内部的函数模块和非内置的包含python代码的文件file.py，
					  collapsed:: true
						- 使用import语句时不需要附加文件扩展名，
					- 如果模块已经被导入，则再次试图导入模块不会产生行为，即python不会重新读取模块，
					  collapsed:: true
						- 若模块在运行过程中被修改，修改内容不会被同步更新，
						- 可以利用importlib库中的reload方法重新导入模块importlib.reload()，但可能导致某些问题，
						- 最好的方式为重启解释器并重新导入模块，
					- 应注意避免文件名与包名出现重复，
				- from import函数
					- `from module import object1, object2…`可以将模块中的指定对象名称直接导入代码，再次使用该对象时就*无须模块名称*，
						- 可以使用`from module import *`将模块中的所有函数导入代码，这样使用所有函数时都*无须模块名称*，
						- 然而，对于较长的程序，这样的语句可能使程序变得不容易理解，
						- 此外，若两个模块都定义了同一个对象名则会发生命名冲突，且第二个模块中的名称将会替换第一个模块中的名称，
					- Python中用前置下划线_func表示私有名称，from import函数不会导入这些语句，
				- as关键字
					- `import numpy as np`可以改写（一般为简写）模块的名称，便于后续使用，
					- 使用时也必须用*新指定*的名称，原名称无法再使用，
			- 模块使用
			  collapsed:: true
				- 类似使用类中的数据，可以通过模块名称和点标价法`numpy.sin()`使用导入的模块中的函数，变量和类，
				- 由于函数与具体的模块绑定，因此可以使用不同模块中的同一名称函数，如numpy.sin()和math.sin()的使用都是合法的，
				- 模块中的函数可以直接访问同一*模块内*定义的其他对象，不需要带上模块名，
			- 脚本模式运行
			  collapsed:: true
				- 模块被导入后，其中的语句会被执行；
				- 可以利用`if __name__ == '__main__':`语句设置作为模块的程序；
				- 若程序以脚本的形式运行，则if语句返回True，语句后的代码将被执行；
				- 当程序作为模块被导入时，if语句返回False（此时`__name__`的值为模块的名称，不再为main），从而代码会被跳过，
			- 模块位置
			  collapsed:: true
				- sys模块中的sys.path语句会给出python解释器在执行import语句时会搜索的模块路径，
				- 以交互模式执行Python时，sys.path的第一个元素为空字符串，Python会将其视为首先在当前目录中搜索模块，
				- 然而，对于脚本模式的操作，上述方法一般不再可行；可以尝试将Python程序要用到的全部模块， 都和程序放在同一目录中；或新建目录用于保存自己的模块，并修改sys.path变量，使之包含该新建目录，
				- 细节可以参考Python Library Reference中关于site模块的介绍，
		- 编写模块
		  collapsed:: true
			- 理论上，“编写模块”不是一个独立的编程过程，编写模块主要指的是编写具体的函数或具体的类，
			- 一般模块*最开始*为三引号标记的注释语句（需要缩进），用于描述模块所包含的函数的类型，可以使用`__doc__`方法访问，
	- 包（package）
	  collapsed:: true
		- 定义
		  collapsed:: true
			- 相互关联的模块的组合，一般由多个文件组成，
			- python规定，只有包含`__init__.py`文件的目录才会被识别为包，因此，一般python的包中的所有目录都会包含一个`__init__.py`文件，
			- 相比模块， 包可以更好地组织“大型”的代码集，
			- 若需要在新的程序中使用这些函数，可以直接利用import函数导入模块，而无需再次编写函数代码，
		- 基本操作
		  collapsed:: true
			- import语句
			  collapsed:: true
				- 类似模块，可以使用import语句导入包，
				- python规定，导入包的顶级模块并*不会加载*其全部子模块，例如import matplotlib并不会同时导入matplotlib.pyplot，
				- 可以通过输入具体的模块名称判断模块是否被导入，
			- 包内的文件*同样需要*用import语句才能访问包内其他文件中的对象，
	- 库（library）
	  collapsed:: true
		- python中的标准库
		  collapsed:: true
			- 数据类型库
				- 字符串库（string，re，struct），
				- 数值库（numbers，math，random），
				- 其它数据库（array，queue，collections）
			- 文件库
				- pathlib，filecmp，pickle，
			- 操作系统库
				- os，time，io，logging，
			- 调试库
				- doctest，pdb，profile，trace，
			- 互联网库
				- socket，email，http.server，
		- pip方法
		  collapsed:: true
			- 可以在cmd（powershell）中使用pip语句pip install package安装互联网上发行的库，
			- Python文档的“Installing Python Modules”提供了更多信息，
		- （虚拟环境）
		- PyPI（Python Package Index）
		  collapsed:: true
			- PyPI是Python代码的官方库，包含了适用于各个Python版本的包，
			- PyPI中的包默认按照添加日期和名称排列，但可通过类别进行搜索，
- 调试
  collapsed:: true
	- 编程错误
	  collapsed:: true
		- 类型
		  collapsed:: true
			- 语法错误：python有规定的语法规则，若语法出错则会报错并停止运行；需要多次练习以熟悉规则，形成习惯，
			- 语义错误：程序可以被执行，但返回的并非程序员想要的结果；可能是因为语法错误，或者函数调用不当，
			- 运行错误
		- 错误信息
		  collapsed:: true
			- python会返回错误信息（Traceback），但是只能返回错误的最后一步；而最后一句出错可能并非语法出错，而是上面的语句出现了语义错误；
		- 语义错误的可能原因
		  collapsed:: true
			- 函数获得的参数有问题，
				- 可以增加一条print语句，打印出函数获得的参数及其类型，便于判断指定的参数，
			- 函数的中间值或者返回值有问题，
				- 可以在return语句之前增加print语句，便于分析返回值；
				- 可以试着用较为简单的取值检查对应结果是否正确，
			- 函数调用参数和返回值的方式有问题，
		- 对分调试
		  collapsed:: true
			- 可以试着将代码分为两部分，寻找一个可以检查的中间值，利用return、print语句验证代码是否运行良好，
			- 如果中间点检查出错了，那么就说明程序的前半部分存在问题。如果没问题，则说明是后半部分出错了，
			- 理论上，这样可以减少调试的数量；其关键在于合理的对代码进行分割，寻找最容易出错误的地方，
	- 异常机制
	  collapsed:: true
		- Python的异常机制
		  collapsed:: true
			- Python异常机制是按照面向对象的规范搭建的，主类为BaseException，
			- 子类为SystemExit、KeyboardInterrupt、GeneratorExit和Exception四类，其中主要的异常都被包括在Exception子类中，
			- 可以自定义新的异常类，
		- raise语句
		  collapsed:: true
			- 可以触发异常，并接受一个详细的错误信息作为可选的实参，
			- 如`raise IndexError("Just kidding")`会触发IndexError: Just kidding，
		- try-except-else语句
		  collapsed:: true
			- try语句
			  collapsed:: true
				- try语句没有额外的语法要求，只需要在代码语句前加入try:语句，
				- python从try子句开始顺序执行，如果一切正常，则程序会一直执行下去，并跳过except语句，
			- except语句
			  collapsed:: true
				- 若出现异常，程序会跳出try子句并逐个搜索except子句，判断是否为对应的情况，然后执行对应的except语句并终止程序，
				- except语句一般用于给出异常情况下的其它可选操作，即`except Exception: print("error information")`，而不是像raise语句一样触发异常，即`except：Exception`，
				- except语句需要*准确*的异常判定，即except Exception:中给出的异常需要与执行try语句后可能出现的异常对应，
				- 如果异常不能准确对应， 则python会继续抛出异常，且except后的语句*不会被执行*，
			- else语句
			  collapsed:: true
				- 需要try语句后的代码的成功执行才能执行的代码可以放在else语句后（类似if-else语句），
				- 也可以没有else语句（即所有语句都写在try语句后），
	- 结果检测
	  collapsed:: true
		- 可以通过assert方法判断函数是否能够返回预期的结果，
		- 一般思路为设置一些例子，将函数运算的结果与预期的结果进行比较，
		- assert语句
		  collapsed:: true
			- `assert (statement), argument`，在statement为False的情况下返回异常，
			- 可选参数argument为返回异常时的信息，一般为字符串，
		- unittest模块
		  collapsed:: true
			- 可以定义一个继承自unittest.TestCase的类（如`class TestFunc(unittest.TestCase):`）
			- 然后在类中使用assert方法对函数进行分析，
				- 基本assert方法包括assertEqual，assertTrue，assertIn等，
			- setUp方法
				- 在测试类的方法的时候，一般需要对类中的一个实例进行测试，
				- 可以在检查类TestFunc中先使用setUp函数设置一个需要测试的实例，
				- 这样就可以在测试方法时使用该实例，而不需要为每组测试都单独设置一个测试实例，
			- 使用`unittest.main()`函数可以运行定义的类中的方法，
		- 对于工作量较大的项目，应该对编写的函数和类的重要行为进行测试，以避免后期可能出现的问题，
- 其它操作
	- 网络操作
	  collapsed:: true
		- 获取（fetching）网络数据
		  collapsed:: true
			- 方式
			  collapsed:: true
				- ftp服务器
				- sftp协议
				- http/https协议
				- api
			- 工具
			  collapsed:: true
				- ftplib模块
				- requests库
			- 数据形式
			  collapsed:: true
				- json
					- 数据结构
						- 基本结构：字符串，数值，布尔值，null值，
						- 复杂结构
							- 对象（object），类似字典的键值对；“键”只能为字符串，“值”可以为数字等其他数据，
							- 数组（array），类似列表，
							- 以上两种数据结构是json的核心，这使得json可以很便捷的通过网络传递信息，
					- 工具
						- json模块
						- requests模块
					- 修改
						- 美观输出（pretty printing）：由于格式简单，json的信息排版可能较为混乱，可以使用pprint模块改善其排版，
				- xml
					- 数据结构
						- xml的数据编排较为复杂，一般以尖括号开始和结束，类似<title> <information...> </title>，并利用缩进来区分不同组的信息，
					- 工具
						- xmltodict库
		- 抓取（scraping）网络数据
	- 数据科学
	  collapsed:: true
		- 数据交互
		  collapsed:: true
			- Jupyter记事本
		- 数据分析
		  collapsed:: true
			- pandas库
		- 数据库
		  collapsed:: true
			- 关系数据库（relational databases）：SQlite，MySQL，PostgreSQL
			- NoSQL数据库：Redis，MongoDB，
	- 帮助
	  collapsed:: true
		- help()函数可以返回输入参数的帮助，
		- dir()函数可以列出特定模块中的全部对象，
		- globals()函数可以显示与对象相关联的值，
-
-
- 其它
-
-
- [[Science]]