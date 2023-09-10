- 准备步骤（WSL）
  collapsed:: true
	- 环境设置（简介）
	  collapsed:: true
		- based on https://docs.aws.amazon.com/corretto/latest/corretto-17-ug/generic-linux-install.html,
		- install the java-common package, use`sudo apt-get update && sudo apt-get install java-common`,
		- Download the Linux .deb file,
		- Install by using `sudo dpkg --install java-17-...-.deb`,
		- check with `java --version`,
	- `stdlib` module
	  collapsed:: true
		- book algorithm's internet page provides an alternative module for input/output stream,
		- https://algs4.cs.princeton.edu/code/ includes Java environment setting, `stdlib` moudle setting, java codes in the book, and some solutions to the exercises,
		- after installation, `javac-introcs`*and* `java-introcs` should be able to(and need to)  use in command line, or the compiler will report mistakes,
		- alternative way : download `.java` file to work directory, which the ordinary `javac` command will works. But the disadvantage is the need to duplicate `.java` file to *every work directory* ,
		- the APIs are described in https://introcs.cs.princeton.edu/java/stdlib/,
- java程序的基本组成
  collapsed:: true
	- 一般的java程序包括三步：代码编写（code），编译（compile），执行（execute），
	- 代码编写
		- 类（class）
		  collapsed:: true
			- java文件`Filename.java`的命名需要与类`public class Filename`的命名相同，
		- main方法（method）
		  collapsed:: true
			- 一般类中的主要方法用main表示，即`public static void main(String[] args)`，
		- 其他方法
		  collapsed:: true
			- 一个类中可以含有多个方法，
			- 静态（static）方法
			  collapsed:: true
				- 不需要经过具体的变量调用（但一般需要指明对应的库），如`System.out.println()`，
				- 方法本身可以有参数或没有参数，
			- 实例（instance）方法
			  collapsed:: true
				- 需要绑定具体的对象使用，如`array1.length()`，
				- 方法本身可以有参数或没有参数，
			- 返回值
		- 变量（variable）
		  collapsed:: true
			- 一般而言，变量可以分为三类：接受的输入变量，运算中的临时变量，输出的结果变量，
			- 部分程序可能不需要接受外界输入的变量，但一般所有程序都会产生输出变量，
			- 在java中使用变量时，需要首先声明变量的数据类型，
	- 编译
		- 机器语言
		  collapsed:: true
			- java不能“直接”执行程序并输出结果，而是需要首先编译才可以运行，
		- javac命令
		  collapsed:: true
			- 可以在cmd中执行`javac file.java`，输入时不能忽略文件的扩展名.java，
			  collapsed:: true
				- 应首先保证cmd的执行位置同代码所在位置相同，
				- 可以使用cd命令更改目录，
					- Linux目录区分大小写，Windows目录不区分大小写，
			- javac语句会形成二进制文件（class），用于执行Java程序，
			  collapsed:: true
				- 若存在语法错误，则不会形成二进制文件class，
			- class文件由java虚拟机（jvm）执行，
		- 静态类型语言（static）
		  collapsed:: true
			- java的每个变量和表达式在编译时都是唯一确定的，不能在编译过程中修改，
	- 执行
		- 可以在cmd中输入`java file`来执行java程序，
	- 中断程序运行
		- 采用Ctrl+C快捷键可以强制终止程序执行，
		- 也可以尝试直接关闭进程，
- 基本编程语法
  collapsed:: true
	- 基本语法
	  collapsed:: true
		- java区分大小写，
		- java利用；来标记每条语句，利用大括号{}来对语句进行分块（block），
		- java默认忽视所有的空白字符，也不通过缩进来区分语句，但保持适当的缩进和空格便于代码的阅读，
	- 变量命名
	  collapsed:: true
		- 常量用全大写字母（数字和下划线）表示，
		- 类名称中的每个单词的首字母大写，
		- 保留字符：public，static，int， class等为java的保留字，不能用于变量名称，
	- 注释
	  collapsed:: true
		- `// comment`（或`/*comment */`）可以用来注释语句，
		-
