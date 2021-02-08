---
description: 'Дополнительные сведения: операторы Sequence'
title: Операторы последовательности
ms.date: 03/30/2017
ms.assetid: 4d332d32-3806-4451-b7af-25af269194ae
ms.openlocfilehash: cf118c7038bae922f94abcefe0d13f6af8078037
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803797"
---
# <a name="sequence-operators"></a><span data-ttu-id="cedde-103">Операторы последовательности</span><span class="sxs-lookup"><span data-stu-id="cedde-103">Sequence Operators</span></span>

<span data-ttu-id="cedde-104">В целом, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не поддерживает операторы последовательности, имеющие одно или несколько следующих свойств.</span><span class="sxs-lookup"><span data-stu-id="cedde-104">Generally speaking, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support sequence operators that have one or more of the following qualities:</span></span>  
  
- <span data-ttu-id="cedde-105">Принимают лямбда-выражение с параметром индекса.</span><span class="sxs-lookup"><span data-stu-id="cedde-105">Take a lambda with an index parameter.</span></span>  
  
- <span data-ttu-id="cedde-106">Основаны на свойствах последовательных строк, например <xref:System.Linq.Queryable.TakeWhile%2A>.</span><span class="sxs-lookup"><span data-stu-id="cedde-106">Rely on the properties of sequential rows, such as <xref:System.Linq.Queryable.TakeWhile%2A>.</span></span>  
  
- <span data-ttu-id="cedde-107">Основаны на произвольной реализации CLR, например <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="cedde-107">Rely on an arbitrary CLR implementation, such as <xref:System.Collections.Generic.IComparer%601>.</span></span>  
  
|<span data-ttu-id="cedde-108">Примеры неподдерживаемых операторов</span><span class="sxs-lookup"><span data-stu-id="cedde-108">Examples of Unsupported</span></span>|  
|-----------------------------|  
|<xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.TakeWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SkipWhile%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.GroupBy%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2CSystem.Collections.Generic.IEnumerable%7B%60%602%7D%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Reverse%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAt%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Range%28System.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Repeat%60%601%28%60%600%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Contains%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%600%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%600%2C%60%600%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.Aggregate%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2C%60%601%2CSystem.Func%7B%60%601%2C%60%600%2C%60%601%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%29?displayProperty=nameWithType>|  
|<xref:System.Linq.Enumerable.SequenceEqual%2A?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="cedde-109">Отличия от платформы .NET</span><span class="sxs-lookup"><span data-stu-id="cedde-109">Differences from .NET</span></span>  

 <span data-ttu-id="cedde-110">Все поддерживаемые операторы последовательности правильно работают в среде (CLR), за исключением `Average`.</span><span class="sxs-lookup"><span data-stu-id="cedde-110">All supported sequence operators work as expected in the common language runtime (CLR) except for `Average`.</span></span> <span data-ttu-id="cedde-111">`Average` возвращает значение, тип которого совпадает с усредняемым типом, тогда как в CLR оператор `Average` всегда возвращает тип <xref:System.Double> или <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="cedde-111">`Average` returns a value of the same type as the type being averaged, whereas in the CLR `Average` always returns either a <xref:System.Double> or a <xref:System.Decimal>.</span></span> <span data-ttu-id="cedde-112">Если исходный аргумент явно приведен к типу double / decimal или селектор приводится к типу double / decimal, в конечном коде SQL также будет присутствовать подобное преобразование и будет получен ожидаемый результат.</span><span class="sxs-lookup"><span data-stu-id="cedde-112">If the source argument is explicitly cast to double / decimal or the selector casts to double / decimal, the resulting SQL will also have such a conversion and the result will be as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedde-113">См. также</span><span class="sxs-lookup"><span data-stu-id="cedde-113">See also</span></span>

- [<span data-ttu-id="cedde-114">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="cedde-114">Data Types and Functions</span></span>](data-types-and-functions.md)
