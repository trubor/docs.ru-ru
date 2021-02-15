---
description: 'Дополнительные сведения: типы значений и ссылочные типы'
title: Value Types and Reference Types
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 22cce68260955545e810f6fefe645b5ad6a37ca5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462143"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="da3dd-103">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="da3dd-103">Value Types and Reference Types</span></span>

<span data-ttu-id="da3dd-104">В Visual Basic есть два типа типов: ссылочные типы и типы значений.</span><span class="sxs-lookup"><span data-stu-id="da3dd-104">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="da3dd-105">В переменных ссылочных типов хранятся ссылки на их данные (объекты), а переменные типа значений содержат свои данные непосредственно.</span><span class="sxs-lookup"><span data-stu-id="da3dd-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="da3dd-106">Две переменные ссылочного типа могут ссылаться на один и тот же объект, поэтому операции над одной переменной могут затрагивать объект, на который ссылается другая переменная.</span><span class="sxs-lookup"><span data-stu-id="da3dd-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="da3dd-107">В случае с типами значений каждая переменная имеет собственную копию данных, и операции с одной переменной не могут влиять на другую (за исключением [модификатора ByRef в параметрах](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="da3dd-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="da3dd-108">Типы значений</span><span class="sxs-lookup"><span data-stu-id="da3dd-108">Value Types</span></span>  

 <span data-ttu-id="da3dd-109">Тип данных — это *тип значения* , если он содержит данные в пределах отдельного выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="da3dd-109">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="da3dd-110">К типам значений относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="da3dd-110">Value types include the following:</span></span>  
  
- <span data-ttu-id="da3dd-111">Все числовые типы данных</span><span class="sxs-lookup"><span data-stu-id="da3dd-111">All numeric data types</span></span>  
  
- <span data-ttu-id="da3dd-112">`Boolean`, `Char` и `Date`.</span><span class="sxs-lookup"><span data-stu-id="da3dd-112">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="da3dd-113">Все структуры, даже если их члены являются ссылочными типами</span><span class="sxs-lookup"><span data-stu-id="da3dd-113">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="da3dd-114">Перечисления, так как их базовый тип всегда,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` или `ULong`</span><span class="sxs-lookup"><span data-stu-id="da3dd-114">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="da3dd-115">Каждая структура является типом значения, даже если она содержит члены ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="da3dd-115">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="da3dd-116">По этой причине типы значений, такие как `Char` и `Integer` , реализуются с помощью структур платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da3dd-116">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="da3dd-117">Тип значения можно объявить с помощью зарезервированного ключевого слова, например `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="da3dd-117">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="da3dd-118">`New`Для инициализации типа значения также можно использовать ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="da3dd-118">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="da3dd-119">Это особенно полезно, если тип имеет конструктор, принимающий параметры.</span><span class="sxs-lookup"><span data-stu-id="da3dd-119">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="da3dd-120">Примером этого является <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> конструктор, который создает новое `Decimal` значение из предоставляемых частей.</span><span class="sxs-lookup"><span data-stu-id="da3dd-120">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="da3dd-121">Ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="da3dd-121">Reference Types</span></span>  

 <span data-ttu-id="da3dd-122">*Ссылочный тип* хранит ссылку на свои данные.</span><span class="sxs-lookup"><span data-stu-id="da3dd-122">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="da3dd-123">К ссылочным типам относятся следующие:</span><span class="sxs-lookup"><span data-stu-id="da3dd-123">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="da3dd-124">Все массивы, даже если их элементы являются типами значений</span><span class="sxs-lookup"><span data-stu-id="da3dd-124">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="da3dd-125">Типы классов, такие как <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="da3dd-125">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="da3dd-126">Делегаты</span><span class="sxs-lookup"><span data-stu-id="da3dd-126">Delegates</span></span>  
  
 <span data-ttu-id="da3dd-127">Класс является *ссылочным типом*.</span><span class="sxs-lookup"><span data-stu-id="da3dd-127">A class is a *reference type*.</span></span> <span data-ttu-id="da3dd-128">Обратите внимание, что каждый массив является ссылочным типом, даже если его члены являются типами значений.</span><span class="sxs-lookup"><span data-stu-id="da3dd-128">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="da3dd-129">Поскольку каждый ссылочный тип представляет базовый класс платформа .NET Framework, при его инициализации необходимо использовать ключевое слово [New operator](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="da3dd-129">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="da3dd-130">Следующая инструкция инициализирует массив.</span><span class="sxs-lookup"><span data-stu-id="da3dd-130">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="da3dd-131">Элементы, не являющиеся типами</span><span class="sxs-lookup"><span data-stu-id="da3dd-131">Elements That Are Not Types</span></span>  

 <span data-ttu-id="da3dd-132">Следующие элементы программирования не являются типами, так как их нельзя указать в качестве типа данных для объявленного элемента:</span><span class="sxs-lookup"><span data-stu-id="da3dd-132">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="da3dd-133">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="da3dd-133">Namespaces</span></span>  
  
- <span data-ttu-id="da3dd-134">Модули</span><span class="sxs-lookup"><span data-stu-id="da3dd-134">Modules</span></span>  
  
- <span data-ttu-id="da3dd-135">События</span><span class="sxs-lookup"><span data-stu-id="da3dd-135">Events</span></span>  
  
- <span data-ttu-id="da3dd-136">Свойства и процедуры</span><span class="sxs-lookup"><span data-stu-id="da3dd-136">Properties and procedures</span></span>  
  
- <span data-ttu-id="da3dd-137">Переменные, константы и поля</span><span class="sxs-lookup"><span data-stu-id="da3dd-137">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="da3dd-138">Работа с типом данных Object</span><span class="sxs-lookup"><span data-stu-id="da3dd-138">Working with the Object Data Type</span></span>  

 <span data-ttu-id="da3dd-139">Переменной типа данных можно присвоить либо ссылочный тип, либо тип значения `Object` .</span><span class="sxs-lookup"><span data-stu-id="da3dd-139">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="da3dd-140">`Object`Переменная всегда хранит ссылку на данные, а не сами данные.</span><span class="sxs-lookup"><span data-stu-id="da3dd-140">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="da3dd-141">Однако при присвоении переменной типа значения `Object` она ведет себя так, как если бы она содержала свои собственные данные.</span><span class="sxs-lookup"><span data-stu-id="da3dd-141">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="da3dd-142">Дополнительные сведения см. в разделе [тип данных объекта](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="da3dd-142">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="da3dd-143">Определить, выступает ли переменная в `Object` качестве ссылочного типа или типа значения, можно, передав ее <xref:Microsoft.VisualBasic.Information.IsReference%2A> методу в <xref:Microsoft.VisualBasic.Information> классе <xref:Microsoft.VisualBasic?displayProperty=nameWithType> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="da3dd-143">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="da3dd-144"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Возвращает, `True` Если содержимое `Object` переменной представляет ссылочный тип.</span><span class="sxs-lookup"><span data-stu-id="da3dd-144"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3dd-145">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="da3dd-145">See also</span></span>

- [<span data-ttu-id="da3dd-146">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="da3dd-146">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="da3dd-147">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da3dd-147">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="da3dd-148">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="da3dd-148">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="da3dd-149">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="da3dd-149">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="da3dd-150">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="da3dd-150">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="da3dd-151">Типы данных</span><span class="sxs-lookup"><span data-stu-id="da3dd-151">Data Types</span></span>](index.md)