- 数据类型
  collapsed:: true
	- 基本数据类型
	  collapsed:: true
		- 声明（declaration）
		  collapsed:: true
			- 类型安全
			  collapsed:: true
				- Java需要在使用变量前先声明变量类型，
				- java中的变量类型在声明后就不能再变化，
					- 已经声明的变量不能被重新声明为新的类型（解释器会报错），
					- 不能将不同类型的值赋值给已经声明的变量（解释器会报错），
			- 声明语句
			  collapsed:: true
				- 基本形式为int var，
				- 可以在同一个语句中声明同一类型的多个变量int var1, var2, ...，
				- 声明语句可以和赋值语句组合在一起，即int var1 = 1, var2 = 2, ...，是合法的，
		- 类型转换（cast）
			- 隐式类型转换（自动转换/coercion）
			  collapsed:: true
				- 部分（数学）运算会自动转换输入的数值的类型（如将11变为11.0），
				- 0-FFFF的任意一个十六进制数也可以自动转换为字符（char），
				- 然而，将输出的运算结果赋值给变量时仍需注意对应的数值类型，
			- 显示转型（cast）
			  collapsed:: true
				- 括号（）可以转换数据类型，一般使用方法为`(type)(value)`，
					- 如11 * 0.25会返回2.75（需要赋值给double），而11 * (int)（0.25）则会返回0（可以赋值给int），因为0.25被取整为0，
					- 具体的转换方式可参考java官方文档，
				- 转型操作的优先级高于算数运算，
			- 显式类型转换
			  collapsed:: true
				- java库中提供的一些方法可以对数据类型进行转换，
				- 如`Integer.parseInt`和`Double.parseDouble`方法可以将字符串转换为int和double，
			- 精度损失
			  collapsed:: true
				- 将double值转换为int值时，可能会产生精度的损失，
		- 整型数int
		  collapsed:: true
			- int为默认的整型数类型，使用32位二进制数表示整数，
				- long/short/byte同样可以用于表达整型数，只是它们分别使用64位/16位/8位二进制数来表示，范围分别为±2^{n-1} -1，
				- short和byte可以节省内存，但保存的位数有限，一般不常应用，
				- 若预期存储的整数位数多于10位，int类型可能会溢出（overflow）并返回一个错误值，应考虑使用long类型，
				- （java允许在整型数间加入下划线，即print(12_34)会返回1234），
			- 进制转换
				- 在数字前加入字符可以在将输入的其它进制数字转换为十进制，
				- 二进制的前置字符为0b，如print(0b1111)；同理，八进制的前置字符为0，十六进制的前置字符为0X，
			- 舍入错误
				- 计算机中设计浮点数的运算都是近似的，因此得到的取值可能与实际值存在差异，
				- 如1.0 - 0.9会返回0.09999998而不是0.1，
		- 实数（双精度浮点数）double
		  collapsed:: true
			- 理论上实数有无限多个（如无限位的小数），但计算机中的浮点数数量是有限的，
			- 因此，计算机中的浮点数一般是对实数的近似，即具体运算时可能出现精度不足的问题，
				- Infinity表示过大的数字，而NaN则代表未定义的结果，因此浮点数计算一般不会抛出异常并终止运行，
			- 可以用科学计数法aEb或aE+b表示实数a * 10 ^b，
			- java也支持用float表示浮点数，float可以节省内存，但一般可以保存7位有效数字；而double则可以保存15位有效数字，
		- 布尔值（boolean）
		  collapsed:: true
			- 布尔值只有True和False，且布尔值的运算只会返回布尔值，
			- 同其它变量一样，布尔值同样需要声明变量类型，
		- 字符（char）
		  collapsed:: true
			- 单引号括起来的字母/符号为字符类型，
				- 字符按照Unicode编码；如'a','%'等，因此可以对字符进行布尔运算（实质为比较其Unicode编码的数值），
				- 布尔运算可以用来判断输入的字符是数字还是字母，也可以用Character库中的方法判断，
			- 字符一般只用于进行赋值操作，
			- 转义字符（Escape Sequence）
				- 反斜号\可以给后面的字符不同的含义，
				- （若希望显示反斜号，可以使用\\）,
	- 高阶数据类型
		- 数组（array）
			- 声明
			  collapsed:: true
				- 类似C的数组，区别在于需要用`new`关键字来声明，即`double[] a = new double[N];`，
				- 同样可以在声明时赋值，此时不需要显式指定数组大小，即`int[] a = { 1, 1, 2, 3, 5, 8 };`,
			- 方法
			  collapsed:: true
				- java中的数组同样可以使用下标方法进行操作，
				- java有专门的数组类和对应的方法，可以使用点标记法使用，
			- 二维数组
			  collapsed:: true
				- 声明类似普通数组，即`double[][] a = new doubl[M][N];`，其中M为行数，N为列数，
				- 二维数组不能直接声明时赋值，可以使用嵌套循环来对数值进行初始化，
		- 字符串（String）
			- 定义
			  collapsed:: true
				- 全由字母/符号组成的数组为一个字符串，一般用双引号括起来，
			- 声明
			  collapsed:: true
				- java中，字符串也是一种独立的数据结构，不需要使用C中的字符数组方式声明，
				- 可以直接声明字符串`String a;`，也可以声明时赋值`String a = "app";`，
				- 应注意声明时String中的S需要大写，
			- 基本操作
				- java中的字符串不能使用下标方法，
				- +可以连接多个字符串，
				  collapsed:: true
					- 对字符串使用+操作时，数值会被主动转换为字符串（即"a" + 5会返回a5而不会报错），
					- 在脚本模式编辑时，字符串中间不能加入换行符，可以用连接符+将两个字符串连接起来，
					- 使用符号+时，应注意运算顺序和括号的使用，
			- 点方法
			  collapsed:: true
				- Java中的字符串方法一般有返回值，即不修改原字符串；使用时应注意方法的注释，
				- `length()`返回字符串中的字符数（int值），
				- `charAt(n)`返回字符串的第n（从0开始）个字符（char值），
				- `str1.concat(str2)`可以连接两个字符串，
				- `str.toLowerCase`和toUpperCase可以将字符串的所有字母转换为小写/大写，
	- 局部变量和整体变量
