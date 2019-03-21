# 泰华Java编码规范V1.0学习贯彻

---

## 规范当前版本

| 版本 | 日期 | 作者 | 审批人 | 版本记录 |
| --- | --- | --- | --- | --- |
| 0.1 | 2019/03/05 | 王守坤 | - | 初始版 |
| 1.0 | 2019/03/14 | 王守坤 | **郝敬全**、公飞 | 发布版 |

---

## 简要说明

- 基于《阿里巴巴Java开发手册》修订而成
- 目标，码出高效，码出质量
- 适用于公司内所有使用Java进行编码的软件，包括**新编写**和**修改**的代码

---

## 术语

- 强制：编码时必须遵守的约定、原则
- 推荐：编码时必须考虑的约定，除非背离是适当的，否则不应当产生
- 说明：对于强制或推荐规则的解释内容，如来源、原因、危害等
- 正例：对于强制和推荐规则给出的正面的示例
- 反例：对于强制和推荐规则给出的反面的示例

---

## 名词解释

@size[0.3em](
- POJO: Plain Ordinary Java Object/ Plain Old Java Object
- OOP: Object Oriented Programming
- ORM: Object Relation Mapping
- NPE: java.lang.NullPointerException
- SOA: Service-Oriented Atrchitechture
- IDE: Integrated Development Environment
- OOM: java.lang.OutOfMemoryError
- 一方库: 本工程内部子项目模块依赖的库（jar包）
- 二方库: 公司内部发布到中央仓库，可供公司内部其它应用依赖的库（jar包）
- 三方库: 公司之外的开源库（jar包）
- RPC: Remote Procedure Call
- 方法签名：由方法名称和一个参数列表（方法的参数的顺序和类型）组成
)
---

## 编程规约

---

### 命名规约 1 【强制】

- 代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。

```java
// 反例
String _name, name_, name$;
Object $Object, object$;

void $func(){}
```

---

### 命名规约 2 【强制】

- 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。

- _说明_ ：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用。

```java
//反例

class DaZhePromotion {}// 打折

float getPingfenByName(String name); //评分

int 某变量 = 3; //中文命名
```

---

### 命名规约 3 【强制】

- 类名使用 UpperCamelCase 风格，必须遵从驼峰形式。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/82/2011_Trampeltier_1528.JPG/240px-2011_Trampeltier_1528.JPG)

```java
// 正例
class MacroPolo{}

// 反例
class marcoPolo{}

```
---

### 命名规约 4 【强制】

- 方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

```java
// 正例
String getName();

// 反例
String GetName();
String getname();
```

---

### 命名规约 5 【强制】

- 常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长

```java
// 正例
public static final int MAX_STOCK_COUNT = 1;

// 反例
public static final int MAX_COUNT = 1;
public static final int max_stock_count = 1;
```

---

### 命名规约 6 【强制】

- 抽象类命名使用 Abstract 或 Base 开头；异常类命名使用 Exception 结尾；测试类命名以它要测试的类的名称开始，以 Test 结尾。

```java
// 正例

abstract class AbstractCoder{}

class BugComeBugGoException extends Exception{}

class JavaCoderTest{}

```

---

### 命名规约 7 【强制】

- 中括号是数组类型的一部分，数组定义如下：String[] args;

```java
// 反例
String args[];
```

---

### 命名规约 8 【强制】

- POJO 类中布尔类型的变量，都不要加 is，否则部分框架解析会引起序列化错误

```java

// 正例
public Boolean getSuccess(){
   // return
}

// 反例
public boolean isSuccess(){
    // return
}
```
---

### 命名规约 9 【强制】

- 包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。

```java
package com.telchina.common.util;

public final class StringUtils{}
```

---

### 命名规约 10 【强制】

- 杜绝完全不规范的缩写，避免望文不知义

```java
// 反例
abstract class AbsClass{}// Abstract 缩写命名成 Abs
```

---

### 命名规约 11 【推荐】

- 如果使用到了设计模式，建议在类名中体现出具体模式。
- 将设计模式体现在名字中，有利于阅读者快速理解架构设计思想。

```java
public class ResourceObserver{}
```

---

### 命名规约 12 【推荐】

- 接口类中的方法和属性不要加任何修饰符号（public 也不要加），保持代码的简洁性，并加上有效的 Javadoc 注释。尽量不要在接口里定义变量，如果一定要定义变量，肯定是与接口方法相关，并且是整个应用的基础常量

```java
public interface SomeInterface{
    String COMPANY = "telchina";
    
    void func();
    
    // 反例
    public abstract void func2();
}
```

--- 

### 命名规约 13.1 【强制】 13.2 【推荐】

- 接口和实现类的命名有两套规则
  1. 对于 Service 和 DAO 类，基于 SOA 的理念，暴露出来的服务一定是接口，内部的实现类用 Impl 的后缀与接口区别。
  1. 如果是形容能力的接口名称，取对应的形容词做接口名（通常是–able 的形式）。

```java
// 13.1
interface CacheService{}

class CacheServiceImpl implements CacheService{}

// 13.2
interface Translatable{}

abstract class AbstractTranslator implements Translatable{}
```

---

### 命名规约 14 【参考】

- 枚举类名建议带上 Enum 后缀，枚举成员名称需要全大写，单词间用下划线隔开

```java
enum DealStatusEnum{
  SUCCESS,
  UNKOWN_REASON
}
```

