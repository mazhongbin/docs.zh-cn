---
title: short（C# 参考）
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 657d5bb3866a3ad88226740ebf7ef12c3654e56b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288159"
---
# <a name="short-c-reference"></a>short（C# 参考）

`short` 表示一种整数数据类型，该类型根据下表显示的大小和范围存储值。  
  
|类型|范围|大小|.NET Framework 类型|  
|----------|-----------|----------|-------------------------|  
|`short`|-32,768 到 32,767|有符号 16 位整数|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>文本  

可以通过为其分配十进制文本、十六进制文本或（从 C# 7.0 开始）二进制文本来声明和初始化 `short` 变量。  如果整数文本在 `short` 范围之外（即，如果它小于 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大于 <xref:System.Int16.MaxValue?displayProperty=nameWithType>），会发生编译错误。 

在以下示例中，等于 1,034、表示为十进制、十六进制和二进制文本的整数从 [int](../../../csharp/language-reference/keywords/int.md) 隐式转换为 `short` 值。  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> 使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。 十进制文本没有前缀。

从 C# 7.0 开始，添加了一些功能以增强可读性。 
 - C# 7.0 允许将下划线字符 (`_`) 用作数字分隔符。
 - C# 7.2 允许将 `_` 用作二进制或十六进制文本的数字分隔符，位于前缀之后。 十进制文本不能够有前导下划线。

下面是一些示例。

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>编译器重载解析

 调用重载方法时必须使用强制转换。 以下面使用 `short` 和 [int](../../../csharp/language-reference/keywords/int.md) 参数的重载方法为例：  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 使用 `short` 强制转换可保证调用正确的类型，例如：  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>转换  

 存在从 `short` 到 [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的预定义隐式转换。  
  
 不能将存储大小更大的非文本数值类型隐式转换为 `short` 类型（有关整型类型的存储大小的信息，请参阅[整型类型表](../../../csharp/language-reference/keywords/integral-types-table.md)）。 以下面两个 `short` 变量 `x` 和 `y` 为例：  
  
```csharp  
short x = 5, y = 12;  
```  
  
 以下赋值语句将产生一个编译器错误，原因是赋值运算符右侧的算术表达式的计算结果默认为 [int](../../../csharp/language-reference/keywords/int.md) 类型。  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 若要解决此问题，请使用强制转换：  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 在目标变量具有相同或更大的存储大小时，还可以使用下列语句：  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 不存在从浮点型到 `short` 类型的隐式转换。 例如，除非使用显式强制转换，否则以下语句将生成编译器错误：  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 有关兼用浮点类型和整型类型的算术表达式的信息，请参阅 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 有关隐式数值转换规则的详细信息，请参阅[隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 语言规范  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Int16>  
 [C# 参考](../../../csharp/language-reference/index.md)  
 [C# 编程指南](../../../csharp/programming-guide/index.md)  
 [C# 关键字](../../../csharp/language-reference/keywords/index.md)  
 [整型表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [内置类型表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [显式数值转换表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
