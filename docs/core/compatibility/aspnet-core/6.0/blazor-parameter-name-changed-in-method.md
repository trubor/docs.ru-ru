---
title: 'Критическое изменение. Blazor: изменено имя параметра в методе RequestImageFileAsync'
description: 'Сведения о критическом изменении в ASP.NET Core 6.0. Blazor: изменено имя параметра в методе RequestImageFileAsync'
no-loc:
- Blazor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 06fe2b0cff17630e09da3f80c506684f1b26e9d4
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292279"
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