- 数据操作
  collapsed:: true
	- 基本操作
		- 赋值
		  collapsed:: true
			- =可以给变量赋值（=不同于数学中的相等），
			- 一般称变量的名称为“标识符”（identifier），
			- 常量赋值
			  collapsed:: true
				- final关键字可以将变量声明为常量final double PI = 3.14，
		- 数学计算
		  collapsed:: true
			- +，-，*，/，%（返回余数），
			- 除法
				- 整除：由于java区分整数和浮点数，所以整数间的除法/实际上为整除运算（如5 / 2 = 2），
				- 小数除法：对于不能整除的小数，需要使用浮点数（5.0 \ 2.0 = 2.5）来运算，
				- 求余：%运算符可以返回整除后的余数（仍为整数），
			- 运算顺序类似其它编程语言，可以用括号（）更改运算顺序，
			- ^并非幂次运算符，可以使用Math.pow(a, b)来计算a^b，
		- 布尔运算
		  collapsed:: true
			- 运算类型
				- 比较运算：==、!=、<、<=、>=，
				- 复合运算：&&（与），||（或），！（非）
					- &，|，^分别表示整数的*位逻辑操作*与，或，异或
					- 对一般的布尔值则需要双运算符，
				- 浮点数的精度有限，因此一般不直接使用浮点数的相等==来判断布尔值，而是通过测试两个数的差值是否小于某个阈值Math.abs(a - b) < c来判断，
			- 运算规则
			  collapsed:: true
				- 比较运算比算数运算的优先度低，比布尔运算的优先度高，
				- 比较运算不能连续进行，即a<b<c是不合法的，
					- 比较运算将非布尔值运算的结果转换为布尔值，
					- 需要连续运算时，应通过复合运算符（如&&）将其连接起来，
				- 同基本数学运算一样，可使用括号等方式组合布尔运算符，进行复杂的布尔运算，
		- 复合赋值语句
		  collapsed:: true
			- 类型
			  collapsed:: true
				- 复合赋值：语句i = i + n（将i的值增加n，并重新赋给i）可以简写为i += n（减法-/乘法*同理），
				- 变量的自增减：语句i = i + 1（将i的值增加1，并重新赋给i）也可以简写为i++，++i；
					- i++，++i只会将i的值增加1，
					- 右加i++先运算语句，再将i的值增加1；左加++i则先将i的值增加1，再运算语句，
					- 减法-同理，
			- 性质
			  collapsed:: true
				- 复合赋值一般只能用于整数，
				- 复合赋值符在其它操作符计算完成后执行，
				- 复合赋值符中间没有空格，
		- 运算符的顺序
		  collapsed:: true
			- java的运算顺序为从右到左，从上到下；即将右侧的值赋给左侧的变量，逐行运算，
			- 结合（associativity）规则
				- 一般的运算符都为左结合（从左往右计算），如a - b + c为（a - b）+ c，
				- 赋值运算为右结合，如a = b = 5先将b赋值为5，再将a赋值为b（5），
	- 控制语句
	  collapsed:: true
		- 条件语句（condition）
		  collapsed:: true
			- if-else语句
			  collapsed:: true
				- 基本用法
				  collapsed:: true
					- 语法为`if(boolean){func;} else{func2;}`，
					- 布尔值之后不需要分号，
					- 需要在语句后加入分号，而并非在大括号后，
				- else if语句
				  collapsed:: true
					- 基本用法为`else if(boolean){func;}`，
					- else if语句需要在if语句之后，其实质为嵌套条件语句，
					- java会逐个检查if/else if后的布尔值，布尔值为true则执行后面的语句，否则就检查下一个条件，直到最后的else语句，
				- else语句
				  collapsed:: true
					- else语句需要在if/else if语句之后，当表达式为false时即执行else后的语句，
					- 可以没有else语句，
					- （若所有条件都为false，且没有else语句，则不会执行任务），
				- 注意事项
					- 使用条件语句时应注意赋值符号=和相等符号==的区分，
					- java不使用缩进来区分语句，因此在写else语句时应注意else匹配的if语句， 并使用花括号{}来标识if语句，
			- 条件操作符
			  collapsed:: true
				- 基本语法为`(boolean)?(statement1):(statement2)；`若布尔值为True，则执行语句1，否则执行语句2，
				- 条件操作符可以简化if语句的书写，但可能会使代码难以理解，
			- switch语句
			  collapsed:: true
				- 面临多个条件时可以使用switch语句，
				  collapsed:: true
					- 理论上，也可以使用嵌套if语句，但这会使代码难以理解，
				- 基本语法为`switch (status) {case var_1: statement_1; break; ... case var_n: statement_n; break; default: statement}`，
				  collapsed:: true
					- 不同于if语句的布尔值条件（T/F两种可能），switch语句可以接受其它条件，
					  collapsed:: true
						- 条件由status语句算出，与case后的结果相对应，
						- 一般条件为0，1，2等整数，也可以为更复杂的字符串（string），
					- `break`语句会在执行完条件对应的语句后终止switch语句，
						- 若不使用break，则执行完case后的语句后，Java会继续判断其它case，直到遇到break或到达switch语句的结尾，
					- 可以在结尾加入default语句，若没有条件匹配则执行default语句后的语句，
		- 循环语句（loop）
		  collapsed:: true
			- while语句：基本用法为`while(boolean){func};`，
			  collapsed:: true
				- while语句可以理解为一系列的if语句，即只要布尔值为true，就执行之后的语句，
			- for语句：基本用法为`for(initialize; boolean; increment){func}`，
			  collapsed:: true
				- for语句一般可以理解为while语句的简化形式，主要用于需要递增（如i = i +1）的语句中，
				- 作用域（scope）：for语句虽然简化了书写，但for语句中的递增变量在语句后就会消失，不能用于以后的运算，
			- 循环语句在计算机编程中十分重要， 但也可能导致错误；可以尝试使用print语句来打印出部分循环的结果，以追踪每次操作，
		- 嵌套（nesting）
		  collapsed:: true
			- 语句与其它函数在编程时地位是相同的，因此可以随时按需使用这些语句，或将语句组合起来形成复合语句，
			- 应注意，在嵌套语句中，外部循环每执行一次，内部循环会执行一整轮，
		- 流程图
		  collapsed:: true
			- 对于复杂的任务，应使用流程图规划嵌套语句，
			- 应首先确定需要设置的变量，然后重点跟踪变量的取值变化，
			- 运算中的临时变量不一定需要单独保留，
	- 函数（function）
	  collapsed:: true
		- 自定义函数
			- 定义
			  collapsed:: true
				- 类似C中的函数，需要声明参数类型和返回值类型，但还需要加上前缀`public static` ，
				- 若没有参数（void）时，则函数原型中的参数也不应写出void类型；但没有返回值时，需要显式写出void类型，即`public static void func()`，
				- void函数虽然没有返回值，但可能会*更改*全局变量，因此编写代码时应注意，
		- main函数
		- 其它
		  collapsed:: true
			- System.currentTimeMillis()函数会返回一个long值，表示当前时间与1970年1月1日之间相差的毫秒数（需要赋值给long），
