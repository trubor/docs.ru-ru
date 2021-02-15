---
description: Дополнительные сведения о группировании данных (Visual Basic)
title: Группировка данных
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: fa6dbcc22c7d991d48775c3974cfc529840ef933
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469803"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="577c5-103">Группирование данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="577c5-103">Grouping Data (Visual Basic)</span></span>

<span data-ttu-id="577c5-104">Группированием называют операцию объединения данных в группы таким образом, чтобы у элементов в каждой группе был общий атрибут.</span><span class="sxs-lookup"><span data-stu-id="577c5-104">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="577c5-105">На следующем рисунке показаны результаты операции группирования последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="577c5-105">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="577c5-106">Ключ для каждой группы — это символ.</span><span class="sxs-lookup"><span data-stu-id="577c5-106">The key for each group is the character.</span></span>  
  
 ![Схема, показывающая операцию группирования LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="577c5-108">Далее перечислены методы стандартных операторов запроса, которые группируют элементы данных.</span><span class="sxs-lookup"><span data-stu-id="577c5-108">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="577c5-109">Методы</span><span class="sxs-lookup"><span data-stu-id="577c5-109">Methods</span></span>  
  
|<span data-ttu-id="577c5-110">Имя метода</span><span class="sxs-lookup"><span data-stu-id="577c5-110">Method Name</span></span>|<span data-ttu-id="577c5-111">Описание</span><span class="sxs-lookup"><span data-stu-id="577c5-111">Description</span></span>|<span data-ttu-id="577c5-112">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="577c5-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="577c5-113">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="577c5-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="577c5-114">GroupBy</span><span class="sxs-lookup"><span data-stu-id="577c5-114">GroupBy</span></span>|<span data-ttu-id="577c5-115">Группирует элементы с общим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="577c5-115">Groups elements that share a common attribute.</span></span> <span data-ttu-id="577c5-116">Каждая группа представлена объектом <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="577c5-116">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="577c5-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="577c5-117">ToLookup</span></span>|<span data-ttu-id="577c5-118">Вставляет элементы в <xref:System.Linq.Lookup%602> (словарь "один ко многим") в зависимости от функции выбора ключа.</span><span class="sxs-lookup"><span data-stu-id="577c5-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="577c5-119">Не применяется</span><span class="sxs-lookup"><span data-stu-id="577c5-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="577c5-120">Пример синтаксиса выражения запроса</span><span class="sxs-lookup"><span data-stu-id="577c5-120">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="577c5-121">В следующем примере кода предложение `Group By` используется для группирования целых чисел в списке на основании четности.</span><span class="sxs-lookup"><span data-stu-id="577c5-121">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="577c5-122">См. также</span><span class="sxs-lookup"><span data-stu-id="577c5-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="577c5-123">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="577c5-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="577c5-124">Предложение GROUP BY</span><span class="sxs-lookup"><span data-stu-id="577c5-124">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="577c5-125">Пошаговое руководство. Группировка файлов по расширению (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="577c5-125">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="577c5-126">Инструкции. Разбиение файла на несколько файлов с помощью групп (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="577c5-126">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
