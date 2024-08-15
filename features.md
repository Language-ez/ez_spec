# 编程语言特性文档 (Programming Language Features)
**这是一种极简主义编译型运行时语言(It's a minimalist compiled runtime language.)**


## 1. 基础类型 (Basic Types)

### 1.1 布尔型 (Boolean)
- **描述 (Description)**: 布尔型用于表示真 (true) 或假 (false) 值。常用于条件判断和控制流中。
- **示例 (Example)**:
  ```plaintext
  flag := true  // 变量 `flag` 的值为 true
  isValid := false  // 变量 `isValid` 的值为 false
  ```

### 1.2 数值型 (Numeric)
- **描述 (Description)**: 数值型用于表示整数和浮点数。支持基本的算术操作，如加减乘除。

#### 1.2.1 整数 (Integer)
- **描述 (Description)**: 整数类型用于表示没有小数部分的数值。通常用于计数、索引等操作。
- **示例 (Example)**:
  ```plaintext
  int number := 42  // 定义一个整数变量 `number`，值为 42
  age := 25  // 自动推断为整数类型，值为 25
  ```

#### 1.2.2 浮点数 (Float)
- **描述 (Description)**: 浮点数类型用于表示带有小数部分的数值。适用于需要更高精度的计算。
- **示例 (Example)**:
  ```plaintext
  pi := 3.14  // 定义一个浮点数变量 `pi`，值为 3.14
  height := 1.75  // 自动推断为浮点数类型，值为 1.75
  ```

### 1.3 字符串型 (String)
- **描述 (Description)**: 字符串型用于表示文本数据。字符串是不可变的，可以包含任何字符。
- **示例 (Example)**:
  ```plaintext
  greeting := "Hello, world!"  // 定义一个字符串变量 `greeting`
  name := "Alice"  // 自动推断为字符串类型，值为 "Alice"
  ```

### 1.4 数组 (Array)
- **描述 (Description)**: 数组是一种固定大小的集合，存储相同类型的元素。数组在定义时即确定了其大小和类型。
- **示例 (Example)**:
  ```plaintext
  numbers := [1, 2, 3, 4, 5]  // 定义一个整数数组，包含5个元素
  fixedSizeArray := int[12]  // 定义一个固定大小为12的整数数组
  ```

### 1.5 动态数组 (Slice)
- **描述 (Description)**: 动态数组（切片）是一种可变大小的数组，支持在运行时动态调整大小。切片在使用时无需预先定义大小。
- **示例 (Example)**:
  ```plaintext
  slice_0 := [1,2,3,]  // 定义一个整数切片，初始值为1,2,3
  slice_1 := int[5,]  // 定义一个容量为5的整数切片，可扩展
  slice_2 := int[5,10]  // 定义一个初始容量为5，最大容量为10的整数切片
  slice := int[]  // 定义一个空的整数切片
  slice.append(4)  // 向切片中添加元素4
  ```

### 1.6 结构体 (Struct)
- **描述 (Description)**: 结构体用于定义用户自定义的数据结构，能够包含多个不同类型的字段。结构体适用于表示复杂的数据对象。
- **示例 (Example)**:
  ```plaintext
  Person := struct {
    <string>name  // 定义结构体字段 `name`，类型为字符串
    <int>age  // 定义结构体字段 `age`，类型为整数
  }

  person := Person { name: "Alice", age: 30 }  // 使用字段名初始化结构体
  person_1 := new Person  // 创建一个空的结构体实例
  ```

### 1.7 函数 (Function)
- **描述 (Description)**: 函数用于封装可重复使用的代码块。支持高阶函数（函数作为参数或返回值）和匿名函数。函数签名允许重载。
- **示例 (Example)**:
  ```plaintext
  add := func(int a, int b) int {
    return a + b  // 返回两个整数的和
  }

  result := add(5, 3)  // 调用函数 `add`，结果为8
  ```

### 1.8 线程 (Thread)
- **描述 (Description)**: 该语言支持多线程并发编程，允许在多个线程中并行执行代码。线程可以独立执行函数或任务。
- **示例 (Example)**:
  ```plaintext
  runInThread := func() {
    // 执行一些任务
  }

  thread := thread(runInThread, 3)  // 创建3个线程来执行 `runInThread` 函数
  run(thread)  // 启动线程
  ```

### 1.9 Map
- **描述 (Description)**: Map 是一种键值对集合，支持动态增加和删除键值对。Map 的键和值可以是任意类型，初始化时会自动推断类型。
- **示例 (Example)**:
  ```plaintext
  map := {"key1": 10, "key2": 20}  // 定义一个键值对，键为字符串，值为整数
  map["key3"] := 30  // 添加一个新的键值对
  ```

## 2. 特性总结 (Feature Summary)

- **基础类型 (Basic Types)**: 布尔型、数值型、字符串型
- **数据结构 (Data Structures)**: 数组、动态数组（切片）、结构体、Map
- **函数支持 (Function Support)**: 支持高阶函数和匿名函数，函数签名允许重载
- **并发支持 (Concurrency Support)**: 支持多线程编程

## 3. 示例 (Examples)

### 示例 1: 使用数组和函数 (Using Arrays and Functions)
```plaintext
sum := func(int[] arr) int {
  total := 0
  for value in arr {
    total := total + value  // 累加数组中的值
  }
  return total  // 返回总和
}

numbers := [1, 2, 3, 4, 5]  // 定义一个整数数组
total := sum(numbers)  // 计算数组元素的总和
```

### 示例 2: 使用动态数组和线程 (Using Dynamic Arrays and Threads)
```plaintext
printNumbers := func() {
  slice := [1, 2, 3,]  // 定义一个切片
  slice.append(4)  // 向切片中添加元素
  for num in slice {
    print(num)  // 打印切片中的每个元素
  }
}

thread := thread(printNumbers)  // 创建一个线程执行 `printNumbers` 函数
thread.run()  // 启动线程
```

### 示例 3: 使用结构体和 Map (Using Structs and Maps)
```plaintext
Book := struct {
  string title  // 定义字段 `title`，类型为字符串
  int pages  // 定义字段 `pages`，类型为整数
}

book := Book { title: "The Great Book", pages: 300 }  // 使用字段名初始化结构体
library := {"book1": book}  // 定义一个 Map，将字符串键与 `Book` 结构体关联
library["book2"] := Book { title: "Another Book", pages: 150 }  // 向 Map 添加新的键值对
```

## 4. 语法特性 (Syntax Features)

- **自动推断类型 (Type Inference)**: 编译器能够根据上下文自动推断变量的类型，通常无需显式指定类型。
- **灵活的语句结束符 (Flexible Statement Terminators)**: 语句可以使用换行或分号 (;) 作为结束符。推荐使用换行符，以提高代码的可读性。
- **注释 (Comments)**: 支持单行注释和多行注释，使用 `//` 表示单行注释，使用 `/* */` 表示多行注释。

