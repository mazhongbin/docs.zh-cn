---
title: "属性 (F#)"
description: "了解有关 F # 属性，哪些是表示与对象相关联的值的成员。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="d98aa-104">属性</span><span class="sxs-lookup"><span data-stu-id="d98aa-104">Properties</span></span>

<span data-ttu-id="d98aa-105">*属性*表示与对象相关联的值的成员。</span><span class="sxs-lookup"><span data-stu-id="d98aa-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="d98aa-106">语法</span><span class="sxs-lookup"><span data-stu-id="d98aa-106">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="d98aa-107">备注</span><span class="sxs-lookup"><span data-stu-id="d98aa-107">Remarks</span></span>
<span data-ttu-id="d98aa-108">属性表示"具有"在面向对象编程中，表示与对象实例，或对于静态属性，与类型关联的数据的关系。</span><span class="sxs-lookup"><span data-stu-id="d98aa-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="d98aa-109">你可以声明两种方式，具体取决于是否想要 （也称为后备存储） 的基础值显式指定的属性，或如果你想要允许编译器自动生成你的后备存储的属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="d98aa-110">通常情况下，你应使用的更明确的方式，如果属性具有非普通实现和自动方法，属性为只需值或变量的简单包装时。</span><span class="sxs-lookup"><span data-stu-id="d98aa-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="d98aa-111">若要显式声明的属性，使用`member`关键字。</span><span class="sxs-lookup"><span data-stu-id="d98aa-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="d98aa-112">此声明性语法后, 跟指定的语法`get`和`set`方法，也称为*访问器*。</span><span class="sxs-lookup"><span data-stu-id="d98aa-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="d98aa-113">在语法部分中所示的显式语法的各种形式用于读/写和只读的只写属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="d98aa-114">对于只读属性，只需定义`get`方法; 对于只写属性，定义仅`set`方法。</span><span class="sxs-lookup"><span data-stu-id="d98aa-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="d98aa-115">请注意，当属性同时具有`get`和`set`访问器中，替代语法，可指定特性和是不同的每个访问器，如下面的代码中所示的可访问性修饰符。</span><span class="sxs-lookup"><span data-stu-id="d98aa-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="d98aa-116">对于读/写属性，同时具有`get`和`set`方法、 的顺序`get`和`set`可逆转。</span><span class="sxs-lookup"><span data-stu-id="d98aa-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="d98aa-117">或者，你可以提供有关所示的语法`get`仅为所示的语法和`set`仅而不是使用组合的语法。</span><span class="sxs-lookup"><span data-stu-id="d98aa-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="d98aa-118">执行此操作，从而更便于注释掉单个`get`或`set`方法时，如果这是你可能需要执行操作。</span><span class="sxs-lookup"><span data-stu-id="d98aa-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="d98aa-119">以下代码演示了此除了使用组合的语法。</span><span class="sxs-lookup"><span data-stu-id="d98aa-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="d98aa-120">私有值属性的数据被称为该保留*后备存储*。</span><span class="sxs-lookup"><span data-stu-id="d98aa-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="d98aa-121">要让编译器自动创建的后备存储，可以使用关键字`member val`，省略自我标识符，然后提供用于初始化属性的表达式。</span><span class="sxs-lookup"><span data-stu-id="d98aa-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="d98aa-122">如果该属性是可变的包括`with get, set`。</span><span class="sxs-lookup"><span data-stu-id="d98aa-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="d98aa-123">例如，下面的类类型包括两个自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="d98aa-124">`Property1`是只读的同时初始化为到主构造函数，提供的自变量和`Property2`是初始化为空字符串可设置属性：</span><span class="sxs-lookup"><span data-stu-id="d98aa-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="d98aa-125">自动实现的属性是一种类型，初始化的一部分，因此它们必须包含在任何其他成员定义之前就像`let`绑定和`do`类型定义中的绑定。</span><span class="sxs-lookup"><span data-stu-id="d98aa-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="d98aa-126">请注意在初始化时和每次访问此属性时不只会计算初始化自动实现的属性的表达式。</span><span class="sxs-lookup"><span data-stu-id="d98aa-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="d98aa-127">此行为的行为是属性的相反的显式实现。</span><span class="sxs-lookup"><span data-stu-id="d98aa-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="d98aa-128">这实际上意味着，代码来初始化这些属性将添加到类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="d98aa-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="d98aa-129">请考虑下面的代码显示此区别：</span><span class="sxs-lookup"><span data-stu-id="d98aa-129">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="d98aa-130">**输出**</span><span class="sxs-lookup"><span data-stu-id="d98aa-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="d98aa-131">前面的代码的输出显示 AutoProperty 的值不变时重复调用而 ExplicitProperty 更改每次调用时。</span><span class="sxs-lookup"><span data-stu-id="d98aa-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="d98aa-132">此示例演示一个自动实现属性的表达式不会评估每个时间，是原样显式属性的 getter 方法。</span><span class="sxs-lookup"><span data-stu-id="d98aa-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="d98aa-133">有某些库，如实体框架 (`System.Data.Entity`)，可以在不很好地使用自动实现属性的初始化的基类构造函数中执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="d98aa-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="d98aa-134">在这些情况下，请尝试使用显式的属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="d98aa-135">属性可以是类、 结构、 可区分的联合、 记录、 接口和类型扩展的成员，并且也可以在对象表达式中定义。</span><span class="sxs-lookup"><span data-stu-id="d98aa-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="d98aa-136">特性可以应用于属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="d98aa-137">将特性应用到的属性，请在单独的属性前面的行上写入属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="d98aa-138">有关更多信息，请参阅[特性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d98aa-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="d98aa-139">默认情况下，属性是公共的。</span><span class="sxs-lookup"><span data-stu-id="d98aa-139">By default, properties are public.</span></span> <span data-ttu-id="d98aa-140">可访问性修饰符也可以应用于属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="d98aa-141">若要应用可访问性修饰符，如果将其添加的属性名之前立即它旨在两者都适用`get`和`set`方法; 这些方法将其之前添加`get`和`set`是否可访问性不同的关键字所需的每个访问器。</span><span class="sxs-lookup"><span data-stu-id="d98aa-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="d98aa-142">*可访问性修饰符*可以是以下之一： `public`， `private`， `internal`。</span><span class="sxs-lookup"><span data-stu-id="d98aa-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="d98aa-143">有关详细信息，请参阅[访问控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="d98aa-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="d98aa-144">每次访问属性时，都会执行属性实现。</span><span class="sxs-lookup"><span data-stu-id="d98aa-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="d98aa-145">静态和实例属性</span><span class="sxs-lookup"><span data-stu-id="d98aa-145">Static and Instance Properties</span></span>
<span data-ttu-id="d98aa-146">属性可以是静态或实例属性。</span><span class="sxs-lookup"><span data-stu-id="d98aa-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="d98aa-147">静态属性可以调用实例情况下，和用于与不具有单个对象的类型相关联的值。</span><span class="sxs-lookup"><span data-stu-id="d98aa-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="d98aa-148">对于静态属性，省略自我标识符。</span><span class="sxs-lookup"><span data-stu-id="d98aa-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="d98aa-149">对于实例属性需要自我标识符。</span><span class="sxs-lookup"><span data-stu-id="d98aa-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="d98aa-150">以下的静态属性定义基于一个方案使用的静态字段`myStaticValue`，它是属性的后备存储。</span><span class="sxs-lookup"><span data-stu-id="d98aa-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="d98aa-151">属性也可以是数组一样，在这种情况下调用它们*索引属性*。</span><span class="sxs-lookup"><span data-stu-id="d98aa-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="d98aa-152">有关详细信息，请参阅[索引化属性](indexed-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d98aa-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="d98aa-153">属性的类型批注</span><span class="sxs-lookup"><span data-stu-id="d98aa-153">Type Annotation for Properties</span></span>
<span data-ttu-id="d98aa-154">在许多情况下，编译器具有足够的信息来推断来自后备存储类型的属性的类型，但你可以通过添加类型批注中显式设置的类型。</span><span class="sxs-lookup"><span data-stu-id="d98aa-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="d98aa-155">使用属性 set 访问器</span><span class="sxs-lookup"><span data-stu-id="d98aa-155">Using Property set Accessors</span></span>
<span data-ttu-id="d98aa-156">您可以设置提供的属性`set`通过使用访问器`<-`运算符。</span><span class="sxs-lookup"><span data-stu-id="d98aa-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="d98aa-157">输出**20**。</span><span class="sxs-lookup"><span data-stu-id="d98aa-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="d98aa-158">抽象属性</span><span class="sxs-lookup"><span data-stu-id="d98aa-158">Abstract Properties</span></span>
<span data-ttu-id="d98aa-159">属性可以是抽象的。</span><span class="sxs-lookup"><span data-stu-id="d98aa-159">Properties can be abstract.</span></span> <span data-ttu-id="d98aa-160">与方法一样，`abstract`只是与属性关联的虚拟调度意味着。</span><span class="sxs-lookup"><span data-stu-id="d98aa-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="d98aa-161">抽象属性可以是真正抽象的也就是说，没有同一类中定义。</span><span class="sxs-lookup"><span data-stu-id="d98aa-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="d98aa-162">因此，包含此属性的类是一个抽象类。</span><span class="sxs-lookup"><span data-stu-id="d98aa-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="d98aa-163">或者，抽象可能只是意味着属性是虚拟的且在这种情况下，定义必须存在于同一个类。</span><span class="sxs-lookup"><span data-stu-id="d98aa-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="d98aa-164">请注意，抽象属性不能为私有的并且一个访问器是抽象的其他必须也是抽象的。</span><span class="sxs-lookup"><span data-stu-id="d98aa-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="d98aa-165">有关抽象类的详细信息，请参阅[抽象类](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="d98aa-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="d98aa-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d98aa-166">See Also</span></span>
[<span data-ttu-id="d98aa-167">成员</span><span class="sxs-lookup"><span data-stu-id="d98aa-167">Members</span></span>](index.md)

[<span data-ttu-id="d98aa-168">方法</span><span class="sxs-lookup"><span data-stu-id="d98aa-168">Methods</span></span>](methods.md)