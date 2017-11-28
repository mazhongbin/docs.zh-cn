---
title: "抽象类 (F#)"
description: "了解有关 F # 抽象类，该类将保留未实现的部分或全部成员和表示的一组不同的对象类型的常见功能。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="0f2c0-104">抽象类</span><span class="sxs-lookup"><span data-stu-id="0f2c0-104">Abstract Classes</span></span>

<span data-ttu-id="0f2c0-105">*抽象类*是留部分或全部成员未实现，以便可以由派生类中提供实现的类。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f2c0-106">语法</span><span class="sxs-lookup"><span data-stu-id="0f2c0-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="0f2c0-107">备注</span><span class="sxs-lookup"><span data-stu-id="0f2c0-107">Remarks</span></span>
<span data-ttu-id="0f2c0-108">在面向对象编程中，一个抽象类用作基类的层次结构，并表示的一组不同的对象类型的通用功能。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="0f2c0-109">名称"抽象"可以看出，抽象类通常并不对应直接拖动到的问题域中的具体实体。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="0f2c0-110">但是，它们表示许多不同的具体实体具有共同。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="0f2c0-111">抽象类必须具有`AbstractClass`属性。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="0f2c0-112">它们可以实现和尚未实现的成员。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="0f2c0-113">使用术语*抽象*当应用于类是与其他.NET 语言; 中的相同但是，使用术语*抽象*当应用于方法 （和属性） 是稍有不同在 F # 从其在其他.NET 语言中使用。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="0f2c0-114">在 F # 中，当的方法标记为`abstract`关键字，这指示成员有一个项，称为*虚拟调度槽*，该类型的虚拟函数的内部表中。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="0f2c0-115">换而言之，方法是虚拟的虽然`virtual`F # 语言中未使用关键字。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="0f2c0-116">关键字`abstract`无论是否实现该方法的虚拟方法上使用。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="0f2c0-117">虚拟调度槽的声明是独立于为该调度槽方法的定义。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="0f2c0-118">因此，虚拟方法声明和定义另一种.NET 语言的 F # 等价内容是一个抽象方法声明和独立的定义，使用的组合`default`关键字或`override`关键字。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="0f2c0-119">有关详细信息和示例，请参阅[方法](members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="0f2c0-120">一个类都被视为抽象仅在没有抽象方法的声明但未定义。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="0f2c0-121">因此，具有抽象方法的类并不一定是抽象类。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="0f2c0-122">除非类具有未定义抽象方法，不要使用**AbstractClass**属性。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="0f2c0-123">在上述语法中，*可访问性修饰符*可以是`public`，`private`或`internal`。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="0f2c0-124">有关详细信息，请参阅[访问控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="0f2c0-125">与其他类型一样，抽象类可以具有的基类和一个或多个基接口。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="0f2c0-126">每个基类或接口显示在单独的行连同`inherit`关键字。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="0f2c0-127">一个抽象类的类型定义可以包含完全定义的成员，但它也可以包含抽象成员。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="0f2c0-128">在上述语法中，抽象成员的语法是单独显示。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="0f2c0-129">在此语法中，*类型签名*的成员的列表包含的参数类型中提供顺序和返回类型、 隔开`->`令牌和/或`*`扩充根据令牌和元组形式参数。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="0f2c0-130">在签名文件中使用和 intellisense Visual Studio 代码编辑器中显示相同的抽象成员类型签名的语法。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="0f2c0-131">下面的代码演示了一个抽象类形状，有两个非抽象派生的类，Square 和圆圈。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="0f2c0-132">该示例演示如何使用抽象类、 方法和属性。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="0f2c0-133">在示例中，抽象类形状表示常见元素的具体实体圆形和正方形。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="0f2c0-134">（二维的坐标系统） 中的所有形状的常见功能都抽象到形状类： 网格、 旋转的角度和区域和外围属性上的位置。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="0f2c0-135">这些可以重写，但位置，其中各个形状无法更改的行为除外。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="0f2c0-136">旋转可以重写方法，如下所示 Circle 类，由于其对称性是固定的旋转。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="0f2c0-137">因此在圆类中，旋转方法替换为不执行任何操作的方法。</span><span class="sxs-lookup"><span data-stu-id="0f2c0-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="0f2c0-138">**输出：**</span><span class="sxs-lookup"><span data-stu-id="0f2c0-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="0f2c0-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f2c0-139">See Also</span></span>
[<span data-ttu-id="0f2c0-140">类</span><span class="sxs-lookup"><span data-stu-id="0f2c0-140">Classes</span></span>](classes.md)

[<span data-ttu-id="0f2c0-141">成员</span><span class="sxs-lookup"><span data-stu-id="0f2c0-141">Members</span></span>](members/index.md)

[<span data-ttu-id="0f2c0-142">方法</span><span class="sxs-lookup"><span data-stu-id="0f2c0-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="0f2c0-143">属性</span><span class="sxs-lookup"><span data-stu-id="0f2c0-143">Properties</span></span>](members/Properties.md)