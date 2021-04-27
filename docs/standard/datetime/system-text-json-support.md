---
title: Поддержка DateTime и DateTimeOffset в System.Text.Json
description: Общие сведения о поддержке типов DateTime и DateTimeOffset в System.Text.Jsв библиотеке.
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 652725192b00ef42a2c51a1ae710239e72203dc9
ms.sourcegitcommit: 381b773c9962aca5f8d0b973d0653c0f4edcc4d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2021
ms.locfileid: "108013792"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Поддержка DateTime и DateTimeOffset в System.Text.Json

System.Text.Jsв библиотеке выполняет синтаксический анализ и запись <xref:System.DateTime> и <xref:System.DateTimeOffset> значения в соответствии с расширенным профилем ISO 8601-1:2019.
[Преобразователи](xref:System.Text.Json.Serialization.JsonConverter%601) обеспечивают пользовательскую поддержку сериализации и десериализации с помощью <xref:System.Text.Json.JsonSerializer> .
Пользовательская поддержка также может быть реализована при использовании <xref:System.Text.Json.Utf8JsonReader> и <xref:System.Text.Json.Utf8JsonWriter> .

## <a name="support-for-the-iso-8601-12019-format"></a>Поддержка формата ISO 8601-1:2019

<xref:System.Text.Json.JsonSerializer>Типы, <xref:System.Text.Json.Utf8JsonReader> , <xref:System.Text.Json.Utf8JsonWriter> и могут <xref:System.Text.Json.JsonElement> анализировать и записывать <xref:System.DateTime> и <xref:System.DateTimeOffset> текстовые представления в соответствии с расширенным профилем формата ISO 8601-1:2019, например 2019-07-26T16:59:57-05:00.

<xref:System.DateTime><xref:System.DateTimeOffset>данные и могут быть сериализованы с помощью <xref:System.Text.Json.JsonSerializer> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/serializing-with-jsonserializer/Program.cs":::

Их также можно десериализовать с помощью <xref:System.Text.Json.JsonSerializer> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/deserializing-with-jsonserializer-valid/Program.cs":::

При использовании параметров по умолчанию входные <xref:System.DateTime> и <xref:System.DateTimeOffset> текстовые представления должны соответствовать расширенному профилю ISO 8601-1:2019.
Попытка десериализовать представления, которые не соответствуют профилю, приведет к <xref:System.Text.Json.JsonSerializer> созданию исключения <xref:System.Text.Json.JsonException> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/deserializing-with-jsonserializer-error/Program.cs":::

<xref:System.Text.Json.JsonDocument>Предоставляет структурированный доступ к содержимому полезных данных JSON, включая <xref:System.DateTime> представления и <xref:System.DateTimeOffset> . В приведенном ниже примере показано, как при наличии коллекции температур можно вычислить среднюю температуру по понедельникам.

:::code language="csharp" source="snippets/system-text-json-support/csharp/computing-with-jsondocument-valid/Program.cs":::

Попытка вычисления средней температуры при наличии полезных данных с несоответствующими <xref:System.DateTime> представлениями вызовет <xref:System.Text.Json.JsonDocument> исключение <xref:System.FormatException> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/computing-with-jsondocument-error/Program.cs":::

<xref:System.Text.Json.Utf8JsonWriter>Записи и данные нижнего уровня <xref:System.DateTime> <xref:System.DateTimeOffset> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/writing-with-utf8jsonwriter/Program.cs":::

<xref:System.Text.Json.Utf8JsonReader> синтаксические анализы <xref:System.DateTime> и <xref:System.DateTimeOffset> данные:

:::code language="csharp" source="snippets/system-text-json-support/csharp/reading-with-utf8jsonreader-valid/Program.cs":::

Попытка чтения несовместимых форматов с <xref:System.Text.Json.Utf8JsonReader> вызовет исключение <xref:System.FormatException> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/reading-with-utf8jsonreader-error/Program.cs":::

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Пользовательская поддержка для <xref:System.DateTime> и <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>При использовании <xref:System.Text.Json.JsonSerializer>

Если вы хотите, чтобы сериализатор выполнял пользовательское синтаксический анализ или форматирование, можно реализовать [пользовательские преобразователи](xref:System.Text.Json.Serialization.JsonConverter%601).
Вот несколько примеров:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Использование `DateTime(Offset).Parse` и `DateTime(Offset).ToString`

