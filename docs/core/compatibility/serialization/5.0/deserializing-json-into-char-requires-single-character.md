---
title: Критическое изменение. Для десериализации символа требуется строка из одного символа
description: Сведения о критическом изменении в .NET 5, где System.Text.Json требует наличия в JSON строки с одним символом при десериализации до целевого символа.
ms.date: 12/15/2020
ms.openlocfilehash: e901f8ee7e7521af948a3bcde5cf969640436f7f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256339"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>Для десериализации символа в System.Text.Json требуется строка из одного символа

Для успешной десериализации <xref:System.Char> с помощью <xref:System.Text.Json>строка JSON должна содержать один символ.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET строка из нескольких `char` в JSON успешно десериализуется в свойство `char` или поле. Используется только первый `char` строки, как показано в следующем примере:

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

В .NET 5 и более поздних версиях передача любой строки, кроме строки с одним `char`, приводит к вызову исключения <xref:System.Text.Json.JsonException>, если целевым объектом десериализации является `char`. Следующий пример строки успешно десериализуется во всех версиях .NET:

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="reason-for-change"></a>Причина изменения

Синтаксический анализ для сериализации должен выполняться только тогда, когда предоставленные полезные данные допустимы для целевого типа. Для типа `char` единственным допустимым набором полезных данных является строка с одним `char`.

## <a name="recommended-action"></a>Рекомендованное действие

При десериализации JSON в целевой объект `char` убедитесь, что строка состоит из одного `char`.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
