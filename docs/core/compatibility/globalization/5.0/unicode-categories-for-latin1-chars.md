---
title: Критическое изменение. Для некоторых символов латиницы-1 изменилась категория Юникода
description: Сведения о критическом изменении глобализации в .NET 5, где методы char теперь возвращают правильную категорию Юникода для символов в диапазоне латиницы-1.
ms.date: 04/07/2020
ms.openlocfilehash: 03355c488d2bdae78f989e647c9b5b7913d73649
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256677"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a>Для некоторых символов латиницы-1 изменилась категория Юникода

Методы <xref:System.Char> теперь возвращают правильную категорию Юникода для символов в диапазоне латиницы-1. Категория соответствует стандарту Юникода.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET методы <xref:System.Char> использовали фиксированный список категорий Юникода для символов в диапазоне латиницы-1. Однако в стандарте Юникода категории некоторых из этих символов были изменены, так как эти API были реализованы, что создает расхождение. Кроме того, существует несоответствие между API <xref:System.Char> и <xref:System.Globalization.CharUnicodeInfo>, которые следуют стандарту Юникода. В .NET 5 и более поздних версиях методы <xref:System.Char> используют и возвращают категорию Юникода, которая соответствует стандарту Юникода для всех символов.

В следующей таблице показаны символы, чьи категории Юникода изменились в .NET 5.0:

| Символ    | Категория Юникода<br>в предыдущих версиях .NET | Категория Юникода<br>в .NET 5 и более поздних версиях |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| § (\u00a7)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| ª (\u00aa)   | `LowercaseLetter`                             | `OtherLetter`                                      |
| SHY (\u00ad) | `DashPunctuation`                             | `Format`                                           |
| ¶ (\u00b6)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| º (\u00ba)   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

Если у вас есть код, который получает категорию символов Юникода с помощью класса <xref:System.Char> и предполагает, что категория никогда не изменится, может потребоваться обновить его.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было сделано таким образом, чтобы категории, возвращаемые типом <xref:System.Char>, соответствовали стандарту Unicode и типу <xref:System.Globalization.CharUnicodeInfo>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

Кроме того, это изменение затрагивает любой класс, зависящий от <xref:System.Char> для получения категории символов Юникода, например <xref:System.Text.RegularExpressions.Regex>.

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