Если не удается определить форматы входных <xref:System.DateTime> или <xref:System.DateTimeOffset> текстовых представлений, можно использовать `DateTime(Offset).Parse` метод в логике чтения преобразователя. Это позволяет использовать. Обширная поддержка для анализа различных <xref:System.DateTime> <xref:System.DateTimeOffset> форматов и текста, в том числе строк, отличных от ISO 8601, и форматов ISO 8601, которые не соответствуют расширенному профилю ISO 8601-1:2019. Этот подход значительно меньше, чем использование собственной реализации сериализатора.

Для сериализации можно использовать `DateTime(Offset).ToString` метод в логике записи преобразователя. Это позволяет писать <xref:System.DateTime> <xref:System.DateTimeOffset> значения и использовать любые [стандартные форматы даты](../base-types/standard-date-and-time-format-strings.md)и времени, а также [пользовательские форматы даты и времени](../base-types/custom-date-and-time-format-strings.md).
Это также значительно менее производительно, чем использование собственной реализации сериализатора.

:::code language="csharp" source="snippets/system-text-json-support/csharp/datetime-converter-examples/example1/Program.cs":::

> [!NOTE]
> При реализации <xref:System.Text.Json.Serialization.JsonConverter%601> , и `T` <xref:System.DateTime> `typeToConvert` параметр всегда будет иметь значение `typeof(DateTime)` .
Параметр полезен для обработки полиморфизмов и использования универсальных шаблонов для получения `typeof(T)` производительного способа.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Использование <xref:System.Buffers.Text.Utf8Parser> и <xref:System.Buffers.Text.Utf8Formatter>

В логике преобразователя можно использовать быстрые методы синтаксического анализа и форматирования на основе UTF-8, если входные <xref:System.DateTime> или <xref:System.DateTimeOffset> текстовые представления совместимы с одним из строк "R", "l", "O" или "G" [стандартного формата даты и времени](../base-types/standard-date-and-time-format-strings.md), или вы хотите писать в соответствии с одним из этих форматов. Это гораздо быстрее, чем использование `DateTime(Offset).Parse` и `DateTime(Offset).ToString` .

