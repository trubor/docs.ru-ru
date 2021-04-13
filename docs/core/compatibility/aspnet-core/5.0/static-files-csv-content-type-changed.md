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
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Статические файлы. Тип содержимого CSV изменен на соответствующий стандартам

В ASP.NET Core 5.0 значение заголовка ответа `Content-Type` по умолчанию, используемое [ПО промежуточного слоя для статических файлов](/aspnet/core/fundamentals/static-files) для *CSV*-файлов, изменилось на соответствующее стандартам значение `text/csv`.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).

## <a name="version-introduced"></a>Представленная версия

5.0 Предварительная версия 1

## <a name="old-behavior"></a>Старое поведение

Использовалось значение `application/octet-stream` заголовка `Content-Type`.

## <a name="new-behavior"></a>Новое поведение

Используется значение `text/csv` заголовка `Content-Type`.

## <a name="reason-for-change"></a>Причина изменения

Соответствие стандарту [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1).

## <a name="recommended-action"></a>Рекомендованное действие

Если это изменение влияет на приложение, можно настроить сопоставление расширения файла с типом MIME. Чтобы вернуться к типу MIME `application/octet-stream`, измените вызов метода <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> в `Startup.Configure`. Пример:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Дополнительные сведения о настройке сопоставления см. в разделе [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
