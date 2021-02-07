---
description: Дополнительные сведения:?. перетаскивани? ()-условные операторы null (Visual Basic)
title: Условные операторы null
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 558b8921d0da4089505dd1035cb6039af24a2802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665371"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="b96ff-104">?.</span><span class="sxs-lookup"><span data-stu-id="b96ff-104">?.</span></span> <span data-ttu-id="b96ff-105">перетаскивани? ()-условные операторы null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b96ff-105">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="b96ff-106">Проверяет значение левого операнда для NULL ( `Nothing` ) перед выполнением операции доступа к члену ( `?.` ) или индекса ( `?()` ); возвращает, `Nothing` если левый операнд принимает значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b96ff-106">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="b96ff-107">Обратите внимание, что в выражениях, которые обычно возвращают типы значений, условный оператор null возвращает <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="b96ff-107">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="b96ff-108">Эти операторы помогают писать меньше кода для проверки значений NULL, особенно при сортировке по структурам данных.</span><span class="sxs-lookup"><span data-stu-id="b96ff-108">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="b96ff-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="b96ff-109">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="b96ff-110">Для сравнения альтернативный код для первого из этих выражений без условного оператора null имеет значение:</span><span class="sxs-lookup"><span data-stu-id="b96ff-110">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="b96ff-111">Иногда необходимо выполнить действие над объектом, который может иметь значение null, на основе значения логического элемента в этом объекте (например, логическое свойство `IsAllowedFreeShipping` в следующем примере):</span><span class="sxs-lookup"><span data-stu-id="b96ff-111">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="b96ff-112">Вы можете сократить код и избежать ручной проверки значения NULL с помощью оператора Conditional, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b96ff-112">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="b96ff-113">Операторы с условием NULL предусматривают сокращенную обработку.</span><span class="sxs-lookup"><span data-stu-id="b96ff-113">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="b96ff-114">Если одна операция в цепочке операций доступа к условному элементу и операциям с индексами возвращает `Nothing` , оставшаяся часть выполнения цепочки останавливается.</span><span class="sxs-lookup"><span data-stu-id="b96ff-114">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="b96ff-115">В следующем примере `C(E)` не вычисляется, если `A` , `B` или `C` имеет значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b96ff-115">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E)
```

<span data-ttu-id="b96ff-116">Другим вариантом использования для доступа к членам с атрибутом null является вызов делегатов потокобезопасным способом с гораздо меньшим объемом кода.</span><span class="sxs-lookup"><span data-stu-id="b96ff-116">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="b96ff-117">В следующем примере определяются два типа: `NewsBroadcaster` и `NewsReceiver` .</span><span class="sxs-lookup"><span data-stu-id="b96ff-117">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="b96ff-118">Элементы новостей отправляются получателю `NewsBroadcaster.SendNews` делегатом.</span><span class="sxs-lookup"><span data-stu-id="b96ff-118">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String)

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="b96ff-119">Если в `SendNews` списке вызовов нет элементов, `SendNews` делегат создает исключение <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="b96ff-119">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="b96ff-120">Перед пустыми условными операторами, код, подобный приведенному ниже, гарантирует, что список вызовов делегата не был `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="b96ff-120">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="b96ff-121">Новый способ гораздо проще:</span><span class="sxs-lookup"><span data-stu-id="b96ff-121">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="b96ff-122">Новый способ является потокобезопасным, так как компилятор создает код для вычисления `SendNews` только один раз, запоминая результат во временной переменной.</span><span class="sxs-lookup"><span data-stu-id="b96ff-122">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="b96ff-123">Необходимо явно вызывать метод `Invoke`, так как отсутствует синтаксис `SendNews?(String)` для вызова делегатов с условием NULL.</span><span class="sxs-lookup"><span data-stu-id="b96ff-123">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b96ff-124">См. также</span><span class="sxs-lookup"><span data-stu-id="b96ff-124">See also</span></span>

- [<span data-ttu-id="b96ff-125">Операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b96ff-125">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="b96ff-126">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b96ff-126">Visual Basic Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b96ff-127">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b96ff-127">Visual Basic Language Reference</span></span>](../index.md)
