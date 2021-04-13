---
title: Критическое изменение. Статические файлы. Тип содержимого CSV изменен на соответствующий стандартам
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Static files. Тип содержимого CSV изменен на соответствующий стандартам
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3a7a1b2fc94f5cc956d85fc93ae72362e2e89b0e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497090"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="a0a95-103">Статические файлы. Тип содержимого CSV изменен на соответствующий стандартам</span><span class="sxs-lookup"><span data-stu-id="a0a95-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="a0a95-104">В ASP.NET Core 5.0 значение заголовка ответа `Content-Type` по умолчанию, используемое [ПО промежуточного слоя для статических файлов](/aspnet/core/fundamentals/static-files) для *CSV*-файлов, изменилось на соответствующее стандартам значение `text/csv`.</span><span class="sxs-lookup"><span data-stu-id="a0a95-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="a0a95-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="a0a95-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a0a95-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a0a95-106">Version introduced</span></span>

<span data-ttu-id="a0a95-107">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="a0a95-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a0a95-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a0a95-108">Old behavior</span></span>

<span data-ttu-id="a0a95-109">Использовалось значение `application/octet-stream` заголовка `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="a0a95-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a0a95-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a0a95-110">New behavior</span></span>

<span data-ttu-id="a0a95-111">Используется значение `text/csv` заголовка `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="a0a95-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a0a95-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a0a95-112">Reason for change</span></span>

<span data-ttu-id="a0a95-113">Соответствие стандарту [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1).</span><span class="sxs-lookup"><span data-stu-id="a0a95-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a0a95-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a0a95-114">Recommended action</span></span>

<span data-ttu-id="a0a95-115">Если это изменение влияет на приложение, можно настроить сопоставление расширения файла с типом MIME.</span><span class="sxs-lookup"><span data-stu-id="a0a95-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="a0a95-116">Чтобы вернуться к типу MIME `application/octet-stream`, измените вызов метода <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> в `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="a0a95-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="a0a95-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="a0a95-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="a0a95-118">Дополнительные сведения о настройке сопоставления см. в разделе [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="a0a95-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a0a95-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a0a95-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
