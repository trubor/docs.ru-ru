---
title: 'Критическое изменение. Blazor: Открытые поля только для чтения RenderTreeFrame стали свойствами'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Открытые поля только для чтения RenderTreeFrame стали свойствами
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c4d70279b4280b079570099b82b056299405508b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498169"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a>Blazor: Открытые поля только для чтения RenderTreeFrame стали свойствами

В ASP.NET Core 3.0 и 3.1 структура <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> содержит различные поля `readonly public`, включая <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> и другие. В ASP.NET Core 5.0 RC1 и более поздних версиях все поля `readonly public` изменились на свойства `readonly public`.

Это изменение не затронет многих разработчиков по следующим причинам.

* Все приложения или библиотеки, которые просто используют файлы `.razor` (или даже выполняемые вручную вызовы <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder>) для определения их компонентов, не ссылаются на этот тип напрямую.
* Сам тип `RenderTreeFrame` рассматривается как компонент реализации, не предназначенный для использования вне платформы. В состав ASP.NET Core 3.0 и более поздних версий входит анализатор, который выдает предупреждения компилятора в случае непосредственного использования типа.
* Даже если вы ссылаетесь на `RenderTreeFrame` напрямую, это изменение нарушает двоичные файлы, но не нарушает исходный код. То есть существующий исходный код будет правильно компилироваться и работать. Ошибка возникнет только при компиляции на платформе .NET Core 3.x и последующем запуске этих двоичных файлов на платформе .NET 5.0 RC1 и более поздних версий.

Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).

## <a name="version-introduced"></a>Представленная версия

5.0 (RC1)

## <a name="old-behavior"></a>Старое поведение

Открытые члены в `RenderTreeFrame` определяются как поля. Например, `renderTreeFrame.Sequence` и `renderTreeFrame.ElementName`.

## <a name="new-behavior"></a>Новое поведение

Открытые члены в `RenderTreeFrame` определяются как свойства с теми же именами, что и раньше. Например, `renderTreeFrame.Sequence` и `renderTreeFrame.ElementName`.

Если более старый предварительно скомпилированный код не был перекомпилирован с момента этого изменения, может возникнуть исключение, похожее на *MissingFieldException. Поле не найдено: "Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType"* .

## <a name="reason-for-change"></a>Причина изменения

Это изменение было необходимо для реализации важных улучшений производительности в отрисовке компонентов Blazor в ASP.NET Core 5.0. Поддерживаются те же уровни безопасности и инкапсуляции.

## <a name="recommended-action"></a>Рекомендованное действие

Это изменение не затрагивает большинство разработчиков Blazor. Оно, скорее всего, повлияет на авторов библиотек и пакетов, но только в редких случаях. В частности, если вы:

* Разрабатываете приложение и используете ASP.NET Core 3.x или выполняете обновление до 5.0 RC1 или более поздней версии, вам не нужно изменять собственный код. Однако если существует зависимость от библиотеки, которая обновлена с учетом этого изменения, необходимо выполнить обновление до более новой версии этой библиотеки.
* Создаете библиотеку и хотите поддерживать только ASP.NET Core 5.0 RC1 или более поздние версии, никаких действий выполнять не требуется. Просто убедитесь, что в файле проекта объявлено значение `<TargetFramework>` `net5.0` или более поздней версии.
* Создаете библиотеку и хотите поддерживать ASP.NET Core 3 x *и* 5.0, определите, считывает ли код элементы `RenderTreeFrame`. Например, оцените `someRenderTreeFrame.FrameType`.
  * Большинство библиотек, включая библиотеки, содержащие компоненты `.razor`, не считывают элементы `RenderTreeFrame`. В этом случае никаких действий выполнять не требуется.
  * Однако если ваша библиотека считывает элементы, вам потребуется несколько целевых платформ для поддержки `netstandard2.1` и `net5.0`. Примените следующие изменения в файле проекта.
    * Замените существующий элемент `<TargetFramework>` на `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.
    * Используйте ссылку на условный пакет `Microsoft.AspNetCore.Components`, чтобы учесть обе версии, которые требуется поддерживать. Пример:

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

Дополнительные пояснения см. на странице [сравнения, где @jsakamoto уже обновил библиотеку `Toolbelt.Blazor.HeadElement`](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
