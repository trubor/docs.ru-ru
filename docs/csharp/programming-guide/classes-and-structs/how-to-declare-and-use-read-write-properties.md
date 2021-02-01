---
title: Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)
description: Узнайте, как использовать свойства чтения и записи в C#. Этот пример содержит два свойства, каждое из которых имеет методы доступа get и set, и поэтому свойства доступны для чтения и записи.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899026"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="06071-104">Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="06071-104">How to declare and use read write properties (C# Programming Guide)</span></span>

<span data-ttu-id="06071-105">Свойства имеют все преимущества открытых членов данных, но не связаны с рисками незащищенного, неконтролируемого и несанкционированного доступа к данным объекта.</span><span class="sxs-lookup"><span data-stu-id="06071-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="06071-106">Это достигается благодаря применению *методов доступа*, которые представляют собой особые методы для присвоения и извлечения значений базового члена данных.</span><span class="sxs-lookup"><span data-stu-id="06071-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="06071-107">Метод доступа [set](../../language-reference/keywords/set.md) присваивает значения членам данных, а метод доступа [get](../../language-reference/keywords/get.md) извлекает их.</span><span class="sxs-lookup"><span data-stu-id="06071-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="06071-108">Это можно продемонстрировать на примере класса `Person`, который содержит два свойства: `Name` (string) и `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="06071-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="06071-109">Для обоих свойств реализованы методы доступа `get` и `set`, благодаря чему они доступны и для чтения, и для записи.</span><span class="sxs-lookup"><span data-stu-id="06071-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06071-110">Пример</span><span class="sxs-lookup"><span data-stu-id="06071-110">Example</span></span>  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a><span data-ttu-id="06071-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="06071-111">Robust Programming</span></span>  

 <span data-ttu-id="06071-112">В предыдущем примере свойства `Name` и `Age` являются [открытыми](../../language-reference/keywords/public.md) и содержат одновременно методы доступа `get` и `set`.</span><span class="sxs-lookup"><span data-stu-id="06071-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="06071-113">Благодаря этому объект может считывать эти свойства и записывать их.</span><span class="sxs-lookup"><span data-stu-id="06071-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="06071-114">Тем не менее в некоторых случаях необходимо исключить один из методов доступа.</span><span class="sxs-lookup"><span data-stu-id="06071-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="06071-115">Например, свойство без метода доступа `set` будет доступно только для чтения:</span><span class="sxs-lookup"><span data-stu-id="06071-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 <span data-ttu-id="06071-116">Кроме того, можно сделать один метод доступа открытым, а другой оставить частным или защищенным.</span><span class="sxs-lookup"><span data-stu-id="06071-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="06071-117">Дополнительные сведения см. в разделе [Асимметричные методы доступа](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="06071-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="06071-118">После объявления свойств их можно использовать так же, как поля класса.</span><span class="sxs-lookup"><span data-stu-id="06071-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="06071-119">Это позволяет получить естественный синтаксис извлечения и установки значения свойства, как показано на примере следующих операторов:</span><span class="sxs-lookup"><span data-stu-id="06071-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 <span data-ttu-id="06071-120">Обратите внимание, что в методе `set` свойства доступна специальная переменная `value`.</span><span class="sxs-lookup"><span data-stu-id="06071-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="06071-121">Она содержит значение, заданное пользователем, например:</span><span class="sxs-lookup"><span data-stu-id="06071-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 <span data-ttu-id="06071-122">Обратите внимание на простой синтаксис приращения свойства `Age` для объекта `Person`:</span><span class="sxs-lookup"><span data-stu-id="06071-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 <span data-ttu-id="06071-123">Если для моделирования свойств использовать отдельные методы `set` и `get`, аналогичный код может иметь следующий вид:</span><span class="sxs-lookup"><span data-stu-id="06071-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="06071-124">В этом примере переопределяется метод `ToString`:</span><span class="sxs-lookup"><span data-stu-id="06071-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 <span data-ttu-id="06071-125">Обратите внимание, что метод `ToString` не используется в этой программе явно.</span><span class="sxs-lookup"><span data-stu-id="06071-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="06071-126">Он вызывается по умолчанию при вызове `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="06071-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06071-127">См. также</span><span class="sxs-lookup"><span data-stu-id="06071-127">See also</span></span>

- [<span data-ttu-id="06071-128">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="06071-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06071-129">Свойства</span><span class="sxs-lookup"><span data-stu-id="06071-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="06071-130">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="06071-130">Classes and Structs</span></span>](./index.md)
