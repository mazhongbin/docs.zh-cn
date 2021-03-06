---
title: 'Fixed 的关键字 （F #）'
description: '了解如何可以固定到堆栈本地，若要防止收集使用 F # fixed 关键字。'
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563871"
---
# <a name="the-fixed-keyword"></a>Fixed 的关键字

F # 4.1 引入了`fixed`关键字，可用于"固定"到堆栈上的本地，以防止其被收集或在垃圾回收期间移动。  它用于低级别编程方案。

## <a name="syntax"></a>语法

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>备注

这将扩展的语法的表达式，以允许提取一个指针，并将其绑定到已阻止正在收集或在垃圾回收期间移动的名称。  

表达式中的指针固定通过`fixed`关键字绑定到通过标识符`use`关键字。  此语义是类似于通过资源管理`use`关键字。  指针被固定在范围内，而超出范围后，它不再被固定。  `fixed` 不能使用的上下文之外`use`绑定。  必须将该指针绑定到的名称与`use`。

利用`fixed`必须在函数或方法中的表达式中执行。  它不能在脚本级别或模块级别的作用域。

像所有的指针代码，这是不安全的功能，将发出警告时使用。

## <a name="example"></a>示例

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>请参阅

[NativePtr 模块](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
