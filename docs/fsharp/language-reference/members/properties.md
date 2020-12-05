---
title: Свойства
description: 'Сведения о свойствах F #, являющихся элементами, которые представляют значения, связанные с объектом.'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740202"
---
# <a name="properties"></a><span data-ttu-id="4ae50-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="4ae50-103">Properties</span></span>

<span data-ttu-id="4ae50-104">*Свойства* — это члены, представляющие значения, связанные с объектом.</span><span class="sxs-lookup"><span data-stu-id="4ae50-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ae50-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ae50-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4ae50-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ae50-106">Remarks</span></span>

<span data-ttu-id="4ae50-107">Свойства представляют собой отношение "имеет" в объектно-ориентированном программировании, представляющее данные, связанные с экземплярами объектов, или для статических свойств с типом.</span><span class="sxs-lookup"><span data-stu-id="4ae50-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="4ae50-108">Свойства можно объявить двумя способами, в зависимости от того, нужно ли явно указать базовое значение (также называемое резервным хранилищем) для свойства, или если вы хотите разрешить компилятору автоматически создавать резервное хранилище.</span><span class="sxs-lookup"><span data-stu-id="4ae50-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="4ae50-109">Как правило, следует использовать более явный способ, если свойство имеет нетривиальные реализации и автоматический способ, если свойство является просто простой оболочкой для значения или переменной.</span><span class="sxs-lookup"><span data-stu-id="4ae50-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="4ae50-110">Чтобы объявить свойство явным образом, используйте `member` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="4ae50-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="4ae50-111">За этим декларативным синтаксисом следует синтаксис, который задает `get` `set` методы и, а также именованные способы *доступа*.</span><span class="sxs-lookup"><span data-stu-id="4ae50-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="4ae50-112">Различные формы явного синтаксиса, показанного в разделе синтаксиса, используются для свойств для чтения и записи, только для чтения и только для записи.</span><span class="sxs-lookup"><span data-stu-id="4ae50-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="4ae50-113">Для свойств только для чтения определяется только `get` метод; для свойств только для записи определите только `set` метод.</span><span class="sxs-lookup"><span data-stu-id="4ae50-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="4ae50-114">Обратите внимание, что если свойство `get` имеет `set` методы доступа и, альтернативный синтаксис позволяет указать атрибуты и модификаторы доступа, которые отличаются для каждого метода доступа, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4ae50-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="4ae50-115">Для свойств чтения и записи, имеющих оба `get` `set` метода и, порядок `get` и `set` может быть отменен.</span><span class="sxs-lookup"><span data-stu-id="4ae50-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="4ae50-116">Кроме того, можно указать синтаксис, отображаемый `get` только для, и синтаксис, отображаемый `set` только вместо использования объединенного синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="4ae50-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="4ae50-117">Это упрощает комментирование отдельных `get` `set` методов или, если это может потребоваться.</span><span class="sxs-lookup"><span data-stu-id="4ae50-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="4ae50-118">В следующем коде показана альтернатива использованию объединенного синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="4ae50-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="4ae50-119">Закрытые значения, которые содержат данные для свойств, называются *резервными хранилищами*.</span><span class="sxs-lookup"><span data-stu-id="4ae50-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="4ae50-120">Чтобы компилятор автоматически создает резервное хранилище, используйте ключевые слова `member val` , опустите сам себя, а затем укажите выражение для инициализации свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="4ae50-121">Если свойство должно быть изменяемым, включите `with get, set` .</span><span class="sxs-lookup"><span data-stu-id="4ae50-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="4ae50-122">Например, следующий тип класса включает два автоматически реализуемых свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="4ae50-123">`Property1` параметр доступен только для чтения и инициализируется с аргументом, предоставленным первичному конструктору, и `Property2` является устанавливаемым свойством, инициализированным в виде пустой строки:</span><span class="sxs-lookup"><span data-stu-id="4ae50-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="4ae50-124">Автоматически реализованные свойства являются частью инициализации типа, поэтому они должны быть включены перед любыми другими определениями элементов, как `let` привязки и `do` привязки в определении типа.</span><span class="sxs-lookup"><span data-stu-id="4ae50-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="4ae50-125">Обратите внимание, что выражение, которое инициализирует автоматически реализуемое свойство, вычисляется только при инициализации, а не всякий раз, когда осуществляется доступ к свойству.</span><span class="sxs-lookup"><span data-stu-id="4ae50-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="4ae50-126">Это поведение отличается от поведения явно реализованного свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="4ae50-127">Это фактически означает, что код для инициализации этих свойств добавляется в конструктор класса.</span><span class="sxs-lookup"><span data-stu-id="4ae50-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="4ae50-128">Рассмотрим следующий код, демонстрирующий это различие:</span><span class="sxs-lookup"><span data-stu-id="4ae50-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

