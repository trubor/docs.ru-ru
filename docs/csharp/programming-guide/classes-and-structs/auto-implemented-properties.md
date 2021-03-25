---
title: Руководство по программированию на C#. Автоматически реализуемые свойства
description: Для автоматического реализуемого свойства в C# компилятор создает закрытое анонимное резервное поле, доступ к которому осуществляется только через методы доступа get и set свойства.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190285"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="9acb3-103">Автоматически реализуемые свойства (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="9acb3-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="9acb3-104">В C# 3.0 и более поздних версиях автоматически реализуемые свойства делают объявление свойств более лаконичным, когда в методах доступа к свойствам не требуется дополнительная логика.</span><span class="sxs-lookup"><span data-stu-id="9acb3-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="9acb3-105">Они также позволяют клиентскому коду создавать объекты.</span><span class="sxs-lookup"><span data-stu-id="9acb3-105">They also enable client code to create objects.</span></span> <span data-ttu-id="9acb3-106">При объявлении свойства, как показано в следующем примере, компилятор создает закрытое анонимное резервное поле, которое может быть доступно только через методы доступа `get` и `set` свойства.</span><span class="sxs-lookup"><span data-stu-id="9acb3-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span> <span data-ttu-id="9acb3-107">В C# 9 и более поздних версий методы доступа `init` также можно объявить как автоматически реализуемые свойства.</span><span class="sxs-lookup"><span data-stu-id="9acb3-107">In C# 9 and later, `init` accessors can also be declared as auto-implemented properties.</span></span>
  
## <a name="example"></a><span data-ttu-id="9acb3-108">Пример</span><span class="sxs-lookup"><span data-stu-id="9acb3-108">Example</span></span>

<span data-ttu-id="9acb3-109">В следующем примере показан простой класс, имеющий несколько автоматически реализуемых свойств.</span><span class="sxs-lookup"><span data-stu-id="9acb3-109">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="9acb3-110">В интерфейсах невозможно объявлять автоматически реализуемые свойства.</span><span class="sxs-lookup"><span data-stu-id="9acb3-110">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="9acb3-111">Автоматически реализуемые свойства объявляют резервное поле частного экземпляра, а интерфейсы могут не объявлять поля экземпляров.</span><span class="sxs-lookup"><span data-stu-id="9acb3-111">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="9acb3-112">Объявление свойства в интерфейсе без определения тела приводит к объявлению свойства с методами доступа, которые должны реализовываться каждым типом, реализующим этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9acb3-112">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="9acb3-113">В C# 6 и более поздних версиях можно инициализировать автоматически реализуемые свойства аналогично полям.</span><span class="sxs-lookup"><span data-stu-id="9acb3-113">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="9acb3-114">Класс, который показан в предыдущем примере, является изменяемым.</span><span class="sxs-lookup"><span data-stu-id="9acb3-114">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="9acb3-115">Клиентский код может изменить значения в объектах после создания.</span><span class="sxs-lookup"><span data-stu-id="9acb3-115">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="9acb3-116">В сложных классах, которые содержат значительные возможности (методы) и данные, часто необходимо иметь открытые свойства.</span><span class="sxs-lookup"><span data-stu-id="9acb3-116">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="9acb3-117">Но для небольших классов или структур, которые просто инкапсулируют набор значений (данных) без какого-либо поведения (или с минимальным поведением), следует использовать один из следующих параметров, чтобы сделать объекты неизменяемыми:</span><span class="sxs-lookup"><span data-stu-id="9acb3-117">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should use one of the following options for making the objects immutable:</span></span>

* <span data-ttu-id="9acb3-118">Объявите только метод доступа `get` (неизменяемое значение везде, за исключением конструктора).</span><span class="sxs-lookup"><span data-stu-id="9acb3-118">Declare only a `get` accessor (immutable everywhere except the constructor).</span></span>
* <span data-ttu-id="9acb3-119">Объявите методы доступа `get` и `init` (неизменяемое значение везде, за исключением создания объекта).</span><span class="sxs-lookup"><span data-stu-id="9acb3-119">Declare a `get` accessor and an `init` accessor (immutable everywhere except during object construction).</span></span>
* <span data-ttu-id="9acb3-120">Объявите метод доступа `set` с атрибутом [private](../../language-reference/keywords/private.md) (неизменяемое значение для потребителей).</span><span class="sxs-lookup"><span data-stu-id="9acb3-120">Declare the `set` accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers).</span></span>

<span data-ttu-id="9acb3-121">Дополнительные сведения см. в статье [Практическое руководство. Реализация облегченного класса с автоматически реализуемыми свойствами](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="9acb3-121">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9acb3-122">См. также</span><span class="sxs-lookup"><span data-stu-id="9acb3-122">See also</span></span>

- [<span data-ttu-id="9acb3-123">Свойства</span><span class="sxs-lookup"><span data-stu-id="9acb3-123">Properties</span></span>](./properties.md)
- [<span data-ttu-id="9acb3-124">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="9acb3-124">Modifiers</span></span>](../../language-reference/keywords/index.md)
