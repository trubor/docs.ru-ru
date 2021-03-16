---
title: Критическое изменение. API-интерфейсы глобализации, которые используют библиотеки ICU в Windows
description: Сведения о критическом изменении глобализации в .NET 5, где для функций глобализации используются библиотеки ICU вместо NLS.
ms.date: 05/19/2020
ms.openlocfilehash: 4b8580fcb3ba3c9b95357a7922e3a3062ccd3728
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256755"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a>API-интерфейсы глобализации, которые используют библиотеки ICU в Windows

.NET 5 и более поздних версий использует библиотеки [ICU (международные компоненты для Юникода)](http://site.icu-project.org/home) для поддержки глобализации при работе в Windows 10 с обновлением за май 2019 года или более поздней версии.

## <a name="change-description"></a>Описание изменений

В .NET Core 1.0–3.1 и .NET Framework 4 и более поздних версий библиотеки .NET используют для функции глобализации в Windows API [Многоязыковой поддержки (NLS)](/windows/win32/intl/national-language-support). Например, функции NLS применялись для сравнения строк, получения данных о языке и региональных параметрах, а также для изменения капитализации строк в соответствии с необходимыми языком и региональными параметрами.

Начиная с .NET 5 для приложений в среде Windows 10 с обновлением за май 2019 года или более поздней версии библиотеки .NET по умолчанию используют API-интерфейсы глобализации [ICU](http://site.icu-project.org/home).

> [!NOTE]
> В Windows 10 с обновлением за май 2019 года и более поздних версий входит библиотека ICU. Если среда выполнения .NET не может загрузить ICU, вместо нее используется NLS.

## <a name="behavioral-differences"></a>Различия в поведении

Вы можете заметить изменения в приложении, даже если не догадываетесь, что используете средства глобализации. В этом разделе перечислено несколько из возможных изменений поведения.

### <a name="stringindexof"></a>String.IndexOf

Рассмотрим следующий код, который вызывает <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType>, чтобы найти в строке индекс символа новой строки.

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- В предыдущих версиях .NET для Windows фрагмент кода выводит `6`.
- В .NET 5 и более поздних версиях на Windows 19H1 и более поздних версий фрагмент кода выводит `-1`.

Чтобы исправить этот код, выполняя порядковый поиск вместо поиска с учетом языка и региональных параметров, вызовите перегрузку <xref:System.String.IndexOf(System.String,System.StringComparison)> и передайте в нее в качестве аргумента <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Вы можете запустить правила анализа кода [CA1307: использование StringComparison, чтобы ясно указать намерение](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) и [CA1309: использование StringComparison по порядковым номерам](../../../../fundamentals/code-analysis/quality-rules/ca1309.md), чтобы найти эти точки вызова в коде.

Дополнительные сведения см. в статье [Изменения поведения при сравнении строк в .NET 5+](../../../../standard/base-types/string-comparison-net-5-plus.md).

### <a name="currency-symbol"></a>Символ валют

Рассмотрим следующий код, который форматирует строку с помощью указателя формата валюты `C`. Для языка и региональных параметров текущего потока заданы настройки только для языка, а не страны.

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- В предыдущих версиях .NET для Windows значение text равно `"100,00 €"`.
- В .NET 5 и более поздних версиях в Windows 19H1 и более поздних версий значение text равно `"100,00 ¤"`, и вместо евро в нем используется международный символ валюты. В ICU валюта является свойством страны или региона, а не языка.

## <a name="reason-for-change"></a>Причина изменения

Это изменение введено для унификации поведения глобализации .NET во всех поддерживаемых операционных системах. Благодаря ему приложения смогут объединять собственные библиотеки глобализации и не зависеть от встроенных библиотек операционных систем.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

От разработчика не требуется никаких действий. Но если вы хотите по-прежнему использовать API-интерфейсы глобализации NLS, настройте [параметр времени выполнения](../../../run-time-config/globalization.md#nls), чтобы вернуться к старому поведению. Дополнительные сведения о доступных параметрах см. в статье [Глобализация .NET и ICU](../../../../standard/globalization-localization/globalization-icu.md).

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Почти все типы в пространстве имен <xref:System.Globalization?displayProperty=fullName>
- <xref:System.Array.Sort%2A?displayProperty=fullName> (при сортировке массива строк)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (если элементы списка являются строками)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (если ключи являются строками)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (если ключи являются строками)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (если набор содержит строки)

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
