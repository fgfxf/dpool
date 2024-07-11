![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg) ![Build status](https://github.com/fgfxf/dpool/assets/38068739/31a6d592-063a-4d7a-b917-db896108bef8)
## 更新
* @author senlinzhan  | fgfxf
* @date 2017  | 2023改进
* @note 用chartGPT辅助下增加了对c++17 20版本的支持，增加了一些get set函数
* @note 线程池会自动回收空闲线程，无需从外部主动释放，请放心上船
* @warning 作为合格的开发者，应当保证线程池单例化，因此函数和声明没有分离，
* 如果想要多实例的线程池，请把本hpp文件中的“非模板类成员函数”分离出来即可。
* @warning set方法没有做健壮性检测，作为合格的开发者，相信您不会犯这样的错误。
* @see https://github.com/senlinzhan/dpool

# dpool 

使用 C++11 实现的动态线程池，主要特性：
- 使用简单，不易出错。 
- 支持线程复用，提升性能。
- 支持懒惰创建线程。
- 必要时自动回收空闲的线程。 

## 快速上手
```C++
#include "ThreadPool.hpp"
#include <iostream>

int compute(int a, int b)
{
    return a + b;
}

int main()
{
    // 设置最大线程数为 10
    dpool::ThreadPool pool(10);

    auto fut = pool.submit(compute, 100, 100);
    std::cout << "100 + 100 = " << fut.get() << std::endl;
    
    return 0;
}
```