<span data-ttu-id="4ae50-129">**Выходные данные**</span><span class="sxs-lookup"><span data-stu-id="4ae50-129">**Output**</span></span>

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="4ae50-130">Выходные данные приведенного выше кода показывают, что значение автосвойства не изменяется при повторном вызове, в то время как ЕксплиЦитпроперти изменяется при каждом вызове.</span><span class="sxs-lookup"><span data-stu-id="4ae50-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="4ae50-131">Это показывает, что выражение для автоматически реализуемого свойства не вычисляется каждый раз, как и метод считывания для явного свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="4ae50-132">Существуют некоторые библиотеки, например Entity Framework ( `System.Data.Entity` ), выполняющие пользовательские операции в конструкторах базовых классов, которые не подходят для инициализации автоматически реализуемых свойств.</span><span class="sxs-lookup"><span data-stu-id="4ae50-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="4ae50-133">В таких случаях попробуйте использовать явные свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="4ae50-134">Свойства могут быть членами классов, структур, размеченных объединений, записей, интерфейсов и расширений типов, а также могут быть определены в выражениях объекта.</span><span class="sxs-lookup"><span data-stu-id="4ae50-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="4ae50-135">Атрибуты могут применяться к свойствам.</span><span class="sxs-lookup"><span data-stu-id="4ae50-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="4ae50-136">Чтобы применить атрибут к свойству, запишите атрибут в отдельной строке перед свойством.</span><span class="sxs-lookup"><span data-stu-id="4ae50-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="4ae50-137">Дополнительные сведения см. в разделе [Атрибуты](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4ae50-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="4ae50-138">По умолчанию свойства являются открытыми.</span><span class="sxs-lookup"><span data-stu-id="4ae50-138">By default, properties are public.</span></span> <span data-ttu-id="4ae50-139">Модификаторы доступа также могут применяться к свойствам.</span><span class="sxs-lookup"><span data-stu-id="4ae50-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="4ae50-140">Чтобы применить модификатор доступа, добавьте его непосредственно перед именем свойства, если оно должно применяться к `get` `set` методам и. Добавьте его перед `get` `set` ключевыми словами и, если для каждого метода доступа требуется разная доступность.</span><span class="sxs-lookup"><span data-stu-id="4ae50-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="4ae50-141">*Модификатором Accessibility* может быть один из следующих: `public` , `private` , `internal` .</span><span class="sxs-lookup"><span data-stu-id="4ae50-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="4ae50-142">Дополнительные сведения см. в статье [Управление доступом](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="4ae50-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="4ae50-143">Реализации свойств выполняются каждый раз при доступе к свойству.</span><span class="sxs-lookup"><span data-stu-id="4ae50-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="4ae50-144">Статические и свойства экземпляра</span><span class="sxs-lookup"><span data-stu-id="4ae50-144">Static and Instance Properties</span></span>

<span data-ttu-id="4ae50-145">Свойства могут быть статическими или свойствами экземпляра.</span><span class="sxs-lookup"><span data-stu-id="4ae50-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="4ae50-146">Статические свойства могут вызываться без экземпляра и использоваться для значений, связанных с типом, а не с отдельными объектами.</span><span class="sxs-lookup"><span data-stu-id="4ae50-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="4ae50-147">Для статических свойств опустите собственный идентификатор.</span><span class="sxs-lookup"><span data-stu-id="4ae50-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="4ae50-148">Для свойств экземпляра необходим собственный идентификатор.</span><span class="sxs-lookup"><span data-stu-id="4ae50-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="4ae50-149">Следующее Статическое определение свойства основано на сценарии, в котором имеется статическое поле `myStaticValue` , являющееся резервным хранилищем для свойства.</span><span class="sxs-lookup"><span data-stu-id="4ae50-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="4ae50-150">Свойства также могут быть подобны массиву, в этом случае они называются *индексированными свойствами*.</span><span class="sxs-lookup"><span data-stu-id="4ae50-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="4ae50-151">Дополнительные сведения см. в разделе [индексированные свойства](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4ae50-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="4ae50-152">Аннотация типа для свойств</span><span class="sxs-lookup"><span data-stu-id="4ae50-152">Type Annotation for Properties</span></span>

<span data-ttu-id="4ae50-153">Во многих случаях компилятор имеет достаточно информации для определения типа свойства из типа резервного хранилища, но можно явно задать тип, добавив аннотацию типа.</span><span class="sxs-lookup"><span data-stu-id="4ae50-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="4ae50-154">Использование методов доступа set свойств</span><span class="sxs-lookup"><span data-stu-id="4ae50-154">Using Property set Accessors</span></span>

<span data-ttu-id="4ae50-155">Свойства, предоставляющие методы доступа, можно задать `set` с помощью `<-` оператора.</span><span class="sxs-lookup"><span data-stu-id="4ae50-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="4ae50-156">Выходные данные имеют значение **20**.</span><span class="sxs-lookup"><span data-stu-id="4ae50-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="4ae50-157">Абстрактные свойства</span><span class="sxs-lookup"><span data-stu-id="4ae50-157">Abstract Properties</span></span>

<span data-ttu-id="4ae50-158">Свойства могут быть абстрактными.</span><span class="sxs-lookup"><span data-stu-id="4ae50-158">Properties can be abstract.</span></span> <span data-ttu-id="4ae50-159">Как и в случае с методами, `abstract` просто означает, что существует виртуальная диспетчеризация, связанная со свойством.</span><span class="sxs-lookup"><span data-stu-id="4ae50-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="4ae50-160">Абстрактные свойства могут быть действительно абстрактными, то есть без определения в том же классе.</span><span class="sxs-lookup"><span data-stu-id="4ae50-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="4ae50-161">Таким образом, класс, содержащий такое свойство, является абстрактным классом.</span><span class="sxs-lookup"><span data-stu-id="4ae50-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="4ae50-162">Кроме того, abstract может означать, что свойство является виртуальным, и в этом случае определение должно присутствовать в том же классе.</span><span class="sxs-lookup"><span data-stu-id="4ae50-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="4ae50-163">Обратите внимание, что абстрактные свойства не должны быть частными, и если один метод доступа является абстрактным, то другой также должен быть абстрактным.</span><span class="sxs-lookup"><span data-stu-id="4ae50-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="4ae50-164">Дополнительные сведения о абстрактных классах см. в разделе [абстрактные классы](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="4ae50-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="4ae50-165">См. также</span><span class="sxs-lookup"><span data-stu-id="4ae50-165">See also</span></span>

- [<span data-ttu-id="4ae50-166">Члены</span><span class="sxs-lookup"><span data-stu-id="4ae50-166">Members</span></span>](index.md)
- [<span data-ttu-id="4ae50-167">Методы</span><span class="sxs-lookup"><span data-stu-id="4ae50-167">Methods</span></span>](methods.md)