- 数据交互
  collapsed:: true
	- I/O streams
	  collapsed:: true
		- standard input/output stream are associated with an application, which supported by either the *operating system* or the *development environment*,
		- it provides the `terminal window` interface for users,
		- By convention, both programming language and the operating system process the user's *input* arguments as *strings*,
	- main函数
	  collapsed:: true
		- like C, Java's main function can receive these inputs as arguments,
		- therefore, main is writed as `main(String[] args)`, and  `String[]` means a string array,
		- *only* main function can deal with strings *followed* by program's name, such as `$ java class 1 2`, other input methods can only receive inputs *after* the class is compiled`$ java class \n`,
	- 基本输入/输出
	  collapsed:: true
		- System.in为基本输入语句，
		  collapsed:: true
			- Scanner类
			  collapsed:: true
				- Scanner对象
				  collapsed:: true
					- 需要先引入（在public class语句之前）Scanner类`import java.util.Scanner;`,
					- 语句Scanner input = new Scanner(System.in);会创建一个Scanner对象input，需要使用后续语句对input进行赋值，然后才能使用变量，
				- Scanner方法
				  collapsed:: true
					- 在cmd中运行java file后，cmd会提供一个新行来接受输入，
					- 行内输入
						- .var1 = input.nextType()将接受的输入赋给变量var1，并按照空格区分不同的输入信息，将行内的输入分别按后续语句赋值给其他变量，
						- 不同的类型需要用不同的next方法，如nextInt，nextDouble等（也需要赋值给声明的不同变量类型），
						- .nextline()方法会将回车/Enter前输入的所有信息作为一整个字符串赋值给对应变量，
						- 回车（Enter）将会结束next方法，并继续执行后续语句，
					- 行间输入
						- 回车（Enter）将会结束next方法，若后续语句仍有下一个next方法var1 = input.nextType()，则cmd会继续提供一个新行来接受输入，同样以回车（Enter）作为结束，
			- 数值输入
				- 可使用int a = Integer.parseInt(args[0])接受外界输入的int值，使用double a = Double.parseDouble(args[0])接受外界输入的double值，
		- System.out为基本输出语句，
		  collapsed:: true
			- system.out.print和system.out.println函数为基本的print函数，区别在于system.out.println函数会自动加入一个换行符，
	- `stdlib` 库
		- 概述
		  collapsed:: true
			- 来自https://introcs.cs.princeton.edu/java/stdlib/,
			- 对Java输入，输出库的一个补充；简化了一些语法，
		- 输出函数
		  collapsed:: true
			- println函数
			  collapsed:: true
				- 类似基本的println函数，可以通过`StdOut.println()`使用，
				- 默认接收参数为一个字符串，但数值输入也可以被打印；可以没有参数，此时会打印一个换行符，
				- 默认添加一个换行符，
			- printf函数
			  collapsed:: true
				- 类似C中的printf函数，可以使用占位符打印“格式化”字符串，
				- %d为int值，%f为浮点数，%s为字符串，
				- 增加宽度
				  collapsed:: true
					- 可以在%和标识符之间加入数值来增加打印变量的“宽度”，
					- 如`%5s`会在字符串的左侧增加空格，直到空格和字符串合起来有五个字符；`%-5s`则会在字符串的右侧增加空格，
					- 如果字符串比设定的宽度要长，宽度会被忽略，
				- 截取宽度
				  collapsed:: true
					- 可以在%和标识符之间加入小数点和数值来减小打印变量的“宽度”，
					- 如`%.2s`只会打印字符串的前两个字符，
					- 如果字符串比设定的宽度要短，宽度会被忽略，
				- 格式化输出和宽度的增减，可以较好的组织输出数据的表示方式，
		- 输入函数
		  collapsed:: true
			- read`type`函数
			  collapsed:: true
				- 可以从输入流（一般为命令行）中读取一个`type`类型的值，并返回一个`type`类型的变量，
			- readAll`type`函数
			  collapsed:: true
				- 可以从输入流（一般为命令行）中读取所有剩余的`type`类型的值，
				- 返回一个元素为`type`类型的数组，
				- Ctrl+D可以结束输入，
			- isEmpty函数
				- 如果输入流中没有剩余的值则返回 true，否则返回 false，
	- 重定向
	  collapsed:: true
		- 类似C，可以使用`file <`，`> file`将输入，输出流重定向为文件，
		- 一般将把一个程序的输出，重定向为另一个程序的输入的流程叫做管道（piping），可以使用` | `  实现，即`java RandomSeq 1000 100.0 200.0 | java Average`，
	- `StdDraw`库
