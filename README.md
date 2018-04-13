# hw2-CoreDll

[Core代码](https://github.com/shirley-wu/hw2-Core)

[作业](http://www.cnblogs.com/silent-zlv/p/8684979.html)

## 使用方法

头文件: dll.h

链接库: 
* x64/Debug/Core.lib, Core.dll
* x64/Release/Core.lib, Core.dll
* x86/Debug/Core.lib, Core.dll
* x86/Release/Core.lib, Core.dll

注: 四个版本的接口完全相同，均使用dll.h即可。Release/的库运行会比Debug/的快，不过考虑到std::string可能会出现不兼容问题，我还是分别提供了两个版本。希望有问题立刻联系我们。

## API

### void set(int num_max, int num_limit, int exp_num, int type = 0, int precision = 2);
* num_max: 操作数的最大值，默认1000，有效范围1 ~ INT_MAX
* num_limit: 操作数最大个数，默认20，有效范围1 ~ INT_MAX
* exp_num: 表达式个数，默认5，有效范围1 ~ INT_MAX
* type: 操作数类型，有效范围0 double, 1 int, 2 fraction，默认double
* precision: 小数精度，默认2，有效范围1 ~ INT_MAX
* 以上几个设置项中，假如有某项的值不在有效范围内，该项不进行设置。

### void set_precision(int precision);
设置小数精度，默认2，有效范围1 ~ INT_MAX。假如值不在有效范围内，不进行设置。

### void set_opr(bool add, bool sub, bool mul, bool div, bool pow);
设置各个操作符是否可用。默认add, sub, mul, div可用，pow不可用。至少有一个为true才有效。假如全为false，不进行修改。

### void set_power_signal(bool s);
设置乘方符号的显示方式。true ^, false **。默认true

### void generate();
生成表达式

### void clear();
清除生成的表达式。（在运行过程中这个可以不用调用，因为generate的时候会自动调用clear，清除之前生成的表达式。__但是退出的时候请调用！！！不然内存就占那里了！！！__）

### bool get_exp(int i, std::string& s, std::string& result);
通过下标 i 获取第i个表达式与结果。s为表达式，result为结果。返回值表示能否成功获取，一般只要下标没越界、内存没崩，就不会返回false。

### bool get_expression(int i, char* s, int size);
通过下标 i 获取第i个表达式。s为char数组指针，size为数组大小。返回值表示能否成功获取。若返回false，可能是因为下标i越界或数组容量不够。

### bool get_answer(int i, char* s, int size);
通过下标 i 获取第i个结果。s为char数组指针，size为数组大小。返回值表示能否成功获取。若返回false，可能是因为下标i越界或数组容量不够。

### bool exp_to_file(const char* dir);
将所有表达式写入一个文件，各个式子之间以'\n'分隔。dir为表达式目标文件的绝对路径，如"D:\\Users\\wu-pc\\repos\\hw2\\expression.txt"。返回值表示是否成功；若文件操作错误，或尚未生成任何式子，返回false。__注：C盘有可能会因为权限不够无法生成文件。__

### bool ans_to_file(const char* dir);
将所有答案写入一个文件，类似exp_to_file。

### 另：
假如ui发现了什么bug或者需要什么别的设置可以告诉我们~本组成员为齐天扬与吴雪晴
