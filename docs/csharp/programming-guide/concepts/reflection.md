---
title: Отражение (C#)
description: Механизм отражения позволяет получать объекты, которые описывают сборки, модули и типы в C#. Если в коде используются атрибуты, отражение обеспечивает доступ к ним.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 91d6d9bbd54199f3468f867d8804596f4a7546d9
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427065"
---
# <a name="reflection-c"></a><span data-ttu-id="ce8c5-104">Отражение (C#)</span><span class="sxs-lookup"><span data-stu-id="ce8c5-104">Reflection (C#)</span></span>

<span data-ttu-id="ce8c5-105">Механизм отражения позволяет получать объекты (типа <xref:System.Type>), которые описывают сборки, модули и типы.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="ce8c5-106">Отражение можно использовать для динамического создания экземпляра типа, привязки типа к существующему объекту, а также получения типа из существующего объекта и вызова его методов или доступа к его полям и свойствам.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="ce8c5-107">Если в коде используются атрибуты, отражение обеспечивает доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="ce8c5-108">Дополнительные сведения см. в разделе [Атрибуты](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce8c5-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="ce8c5-109">Вот простой пример отражения, в котором для получения типа переменной используется метод <xref:System.Object.GetType>, наследуемый всеми типами от базового класса `Object`:</span><span class="sxs-lookup"><span data-stu-id="ce8c5-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="ce8c5-110">Убедитесь, что вы добавили `using System;` и `using System.Reflection;` в верхней части файла *.cs*.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="ce8c5-111">Выходные данные: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="ce8c5-112">В этом примере отражение используется для получения полного имени загруженной сборки.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="ce8c5-113">Выходные данные: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="ce8c5-114">Ключевые слова C# `protected` и `internal` не имеют никакого значения в промежуточном языке и не используются в интерфейсах API отражения.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-114">The C# keywords `protected` and `internal` have no meaning in Intermediate Language (IL) and are not used in the reflection APIs.</span></span> <span data-ttu-id="ce8c5-115">Соответствующими терминами в промежуточном языке являются *Family* и *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="ce8c5-116">Для идентификации метода `internal` с помощью отражения используйте свойство <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="ce8c5-117">Для идентификации метода `protected internal` используйте <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="ce8c5-118">Общие сведения об отражении</span><span class="sxs-lookup"><span data-stu-id="ce8c5-118">Reflection overview</span></span>

<span data-ttu-id="ce8c5-119">Отражение удобно использовать в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="ce8c5-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="ce8c5-120">При необходимости доступа к атрибутам в метаданных программы.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="ce8c5-121">Дополнительные сведения см. в разделе [Извлечение информации, сохраненной в атрибуте](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ce8c5-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="ce8c5-122">Для проверки и создания экземпляров типов в сборке.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="ce8c5-123">Для создания типов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-123">For building new types at runtime.</span></span> <span data-ttu-id="ce8c5-124">Используйте классы в <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="ce8c5-125">Для выполнения позднего связывания, которое обеспечивает доступ к методам в типах, созданных во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="ce8c5-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="ce8c5-126">См. раздел [Динамическая загрузка и использование типов](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="ce8c5-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="ce8c5-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="ce8c5-127">Related sections</span></span>

<span data-ttu-id="ce8c5-128">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="ce8c5-128">For more information:</span></span>

- [<span data-ttu-id="ce8c5-129">Отражение</span><span class="sxs-lookup"><span data-stu-id="ce8c5-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="ce8c5-130">Просмотр сведений о типах</span><span class="sxs-lookup"><span data-stu-id="ce8c5-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="ce8c5-131">Отражение и универсальные типы</span><span class="sxs-lookup"><span data-stu-id="ce8c5-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="ce8c5-132">Извлечение информации, сохраненной в атрибуте</span><span class="sxs-lookup"><span data-stu-id="ce8c5-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="ce8c5-133">См. также</span><span class="sxs-lookup"><span data-stu-id="ce8c5-133">See also</span></span>

- [<span data-ttu-id="ce8c5-134">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ce8c5-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce8c5-135">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="ce8c5-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
