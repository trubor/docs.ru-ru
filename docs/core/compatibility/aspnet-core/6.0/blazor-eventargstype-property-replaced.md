---
title: 'Критическое изменение в Blazor: свойство WebEventDescriptor.EventArgsType заменено'
description: 'Сведения о критическом изменении в ASP.NET Core 6.0: свойство WebEventDescriptor.EventArgsType заменено свойством EventName.'
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: fb82e27d7ab55b78293f40debe917da2d99239a7
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255216"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a>Blazor: свойство :::no-loc text="WebEventDescriptor.EventArgsType"::: заменено

Класс <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> является частью внутреннего протокола Blazor для обмена событиями между JavaScript и .NET. Этот класс обычно используется не кодом приложения, а разработчиками платформы.

Начиная с ASP.NET Core 6.0, свойство <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> в `WebEventDescriptor` заменяется новым свойством `EventName`. Это изменение не должно повлиять на код приложения, так как относится к низкоуровневой реализации платформы.

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0

## <a name="old-behavior"></a>Старое поведение

В ASP.NET Core 5.0 и более ранних версий свойство `EventArgsType` описывает нестандартное имя категории, используемое только в Blazor, для групп типов событий DOM. Например, события `click` и `mousedown` сопоставлены со значением `EventArgsType`=`mouse`. Аналогично, события `cut`, `copy` и `paste` сопоставлены со значением `EventArgsType`=`clipboard`. Эти имена категорий используются для определения типа .NET, используемого при десериализации входных данных аргументов события.

## <a name="new-behavior"></a>Новое поведение

Начиная с ASP.NET Core 6.0, новое свойство `EventName` содержит только имя исходного события. Примеры: `click`, `mousedown`, `cut`, `copy` или `paste`. Больше нет необходимости предоставлять имя категории для Blazor. По этой причине старое свойство `EventArgsType` удаляется.

## <a name="reason-for-change"></a>Причина изменения

В запросе на вытягивание [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993) была добавлена поддержка классов пользовательских аргументов событий. В рамках этой поддержки платформа больше не предполагает, что все события относятся к предопределенному набору категорий. Теперь платформе достаточно знать имя исходного события.

## <a name="recommended-action"></a>Рекомендованное действие

Это не должно повлиять на код приложений, и вам ничего не придется изменять.

Если вы создаете пользовательскую платформу отрисовки Blazor, может потребоваться обновить механизм диспетчеризации событий в `Renderer`. Замените все жестко закодированные правила для категорий событий на более простую логику, которая предоставляет исходное имя необработанного события.

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