В этом примере показан пользовательский преобразователь, который сериализует и десериализует <xref:System.DateTime> значения в соответствии со [стандартным форматом "R"](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

:::code language="csharp" source="snippets/system-text-json-support/csharp/datetime-converter-examples/example2/Program.cs":::

> [!NOTE]
> Стандартный формат "R" всегда будет иметь длину 29 символов.
>
> Формат "l" (строчные буквы "L") не документирован в других [строках стандартного формата даты и времени](../base-types/standard-date-and-time-format-strings.md) , так как он поддерживается только `Utf8Parser` типами и `Utf8Formatter` . Формат имеет нижний регистр RFC 1123 (версия формата R в нижнем регистре), например: "Четверг, 25 июля 2019 06:36:07 GMT".

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Использование в `DateTime(Offset).Parse` качестве резервного варианта для собственного анализа сериализатора

Если обычно вход <xref:System.DateTime> или <xref:System.DateTimeOffset> данные должны соответствовать расширенному профилю ISO 8601-1:2019, можно использовать собственную логику синтаксического анализа сериализатора. Также можно реализовать резервный механизм, как и в случае.
В этом примере показано, что после сбоя синтаксического анализа <xref:System.DateTime> текстового представления с помощью <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> преобразователь успешно проанализирует данные с помощью <xref:System.DateTime.Parse(System.String)> .

:::code language="csharp" source="snippets/system-text-json-support/csharp/datetime-converter-examples/example3/Program.cs":::

#### <a name="using-unix-epoch-date-format"></a>Использование формата даты эпохи UNIX

Следующие конвертеры обрабатывали формат эпохи UNIX с часовым поясом или без него (такие значения, как `/Date(1590863400000-0700)/` или `/Date(1590863400000)/` ):

:::code language="csharp" source="../serialization/snippets/system-text-json-how-to-5-0/csharp/CustomConverterUnixEpochDate.cs" id="ConverterOnly":::

:::code language="csharp" source="../serialization/snippets/system-text-json-how-to-5-0/csharp/CustomConverterUnixEpochDateNoZone.cs" id="ConverterOnly":::

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>При записи с помощью <xref:System.Text.Json.Utf8JsonWriter>

Если вы хотите написать пользовательское <xref:System.DateTime> или <xref:System.DateTimeOffset> текстовое представление с помощью <xref:System.Text.Json.Utf8JsonWriter> , можно отформатировать пользовательское представление до <xref:System.String> , `ReadOnlySpan<Byte>` , `ReadOnlySpan<Char>` или <xref:System.Text.Json.JsonEncodedText> , а затем передать его в соответствующий <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> метод или <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> .

В следующем примере показано <xref:System.DateTime> , как можно создать настраиваемый формат с помощью <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> , а затем написать с помощью <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> метода:

:::code language="csharp" source="snippets/system-text-json-support/csharp/custom-writing-with-utf8jsonwriter/Program.cs":::

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>При чтении с <xref:System.Text.Json.Utf8JsonReader>

Если вы хотите прочитать Пользовательское <xref:System.DateTime> или <xref:System.DateTimeOffset> текстовое представление с помощью <xref:System.Text.Json.Utf8JsonReader> , можно получить значение текущего маркера JSON в качестве <xref:System.String> использования <xref:System.Text.Json.Utf8JsonReader.GetString> , а затем проанализировать значение с помощью пользовательской логики.

В следующем примере показано, как пользовательское <xref:System.DateTimeOffset> текстовое представление можно получить с помощью <xref:System.Text.Json.Utf8JsonReader.GetString> , а затем выполнить синтаксический анализ с помощью <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> :

:::code language="csharp" source="snippets/system-text-json-support/csharp/custom-reading-with-utf8jsonreader/Program.cs":::

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Расширенный профиль ISO 8601-1:2019 в System.Text.Jsна

### <a name="date-and-time-components"></a>Компоненты даты и времени

Расширенный профиль ISO 8601-1:2019, реализованный в <xref:System.Text.Json> , определяет следующие компоненты для представлений даты и времени. Эти компоненты используются для определения различных уровней детализации, поддерживаемых при анализе и форматировании и <xref:System.DateTime> <xref:System.DateTimeOffset> представлениях.

| Компонент       | Формат                      | Описание                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Год            | "yyyy"                      | 0001-9999                                                                       |
| Месяц           | "MM"                        | 01-12                                                                           |
| День             | "dd"                        | 01-28, 01-29, 01-30, 01-31 в зависимости от месяца/года                                  |
| Час            | "HH"                        | 00-23                                                                           |
| Минута          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| Вторая дробь | "FFFFFFF"                   | Минимум одна цифра, максимум 16 цифр                                      |
| Смещение времени     | "K"                         | "Z" или "(' + '/'-') HH ': ' mm '                                                |
| Частичное время    | "HH": "mm": "SS [FFFFFFF]"     | Время без сведений о смещении UTC                                             |
| Полная дата       | "yyyy'-'MM'-'дд"            | Дата календаря                                                                   |
| Полное время       | "Partial Тиме'к"           | Время суток в формате UTC или местного времени дня с смещением времени между местным временем и временем в формате UTC |
| Дата и время       | "' Полная дата ' \ ' ' полное время ' ' | Календарная дата и время суток, например 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Поддержка синтаксического анализа

Для синтаксического анализа определены следующие уровни детализации:

1. "Полная дата"
    1. "yyyy'-'MM'-'дд"

2. "' Полная дата ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '
    1. "yyyy'-'MM'-'dd'T'HH": "mm"

3. "' Полная дата ' 'T ' ' частичное время ' '
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([Описатель сортируемого формата ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF

4. "' Полная дата ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '
    1. "yyyy'-'MM'-'dd'T'HH": "ММЗ"
    2. "yyyy'-'MM'-'dd'T'HH": "mm (' + '/'-') HH ': ' mm"

5. "Дата и время"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "ссZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' ФФФФФФФЗ "
    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '
    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF (' + '/'-') HH ': ' mm '

    Этот уровень детализации соответствует стандарту [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6), широко принятому профилю ISO 8601, используемому для получения сведений о дате и времени. Однако в System.Text.Jsреализации существует несколько ограничений.

    - В RFC 3339 не указывается максимальное число цифр дробной части секунды, но указывает, что по крайней мере одна цифра должна следовать за точкой, если имеется раздел с долей секунды. Реализация в System.Text.Jsпозволяет до 16 цифр (для поддержки взаимодействия с другими языками программирования и платформами), но анализирует только первые семь. <xref:System.Text.Json.JsonException>Если при чтении `DateTime` и экземплярах используется более 16 долей секунды, будет выдано исключение `DateTimeOffset` .
    - RFC 3339 позволяет использовать символы "T" и "Z", соответственно, как "t" или "z", но позволяет приложениям ограничить поддержку только вариантами верхнего регистра. Реализация в System.Text.Jsдля требует, чтобы они были "T" и "Z". <xref:System.Text.Json.JsonException>Будет создано исключение, если входные данные содержат "t" или "z" при чтении `DateTime` и `DateTimeOffset` экземплярах.
    - RFC 3339 указывает, что разделы даты и времени разделены символом "T", но они позволяют приложениям разделять их пробелами (""). System.Text.Jsдля требует, чтобы разделы даты и времени были разделены символом "T". <xref:System.Text.Json.JsonException>Будет создано исключение, если входные данные содержат пробел ("") при чтении `DateTime` и в `DateTimeOffset` экземплярах.

Если в секундах есть десятичные дроби, должна быть хотя бы одна цифра; `2019-07-26T00:00:00.` не допускается.
Хотя допускается до 16 цифр дробной части, анализируются только первые семь. Все, что больше, считается нулем.
Например, `2019-07-26T00:00:00.1234567890` будет анализироваться так, как если бы он был `2019-07-26T00:00:00.1234567` .
Это позволяет обеспечить совместимость с <xref:System.DateTime> реализацией, которая ограничена этим разрешением.

Високосные секунды не поддерживаются.

### <a name="support-for-formatting"></a>Поддержка форматирования

Для форматирования определены следующие уровни гранулярности:

1. "' Полная дата ' 'T ' ' частичное время ' '
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([Описатель сортируемого формата ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Используется для форматирования <xref:System.DateTime> без дробной части секунд и без сведений о смещении.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF

        Используется для форматирования <xref:System.DateTime> с долей секунды, но без сведений о смещении.

2. "Дата и время"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "ссZ"

        Используется для форматирования <xref:System.DateTime> без доли секунды, но с смещением в формате UTC.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' ФФФФФФФЗ "

        Используется для форматирования <xref:System.DateTime> с долей секунд и смещения в формате UTC.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '

        Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> без доли секунды, но с локальным смещением.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS '. ' FFFFFFF (' + '/'-') HH ': ' mm '

        Используется для форматирования <xref:System.DateTime> или <xref:System.DateTimeOffset> с долей секунды и с локальным смещением.

    Этот уровень детализации соответствует [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6).

Если представление [формата кругового](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) пути <xref:System.DateTime> или <xref:System.DateTimeOffset> экземпляра или имеет конечные нули в долях секунды, то <xref:System.Text.Json.JsonSerializer> и <xref:System.Text.Json.Utf8JsonWriter> будет форматировать представление экземпляра без конечных нулей.
Например, экземпляр, <xref:System.DateTime> представление [формата обратной](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) передачи которого имеет значение `2019-04-24T14:50:17.1010000Z` , будет отформатировано как `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> и <xref:System.Text.Json.Utf8JsonWriter> .

Если представление [формата обратной](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) передачи <xref:System.DateTime> <xref:System.DateTimeOffset> экземпляра или имеет все нули в долях секунды, то <xref:System.Text.Json.JsonSerializer> и <xref:System.Text.Json.Utf8JsonWriter> будет форматировать представление экземпляра без доли секунды.
Например, экземпляр, <xref:System.DateTime> представление [формата обратной](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) передачи которого имеет значение `2019-04-24T14:50:17.0000000+02:00` , будет отформатировано как `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> и <xref:System.Text.Json.Utf8JsonWriter> .

Усечение нулей в долях секунды позволяет получить наименьший объем выходных данных, необходимых для сохранения информации во время цикла обработки.

Записываются не более 7 цифр в долях секунды. Это соответствует <xref:System.DateTime> реализации, которая ограничена этим разрешением.
