---
title: Критическое изменение. HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные
description: Сведения о критическом изменении в ASP.NET Core 5.0 — HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5837018def634b732b4f273f1a794267f4d17972
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498143"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` были помечены как устаревшие и изменены, чтобы быть производными от `Microsoft.AspNetCore.Http.BadHttpRequestException`. Серверы Kestrel и IIS по-прежнему выдают старые типы исключений для обеспечения обратной совместимости. Устаревшие типы будут удалены в будущем выпуске.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).

## <a name="version-introduced"></a>Представленная версия

5.0, предварительная версия 4

## <a name="old-behavior"></a>Старое поведение

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` являются производными от <xref:System.IO.IOException?displayProperty=nameWithType>.

## <a name="new-behavior"></a>Новое поведение

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` являются устаревшими. Типы являются производными от `Microsoft.AspNetCore.Http.BadHttpRequestException`, который является производным от `System.IO.IOException`.

## <a name="reason-for-change"></a>Причина изменения

Изменение было внесено в следующих целях:

* Консолидация повторяющихся типов.
* Унификация поведения различных серверных реализаций.

Теперь приложение может перехватывать базовое исключение `Microsoft.AspNetCore.Http.BadHttpRequestException` при использовании Kestrel или IIS.

## <a name="recommended-action"></a>Рекомендованное действие

Замените `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` на `Microsoft.AspNetCore.Http.BadHttpRequestException`.

## <a name="affected-apis"></a>Затронутые API

- [Microsoft.AspNetCore.Server.IIS.BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
