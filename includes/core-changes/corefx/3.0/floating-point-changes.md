---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032094"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="aaf87-101">Изменено поведение форматирования и анализа при наличии плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="aaf87-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="aaf87-102">Поведение форматирования и анализа при наличии плавающей запятой (с помощью типов <xref:System.Double> и <xref:System.Single>) теперь совместимо со стандартами IEEE.</span><span class="sxs-lookup"><span data-stu-id="aaf87-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="aaf87-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="aaf87-103">Change description</span></span>

<span data-ttu-id="aaf87-104">В .NET Core 2.2 и более ранних версиях форматирование с помощью <xref:System.Double.ToString%2A?displayProperty=nameWithType> и <xref:System.Single.ToString%2A?displayProperty=nameWithType> и анализ с помощью <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> и <xref:System.Single.TryParse%2A?displayProperty=nameWithType> не были совместимы со стандартами IEEE.</span><span class="sxs-lookup"><span data-stu-id="aaf87-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="aaf87-105">В результате невозможно гарантировать, что значение будет соответствовать какой-либо поддерживаемой стандартной или пользовательской строке формата.</span><span class="sxs-lookup"><span data-stu-id="aaf87-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="aaf87-106">Для некоторых входных данных попытка проанализировать отформатированное значение может завершиться ошибкой, а для других — проанализированное значение не равно исходному.</span><span class="sxs-lookup"><span data-stu-id="aaf87-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="aaf87-107">Начиная с .NET Core 3.0, операции анализа и форматирования совместимы со стандартом IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="aaf87-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="aaf87-108">Благодаря этому поведение типов с плавающей запятой в .NET соответствует их поведению в языках, совместимых с IEEE, например C#.</span><span class="sxs-lookup"><span data-stu-id="aaf87-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="aaf87-109">Дополнительные сведения см. в записи блога [Улучшения в синтаксическом анализе и форматировании плавающей запятой в .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="aaf87-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aaf87-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="aaf87-110">Version introduced</span></span>

<span data-ttu-id="aaf87-111">3.0</span><span class="sxs-lookup"><span data-stu-id="aaf87-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aaf87-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="aaf87-112">Recommended action</span></span>

<span data-ttu-id="aaf87-113">В разделе "Потенциальное влияние на существующий код" записи блога [Улучшения в синтаксическом анализе и форматировании плавающей запятой в .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) предлагаются изменения, которые можно внести в код, если по сравнению с .NET Core 2.2 поведение приложения изменилось. Как правило, предполагается использование другой стандартной или пользовательской строки формата для обеспечения требуемого поведения.</span><span class="sxs-lookup"><span data-stu-id="aaf87-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="aaf87-114">Для некоторых результатов обходное решение может отсутствовать, если ранее они были неверны.</span><span class="sxs-lookup"><span data-stu-id="aaf87-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="aaf87-115">Категория</span><span class="sxs-lookup"><span data-stu-id="aaf87-115">Category</span></span>

<span data-ttu-id="aaf87-116">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="aaf87-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aaf87-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="aaf87-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
