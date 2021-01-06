---
title: Руководство по программированию на C#. Инициализация словаря с помощью инициализатора набора
description: Узнайте, как в C# инициализировать словарь с помощью метода Add или инициализатора индекса. В этом примере показаны оба варианта.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: bcb9c5af215ff468812d08e93d37eecc40d745ea
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513085"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="2ff22-104">Практическое руководство. Инициализация словаря с помощью инициализатора коллекции (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="2ff22-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="2ff22-105"><xref:System.Collections.Generic.Dictionary%602> содержит коллекцию пар "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="2ff22-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="2ff22-106">Ее метод <xref:System.Collections.Generic.Dictionary%602.Add%2A> принимает два параметра: один для ключа, другой — для значения.</span><span class="sxs-lookup"><span data-stu-id="2ff22-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="2ff22-107">Для инициализации <xref:System.Collections.Generic.Dictionary%602> или любой коллекции, метод `Add` которой принимает несколько параметров, можно заключить каждый набор параметров в скобки, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="2ff22-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="2ff22-108">Другой вариант — использовать инициализатор индекса, как показано также в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="2ff22-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="2ff22-109">Пример</span><span class="sxs-lookup"><span data-stu-id="2ff22-109">Example</span></span>

<span data-ttu-id="2ff22-110">В следующем примере кода <xref:System.Collections.Generic.Dictionary%602> инициализируется экземплярами типа `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2ff22-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="2ff22-111">Первая инициализация использует метод `Add` с двумя аргументами.</span><span class="sxs-lookup"><span data-stu-id="2ff22-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="2ff22-112">Компилятор создает вызов метода `Add` для каждой пары ключа `int` и значения `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2ff22-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="2ff22-113">Вторая инициализация использует общедоступный метод индексатора чтения и записи класса `Dictionary`:</span><span class="sxs-lookup"><span data-stu-id="2ff22-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="2ff22-114">Обратите внимание на две пары фигурных скобок в каждом элементе коллекции в первом объявлении.</span><span class="sxs-lookup"><span data-stu-id="2ff22-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="2ff22-115">Во внутренней паре фигурных скобок заключен инициализатор объекта `StudentName`, а во внешней паре — инициализатор пары "ключ-значение", которая будет добавлена в коллекцию `students` <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="2ff22-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="2ff22-116">И наконец, весь инициализатор коллекции для словаря заключается в фигурные скобки.</span><span class="sxs-lookup"><span data-stu-id="2ff22-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="2ff22-117">Во второй инициализации левая часть оператора присваивания является ключом, а правая часть — значением, использующим инициализатор объекта для `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2ff22-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ff22-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2ff22-118">See also</span></span>

- [<span data-ttu-id="2ff22-119">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="2ff22-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2ff22-120">Инициализаторы объектов и коллекций</span><span class="sxs-lookup"><span data-stu-id="2ff22-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
