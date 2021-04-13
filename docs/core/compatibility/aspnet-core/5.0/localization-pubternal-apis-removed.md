---
title: Критическое изменение. Удалены API-интерфейсы Pubternal
description: Сведения о критическом изменении в ASP.NET Core 5.0, где были удалены некоторые API локализации pubternal
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b6f80569945e54367117446ea96107d6c5199c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497674"
---
# <a name="localization-pubternal-apis-removed"></a>Локализация. Удалены API-интерфейсы Pubternal

Чтобы сохранить порядок в среде общедоступных API на платформе ASP.NET Core, некоторые API локализации :::no-loc text="\"pubternal\""::: были удалены. API :::no-loc text="\"pubternal\""::: имеет модификатор доступа `public` и определен в пространстве имен, предполагающем использование намерения [internal](../../../../csharp/language-reference/keywords/internal.md).

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).

## <a name="version-introduced"></a>Представленная версия

5.0, предварительная версия 6

## <a name="old-behavior"></a>Старое поведение

Следующие API были `public`:

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- Перегрузки конструктора `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`, принимающие один из следующих типов параметров:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a>Новое поведение

В следующем списке перечислены изменения.

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper` стал `Microsoft.Extensions.Localization.AssemblyWrapper` и теперь является `internal`.
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` стал `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` и теперь является `internal`.
- Перегрузки конструктора `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`, принимающие один из следующих типов параметров, теперь являются `internal`:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a>Причина изменения

Более подробное описание приведено на странице [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), типы :::no-loc text="\"pubternal\""::: были удалены из области API `public`. В соответствии с этими изменениями в процесс разработки можно включить больше классов. Рассматриваемые классы предназначались для использования в качестве точек расширения для внутреннего тестирования команды.

## <a name="recommended-action"></a>Рекомендованное действие

Хотя это маловероятно, некоторые приложения могут намеренно или случайно зависеть от типов :::no-loc text="\"pubternal\"":::. Сведения о переходе с конкретных типов см. в разделах [Новое поведение](#new-behavior).

Если возникла ситуация, в которой общедоступный API можно было использовать до этого изменения, а сейчас нельзя, разместите вопрос о проблеме на странице [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

## <a name="affected-apis"></a>Затронутые API

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
