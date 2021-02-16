---
description: 'Дополнительные сведения: Фильтрация данных (Visual Basic)'
title: Фильтрация данных
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 2e259209df35a89eb4730f79ffccfee7cb64b9e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428601"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="0a1f0-103">Фильтрация данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-103">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="0a1f0-104">Фильтрация — это операция по ограничению значений в результирующем наборе только элементами, соответствующими указанному условию.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-104">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="0a1f0-105">Это также называется выборкой.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-105">It is also known as selection.</span></span>

<span data-ttu-id="0a1f0-106">На следующем рисунке показаны результаты операции фильтрации последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-106">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="0a1f0-107">Предикат для операции фильтрации указывает, что символ должен быть "A".</span><span class="sxs-lookup"><span data-stu-id="0a1f0-107">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Схема, иллюстрирующая операцию фильтрации LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="0a1f0-109">Методы стандартных операторов запросов, которые выполняют выборку, перечислены в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-109">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="0a1f0-110">Методы</span><span class="sxs-lookup"><span data-stu-id="0a1f0-110">Methods</span></span>

|<span data-ttu-id="0a1f0-111">Имя метода</span><span class="sxs-lookup"><span data-stu-id="0a1f0-111">Method Name</span></span>|<span data-ttu-id="0a1f0-112">Описание</span><span class="sxs-lookup"><span data-stu-id="0a1f0-112">Description</span></span>|<span data-ttu-id="0a1f0-113">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a1f0-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0a1f0-114">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="0a1f0-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="0a1f0-115">OfType</span><span class="sxs-lookup"><span data-stu-id="0a1f0-115">OfType</span></span>|<span data-ttu-id="0a1f0-116">Выбирает значения в зависимости от возможности приведения их к указанному типу.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-116">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="0a1f0-117">Не применяется</span><span class="sxs-lookup"><span data-stu-id="0a1f0-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0a1f0-118">Where</span><span class="sxs-lookup"><span data-stu-id="0a1f0-118">Where</span></span>|<span data-ttu-id="0a1f0-119">Выбирает значения, основанные на функции предиката.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-119">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="0a1f0-120">Пример синтаксиса выражения запроса</span><span class="sxs-lookup"><span data-stu-id="0a1f0-120">Query Expression Syntax Example</span></span>

<span data-ttu-id="0a1f0-121">В следующем примере используется `Where` для фильтрации из массива строк, имеющих определенную длину.</span><span class="sxs-lookup"><span data-stu-id="0a1f0-121">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="0a1f0-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0a1f0-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0a1f0-123">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="0a1f0-124">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="0a1f0-124">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- <span data-ttu-id="0a1f0-125">[How to: Filter Query Results](../../language-features/linq/how-to-filter-query-results-by-using-linq.md) (Практическое руководство. Фильтрование результатов запроса)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-125">[How to: Filter Query Results](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)</span></span>
- [<span data-ttu-id="0a1f0-126">Как запрашивать метаданные сборки с помощью отражения (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-126">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="0a1f0-127">Как запросить файлы с указанным атрибутом или именем (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-127">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="0a1f0-128">Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1f0-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
