---
title: Критическое изменение. Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
description: Сведения о критическом изменении в ASP.NET Core 5.0 — расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 82ee5129d6422d0a5ea4a0f14632a42e779f6ded
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497740"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet

При переносе некоторых пакетов NuGet `Microsoft.Extensions.*` из репозитория [dotnet/extensions](https://github.com/dotnet/extensions) в [dotnet/runtime](https://github.com/dotnet/runtime), как описано на странице [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), изменения в пакетах применяются к некоторым перенесенным пакетам. Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).

## <a name="version-introduced"></a>Представленная версия

5.0, предварительная версия 4

## <a name="old-behavior"></a>Старое поведение

Некоторые пакеты `Microsoft.Extensions.*` включают ссылки на пакеты для API, использовавшиеся приложением.

## <a name="new-behavior"></a>Новое поведение

Приложению может потребоваться добавить зависимости пакета `Microsoft.Extensions.*`.

## <a name="reason-for-change"></a>Причина изменения

Политики упаковки были обновлены для согласованности с репозиторием *dotnet/runtime*. В новой политике неиспользуемые ссылки на пакеты удаляются из файлов *NUPKG* во время упаковки.

## <a name="recommended-action"></a>Рекомендованное действие

Пользователи затронутых пакетов должны добавить прямую зависимость от удаленной зависимости пакета в своем проекте, если используются API из удаленной зависимости пакета. В следующей таблице перечислены затронутые пакеты и соответствующие изменения.

|Имя пакета|Описание изменений|
|------------|------------------|
|[Microsoft.Extensions.Configuration.Binder](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Удалена ссылка на `Microsoft.Extensions.Configuration`|
|[Microsoft.Extensions.Configuration.Json](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Удалена ссылка на `System.Threading.Tasks.Extensions`|
|[Microsoft.Extensions.Hosting.Abstractions](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Удалена ссылка на `Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Удалена ссылка на `Microsoft.Extensions.Configuration.Binder`|
|[Microsoft.Extensions.Logging.Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Удалена ссылка на `Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft.Extensions.Logging.EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |Удалена ссылка на `System.Diagnostics.EventLog` для моникера целевой платформы .NET Framework 4.6.1|
|[Microsoft.Extensions.Logging.EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Удалена ссылка на `System.Threading.Tasks.Extensions`|
|[Microsoft.Extensions.Options](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Удалена ссылка на `System.ComponentModel.Annotations`|

Например, ссылка на пакет `Microsoft.Extensions.Configuration` была удалена из `Microsoft.Extensions.Configuration.Binder`. В пакете не использовался API из зависимости. Пользователи `Microsoft.Extensions.Configuration.Binder`, которые зависят от API из `Microsoft.Extensions.Configuration`, должны добавить прямую ссылку на него в своем проекте.

## <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
