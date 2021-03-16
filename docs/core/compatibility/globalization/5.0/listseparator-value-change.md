---
title: Критическое изменение. Изменение значения TextInfo.ListSeparator
description: Узнайте о критическом изменении .NET 5, которое связано с тем, что значение по умолчанию TextInfo.ListSeparator изменилось между версиями 5.0 и 5.0.1.
ms.date: 12/10/2020
ms.openlocfilehash: 9a319da8ea8e3cbf62cbf4730e553b03f5bfdc89
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256729"
---
# <a name="textinfolistseparator-values-changed"></a>Изменение значения TextInfo.ListSeparator

Значения по умолчанию <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> для разных языков и региональных параметров изменились во всех операционных системах.

## <a name="change-description"></a>Описание изменений

В .NET 5.0.0 в рамках [переключения с NLS на библиотеки ICU](icu-globalization-api.md) значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> по умолчанию для различных языков и региональных параметров в Windows изменились. В качестве значений <xref:System.Globalization.TextInfo.ListSeparator> были использованы значения десятичных разделителей, полученные из международных компонентов для Юникода (ICU). В Linux и macOS значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> не изменились, то есть по-прежнему используются значения десятичного разделителя.

Для всех операционных систем в .NET 5.0.1 и более поздних версий значения для <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> эквивалентны значениям, полученным из NLS. Для Windows это означает, что значения эквивалентны тем, что были в .NET Framework и .NET Core 1.0–3.1. Для Linux и macOS значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> теперь соответствуют значениям <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> для Windows.

В следующей таблице приведены изменения для значений <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>.

| | .NET Framework<br/>.NET Core 1.0–3.1 | .NET 5 | .NET 5.0.1 |
-|-|-|-
| **Windows** | Получение из NLS | Десятичный разделитель из ICU.<br/>Можно переключиться обратно на NLS. | Эквивалентно NLS |
| **Linux и macOS** | Десятичный разделитель из ICU | Десятичный разделитель из ICU | Эквивалентно NLS |

## <a name="version-introduced"></a>Представленная версия

5.0.1

## <a name="reason-for-change"></a>Причина изменения

Разработчики сообщили, что они используют свойство <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> при анализе файлов с разделителями-запятыми (CSV), а новые значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> нарушают этот синтаксический анализ.

## <a name="recommended-action"></a>Рекомендованное действие

Если код зависит от предыдущих значений десятичного разделителя, можно жестко закодировать требуемые значения <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