--- 

### 命名规约 15 【参考】

- Service/DAO 层方法命名规约
  - 获取单个对象的方法用 get 做前缀。
  - 获取多个对象的方法用 list 做前缀。
  - 获取统计值的方法用 count 做前缀。
  - 插入的方法用 save（推荐）或 insert 做前缀。
  - 删除的方法用 remove（推荐）或 delete 做前缀。
  - 修改的方法用 update 做前缀。
- 领域模型命名规约
  - 数据对象：xxxDO，xxx 即为数据表名。
  - 数据传输对象：xxxDTO，xxx 为业务领域相关的名称。
  - 展示对象：xxxVO，xxx 一般为网页名称。
  - POJO 是 DO/DTO/BO/VO 的统称，禁止命名成 xxxPOJO。

---

### 常量定义 1 【强制】

- 不允许出现任何魔法值（即未经定义的常量）直接出现在代码中

```java
// 反例
String key = "0x0801_" + id; // "0x0801_"具有一定业务规则意义，须定义常量
map.put(key, value);
```

---

### 常量定义 2 【强制】

- long 或者 Long 初始赋值时，必须使用大写的 L，不能是小写的 l，小写容易跟数字1 混淆，造成误解

```java
// 反例
Long a = 2l;

// 正例
Long b = 2L;
```

---

### 常量定义 3 【推荐】

- 不要使用一个常量类维护所有常量，应该按常量功能进行归类，分开维护。如：缓存相关的常量放在类：CacheConsts 下；系统配置相关的常量放在类：ConfigConsts 下

---

### 常量定义 4 【推荐】

- 常量的复用层次有五层：跨应用共享常量、应用内共享常量、子工程内共享常量、包内共享常量、类内共享常量。
  - 跨应用共享常量：放置在二方库中，通常是 client.jar 中的 constant 目录下。
  - 应用内共享常量：放置在一方库的 modules 中的 constant 目录下。
  - 子工程内部共享常量：即在当前子工程的 constant 目录下。
  - 包内共享常量：即在当前包下单独的 constant 目录下。
  - 类内共享常量：直接在类内部 private static final 定义。

---

### 常量定义 5 【推荐】

- 如果变量值仅在一个范围内变化用 Enum 类。
- 如果还带有名称之外的延伸属性，必须使用 Enum 类。

```java
    enum WeekDate{
        MONDAY(1), TUESDAY(2), WEDNESDAY(3), THURSDAY(4), FRIDAY(5),
        SATURDAY(6), SUNDAY(7);
        
        private final int value;
        WeekDate(int v){
            this.value = v;
        }

        public int getValue() {
            return value;
        }
    }
    
    
    void exmple(WeekDate weekDate){
      System.out.println(weekDate.getValue() > 5 ? "gogogo" : "nonono");
    }
```

---

### 格式规约 1 【强制】

- 大括号的使用约定。如果是大括号内为空，则简洁地写成{}即可，不需要换行；如果是非空代码块则：
  - 左大括号前不换行。
  - 左大括号后换行。
  - 右大括号前换行。
  - 右大括号后还有 else 等代码则不换行；表示终止右大括号后必须换行。
  
---

### 格式规约 2 【强制】

- 左小括号和字符之间不出现空格；同样，右小括号和字符之间也不出现空格；而左大括号前需要空格。

---

### 格式规约 3 【强制】

- if/for/while/switch/do 等保留字与左右括号之间都必须加空格

---

### 格式规约 4 【强制】

- 任何运算符左右必须加一个空格
- 运算符包括赋值运算符=、逻辑运算符&&、加减乘除符号、三目运行符等

---

### 格式规约 5 【强制】

- 缩进采用 4 个空格，禁止使用 tab 字符

---

### 格式规约1-5示例

```java
public static void main(String args[]) {
    // 缩进 4 个空格
    String say = "hello";
    // 运算符的左右必须有一个空格
    int flag = 0;
    // 关键词 if 与括号之间必须有一个空格，括号内的 f 与左括号，0 与右括号不需要空格
    if (flag == 0) { 
        System.out.println(say);
    }
    // 左大括号前加空格且不换行；左大括号后换行
    if (flag == 1) { 
        System.out.println("world");
        // 右大括号前换行，右大括号后有 else，不用换行
    } else {
        System.out.println("ok");
        // 在右大括号后直接结束，则必须换行
    }
}
```
---

### 格式规约 6 【强制】

- 单行字符数限制不超过 120 个，超出需要换行，换行时遵循如下原则：
  - 第二行相对第一行缩进 4 个空格，从第三行开始，不再继续缩进，参考示例。
  - 运算符与下文一起换行。
  - 方法调用的点符号与下文一起换行。
  - 在多个参数超长，逗号后进行换行。
  - 在括号前不要换行。

```java
// 正例
StringBuffer sb = new StringBuffer();
//超过 120 个字符的情况下，换行缩进 4 个空格，并且方法前的点符号一起换行
sb.append("zi").append("xin")...
    .append("huang")...
    .append("huang")...
    .append("huang");
    
// 反例：
StringBuffer sb = new StringBuffer();
//超过 120 个字符的情况下，不要在括号前换行
sb.append("zi").append("xin")...append
    ("huang");
//参数很多的方法调用可能超过 120 个字符，不要在逗号前换行
method(args1, args2, args3, ...
    , argsX);
```
