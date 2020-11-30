---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032075"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="806bd-101">Для свойств UriBuilder больше не добавляются начальные символы</span><span class="sxs-lookup"><span data-stu-id="806bd-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="806bd-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> больше не добавляет начальный символ `#`, а <xref:System.UriBuilder.Query?displayProperty=nameWithType> больше не добавляет начальный символ `?`, если он уже существует.</span><span class="sxs-lookup"><span data-stu-id="806bd-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="806bd-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="806bd-103">Change description</span></span>

<span data-ttu-id="806bd-104">В .NET Framework свойства <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> и <xref:System.UriBuilder.Query?displayProperty=nameWithType> всегда добавляют к сохраненному значению в начале символ `#` или `?` соответственно.</span><span class="sxs-lookup"><span data-stu-id="806bd-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="806bd-105">Такое поведение может привести к появлению нескольких символов `#` или `?` в сохраненном значении, если строка уже содержит один из этих начальных символов.</span><span class="sxs-lookup"><span data-stu-id="806bd-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="806bd-106">Например, значение <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> может стать `##main`.</span><span class="sxs-lookup"><span data-stu-id="806bd-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="806bd-107">Начиная с .NET Core 1.0 эти свойства больше не добавляют начальные символы `#` или `?` к сохраненному значению, если в начале строки уже есть начальный символ.</span><span class="sxs-lookup"><span data-stu-id="806bd-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="806bd-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="806bd-108">Version introduced</span></span>

<span data-ttu-id="806bd-109">1.0</span><span class="sxs-lookup"><span data-stu-id="806bd-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="806bd-110">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="806bd-110">Recommended action</span></span>

<span data-ttu-id="806bd-111">При задании значений свойств больше не нужно явно удалять эти начальные символы.</span><span class="sxs-lookup"><span data-stu-id="806bd-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="806bd-112">Это особенно полезно при добавлении значений, так как больше не нужно каждый раз удалять начальные символы `#` или `?`.</span><span class="sxs-lookup"><span data-stu-id="806bd-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="806bd-113">Например, в следующем фрагменте кода показано различие в поведении между .NET Framework и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="806bd-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="806bd-114">В .NET Framework выходными данными будет `????one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="806bd-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="806bd-115">В .NET Core выходными данными будет `?one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="806bd-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="806bd-116">Категория</span><span class="sxs-lookup"><span data-stu-id="806bd-116">Category</span></span>

<span data-ttu-id="806bd-117">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="806bd-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="806bd-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="806bd-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
