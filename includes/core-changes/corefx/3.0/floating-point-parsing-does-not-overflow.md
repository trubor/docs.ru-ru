---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032103"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="c6763-101">Операции синтаксического анализа с плавающей запятой больше не завершаются ошибкой и не вызывают исключение OverflowException</span><span class="sxs-lookup"><span data-stu-id="c6763-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="c6763-102">Методы синтаксического анализа с плавающей запятой больше не вызывают <xref:System.OverflowException> и не возвращают `false` при синтаксическом анализе строки, числовое значение которой находится вне диапазона типа с плавающей запятой <xref:System.Single> или <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="c6763-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c6763-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c6763-103">Change description</span></span>

<span data-ttu-id="c6763-104">В .NET Core 2.2 и более ранних версиях методы <xref:System.Double.Parse%2A?displayProperty=nameWithType> и <xref:System.Single.Parse%2A?displayProperty=nameWithType> вызывают <xref:System.OverflowException> для значений, которые выходят за пределы диапазона соответствующего типа.</span><span class="sxs-lookup"><span data-stu-id="c6763-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="c6763-105">Методы <xref:System.Double.TryParse%2A?displayProperty=nameWithType> и <xref:System.Single.TryParse%2A?displayProperty=nameWithType> возвращают `false` для строковых представлений числовых значений вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="c6763-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="c6763-106">Начиная с .NET Core 3.0 методы <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> и <xref:System.Single.TryParse%2A?displayProperty=nameWithType> больше не завершаются сбоем при анализе числовых строк вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="c6763-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="c6763-107">Вместо этого методы синтаксического анализа <xref:System.Double> возвращают <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> для значений, превышающих <xref:System.Double.MaxValue?displayProperty=nameWithType>, и <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> — для значений, которые меньше <xref:System.Double.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6763-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c6763-108">Подобным образом, методы синтаксического анализа <xref:System.Single> возвращают <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> для значений, превышающих <xref:System.Single.MaxValue?displayProperty=nameWithType>, и <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> — для значений, которые меньше <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6763-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c6763-109">Это изменение было внесено для улучшения соответствия требованиям IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="c6763-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c6763-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c6763-110">Version introduced</span></span>

<span data-ttu-id="c6763-111">3.0</span><span class="sxs-lookup"><span data-stu-id="c6763-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c6763-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c6763-112">Recommended action</span></span>

<span data-ttu-id="c6763-113">Это изменение может повлиять на код одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="c6763-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="c6763-114">Код зависит от обработчика <xref:System.OverflowException> для выполнения при переполнении.</span><span class="sxs-lookup"><span data-stu-id="c6763-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="c6763-115">В этом случае следует удалить оператор `catch` и поместить необходимый код в инструкцию `If`, которая проверяет, является ли <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> или <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>`true`.</span><span class="sxs-lookup"><span data-stu-id="c6763-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="c6763-116">В коде предполагается, что значения с плавающей запятой не являются `Infinity`.</span><span class="sxs-lookup"><span data-stu-id="c6763-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="c6763-117">В этом случае следует добавить необходимый код для проверки значений с плавающей запятой `PositiveInfinity` и `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="c6763-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="c6763-118">Категория</span><span class="sxs-lookup"><span data-stu-id="c6763-118">Category</span></span>

<span data-ttu-id="c6763-119">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="c6763-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6763-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c6763-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
