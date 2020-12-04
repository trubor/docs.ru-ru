---
title: Критическое изменение. Статические файлы. Тип содержимого CSV изменен на соответствующий стандартам
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Static files. Тип содержимого CSV изменен на соответствующий стандартам
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760057"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="1ee98-103">Статические файлы. Тип содержимого CSV изменен на соответствующий стандартам</span><span class="sxs-lookup"><span data-stu-id="1ee98-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="1ee98-104">В ASP.NET Core 5.0 значение заголовка ответа `Content-Type` по умолчанию, используемое [ПО промежуточного слоя для статических файлов](/aspnet/core/fundamentals/static-files) для *CSV*-файлов, изменилось на соответствующее стандартам значение `text/csv`.</span><span class="sxs-lookup"><span data-stu-id="1ee98-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="1ee98-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="1ee98-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1ee98-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1ee98-106">Version introduced</span></span>

<span data-ttu-id="1ee98-107">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="1ee98-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="1ee98-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="1ee98-108">Old behavior</span></span>

<span data-ttu-id="1ee98-109">Использовалось значение `application/octet-stream` заголовка `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="1ee98-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="1ee98-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="1ee98-110">New behavior</span></span>

<span data-ttu-id="1ee98-111">Используется значение `text/csv` заголовка `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="1ee98-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="1ee98-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="1ee98-112">Reason for change</span></span>

<span data-ttu-id="1ee98-113">Соответствие стандарту [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1).</span><span class="sxs-lookup"><span data-stu-id="1ee98-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1ee98-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="1ee98-114">Recommended action</span></span>

<span data-ttu-id="1ee98-115">Если это изменение влияет на приложение, можно настроить сопоставление расширения файла с типом MIME.</span><span class="sxs-lookup"><span data-stu-id="1ee98-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="1ee98-116">Чтобы вернуться к типу MIME `application/octet-stream`, измените вызов метода <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> в `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="1ee98-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="1ee98-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="1ee98-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="1ee98-118">Дополнительные сведения о настройке сопоставления см. в разделе [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="1ee98-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1ee98-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="1ee98-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
