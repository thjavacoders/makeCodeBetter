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

-	强制：编码时必须遵守的约定、原则
- 推荐：编码时必须考虑的约定，除非背离是适当的，否则不应当产生
- 说明：对于强制或推荐规则的解释内容，如来源、原因、危害等
- 正例：对于强制和推荐规则给出的正面的示例
- 反例：对于强制和推荐规则给出的反面的示例

---

## 名词解释

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

---

## 编程规约

---

### 命名规约 1 【强制】

代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。

```java
// 反例
String _name, name_, name$;
Object $Object, object$;

void $func(){}
```

---

### 命名规约 2 【强制】

代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。

_说明_：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用。

```java
//反例

class DaZhePromotion {}// 打折

float getPingfenByName(String name); //评分

int 某变量 = 3; //中文命名
```

---

### 命名规约 3 【强制】

类名使用 UpperCamelCase 风格，必须遵从驼峰形式。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/82/2011_Trampeltier_1528.JPG/240px-2011_Trampeltier_1528.JPG)

```java
// 正例
class MacroPolo{}

// 反例
class marcoPolo{}

```
---

### 命名规约 4 【强制】

方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

```java
// 正例
String getName();

// 反例
String GetName();
String getname();
```

---

### 命名规约 5 【强制】

常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长

```java
// 正例
public static final int MAX_STOCK_COUNT = 1;

// 反例
public static final int MAX_COUNT = 1;
public static final int max_stock_count = 1;
```





