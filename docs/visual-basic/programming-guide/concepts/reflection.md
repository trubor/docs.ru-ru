---
description: 'Дополнительные сведения: отражение (Visual Basic)'
title: Отражение
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 532087f2ac32242b473d4524a6026519951d96d2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486814"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="2bbd2-103">Reflection (Visual Basic) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="2bbd2-103">Reflection (Visual Basic)</span></span>

<span data-ttu-id="2bbd2-104">Механизм отражения позволяет получать объекты (типа <xref:System.Type>), которые описывают сборки, модули и типы.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-104">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="2bbd2-105">Отражение можно использовать для динамического создания экземпляра типа, привязки типа к существующему объекту, а также получения типа из существующего объекта и вызова его методов или доступа к его полям и свойствам.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-105">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="2bbd2-106">Если в коде используются атрибуты, отражение обеспечивает доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-106">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="2bbd2-107">Дополнительные сведения см. в разделе [Атрибуты](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd2-107">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="2bbd2-108">Вот простой пример отражения, в котором для получения типа переменной используется статический метод `GetType`, наследуемый всеми типами от базового класса `Object`.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-108">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="2bbd2-109">Результат.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-109">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="2bbd2-110">В этом примере отражение используется для получения полного имени загруженной сборки.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="2bbd2-111">Результат.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-111">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="2bbd2-112">Общие сведения об отражении</span><span class="sxs-lookup"><span data-stu-id="2bbd2-112">Reflection Overview</span></span>  

 <span data-ttu-id="2bbd2-113">Отражение удобно использовать в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="2bbd2-113">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="2bbd2-114">При необходимости доступа к атрибутам в метаданных программы.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-114">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="2bbd2-115">Дополнительные сведения см. в разделе [Извлечение информации, сохраненной в атрибуте](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd2-115">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="2bbd2-116">Для проверки и создания экземпляров типов в сборке.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-116">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="2bbd2-117">Для создания типов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-117">For building new types at runtime.</span></span> <span data-ttu-id="2bbd2-118">Используйте классы в <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-118">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="2bbd2-119">Для выполнения позднего связывания, которое обеспечивает доступ к методам в типах, созданных во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2bbd2-119">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="2bbd2-120">См. раздел [Динамическая загрузка и использование типов](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd2-120">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2bbd2-121">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="2bbd2-121">Related Sections</span></span>  

 <span data-ttu-id="2bbd2-122">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="2bbd2-122">For more information:</span></span>  
  
- [<span data-ttu-id="2bbd2-123">Отражение</span><span class="sxs-lookup"><span data-stu-id="2bbd2-123">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="2bbd2-124">Просмотр сведений о типах</span><span class="sxs-lookup"><span data-stu-id="2bbd2-124">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="2bbd2-125">Отражение и универсальные типы</span><span class="sxs-lookup"><span data-stu-id="2bbd2-125">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="2bbd2-126">Извлечение информации, сохраненной в атрибуте</span><span class="sxs-lookup"><span data-stu-id="2bbd2-126">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="2bbd2-127">См. также</span><span class="sxs-lookup"><span data-stu-id="2bbd2-127">See also</span></span>

- [<span data-ttu-id="2bbd2-128">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bbd2-128">Visual Basic Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2bbd2-129">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="2bbd2-129">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
