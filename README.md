# 结构化绑定

[# 结构化绑定](#std::array)

[# 结构化绑定](# std::array)


1.绑定到数组

```cpp
int array[3] {1, 2, 3};
auto[a, b, c] = array; //a = 1, b = 2, c = 3
auto&[x, y, z] = array; //元素都是引用类型
x = 42; //x = 42, y = 2, z = 3;
```

2.结构化绑定到pair

```cpp
std::pair pr {"cpp", "refer"};
auto[v1, v2] = pr;
```

README/#6

README.md/#6

3.结构化绑定到 map 数据结构

```cpp
std::map<int, double> m { {1, 20.3}, {2, 15.8} };
//假设只需要开头元素：
auto[first_key, first_value] = *m.begin();
cout << "f_key: " << first_key << ", f_value: " << first_value << endl;
//循环遍历：
for(auto&[key, value] : m) {
    cout << "key: " << key << ", value: " << value << endl;
}
```

4.绑定到自定义结构

```cpp
struct user{
    int id;
    double score;
};
user ur(1,100);
auto[Id, Score] = ur;
```

5.绑定到 tuple

```cpp
std::tuple<int, double> tpe {2,98};
auto&[t1, t2] = tpe;
std::cout << std::get<0>(tpe) << std::get<1>(tpe) << std::endl;
//利用std::tie()绑定到 tuple
int as;
std::tie(std::ignore, as) = tpe; //省略第一个参数
std::cout << as << std::endl;
```

# std::array

C++11新增的STL容器，设计目的是提供与数组相似的功能。不过他与其他的STL容器有一些不同：（1）array的元素是存放在实力内部而非在堆上分配空间，（2）array的内部大小必须在编译期确定，（3）array的ctor、dtor 和 copy ctor 是隐式声明的

