---
description: 'Дополнительные сведения: тип данных Object'
title: Object Data Type
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: b1f169e4e590335a0879f5ecd9b68507a3fa2ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792158"
---
# <a name="object-data-type"></a><span data-ttu-id="a68fb-103">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="a68fb-103">Object Data Type</span></span>

<span data-ttu-id="a68fb-104">Содержит адреса, которые ссылаются на объекты.</span><span class="sxs-lookup"><span data-stu-id="a68fb-104">Holds addresses that refer to objects.</span></span> <span data-ttu-id="a68fb-105">В переменную можно назначить любой ссылочный тип (строка, массив, класс или интерфейс) `Object` .</span><span class="sxs-lookup"><span data-stu-id="a68fb-105">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="a68fb-106">`Object`Переменная также может ссылаться на данные любого типа значения (числовой,,,, `Boolean` `Char` `Date` Структура или перечисление).</span><span class="sxs-lookup"><span data-stu-id="a68fb-106">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="a68fb-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="a68fb-107">Remarks</span></span>

<span data-ttu-id="a68fb-108">`Object`Тип данных может указывать на данные любого типа данных, включая любой экземпляр объекта, распознаваемый приложением.</span><span class="sxs-lookup"><span data-stu-id="a68fb-108">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="a68fb-109">Используйте `Object` , если во время компиляции неизвестно, на какой тип данных может указывать переменная.</span><span class="sxs-lookup"><span data-stu-id="a68fb-109">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="a68fb-110">Значение по умолчанию `Object` — `Nothing` (пустая ссылка).</span><span class="sxs-lookup"><span data-stu-id="a68fb-110">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="a68fb-111">Типы данных</span><span class="sxs-lookup"><span data-stu-id="a68fb-111">Data Types</span></span>

<span data-ttu-id="a68fb-112">Переменной можно присвоить переменную, константу или выражение любого типа данных `Object` .</span><span class="sxs-lookup"><span data-stu-id="a68fb-112">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="a68fb-113">Чтобы определить тип данных `Object` , на который в настоящее время ссылается переменная, можно использовать <xref:System.Type.GetTypeCode%2A> метод <xref:System.Type?displayProperty=nameWithType> класса.</span><span class="sxs-lookup"><span data-stu-id="a68fb-113">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a68fb-114">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a68fb-114">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="a68fb-115">`Object`Тип данных является ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="a68fb-115">The `Object` data type is a reference type.</span></span> <span data-ttu-id="a68fb-116">Однако Visual Basic обрабатывает `Object` переменную как тип значения, если она ссылается на данные типа значения.</span><span class="sxs-lookup"><span data-stu-id="a68fb-116">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="a68fb-117">Память</span><span class="sxs-lookup"><span data-stu-id="a68fb-117">Storage</span></span>

<span data-ttu-id="a68fb-118">Любой тип данных, на который он ссылается, `Object` переменная не содержит само значение данных, а указатель на это значение.</span><span class="sxs-lookup"><span data-stu-id="a68fb-118">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="a68fb-119">Он всегда использует четыре байта в памяти компьютера, но не включает хранилище для данных, представляющих значение переменной.</span><span class="sxs-lookup"><span data-stu-id="a68fb-119">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="a68fb-120">Из-за кода, использующего указатель для нахождение данных, `Object` переменные, содержащие типы значений, немного медленнее, чем явно типизированные переменные.</span><span class="sxs-lookup"><span data-stu-id="a68fb-120">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="a68fb-121">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="a68fb-121">Programming Tips</span></span>

- <span data-ttu-id="a68fb-122">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="a68fb-122">**Interop Considerations.**</span></span> <span data-ttu-id="a68fb-123">Если вы взаимодействуете с компонентами, которые не написаны для платформа .NET Framework, например автоматизации или COM-объекты, помните, что типы указателей в других средах несовместимы с `Object` типом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a68fb-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="a68fb-124">**Производительность.**</span><span class="sxs-lookup"><span data-stu-id="a68fb-124">**Performance.**</span></span> <span data-ttu-id="a68fb-125">Переменная, объявляемая с `Object` типом, достаточно гибка, чтобы содержать ссылку на любой объект.</span><span class="sxs-lookup"><span data-stu-id="a68fb-125">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="a68fb-126">Однако при вызове метода или свойства для такой переменной всегда вызывается *позднее связывание* (во время выполнения).</span><span class="sxs-lookup"><span data-stu-id="a68fb-126">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="a68fb-127">Чтобы принудительно выполнить *раннее связывание* (во время компиляции) и повысить производительность, объявите переменную с конкретным именем класса или приведите ее к конкретному типу данных.</span><span class="sxs-lookup"><span data-stu-id="a68fb-127">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="a68fb-128">При объявлении объектной переменной попробуйте использовать конкретный тип класса, например <xref:System.OperatingSystem> , вместо обобщенного `Object` типа.</span><span class="sxs-lookup"><span data-stu-id="a68fb-128">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="a68fb-129">Также следует использовать наиболее конкретный класс, например <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control> , вместо, чтобы получить доступ к его свойствам и методам.</span><span class="sxs-lookup"><span data-stu-id="a68fb-129">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="a68fb-130">Для поиска доступных имен классов обычно можно использовать список **классы** в **обозревателе объектов** .</span><span class="sxs-lookup"><span data-stu-id="a68fb-130">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="a68fb-131">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="a68fb-131">**Widening.**</span></span> <span data-ttu-id="a68fb-132">Все типы данных и все ссылочные типы расширяются до `Object` типа данных.</span><span class="sxs-lookup"><span data-stu-id="a68fb-132">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="a68fb-133">Это означает, что можно преобразовать любой тип в `Object` без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="a68fb-133">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="a68fb-134">Однако при преобразовании между типами значений и `Object` Visual Basic выполняет операции, называемые *упаковкой* и *распаковкой*, что делает выполнение более медленным.</span><span class="sxs-lookup"><span data-stu-id="a68fb-134">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="a68fb-135">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="a68fb-135">**Type Characters.**</span></span> <span data-ttu-id="a68fb-136">`Object` не имеет символа типа литерала или символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="a68fb-136">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="a68fb-137">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="a68fb-137">**Framework Type.**</span></span> <span data-ttu-id="a68fb-138">Соответствующий тип в платформа .NET Framework — это <xref:System.Object?displayProperty=nameWithType> класс.</span><span class="sxs-lookup"><span data-stu-id="a68fb-138">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="a68fb-139">Пример</span><span class="sxs-lookup"><span data-stu-id="a68fb-139">Example</span></span>

<span data-ttu-id="a68fb-140">В следующем примере показана `Object` переменная, указывающая на экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="a68fb-140">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="a68fb-141">См. также</span><span class="sxs-lookup"><span data-stu-id="a68fb-141">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="a68fb-142">Типы данных</span><span class="sxs-lookup"><span data-stu-id="a68fb-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="a68fb-143">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="a68fb-143">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="a68fb-144">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="a68fb-144">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="a68fb-145">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="a68fb-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="a68fb-146">Практическое руководство. Определение наличия связи между двумя объектами</span><span class="sxs-lookup"><span data-stu-id="a68fb-146">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="a68fb-147">Практическое руководство. Определение идентичности двух объектов</span><span class="sxs-lookup"><span data-stu-id="a68fb-147">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
