---
title: Критическое изменение. IIS. Строки запросов ПО промежуточного слоя UrlRewrite сохраняются
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 — IIS: Строки запросов ПО промежуточного слоя UrlRewrite сохраняются'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3439844f04c89059a027c1264401efc46cd0d57e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497670"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS. Строки запросов ПО промежуточного слоя UrlRewrite сохраняются

Ошибки в ПО промежуточного слоя IIS UrlRewrite не позволили сохранить строку запроса в правиле перезаписи. Эта ошибка исправлена, чтобы обеспечить соответствие поведению модуля IIS UrlRewrite.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 5.0 (предварительная версия 7)

## <a name="old-behavior"></a>Старое поведение

Рассмотрим следующее правило перезаписи.

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

Предыдущее правило не присоединяет строку запроса. Универсальный код ресурса (URI), такой как `/about?id=1`, перенаправляет в `/contact` вместо `/contact?id=1`. По умолчанию атрибут `appendQueryString` имеет значение `true`.

## <a name="new-behavior"></a>Новое поведение

Строка запроса сохраняется. Код URI из примера в разделе [Старое поведение](#old-behavior) будет иметь значение `/contact?id=1`.

## <a name="reason-for-change"></a>Причина изменения

Старое поведение не соответствовало поведению модуля IIS UrlRewrite. Для поддержки переноса между ПО промежуточного слоя и модулем важно обеспечить согласованное поведение.

## <a name="recommended-action"></a>Рекомендованное действие

Если удаление строки запроса является предпочтительным поведением, следует установить для элемента `action` значение `appendQueryString="false"`.

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
