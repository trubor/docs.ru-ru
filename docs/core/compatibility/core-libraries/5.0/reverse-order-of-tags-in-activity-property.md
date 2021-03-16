---
title: Критическое изменение. Порядок тегов в действии Activity.Tags обращен
description: Сведения о критическом изменении в .NET 5 в основных библиотеках .NET, где Activity.Tags теперь сохраняет элементы в списке в соответствии с порядком их добавления.
ms.date: 11/01/2020
ms.openlocfilehash: f37f44cbe2ea467f0962cd8971d5bf38ce958dfd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257132"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a>Порядок тегов в действии Activity.Tags обращен

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> теперь сохраняет элементы в списке в соответствии с порядком их добавления, то есть первый добавленный элемент отображается в списке первым. Это изменение было внесено в соответствии со [спецификацией атрибутов OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> сохраняет элементы в порядке, обратном их добавлению. Это значит, что первый добавленный элемент является последним в списке. Начиная с .NET 5 порядок элементов теперь обратный, и первый добавленный элемент всегда находится в списке первым.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Если приложение зависит от порядка элементов в списке <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> и выполняется обновление до .NET 5 или более поздней версии, необходимо изменить эту часть кода.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
