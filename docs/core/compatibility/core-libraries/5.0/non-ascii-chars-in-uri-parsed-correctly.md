---
title: Критическое изменение. В UNIX правильно анализируются пути URI с символами, отличными от ASCII
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где абсолютные пути URI, которые содержат символы, отличные от ASCII, теперь правильно анализируются на платформах UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 50e9b4597a5ac0b73732a38ce662037292777a03
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257418"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>В UNIX правильно анализируются пути URI с символами, отличными от ASCII

В классе <xref:System.Uri?displayProperty=fullName> была исправлена ошибка таким образом, что абсолютные пути URI, которые содержат символы, отличные от ASCII, теперь правильно анализируются на платформах UNIX.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET абсолютные пути URI, содержащие символы, отличные от ASCII, анализировались неправильно на платформах UNIX, а сегменты пути дублировались. (Абсолютный путь — это путь, который начинается с "/".) Проблема анализа исправлена в .NET 5.0. При переходе с предыдущей версии .NET на .NET 5 и более поздние версии вы получите различные значения, создаваемые <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType> и другими членами <xref:System.Uri>.

Рассмотрим выходные данные следующего кода при выполнении в UNIX.

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

Выходные данные в предыдущей версии .NET:

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

Выходные данные в .NET 5 и более поздних версиях:

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Если у вас есть код, который ожидает и учитывает повторяющиеся сегменты пути, то можно удалить этот код.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