- 库（module）
  collapsed:: true
	- 基本概念
	  collapsed:: true
		- 包含了已经写好的函数的java代码，也会包含一些具体数值（如自然对数e），
		- api（应用程序编程接口）
			- 对如何应用库中的方法的描述，
			- 一般由库的在线文档给出，因此使用方法时应考虑在在线文档中搜索，
	- 库的使用
		- import语句
		  collapsed:: true
			- 使用部分Java的内置库和同一路径下的java文件时，不需要使用显式的`import`语句，
			- 使用其它的库则需要使用`import module;`引入（在public class语句之前），
		- 命名空间
		  collapsed:: true
			- 类似python，Java中的方法也与库的名称对应，
			- 因此使用相同名称的方法不会冲突，但需要加上类的名称，如`StdOut.println()`和`System.out.println()` ，
	- Math库
		- 常量
		  collapsed:: true
			- `Math.PI`, `Math.E`为double型常量，
		- 方法
		  collapsed:: true
			- 三角函数/反三角函数
				- 函数接受的都为double值，但默认单位为弧度，
				- 可以用toRadians或toDegrees方法相互转换，
			- 指数函数/对数函数
				- .pow(a，b)函数可以用来计算幂，log()可以计算自然对数，
			- .random()函数会返回一个0.0-1.0之间的随机浮点数，
				- 生成的数值需要赋值给double，也可以使用类型转换将其更改为int类型，
			- .abs()函数可以接受double值或int值，返回数值的绝对值（同类型），
			- .ceil(), floor()分别为向上，向下取整，
			- .min(), max()返回两个值中的较小/较大值，
	- Character库
	  collapsed:: true
		- 接受一个字符，返回一个布尔值，
		- 一般用于判断数字/字符，或字符的大小写，
-
-
-
-
-
-
-
-
- 其它
	- （计算机基础）
	  collapsed:: true
		- 内存：存储程序和程序需要的数据，每个字节（bit）都有唯一的位置，
		- 机器语言（二进制），汇编语言，高级语言，
		- 操作系统：给不同的程序分配计算机资源，
	- 计算机程序
	  collapsed:: true
		- 算法
			- 通过计算机擅长的方式设计解决问题的策略，
			- 包括需要执行的动作，和动作的执行顺序，
			- 关键在于解决问题，因此可以通过部分“伪代码”来描述，
		- 实现
			- 利用编程语言实现算法，
	- 软件开发
	  collapsed:: true
		- 需求分析
		- 软件框架
			- 确定系统的输入与输出，
			- 一般的程序更注重输出的结果，再通过希望得到的结果分析需要怎样的输出，
		- 系统设计
			- 将问题分解为多个小部分，
			- 设计每个组成部分的具体方案
			- 将系统设计翻译为程序（实现/Implementation），
		- 系统调试
			- 测试系统的可执行性，
			- 调试
				- 语法（syntax）错误/编译（compile）错误
				- 运行时（runtime）错误
				- 逻辑（logic）错误
		- 部署与维护
-
- [[数据结构]]