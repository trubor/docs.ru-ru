---
title: 'Критическое изменение. Blazor: изменено имя параметра в методе RequestImageFileAsync'
description: Сведения о критическом изменении в ASP.NET Core 6.0 — Blazor. изменено имя параметра в методе RequestImageFileAsync
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 645b53e341507ffd9f369eea1b940232b7c14770
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255185"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a>Blazor: изменено имя параметра в методе RequestImageFileAsync

Параметр `maxWith` метода `RequestImageFileAsync` был переименован из `maxWith` в `maxWidth`.

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0 (предварительная версия 1)

## <a name="old-behavior"></a>Старое поведение

Имя параметра пишется как `maxWith`.

## <a name="new-behavior"></a>Новое поведение

Имя параметра пишется как `maxWidth`.

## <a name="reason-for-change"></a>Причина изменения

Исходное имя параметра было типографической ошибкой.

## <a name="recommended-action"></a>Рекомендованное действие

Если вы используете именованные параметры в API `RequestImageFile`, измените имя параметра `maxWith` на `maxWidth`. В противном случае изменение не требуется.

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
