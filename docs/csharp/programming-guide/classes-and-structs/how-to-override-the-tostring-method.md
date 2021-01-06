---
title: Практическое руководство. Переопределение метода ToString (руководство по программированию на C#)
description: Узнайте, как переопределить метод ToString в C#. Каждый класс или структура наследует класс Object и получает метод ToString, который возвращает строковое представление этого объекта.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 9573e6b97383d6f422c6a2802040fb9d6db709dd
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512747"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="77493-104">Практическое руководство. Переопределение метода ToString (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="77493-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="77493-105">Каждый класс или структура в языке C# неявно наследует класс <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="77493-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="77493-106">Поэтому каждый объект в языке C# получает метод <xref:System.Object.ToString%2A>, который возвращает строковое представление данного объекта.</span><span class="sxs-lookup"><span data-stu-id="77493-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="77493-107">Например, все переменные типа `int` имеют метод `ToString`, который позволяет им возвращать их содержимое в виде строки:</span><span class="sxs-lookup"><span data-stu-id="77493-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="77493-108">При создании пользовательского класса или структуры необходимо переопределить метод <xref:System.Object.ToString%2A>, чтобы передать информацию о типе клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="77493-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="77493-109">Дополнительные сведения об использовании строк форматирования и других типов пользовательского форматирования с методом `ToString` см. в разделе [Типы форматирования](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="77493-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77493-110">При принятии решения относительно того, какая информация должна будет предоставляться посредством этого метода, подумайте, будет ли создаваемый класс или структура когда-либо использоваться ненадежным кодом.</span><span class="sxs-lookup"><span data-stu-id="77493-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="77493-111">Постарайтесь не предоставлять информацию, которая может быть использована вредоносным кодом.</span><span class="sxs-lookup"><span data-stu-id="77493-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="77493-112">Чтобы переопределить метод `ToString` в классе или структуре, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="77493-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="77493-113">Объявите метод `ToString` со следующими модификаторами и типом возвращаемого значения:</span><span class="sxs-lookup"><span data-stu-id="77493-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="77493-114">Реализуйте этот метод таким образом, чтобы он возвращал строку.</span><span class="sxs-lookup"><span data-stu-id="77493-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="77493-115">В приведенном ниже примере возвращается не только имя класса, но и специфические данные для конкретного экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="77493-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="77493-116">Метод `ToString` можно проверить с помощью показанного ниже кода.</span><span class="sxs-lookup"><span data-stu-id="77493-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="77493-117">См. также</span><span class="sxs-lookup"><span data-stu-id="77493-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="77493-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="77493-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="77493-119">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="77493-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="77493-120">Строки</span><span class="sxs-lookup"><span data-stu-id="77493-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="77493-121">string</span><span class="sxs-lookup"><span data-stu-id="77493-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="77493-122">override</span><span class="sxs-lookup"><span data-stu-id="77493-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="77493-123">virtual</span><span class="sxs-lookup"><span data-stu-id="77493-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="77493-124">Типы форматирования</span><span class="sxs-lookup"><span data-stu-id="77493-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
