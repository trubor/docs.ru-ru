---
description: 'Дополнительные сведения: семантика со значением NULL'
title: Семантика NULL
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 2326cd20a225f31693260aa038477f1f6090d02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695584"
---
# <a name="null-semantics"></a><span data-ttu-id="ccacd-103">Семантика NULL</span><span class="sxs-lookup"><span data-stu-id="ccacd-103">Null Semantics</span></span>

<span data-ttu-id="ccacd-104">В следующей таблице приведены ссылки на различные части [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] документации `null` , где `Nothing` обсуждаются проблемы (в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ccacd-104">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="ccacd-105">Раздел</span><span class="sxs-lookup"><span data-stu-id="ccacd-105">Topic</span></span>|<span data-ttu-id="ccacd-106">Описание</span><span class="sxs-lookup"><span data-stu-id="ccacd-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ccacd-107">Несоответствия типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="ccacd-107">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="ccacd-108">В подразделе "семантика со значением NULL" этого раздела описывается логическое значение SQL Boolean и два состояния среды CLR <xref:System.Boolean> , литерал `Nothing` (Visual Basic) и `null` (C#), а также другие аналогичные проблемы.</span><span class="sxs-lookup"><span data-stu-id="ccacd-108">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="ccacd-109">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="ccacd-109">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="ccacd-110">В подразделе "Семантика со значениями NULL" данного раздела описывается семантика сравнений со значением NULL в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccacd-110">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="ccacd-111">Методы System.String</span><span class="sxs-lookup"><span data-stu-id="ccacd-111">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="ccacd-112">В подразделе "Отличия от платформы .NET" данного раздела описывается, каким образом значение 0, возвращенное методом <xref:System.String.LastIndexOf%2A> , может означать, что строка равна значению NULL либо найденная позиция равна 0.</span><span class="sxs-lookup"><span data-stu-id="ccacd-112">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="ccacd-113">Вычисление суммы значений в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="ccacd-113">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="ccacd-114">Описывает, как <xref:System.Linq.Enumerable.Sum%2A> оператор вычисляет значение `null` ( `Nothing` в Visual Basic) вместо 0 для последовательности, содержащей только значения NULL или для пустой последовательности.</span><span class="sxs-lookup"><span data-stu-id="ccacd-114">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccacd-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ccacd-115">See also</span></span>

- [<span data-ttu-id="ccacd-116">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="ccacd-116">Data Types and Functions</span></span>](data-types-and-functions.md)
