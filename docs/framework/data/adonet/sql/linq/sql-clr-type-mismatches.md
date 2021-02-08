---
description: 'Дополнительные сведения: несоответствия типов SQL-CLR'
title: Несоответствия типов SQL-CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 9a2e1d360fc2a54f401572e46d92654f2b9284db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803728"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="357a6-103">Несоответствия типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="357a6-103">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="357a6-104">автоматизирует большую часть преобразований между объектной моделью и SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-104">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="357a6-105">Однако существуют ситуации, препятствующие точному преобразованию.</span><span class="sxs-lookup"><span data-stu-id="357a6-105">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="357a6-106">Эти основные несоответствия между типами среды CLR и типами баз данных SQL Server перечислены в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="357a6-106">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="357a6-107">Дополнительные сведения об особенностях сопоставления типов и переводе функций см. в статье [Сопоставление типов SQL-CLR](sql-clr-type-mapping.md) и [типы данных и функции](data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="357a6-107">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="357a6-108">Типы данных</span><span class="sxs-lookup"><span data-stu-id="357a6-108">Data Types</span></span>

<span data-ttu-id="357a6-109">Преобразование между CLR и SQL Server происходит в тот момент, когда запрос направляется в базу данных, а также когда результаты отправляются обратно в модель объектов.</span><span class="sxs-lookup"><span data-stu-id="357a6-109">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="357a6-110">Например, в следующем запросе Transact-SQL необходимы два преобразования значений:</span><span class="sxs-lookup"><span data-stu-id="357a6-110">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="357a6-111">Перед тем как запрос можно будет выполнить в SQL Server, должно быть указано значение параметра Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-111">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="357a6-112">В этом примере значение параметра `id` должно быть сначала преобразовано из типа CLR <xref:System.Int32?displayProperty=nameWithType> в тип SQL Server `INT`, чтобы база данных могла понять, каково это значение.</span><span class="sxs-lookup"><span data-stu-id="357a6-112">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="357a6-113">Затем, чтобы получить результат, столбец SQL Server `DateOfBirth` должен быть преобразован из типа SQL Server `DATETIME` в тип CLR <xref:System.DateTime?displayProperty=nameWithType>, чтобы его можно было использовать в модели объектов.</span><span class="sxs-lookup"><span data-stu-id="357a6-113">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="357a6-114">В этом примере типы модели объектов CLR естественным образом сопоставляются с типами базы данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-114">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="357a6-115">Но так происходит не всегда.</span><span class="sxs-lookup"><span data-stu-id="357a6-115">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="357a6-116">Отсутствие аналогов</span><span class="sxs-lookup"><span data-stu-id="357a6-116">Missing Counterparts</span></span>

<span data-ttu-id="357a6-117">Следующие типы не имеют соответствующих аналогов.</span><span class="sxs-lookup"><span data-stu-id="357a6-117">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="357a6-118">Несоответствия в пространстве имен CLR <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="357a6-118">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="357a6-119">**Целые числа без знака**.</span><span class="sxs-lookup"><span data-stu-id="357a6-119">**Unsigned integers**.</span></span> <span data-ttu-id="357a6-120">Эти типы обычно сопоставляются со своими более крупными аналогами со знаками, чтобы избежать переполнения.</span><span class="sxs-lookup"><span data-stu-id="357a6-120">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="357a6-121">На основе значения литералы могут быть преобразованы в числа со знаками такого же или меньшего размера.</span><span class="sxs-lookup"><span data-stu-id="357a6-121">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="357a6-122">**Boolean**.</span><span class="sxs-lookup"><span data-stu-id="357a6-122">**Boolean**.</span></span> <span data-ttu-id="357a6-123">Эти типы могут быть сопоставлены битам, большим числам или строкам.</span><span class="sxs-lookup"><span data-stu-id="357a6-123">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="357a6-124">Литерал может быть сопоставлен выражению, имеющему такое же значение (например, `1=1` в SQL для `True` в CLS).</span><span class="sxs-lookup"><span data-stu-id="357a6-124">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="357a6-125">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="357a6-125">**TimeSpan**.</span></span> <span data-ttu-id="357a6-126">Этот тип представляет различие между двумя значениями `DateTime` и не соответствует типу `timestamp` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-126">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="357a6-127">В некоторых случаях тип CLR <xref:System.TimeSpan?displayProperty=nameWithType> может также сопоставляться с типом `TIME` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-127">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="357a6-128">Назначение типа SQL Server `TIME` состоит только в том, чтобы представлять положительные значения менее суток.</span><span class="sxs-lookup"><span data-stu-id="357a6-128">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="357a6-129">Диапазон типа CLR <xref:System.TimeSpan> значительно шире.</span><span class="sxs-lookup"><span data-stu-id="357a6-129">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="357a6-130">В <xref:System.Data.SqlTypes> этом сравнении не учитываются типы платформа .NET Framework, относящиеся к SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-130">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="357a6-131">Несоответствия в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-131">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="357a6-132">**Символьные типы фиксированной длины**.</span><span class="sxs-lookup"><span data-stu-id="357a6-132">**Fixed length character types**.</span></span> <span data-ttu-id="357a6-133">Transact-SQL различает категории Юникода и не в Юникоде и имеет три различных типа в каждой категории: фиксированная длина `nchar` / `char` , переменная длина `nvarchar` / `varchar` и больший размер `ntext` / `text` .</span><span class="sxs-lookup"><span data-stu-id="357a6-133">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="357a6-134">Символьные типы фиксированной длины могут быть сопоставлены с типом CLR <xref:System.Char?displayProperty=nameWithType> для получения символов, однако они не совсем соответствуют такому же типу в преобразованиях и поведении.</span><span class="sxs-lookup"><span data-stu-id="357a6-134">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="357a6-135">**Бит**.</span><span class="sxs-lookup"><span data-stu-id="357a6-135">**Bit**.</span></span> <span data-ttu-id="357a6-136">Хотя домен `bit` имеет то же число значений, что и `Nullable<Boolean>`, это два различных типа.</span><span class="sxs-lookup"><span data-stu-id="357a6-136">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="357a6-137">`Bit`принимает значения `1` и `0` вместо `true` / `false` , и не может использоваться в качестве эквивалента логическим выражениям.</span><span class="sxs-lookup"><span data-stu-id="357a6-137">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="357a6-138">**Метка времени**.</span><span class="sxs-lookup"><span data-stu-id="357a6-138">**Timestamp**.</span></span> <span data-ttu-id="357a6-139">В отличие от типа CLR <xref:System.TimeSpan?displayProperty=nameWithType> тип SQL Server `TIMESTAMP` представляет созданное базой данных 8-разрядное число, уникальное для каждого обновления и не основанное на различии между значениями <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="357a6-139">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="357a6-140">**Money** и **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="357a6-140">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="357a6-141">Эти типы могут быть сопоставлены типу <xref:System.Decimal>, однако являются, по существу, разными типами и рассматриваются как таковые серверными функциями и преобразованиями.</span><span class="sxs-lookup"><span data-stu-id="357a6-141">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="357a6-142">Множественные сопоставления</span><span class="sxs-lookup"><span data-stu-id="357a6-142">Multiple Mappings</span></span>

<span data-ttu-id="357a6-143">Существует множество типов данных SQL Server, которые могут быть сопоставлены одному или нескольким типам данных CLR.</span><span class="sxs-lookup"><span data-stu-id="357a6-143">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="357a6-144">С другой стороны, имеется множество типов CLR, которые могут быть сопоставлены с одним или несколькими типами SQL Server.</span><span class="sxs-lookup"><span data-stu-id="357a6-144">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="357a6-145">Хотя сопоставление может быть поддержано средствами LINQ to SQL, это не значит, что два сопоставляемых типа, относящихся к CLR и SQL Server, полностью соответствуют друг другу по точности, диапазону и семантике.</span><span class="sxs-lookup"><span data-stu-id="357a6-145">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="357a6-146">Некоторые сопоставления могут включать различия по любому из упомянутых измерений или по всем измерениям.</span><span class="sxs-lookup"><span data-stu-id="357a6-146">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="357a6-147">Сведения о возможных различиях между различными возможностями сопоставления см. в статье [Сопоставление типов SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="357a6-147">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="357a6-148">Определяемые пользователем типы</span><span class="sxs-lookup"><span data-stu-id="357a6-148">User-defined Types</span></span>

<span data-ttu-id="357a6-149">Определяемые пользователем типы CLR разработаны, чтобы помочь устранить разрыв в системе типов.</span><span class="sxs-lookup"><span data-stu-id="357a6-149">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="357a6-150">Однако с их помощью выявляются интересные моменты, касающиеся управления версиями типа.</span><span class="sxs-lookup"><span data-stu-id="357a6-150">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="357a6-151">Изменение версии в клиенте может не иметь соответствующего изменения типа, хранящегося на сервере базы данных.</span><span class="sxs-lookup"><span data-stu-id="357a6-151">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="357a6-152">Любое такое изменение приводит к несоответствию другого типа, при котором может отсутствовать соответствие семантик типа и может стать очевидным пропуск версии.</span><span class="sxs-lookup"><span data-stu-id="357a6-152">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="357a6-153">Дальнейшие сложности возникают при оптимизации иерархий наследования в последующих версиях.</span><span class="sxs-lookup"><span data-stu-id="357a6-153">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="357a6-154">Семантики выражений</span><span class="sxs-lookup"><span data-stu-id="357a6-154">Expression Semantics</span></span>

<span data-ttu-id="357a6-155">Кроме парного несоответствия между типами CLR и базы данных, несоответствие осложняется и выражениями.</span><span class="sxs-lookup"><span data-stu-id="357a6-155">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="357a6-156">Необходимо учесть несоответствия в семантиках операторов, функций, в неявных преобразованиях типов, а также правила приоритета.</span><span class="sxs-lookup"><span data-stu-id="357a6-156">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="357a6-157">В следующих подразделах показано несоответствие между внешне схожими выражениями.</span><span class="sxs-lookup"><span data-stu-id="357a6-157">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="357a6-158">Можно создать выражения SQL, которые семантически эквивалентны заданному выражению CLR.</span><span class="sxs-lookup"><span data-stu-id="357a6-158">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="357a6-159">Однако не совсем ясно, являются ли семантические различия между внешне схожими выражениями очевидными для пользователя CLR и нужны ли изменения, необходимые для семантической равнозначности.</span><span class="sxs-lookup"><span data-stu-id="357a6-159">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="357a6-160">Это является особенно важным вопросом при вычислении выражения для набора значений.</span><span class="sxs-lookup"><span data-stu-id="357a6-160">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="357a6-161">Видимость различий может зависеть от данных и может быть труднораспознаваемой при кодировании и отладке.</span><span class="sxs-lookup"><span data-stu-id="357a6-161">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="357a6-162">Семантика NULL</span><span class="sxs-lookup"><span data-stu-id="357a6-162">Null Semantics</span></span>

<span data-ttu-id="357a6-163">Выражения SQL предоставляют логику с тремя значениями для логических выражений.</span><span class="sxs-lookup"><span data-stu-id="357a6-163">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="357a6-164">Возможен следующий результат: true, false или NULL.</span><span class="sxs-lookup"><span data-stu-id="357a6-164">The result can be true, false, or null.</span></span> <span data-ttu-id="357a6-165">С другой стороны, CLR указывает логический результат с двумя значениями для сравнений, использующих значения NULL.</span><span class="sxs-lookup"><span data-stu-id="357a6-165">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="357a6-166">Рассмотрим следующий код:</span><span class="sxs-lookup"><span data-stu-id="357a6-166">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="357a6-167">Схожая проблема возникает, исходя из предположения результатов с двумя значениями.</span><span class="sxs-lookup"><span data-stu-id="357a6-167">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="357a6-168">В предыдущем случае можно получить эквивалентное поведение при создании SQL, однако преобразование может неточно отразить ваше намерение.</span><span class="sxs-lookup"><span data-stu-id="357a6-168">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="357a6-169">не накладывает `null` `nothing` семантику сравнения C# или Visual Basic в SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-169">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="357a6-170">Операторы сравнения синтаксически преобразуются в эквивалентные команды SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-170">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="357a6-171">Семантики отражают семантики SQL в соответствии с параметрами сервера или подключения.</span><span class="sxs-lookup"><span data-stu-id="357a6-171">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="357a6-172">В заданных по умолчанию параметрах SQL два значения NULL считаются неравными (хотя, чтобы изменить семантики, можно изменить эти параметры).</span><span class="sxs-lookup"><span data-stu-id="357a6-172">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="357a6-173">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не учитывает параметры сервера в преобразовании запроса.</span><span class="sxs-lookup"><span data-stu-id="357a6-173">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="357a6-174">Сравнение с литералом `null` (`nothing`) преобразуется в соответствующую версию SQL (`is null` или `is not null`).</span><span class="sxs-lookup"><span data-stu-id="357a6-174">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="357a6-175">Значение `null` (`nothing`) в сортировке определено SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] не изменяет сортировку.</span><span class="sxs-lookup"><span data-stu-id="357a6-175">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="357a6-176">Преобразование и повышение типов</span><span class="sxs-lookup"><span data-stu-id="357a6-176">Type Conversion and Promotion</span></span>

<span data-ttu-id="357a6-177">SQL поддерживает широкий набор неявных преобразований в выражениях.</span><span class="sxs-lookup"><span data-stu-id="357a6-177">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="357a6-178">Для схожих выражений в C# потребуется явное приведение</span><span class="sxs-lookup"><span data-stu-id="357a6-178">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="357a6-179">Пример:</span><span class="sxs-lookup"><span data-stu-id="357a6-179">For example:</span></span>

- <span data-ttu-id="357a6-180">Типы `Nvarchar` и `DateTime` можно сравнить в SQL без явных приведений; C# требует явного преобразования.</span><span class="sxs-lookup"><span data-stu-id="357a6-180">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="357a6-181">`Decimal` неявно преобразуется в `DateTime` в SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-181">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="357a6-182">Язык C# не допускает неявных преобразований.</span><span class="sxs-lookup"><span data-stu-id="357a6-182">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="357a6-183">Аналогично: приоритеты типов в Transact-SQL отличаются от приоритетов типов C# из-за отличий в базовом наборе типов.</span><span class="sxs-lookup"><span data-stu-id="357a6-183">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="357a6-184">В действительности же явная связь поднабора/расширенного набора между списками приоритетов отсутствует.</span><span class="sxs-lookup"><span data-stu-id="357a6-184">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="357a6-185">Так, при сравнении типов `nvarchar` с `varchar` выполняется неявное преобразование выражения типа `varchar` в `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="357a6-185">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="357a6-186">Среда CLR не предоставляет эквивалентного повышения.</span><span class="sxs-lookup"><span data-stu-id="357a6-186">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="357a6-187">В простых случаях различия приводят к выражениям CLR с приведениями, которые избыточны для соответствующего выражения SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-187">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="357a6-188">Более важно то, что промежуточные результаты выражения SQL могут быть неявно повышены до типа, не имеющего точного аналога в языке C#, и наоборот.</span><span class="sxs-lookup"><span data-stu-id="357a6-188">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="357a6-189">В целом тестирование, отладка и проверка таких выражений является дополнительной значительной нагрузкой для пользователя.</span><span class="sxs-lookup"><span data-stu-id="357a6-189">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="357a6-190">Параметры сортировки</span><span class="sxs-lookup"><span data-stu-id="357a6-190">Collation</span></span>

<span data-ttu-id="357a6-191">Transact-SQL поддерживает явные параметры сортировки в качестве заметок к типам символьных строк.</span><span class="sxs-lookup"><span data-stu-id="357a6-191">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="357a6-192">Эти параметры сортировки определяют допустимость определенных сравнений.</span><span class="sxs-lookup"><span data-stu-id="357a6-192">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="357a6-193">Например, сравнение двух столбцов с различными явными параметры сортировки недопустимо.</span><span class="sxs-lookup"><span data-stu-id="357a6-193">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="357a6-194">Использование более простого строкового типа CTS не вызывает подобных ошибок.</span><span class="sxs-lookup"><span data-stu-id="357a6-194">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="357a6-195">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="357a6-195">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="357a6-196">По сути, вложенное предложение collation создает *ограниченный тип* , который не поддается замене.</span><span class="sxs-lookup"><span data-stu-id="357a6-196">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="357a6-197">Аналогично, в системах типов могут применяться самые разные порядки сортировки.</span><span class="sxs-lookup"><span data-stu-id="357a6-197">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="357a6-198">Это различие влияет на сортировку результатов.</span><span class="sxs-lookup"><span data-stu-id="357a6-198">This difference affects the sorting of results.</span></span> <span data-ttu-id="357a6-199">Идентификатор <xref:System.Guid> сортируется во всех 16 байтах в лексикографическом порядке (`IComparable()`), тогда как T-SQL сравнивает идентификаторы GUID в следующем порядке: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="357a6-199"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="357a6-200">Это упорядочивание выполнялось в SQL 7.0, где идентификаторы GUID, созданные NT-системой, имели именно такой октетный порядок.</span><span class="sxs-lookup"><span data-stu-id="357a6-200">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="357a6-201">Данный способ обеспечивал, что GUID, созданные на одном кластере узла, последовательно объединялись в соответствии с меткой времени.</span><span class="sxs-lookup"><span data-stu-id="357a6-201">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="357a6-202">Он также использовался для создания индексов (вставки становились добавлениями вместо случайных операций ввода-вывода).</span><span class="sxs-lookup"><span data-stu-id="357a6-202">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="357a6-203">Позднее в Windows порядок был зашифрован в связи с вопросами обеспечения конфиденциальности, однако SQL должен поддерживать совместимость.</span><span class="sxs-lookup"><span data-stu-id="357a6-203">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="357a6-204">Обходной путь заключается в использовании <xref:System.Data.SqlTypes.SqlGuid> вместо <xref:System.Guid> .</span><span class="sxs-lookup"><span data-stu-id="357a6-204">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="357a6-205">Отличия функции и оператора</span><span class="sxs-lookup"><span data-stu-id="357a6-205">Operator and Function Differences</span></span>

<span data-ttu-id="357a6-206">Операторы и функции, являющиеся по существу сравнимыми, имеют незначительно отличающиеся семантики.</span><span class="sxs-lookup"><span data-stu-id="357a6-206">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="357a6-207">Пример:</span><span class="sxs-lookup"><span data-stu-id="357a6-207">For example:</span></span>

- <span data-ttu-id="357a6-208">C# задает сокращенные семантики на основе лексического порядка операндов для логических операторов `&&` и `||`.</span><span class="sxs-lookup"><span data-stu-id="357a6-208">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="357a6-209">С другой стороны, SQL предназначен для запросов на основе наборов и поэтому предоставляет оптимизатору больше возможностей при выборе порядка выполнения.</span><span class="sxs-lookup"><span data-stu-id="357a6-209">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="357a6-210">Ниже приведены некоторые выводы.</span><span class="sxs-lookup"><span data-stu-id="357a6-210">Some of the implications include the following:</span></span>

  - <span data-ttu-id="357a6-211">Для семантического эквивалентного преобразования требуется " `CASE` ...</span><span class="sxs-lookup"><span data-stu-id="357a6-211">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="357a6-212">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="357a6-212">`WHEN` …</span></span> <span data-ttu-id="357a6-213">`THEN`"конструкция в SQL, чтобы избежать переупорядочения выполнения операнда.</span><span class="sxs-lookup"><span data-stu-id="357a6-213">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="357a6-214">Свободное преобразование к `AND` / `OR` операторам может привести к непредвиденным ошибкам, если выражение C# полагается на вычисление второго операнда на основе результата вычисления первого операнда.</span><span class="sxs-lookup"><span data-stu-id="357a6-214">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="357a6-215">`Round()` функция имеет другую семантику в платформа .NET Framework и в T-SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-215">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="357a6-216">Начальный индекс для строк в CLR равен нулю, а в SQL - 1.</span><span class="sxs-lookup"><span data-stu-id="357a6-216">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="357a6-217">Поэтому для каждой функции с индексом необходимо преобразование индекса.</span><span class="sxs-lookup"><span data-stu-id="357a6-217">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="357a6-218">В отличие от SQL, среда CLR поддерживает оператор остатка от деления (%) для чисел с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="357a6-218">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="357a6-219">Оператор `Like` эффективно использует автоматические перегрузки на основе неявных преобразований.</span><span class="sxs-lookup"><span data-stu-id="357a6-219">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="357a6-220">Несмотря на то, что оператор `Like` определен для действия в типах символьных строк, неявное преобразование из числовых типов или типов `DateTime` допускает использование нестроковых типов с `Like`.</span><span class="sxs-lookup"><span data-stu-id="357a6-220">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="357a6-221">В CTS сравнимые неявные преобразования не существуют.</span><span class="sxs-lookup"><span data-stu-id="357a6-221">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="357a6-222">Поэтому необходимы дополнительные перегрузки.</span><span class="sxs-lookup"><span data-stu-id="357a6-222">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="357a6-223">Это поведение оператора `Like` характерно только для языка C#; ключевое слово `Like` Visual Basic остается неизменным.</span><span class="sxs-lookup"><span data-stu-id="357a6-223">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="357a6-224">Переполнение всегда проверяется в SQL, но его необходимо явно указать в C# (не в Visual Basic), чтобы избежать врапараунд.</span><span class="sxs-lookup"><span data-stu-id="357a6-224">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="357a6-225">Даны столбцы целых чисел C1, C2 и C3, если C1+C2 хранится в C3 (Обновление T Set C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="357a6-225">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="357a6-226">SQL выполняет симметричное арифметическое округление, а платформа .NET Framework использует округление банка.</span><span class="sxs-lookup"><span data-stu-id="357a6-226">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="357a6-227">Дополнительные сведения см. в статье 196652 базы знаний.</span><span class="sxs-lookup"><span data-stu-id="357a6-227">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="357a6-228">По умолчанию для распространенных языков символьно-строковые сравнения в SQL не зависят от регистра.</span><span class="sxs-lookup"><span data-stu-id="357a6-228">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="357a6-229">В Visual Basic и C# сравнения выполняются с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="357a6-229">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="357a6-230">Например, `s == "Food"` ( `s = "Food"` в Visual Basic) и `s == "Food"` может давать разные результаты, если `s` имеет значение `food` .</span><span class="sxs-lookup"><span data-stu-id="357a6-230">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="357a6-231">Семантики операторов или функций, примененных к аргументам символьных типов фиксированной длины в SQL, значительно отличаются от семантик таких же операторов/функций, примененных к строке <xref:System.String?displayProperty=nameWithType> CLR.</span><span class="sxs-lookup"><span data-stu-id="357a6-231">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="357a6-232">Этот вопрос также можно рассмотреть как распространение проблемы отсутствующего аналога, которая обсуждается в разделе о типах.</span><span class="sxs-lookup"><span data-stu-id="357a6-232">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="357a6-233">Похожая проблема возникает при объединении строк.</span><span class="sxs-lookup"><span data-stu-id="357a6-233">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="357a6-234">В результате для выражений CLR могут потребоваться сложные преобразования, а для доступа к возможностям SQL могут быть необходимы дополнительные операторы и функции.</span><span class="sxs-lookup"><span data-stu-id="357a6-234">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="357a6-235">Приведение типа</span><span class="sxs-lookup"><span data-stu-id="357a6-235">Type Casting</span></span>

<span data-ttu-id="357a6-236">В C# и SQL пользователи могут переопределить заданные по умолчанию семантики выражений за счет использования явных приведений типов (`Cast` и `Convert`).</span><span class="sxs-lookup"><span data-stu-id="357a6-236">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="357a6-237">Однако предоставление этой возможности в рамках системы типа создает трудности.</span><span class="sxs-lookup"><span data-stu-id="357a6-237">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="357a6-238">Приведение SQL, предоставляющее необходимые семантики, не может быть просто преобразовано в соответствующее приведение C#.</span><span class="sxs-lookup"><span data-stu-id="357a6-238">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="357a6-239">С другой стороны, приведение C# нельзя напрямую преобразовать в эквивалентное приведение SQL в связи с несоответствием типов, отсутствием аналогов и наличием иерархий приоритетов различных типов.</span><span class="sxs-lookup"><span data-stu-id="357a6-239">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="357a6-240">Приходится идти на компромисс между несовпадением системы типа и потерей эффективности выражения.</span><span class="sxs-lookup"><span data-stu-id="357a6-240">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="357a6-241">В других случаях приведение типа может и не потребоваться в домене для проверки выражения, однако оно может быть необходимо для гарантии правильного применения к выражению нестандартного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="357a6-241">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="357a6-242">Проблемы с производительностью</span><span class="sxs-lookup"><span data-stu-id="357a6-242">Performance Issues</span></span>

<span data-ttu-id="357a6-243">Учет некоторых различий типов SQL Server-CLR может привести к снижению производительности при пересечении систем CLR и SQL Server типов.</span><span class="sxs-lookup"><span data-stu-id="357a6-243">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="357a6-244">Помимо этого, возможны следующие сценарии, приводящие к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="357a6-244">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="357a6-245">Принудительный порядок оценки логических операторов and и or.</span><span class="sxs-lookup"><span data-stu-id="357a6-245">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="357a6-246">Создание SQL-запроса для принудительного порядка оценки предикатов ограничивает возможности оптимизатора SQL.</span><span class="sxs-lookup"><span data-stu-id="357a6-246">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="357a6-247">Преобразования типов, представленные компилятором CLR или реализацией объектно-реляционного запроса, могут ограничить использование индекса.</span><span class="sxs-lookup"><span data-stu-id="357a6-247">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="357a6-248">Например,</span><span class="sxs-lookup"><span data-stu-id="357a6-248">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="357a6-249">Рассмотрим преобразование выражения `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="357a6-249">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="357a6-250">Наряду с семантическими различиями при переходах между системами типов SQL Server и CLR важно учитывать изменение производительности.</span><span class="sxs-lookup"><span data-stu-id="357a6-250">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="357a6-251">Для больших наборов данных подобные проблемы производительности могут определить, является ли приложение развертываемым.</span><span class="sxs-lookup"><span data-stu-id="357a6-251">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="357a6-252">См. также</span><span class="sxs-lookup"><span data-stu-id="357a6-252">See also</span></span>

- [<span data-ttu-id="357a6-253">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="357a6-253">Background Information</span></span>](background-information.md)
