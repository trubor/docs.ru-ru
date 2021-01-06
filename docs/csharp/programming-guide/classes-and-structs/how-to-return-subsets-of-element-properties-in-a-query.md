---
title: Практическое руководство. Возвращение поднаборов свойств элементов в запросе (руководство по программированию на C#)
description: Узнайте, как использовать анонимный тип в выражении запроса в C# для возврата некоторых свойств каждого исходного элемента.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 5784d6a288af374d357346e32535ebe9c1877bcc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512799"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="334c0-103">Практическое руководство. Возвращение поднаборов свойств элементов в запросе (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="334c0-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>

<span data-ttu-id="334c0-104">Используйте анонимный тип в выражении запроса, если выполняются оба следующих условия:</span><span class="sxs-lookup"><span data-stu-id="334c0-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="334c0-105">требуется возвращать только некоторые свойства каждого исходного элемента;</span><span class="sxs-lookup"><span data-stu-id="334c0-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="334c0-106">не требуется хранить результаты запроса за пределами области метода, в котором выполняется запрос.</span><span class="sxs-lookup"><span data-stu-id="334c0-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="334c0-107">Если требуется возвращать только одно свойство или поле из каждого исходного элемента, вы можете использовать оператор "точка" в предложении `select`.</span><span class="sxs-lookup"><span data-stu-id="334c0-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="334c0-108">Например, чтобы вернуть только `ID` для каждого элемента `student`, напишите предложение `select` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="334c0-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="334c0-109">Пример</span><span class="sxs-lookup"><span data-stu-id="334c0-109">Example</span></span>  

 <span data-ttu-id="334c0-110">В следующем примере показано, как использовать анонимный тип для возвращения только конкретного набора свойств каждого исходного элемента, соответствующего указанному условию.</span><span class="sxs-lookup"><span data-stu-id="334c0-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="334c0-111">Обратите внимание, что анонимный тип использует имена исходных элементов для соответствующих свойств, если имена не заданы.</span><span class="sxs-lookup"><span data-stu-id="334c0-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="334c0-112">Чтобы присваивать новые имена свойствам в анонимном типе, напишите инструкцию `select` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="334c0-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="334c0-113">Если вы попробуете сделать это в предыдущем примере, также необходимо изменить инструкцию `Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="334c0-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="334c0-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="334c0-114">Compiling the Code</span></span>  
  
<span data-ttu-id="334c0-115">Чтобы выполнить этот код, скопируйте и вставьте класс в консольное приложение C# с директивой `using` для пространства имен System.Linq.</span><span class="sxs-lookup"><span data-stu-id="334c0-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="334c0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="334c0-116">See also</span></span>

- [<span data-ttu-id="334c0-117">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="334c0-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="334c0-118">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="334c0-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="334c0-119">LINQ в C#</span><span class="sxs-lookup"><span data-stu-id="334c0-119">LINQ in C#</span></span>](../../linq/index.md)
