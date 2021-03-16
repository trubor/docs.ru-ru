---
title: 'Критическое изменение: переименованы параметры в типах, производных от Stream'
description: Сведения о критическом изменении в .NET 6.0 в основных библиотеках .NET, в результате которого изменились некоторые имена параметров в методах типов, производных от Stream.
ms.date: 03/04/2021
ms.openlocfilehash: c685fae6a7ed20ea47815d5f89a4e066c75e1178
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260014"
---
# <a name="some-parameters-in-stream-derived-types-are-renamed"></a><span data-ttu-id="b8cf2-103">Некоторые параметры в типах, производных от Stream, были переименованы</span><span class="sxs-lookup"><span data-stu-id="b8cf2-103">Some parameters in Stream-derived types are renamed</span></span>

<span data-ttu-id="b8cf2-104">В .NET 6 некоторые параметры методов типов, производных от <xref:System.IO.Stream?displayProperty=fullName>, были переименованы в соответствии с базовым классом.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-104">In .NET 6, some parameters of methods on types derived from <xref:System.IO.Stream?displayProperty=fullName> have been renamed to match the base class.</span></span>

## <a name="change-description"></a><span data-ttu-id="b8cf2-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="b8cf2-105">Change description</span></span>

<span data-ttu-id="b8cf2-106">В предыдущих версиях .NET некоторые типы, производные от <xref:System.IO.Stream>, переопределяют методы и используют имена параметров, отличные от имен базового типа.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-106">In previous .NET versions, several types derived from <xref:System.IO.Stream> override methods but use different parameter names than those used by the base type.</span></span> <span data-ttu-id="b8cf2-107">Например, параметр <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> типа "массив байтов" имеет имя `array`, а соответствующий аргумент в методе базового класса — `buffer`.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-107">For example, the byte array parameter of <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> is named `array` while the corresponding argument in the base class method is named `buffer`.</span></span>

<span data-ttu-id="b8cf2-108">В .NET 6 все типы, производные от <xref:System.IO.Stream?displayProperty=fullName>, которые имели несовпадающие имена параметров, были приведены в соответствие с базовым типом и используют те же имена параметров, что и базовый тип.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-108">In .NET 6, all types that derive from <xref:System.IO.Stream?displayProperty=fullName> that had mismatched parameter names have been brought into conformance with the base type by using the same parameter names as the base type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b8cf2-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="b8cf2-109">Version introduced</span></span>

<span data-ttu-id="b8cf2-110">6.0, предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="b8cf2-110">6.0 Preview 1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b8cf2-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="b8cf2-111">Reason for change</span></span>

<span data-ttu-id="b8cf2-112">Для этого изменения есть несколько причин.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-112">There are several reasons for the change:</span></span>

- <span data-ttu-id="b8cf2-113">Если передан недопустимый аргумент и было вызвано исключение, это исключение может содержать имя базового параметра или имя производного параметра в зависимости от реализации.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-113">If an invalid argument was passed and an exception was thrown, that exception might have contained the base parameter's name or the derived parameter's name, depending on the implementation.</span></span> <span data-ttu-id="b8cf2-114">Поскольку вызывающий объект мог использовать ссылку, типизированную как базовый тип или как производный тип, имя аргумента в исключении всегда должно быть правильным.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-114">Since the caller may have been using a reference typed as the base or as the derived type, it's impossible for the argument name in the exception to always be correct.</span></span>
- <span data-ttu-id="b8cf2-115">Наличие различных имен параметров затрудняет согласованность поведения во всех реализациях <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-115">Having different parameter names makes it harder to consistently validate behavior across all <xref:System.IO.Stream> implementations.</span></span>
- <span data-ttu-id="b8cf2-116">В .NET 6 добавлен открытый метод <xref:System.IO.Stream> для проверки аргументов, и эти методы должны иметь одинаковое имя параметра для использования.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-116">.NET 6 adds a public method on <xref:System.IO.Stream> for validating arguments, and that methods needs to have a consistent parameter name to use.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b8cf2-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="b8cf2-117">Recommended action</span></span>

<span data-ttu-id="b8cf2-118">Последствия этого критического изменения минимальны.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-118">The effect of this breaking change is minimal:</span></span>

- <span data-ttu-id="b8cf2-119">Для существующих двоичных файлов его влияние ограничено кодом, использующим отражение для проверки имен параметров в затронутых производных типах.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-119">For existing binaries, its impact is limited to code that uses reflection to examine the names of parameters on the affected derived types.</span></span>
- <span data-ttu-id="b8cf2-120">Для исходного кода влияние ограничено кодом, который использует именованные параметры для вызова методов для производного типа потока с использованием переменной, типизированной как производный тип.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-120">For source code, its impact is limited to code that uses named parameters to invoke methods on the derived stream type using a variable typed as that derived type.</span></span>

<span data-ttu-id="b8cf2-121">В обоих случаях рекомендуемым действием является согласованное использование имени параметра базового типа.</span><span class="sxs-lookup"><span data-stu-id="b8cf2-121">In both cases, the recommended action is to consistently use the base parameter name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b8cf2-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="b8cf2-122">Affected APIs</span></span>

- <xref:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`

-->
