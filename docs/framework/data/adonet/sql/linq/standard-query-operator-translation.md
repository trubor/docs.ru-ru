---
description: Дополнительные сведения о переводе стандартных операторов запросов
title: Трансляция стандартных операторов запросов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: e7e45e8f27f1e7d3c572f00ea014b4edb288b2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681530"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="07659-103">Трансляция стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="07659-103">Standard Query Operator Translation</span></span>

<span data-ttu-id="07659-104">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует стандартные операторы запросов в команды SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="07659-105">Семантика выполнения преобразования SQL определяется обработчиком запросов базы данных.</span><span class="sxs-lookup"><span data-stu-id="07659-105">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="07659-106">Стандартные операторы запросов определяются для *последовательностей*.</span><span class="sxs-lookup"><span data-stu-id="07659-106">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="07659-107">Последовательность *упорядочена* и зависит от ссылочного удостоверения для каждого элемента последовательности.</span><span class="sxs-lookup"><span data-stu-id="07659-107">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="07659-108">Дополнительные сведения см. в разделе Общие сведения [о стандартных операторах запросов (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) или [Общие сведения о стандартных операторах запросов (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07659-108">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="07659-109">SQL работает преимущественно с *неупорядоченными наборами значений*.</span><span class="sxs-lookup"><span data-stu-id="07659-109">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="07659-110">Упорядочение, которое, как правило, задается явным образом, является операцией завершающей обработки, применяемой к окончательному результату запроса, а не к промежуточным результатам.</span><span class="sxs-lookup"><span data-stu-id="07659-110">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="07659-111">Идентификация определяется значениями.</span><span class="sxs-lookup"><span data-stu-id="07659-111">Identity is defined by values.</span></span> <span data-ttu-id="07659-112">По этой причине SQL-запросы обрабатываются с использованием множества наборов (*сумки*) вместо *наборов*.</span><span class="sxs-lookup"><span data-stu-id="07659-112">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="07659-113">Далее приводится описание различий между стандартными операторами запросов и их преобразованиями SQL для поставщика SQL Server для [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07659-113">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="07659-114">Поддержка операторов</span><span class="sxs-lookup"><span data-stu-id="07659-114">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="07659-115">Concat</span><span class="sxs-lookup"><span data-stu-id="07659-115">Concat</span></span>

<span data-ttu-id="07659-116">Метод <xref:System.Linq.Enumerable.Concat%2A> определен для упорядоченных множественных наборов, в которых порядок получателя и аргумента совпадают.</span><span class="sxs-lookup"><span data-stu-id="07659-116">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="07659-117">Метод <xref:System.Linq.Enumerable.Concat%2A> работает как предложение `UNION ALL` для мультинаборов с общим порядком.</span><span class="sxs-lookup"><span data-stu-id="07659-117"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="07659-118">Завершающее действие состоит в упорядочении в SQL перед возвратом результатов.</span><span class="sxs-lookup"><span data-stu-id="07659-118">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="07659-119">Метод <xref:System.Linq.Enumerable.Concat%2A> не сохраняет порядок своих аргументов.</span><span class="sxs-lookup"><span data-stu-id="07659-119"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="07659-120">Чтобы обеспечить соответствующее упорядочение, необходимо явно упорядочить результаты метода <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="07659-120">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="07659-121">Intersect, Except, Union</span><span class="sxs-lookup"><span data-stu-id="07659-121">Intersect, Except, Union</span></span>

<span data-ttu-id="07659-122">Методы <xref:System.Linq.Enumerable.Intersect%2A> и <xref:System.Linq.Enumerable.Except%2A> правильно определяются только для наборов.</span><span class="sxs-lookup"><span data-stu-id="07659-122">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="07659-123">Семантика для мультинаборов не определена.</span><span class="sxs-lookup"><span data-stu-id="07659-123">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="07659-124">Метод <xref:System.Linq.Enumerable.Union%2A> определен для мультинаборов как неупорядоченное объединение мультинаборов (в действительности, он возвращает результат, аналогичный предложению UNION ALL в SQL).</span><span class="sxs-lookup"><span data-stu-id="07659-124">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="07659-125">Take, Skip</span><span class="sxs-lookup"><span data-stu-id="07659-125">Take, Skip</span></span>

<span data-ttu-id="07659-126"><xref:System.Linq.Enumerable.Take%2A><xref:System.Linq.Enumerable.Skip%2A>методы и хорошо определяются только для *упорядоченных наборов*.</span><span class="sxs-lookup"><span data-stu-id="07659-126"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="07659-127">Семантика для неупорядоченных наборов или мультинаборов не определена.</span><span class="sxs-lookup"><span data-stu-id="07659-127">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="07659-128">На методы <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A> накладываются некоторые ограничения при их использовании в запросах для SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="07659-128"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="07659-129">Дополнительные сведения см. в записи "пропуск и получение исключений в SQL Server 2000" раздела [Устранение неполадок](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="07659-129">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="07659-130">Из-за ограничений по упорядочению в SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] пытается переместить порядок аргументов этих методов в результат метода.</span><span class="sxs-lookup"><span data-stu-id="07659-130">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="07659-131">Рассмотрим, например, следующий запрос [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="07659-131">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="07659-132">В созданных для этого кода командах SQL упорядочение перемещается в конец:</span><span class="sxs-lookup"><span data-stu-id="07659-132">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="07659-133">Становится очевидным, что при объединении методов <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A> все указанные операции упорядочения должны быть согласованными.</span><span class="sxs-lookup"><span data-stu-id="07659-133">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="07659-134">В противном случае результаты не определены.</span><span class="sxs-lookup"><span data-stu-id="07659-134">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="07659-135">Методы <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A> правильно определяются для неотрицательных постоянных интегральных аргументов, соответствующих спецификации стандартных операторов запросов.</span><span class="sxs-lookup"><span data-stu-id="07659-135">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="07659-136">Операторы без преобразования</span><span class="sxs-lookup"><span data-stu-id="07659-136">Operators with No Translation</span></span>

<span data-ttu-id="07659-137">Перечисленные ниже методы не преобразуются технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07659-137">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="07659-138">Причиной этого, чаще всего, является различие между неупорядоченными мультинаборами и последовательностями.</span><span class="sxs-lookup"><span data-stu-id="07659-138">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="07659-139">Операторы</span><span class="sxs-lookup"><span data-stu-id="07659-139">Operators</span></span>|<span data-ttu-id="07659-140">Правильно</span><span class="sxs-lookup"><span data-stu-id="07659-140">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="07659-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="07659-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="07659-142">SQL-запросы работают с мультинаборами и не работают с последовательностями.</span><span class="sxs-lookup"><span data-stu-id="07659-142">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="07659-143">Атрибут `ORDER BY` должен быть последним предложением, применяемым к статистической функции.</span><span class="sxs-lookup"><span data-stu-id="07659-143">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="07659-144">По этой причине преобразование общего назначения для этих двух методов отсутствует.</span><span class="sxs-lookup"><span data-stu-id="07659-144">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="07659-145">Преобразование этого метода возможно для упорядоченных наборов, однако в настоящее время он не преобразуется технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07659-145">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="07659-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="07659-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="07659-147">Преобразование этих методов возможно для упорядоченных наборов, однако в настоящее время они не преобразуются технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07659-147">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="07659-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="07659-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="07659-149">Запросы SQL работают с мультинаборами и не работают с индексируемыми последовательностями.</span><span class="sxs-lookup"><span data-stu-id="07659-149">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="07659-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (перегрузка с аргументом по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="07659-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="07659-151">В общем случае значение по умолчанию для произвольного кортежа указать невозможно.</span><span class="sxs-lookup"><span data-stu-id="07659-151">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="07659-152">В некоторых случаях для кортежей можно указать нулевые значения через внешние соединения.</span><span class="sxs-lookup"><span data-stu-id="07659-152">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="07659-153">Преобразование выражений</span><span class="sxs-lookup"><span data-stu-id="07659-153">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="07659-154">Семантика значений NULL</span><span class="sxs-lookup"><span data-stu-id="07659-154">Null semantics</span></span>

<span data-ttu-id="07659-155">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не накладывает семантику сравнения со значением NULL на команды SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-155">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="07659-156">Операторы сравнения синтаксически преобразуются в эквивалентные команды SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-156">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="07659-157">По этой причине семантика отражает семантику SQL в соответствии с параметрами сервера или подключения.</span><span class="sxs-lookup"><span data-stu-id="07659-157">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="07659-158">Например, в соответствии с заданными по умолчанию параметрами SQL Server два значения NULL считаются неравными, хотя можно изменить эти параметры, чтобы изменить семантику.</span><span class="sxs-lookup"><span data-stu-id="07659-158">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07659-159">не учитывает параметры сервера при преобразовании запросов.</span><span class="sxs-lookup"><span data-stu-id="07659-159">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="07659-160">Сравнение с литералом NULL преобразуется в соответствующую версию SQL (`is null` или `is not null`).</span><span class="sxs-lookup"><span data-stu-id="07659-160">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="07659-161">Значение `null` в параметрах сортировки определяется SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07659-161">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07659-162">не изменяет параметров сортировки.</span><span class="sxs-lookup"><span data-stu-id="07659-162">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="07659-163">Статистические выражения</span><span class="sxs-lookup"><span data-stu-id="07659-163">Aggregates</span></span>

<span data-ttu-id="07659-164">Агрегатный метод <xref:System.Linq.Enumerable.Sum%2A>, который входит в состав стандартных операторов запросов, выполняет сравнение с нулем для поиска пустой последовательности или последовательности, содержащей только значения NULL.</span><span class="sxs-lookup"><span data-stu-id="07659-164">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="07659-165">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] семантика SQL остается неизменной и <xref:System.Linq.Enumerable.Sum%2A> принимает значение `null` вместо нуля для пустой последовательности или для последовательности, содержащей только значения NULL.</span><span class="sxs-lookup"><span data-stu-id="07659-165">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="07659-166">Ограничения SQL для промежуточных результатов применяются к агрегатным выражениям в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07659-166">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="07659-167">Результат метода <xref:System.Linq.Enumerable.Sum%2A>, суммирующего 32-разрядные целые значения, вычисляется не на основе 64-разрядных результатов.</span><span class="sxs-lookup"><span data-stu-id="07659-167">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="07659-168">При преобразовании [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для метода <xref:System.Linq.Enumerable.Sum%2A> может произойти переполнение даже в том случае, если выполнение реализации стандартного оператора запроса для соответствующей последовательности в памяти не приводит к переполнению.</span><span class="sxs-lookup"><span data-stu-id="07659-168">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="07659-169">Аналогичным образом преобразование [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для метода <xref:System.Linq.Enumerable.Average%2A>, вычисляющего среднее значение целых чисел, возвращает тип `integer`, а не `double`.</span><span class="sxs-lookup"><span data-stu-id="07659-169">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="07659-170">Аргументы сущностей</span><span class="sxs-lookup"><span data-stu-id="07659-170">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07659-171">позволяет использовать типы сущностей в <xref:System.Linq.Enumerable.GroupBy%2A> <xref:System.Linq.Enumerable.OrderBy%2A> методах и.</span><span class="sxs-lookup"><span data-stu-id="07659-171">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="07659-172">При преобразовании этих операторов использование аргумента типа рассматривается как указание всех членов данного типа.</span><span class="sxs-lookup"><span data-stu-id="07659-172">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="07659-173">Ниже приведены примеры эквивалентного кода.</span><span class="sxs-lookup"><span data-stu-id="07659-173">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="07659-174">Сравниваемые и проверяемые на равенство аргументы</span><span class="sxs-lookup"><span data-stu-id="07659-174">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="07659-175">Ниже перечислены методы, в реализации которых требуется равенство аргументов.</span><span class="sxs-lookup"><span data-stu-id="07659-175">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07659-176">поддерживает равенство и сравнение для *неструктурированных* аргументов, но не для аргументов, которые являются или содержат последовательности.</span><span class="sxs-lookup"><span data-stu-id="07659-176">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="07659-177">Плоский аргумент представляет собой тип, который можно сопоставить со строкой SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-177">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="07659-178">Проекция одного или нескольких типов сущностей, которые можно статически определить как не содержащие последовательностей, считается плоским аргументом.</span><span class="sxs-lookup"><span data-stu-id="07659-178">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="07659-179">Ниже приведены примеры неструктурированных аргументов.</span><span class="sxs-lookup"><span data-stu-id="07659-179">The following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="07659-180">Ниже приведены примеры неструктурированных (иерархических) аргументов.</span><span class="sxs-lookup"><span data-stu-id="07659-180">The following are examples of non-flat (hierarchical) arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="07659-181">Преобразование функций Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07659-181">Visual Basic Function Translation</span></span>

<span data-ttu-id="07659-182">Ниже перечислены используемые компилятором Visual Basic вспомогательные функции, которые преобразуются в соответствующие операторы и функции SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-182">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="07659-183">Методы преобразования:</span><span class="sxs-lookup"><span data-stu-id="07659-183">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="07659-184">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="07659-184">ToBoolean</span></span>|<span data-ttu-id="07659-185">ToSByte</span><span class="sxs-lookup"><span data-stu-id="07659-185">ToSByte</span></span>|<span data-ttu-id="07659-186">ToByte</span><span class="sxs-lookup"><span data-stu-id="07659-186">ToByte</span></span>|<span data-ttu-id="07659-187">ToChar</span><span class="sxs-lookup"><span data-stu-id="07659-187">ToChar</span></span>|
|<span data-ttu-id="07659-188">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="07659-188">ToCharArrayRankOne</span></span>|<span data-ttu-id="07659-189">ToDate</span><span class="sxs-lookup"><span data-stu-id="07659-189">ToDate</span></span>|<span data-ttu-id="07659-190">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="07659-190">ToDecimal</span></span>|<span data-ttu-id="07659-191">ToDouble</span><span class="sxs-lookup"><span data-stu-id="07659-191">ToDouble</span></span>|
|<span data-ttu-id="07659-192">ToInteger</span><span class="sxs-lookup"><span data-stu-id="07659-192">ToInteger</span></span>|<span data-ttu-id="07659-193">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="07659-193">ToUInteger</span></span>|<span data-ttu-id="07659-194">ToLong</span><span class="sxs-lookup"><span data-stu-id="07659-194">ToLong</span></span>|<span data-ttu-id="07659-195">ToULong</span><span class="sxs-lookup"><span data-stu-id="07659-195">ToULong</span></span>|
|<span data-ttu-id="07659-196">ToShort</span><span class="sxs-lookup"><span data-stu-id="07659-196">ToShort</span></span>|<span data-ttu-id="07659-197">ToUShort</span><span class="sxs-lookup"><span data-stu-id="07659-197">ToUShort</span></span>|<span data-ttu-id="07659-198">ToSingle</span><span class="sxs-lookup"><span data-stu-id="07659-198">ToSingle</span></span>|<span data-ttu-id="07659-199">ToString</span><span class="sxs-lookup"><span data-stu-id="07659-199">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="07659-200">Поддержка наследования</span><span class="sxs-lookup"><span data-stu-id="07659-200">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="07659-201">Ограничения сопоставления при наследовании</span><span class="sxs-lookup"><span data-stu-id="07659-201">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="07659-202">Дополнительные сведения см. [в разделе Инструкции: Map иерархии наследования](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="07659-202">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="07659-203">Наследование в запросах</span><span class="sxs-lookup"><span data-stu-id="07659-203">Inheritance in Queries</span></span>

<span data-ttu-id="07659-204">В проекции поддерживаются только приведения типов C#.</span><span class="sxs-lookup"><span data-stu-id="07659-204">C# casts are supported only in projection.</span></span> <span data-ttu-id="07659-205">Приведения типов, используемые в других средах, пропускаются и не преобразуются.</span><span class="sxs-lookup"><span data-stu-id="07659-205">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="07659-206">Помимо преобразования имен функций SQL, SQL фактически выполняет действия, эквивалентные операциям класса <xref:System.Convert> среды CLR.</span><span class="sxs-lookup"><span data-stu-id="07659-206">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="07659-207">Это означает, что SQL может изменить значение одного типа на значение другого типа.</span><span class="sxs-lookup"><span data-stu-id="07659-207">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="07659-208">Здесь нет операции, эквивалентной приведению типов в среде CLR, поскольку отсутствует понятие повторной интерпретации тех же битов как битов другого типа.</span><span class="sxs-lookup"><span data-stu-id="07659-208">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="07659-209">По этой причине приведение типов C# работает только на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="07659-209">That is why a C# cast works only locally.</span></span> <span data-ttu-id="07659-210">Оно не используется для удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="07659-210">It is not remoted.</span></span>

<span data-ttu-id="07659-211">Операторы `is` и `as`, а также метод `GetType` не ограничены оператором `Select`.</span><span class="sxs-lookup"><span data-stu-id="07659-211">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="07659-212">Они могут использоваться также и в других операторах запроса.</span><span class="sxs-lookup"><span data-stu-id="07659-212">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="07659-213">Поддержка SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="07659-213">SQL Server 2008 Support</span></span>

<span data-ttu-id="07659-214">Начиная с версии .NET Framework 3.5 с пакетом обновления 1 (SP1), LINQ to SQL поддерживает сопоставление с новыми типами даты и времени, которые появились в SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="07659-214">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="07659-215">Однако операторы запросов LINQ to SQL, которые иногда используются при обработке значений, сопоставляемых с этими новыми типами, имеют определенные ограничения.</span><span class="sxs-lookup"><span data-stu-id="07659-215">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="07659-216">Неподдерживаемые операторы запросов</span><span class="sxs-lookup"><span data-stu-id="07659-216">Unsupported Query Operators</span></span>

<span data-ttu-id="07659-217">Следующие операторы запросов не поддерживаются для значений, сопоставляемых с новыми типами даты и времени SQL Server: `DATETIME2`, `DATE`, `TIME` и `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="07659-217">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="07659-218">Дополнительные сведения о сопоставлении с этими SQL Server типами даты и времени см. в разделе [Сопоставление типов SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="07659-218">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="07659-219">Поддержка SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="07659-219">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07659-220">не поддерживает следующие функции SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="07659-220">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="07659-221">Хранимые процедуры, написанные для среды SQL CLR.</span><span class="sxs-lookup"><span data-stu-id="07659-221">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="07659-222">Пользовательский тип.</span><span class="sxs-lookup"><span data-stu-id="07659-222">User-defined type.</span></span>

- <span data-ttu-id="07659-223">Функции запросов XML.</span><span class="sxs-lookup"><span data-stu-id="07659-223">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="07659-224">Поддержка SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="07659-224">SQL Server 2000 Support</span></span>

<span data-ttu-id="07659-225">Следующие ограничения SQL Server 2000 (по сравнению с Microsoft SQL Server 2005) влияют на [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] поддержку.</span><span class="sxs-lookup"><span data-stu-id="07659-225">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="07659-226">Операторы «Cross Apply» и «Outer Apply»</span><span class="sxs-lookup"><span data-stu-id="07659-226">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="07659-227">Эти операторы недоступны в SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="07659-227">These operators are not available in SQL Server 2000.</span></span> <span data-ttu-id="07659-228">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] пытается выполнить ряд операций перезаписи, чтобы заменить их соответствующими объединениями.</span><span class="sxs-lookup"><span data-stu-id="07659-228">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="07659-229">Операторы `Cross Apply` и `Outer Apply` создаются для перехода по отношениям.</span><span class="sxs-lookup"><span data-stu-id="07659-229">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="07659-230">Набор запросов, для которого такие операции перезаписи возможны, не является правильно определенным.</span><span class="sxs-lookup"><span data-stu-id="07659-230">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="07659-231">По этой причине минимальный набор запросов, поддерживаемых для SQL Server 2000, — это набор, не охватывающий навигацию по связям.</span><span class="sxs-lookup"><span data-stu-id="07659-231">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="07659-232">text / ntext</span><span class="sxs-lookup"><span data-stu-id="07659-232">text / ntext</span></span>

<span data-ttu-id="07659-233">Типы данных `text`  /  `ntext` не могут использоваться в определенных операциях запросов к `varchar(max)`  /  `nvarchar(max)` , которые поддерживаются Microsoft SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="07659-233">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="07659-234">Способов разрешения проблем, связанных с этим ограничением, не существует.</span><span class="sxs-lookup"><span data-stu-id="07659-234">No resolution is available for this limitation.</span></span> <span data-ttu-id="07659-235">В частности, метод `Distinct()` нельзя использовать для результата, который содержит члены, сопоставленные с `text` или `ntext`.</span><span class="sxs-lookup"><span data-stu-id="07659-235">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="07659-236">Поведение, инициируемое вложенными запросами</span><span class="sxs-lookup"><span data-stu-id="07659-236">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="07659-237">Связыватель SQL Server 2000 (до SP4) имеет некоторые особенности, активируемые вложенными запросами.</span><span class="sxs-lookup"><span data-stu-id="07659-237">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="07659-238">Набор запросов SQL, которые инициируют эти особенности, не является правильно определенным.</span><span class="sxs-lookup"><span data-stu-id="07659-238">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="07659-239">По этой причине нельзя определить набор [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] запросов, которые могут вызвать исключения SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07659-239">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="07659-240">Операторы «Skip» и «Take»</span><span class="sxs-lookup"><span data-stu-id="07659-240">Skip and Take Operators</span></span>

<span data-ttu-id="07659-241">На методы <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A> накладываются некоторые ограничения при их использовании в запросах для SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="07659-241"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="07659-242">Дополнительные сведения см. в записи "пропуск и получение исключений в SQL Server 2000" раздела [Устранение неполадок](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="07659-242">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="07659-243">Материализация объектов</span><span class="sxs-lookup"><span data-stu-id="07659-243">Object Materialization</span></span>

<span data-ttu-id="07659-244">Материализация создает объекты среды CLR из строк, возвращаемых одним или несколькими запросами SQL.</span><span class="sxs-lookup"><span data-stu-id="07659-244">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="07659-245">Следующие вызовы *выполняются локально* как часть материализации:</span><span class="sxs-lookup"><span data-stu-id="07659-245">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="07659-246">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="07659-246">Constructors</span></span>

  - <span data-ttu-id="07659-247">Методы `ToString` в проекциях</span><span class="sxs-lookup"><span data-stu-id="07659-247">`ToString` methods in projections</span></span>

  - <span data-ttu-id="07659-248">Приведения типов в проекциях</span><span class="sxs-lookup"><span data-stu-id="07659-248">Type casts in projections</span></span>

- <span data-ttu-id="07659-249">Методы, которые следуют за <xref:System.Linq.Enumerable.AsEnumerable%2A> методом, *выполняются локально*.</span><span class="sxs-lookup"><span data-stu-id="07659-249">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="07659-250">Этот метод не приводит к немедленному выполнению.</span><span class="sxs-lookup"><span data-stu-id="07659-250">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="07659-251">В качестве типа возвращаемых данных результата запроса или члена типа результата можно использовать значение `struct`.</span><span class="sxs-lookup"><span data-stu-id="07659-251">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="07659-252">Сущности должны быть классами.</span><span class="sxs-lookup"><span data-stu-id="07659-252">Entities are required to be classes.</span></span> <span data-ttu-id="07659-253">Анонимные типы материализуются как экземпляры классов, но в проекциях можно использовать структуры (не сущности).</span><span class="sxs-lookup"><span data-stu-id="07659-253">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="07659-254">Член типа возвращаемого значения может быть типом, реализующим интерфейс <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="07659-254">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="07659-255">Он материализуется как локальная коллекция.</span><span class="sxs-lookup"><span data-stu-id="07659-255">It is materialized as a local collection.</span></span>

- <span data-ttu-id="07659-256">Следующие методы вызывают *немедленное материализации* последовательности, к которой применяются методы.</span><span class="sxs-lookup"><span data-stu-id="07659-256">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="07659-257">См. также</span><span class="sxs-lookup"><span data-stu-id="07659-257">See also</span></span>

- [<span data-ttu-id="07659-258">Ссылки</span><span class="sxs-lookup"><span data-stu-id="07659-258">Reference</span></span>](reference.md)
- [<span data-ttu-id="07659-259">Возврат или пропуск элементов последовательности</span><span class="sxs-lookup"><span data-stu-id="07659-259">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="07659-260">Сцепление двух последовательностей</span><span class="sxs-lookup"><span data-stu-id="07659-260">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="07659-261">Возврат разности наборов между двумя последовательностями</span><span class="sxs-lookup"><span data-stu-id="07659-261">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="07659-262">Возврат пересечения наборов двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="07659-262">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="07659-263">Возврат объединения наборов двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="07659-263">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
