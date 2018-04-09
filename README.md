# hw2-CoreDll

[Core代码](https://github.com/shirley-wu/hw2-Core)

[作业](http://www.cnblogs.com/silent-zlv/p/8684979.html)

## API

### void set(int num_max, int num_limit, int exp_num, int type = 0, int precision = 2);
* num_max: 操作数的最大值，默认1000
* num_limit: 操作数最大个数，默认20
* exp_num: 表达式个数，默认5
* type: 操作数类型，0 double, 1 int, 2 fraction，默认double
* precision: 小数精度，默认2

### void set_precision(int precision);
设置小数精度，默认2

### void set_opr(bool add, bool sub, bool mul, bool div, bool pow);
设置各个操作符是否可用。默认add, sub, mul, div可用，pow不可用

### void set_power_signal(bool s);
设置乘方符号的显示方式。true ^, false **。默认true

### void generate();
生成表达式

### void clear();
清除生成的表达式。（在运行过程中这个可以不用调用，因为generate的时候会自动调用clear，清除之前生成的表达式。__但是退出的时候请调用！！！不然内存就占那里了！！！__）

### bool get_exp(int i, std::string& s, std::string& result);
通过下标 i 获取表达式与结果。s为表达式，result为结果。返回值表示能否成功获取，一般只要下标没越界、内存没崩，就不会返回false。

### 另：
假如ui发现了什么bug或者需要什么别的设置可以告诉我们~
