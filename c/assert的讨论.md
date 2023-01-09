# assert的讨论



百度百科解释：

> 编写代码时，我们总是会做出一些假设，断言就是用于在代码中捕捉这些假设，可以将断言看作是异常处理的一种高级形式。断言表示为一些布尔表达式，程序员相信在程序中的某个特定点该表达式值为真。可以在任何时候启用和禁用断言验证，因此可以在测试时启用断言，而在部署时禁用断言。同样，程序投入运行后，最终用户在遇到问题时可以重新启用断言。

我在《C Primer Plus第六版》查到的解释是这样的：

> assert()宏是 为了标识出程序中某些条件为真的关键位置，如果其中的一个具体条件为 假，就用 assert()语句终止程序。

我认为可以将assert()理解为一个判断if(条件)是否成立的判断语句，如果条件为假则终止程序，否则继续执行程序。

```c
if()
{
	程序正常运行;
}
else
{
	报错&&终止程序; // 避免由该错误导致更大的程序运行错误
}
```

## assert体验

借用《C Primer Plus第六版》16.12.1的案例来体验一下assert的使用。

```c
#include <stdio.h>
#include <math.h>
#include <assert.h>

int main(int argc, char const *argv[])
{
    double x, y, z;
    puts("Enter a pair of numbers(0 0 to quit): ");
    while (scanf("%lf%lf", &x, &y) == 2 && (x != 0 || y!= 0))
    {
        z = x * x - y * y; // 应该用+
        assert(z >= 0);
        printf("answer is %f\n", sqrt(z));
        puts("Next pair of numbers: ");
    }
    puts("Done!");
    return 0;
}
```

**执行结果：**

![image-20230105173542081](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20230105173542081.png)

可以看到当z >= 0的结果不成立时，程序会报出错误所在的行及其原因，并终止程序。

## 编程规范

### 断言必须使用宏定义，禁止直接调用系统提供的assert()

断言只能在调试版本中使用，在正式发布版本中严禁使用断言，因为断言一旦被触发，程序就会立即退出。

**错误用法：**

```c
int Foo(int *array, int size)
{
	assert(array != NULL);
	...
}
```

**正确用法：**

```c
#include <assert.h>
#ifdef DEBUG
#define ASSERT(f) assert(f)
#else
#define ASSERT(f) ((void)0)
#endif
...
int Foo(int *array, int size)
{
	ASSERT(array != NULL);
	...
}
```

这样就可以通过编译选项进行控制

### 运行时可能会导致的错误，严禁使用断言

断言不能用于校验程序在运行期间可能导致的错误。

**错误用法：**

```c
FILE *fp = fopen(path, "r");
ASSERT(fp != NULL); //文件有可能打开失败
char *str = (char *)malloc(MAX_LINE);
ASSERT(str != NULL); //内存有可能分配失败
ReadLine(fp, str);
char *p = strstr(str, 'age=');
ASSERT(p != NULL); //文件中不一定存在该字符串
int age = atoi(p+4);
ASSERT(age > 0); //文件内容不一定符合预期
```

### 严禁在断言内改变运行环境

在程序正式发布阶段，断言不会被编译进去，为了确保调试版和正式版的功能一致性，严禁在断言中使用任何赋 值、修改变量、资源操作、内存申请等操作。

**错误用法：**

```c
ASSERT(p1 = p2);        // p1被修改
ASSERT(i++ > 1000);     // i被修改
ASSERT(close(fd) == 0); // fd被修改
```

### 不要将多条语句放到同一个断言中

为了更加准确地发现错误的位置，每一条断言只校验一个条件。如果一个断言同时校验多个条件，在断言触发的时 候，无法判断到底是哪一个条件导致的错误：

**错误用法：**

```c
inf Foo(int *array, int size)
{
	ASSERT(array != NULL && size > 0 && size < MAX_SIZE);
    ...
}
```

**正确用法：**

```c
inf Foo(int *array, int size)
{
	ASSERT(array != NULL);
	ASSERT(size > 0);
	ASSERT(size < NAX_SIZE);
    ...
}
```

### assert和后面的语句应空一行，以形成逻辑和视觉上的一致性





## 扩展：_Static_assert(C11)

C11新增了一个特性：`_Static_assert` 声明，其可以在编译时检查`assert()`表达式。

`_Static_assert()` 接受两个参数，第一个参数是**整型常量表达式**，第二个参数是**一个字符串**。当第一个参数求值为0（或_False），编译器会显示字符串，并终止编译。

借用《C Primer Plus第六版》16.12.2的案例来体验一下`Static_assert`的使用。

```c
#include <stdio.h>
#include <limits.h>
_Static_assert(CHAR_BIT == 16, "16-bit char falsely assumed");

int main(int argc, char const *argv[])
{
    puts("char is 16 bits.");
    return 0;
}
```

**执行结果：**

![image-20230105175430738](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20230105175430738.png)