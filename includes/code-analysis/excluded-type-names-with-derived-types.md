---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97531887"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>Исключение определенных типов и их производных типов

Из анализа можно исключать определенные типы и их производные типы. Например, чтобы указать, что правило не должно выполняться в каких-либо методах типов `MyType` и их производных типов, добавьте следующую пару "ключ-значение" в файл *.editorconfig* своего проекта:

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

Допустимые форматы имени символа в значении параметра (разделенные `|`):

- Только имя типа (включает все типы с этим именем, любого типа и в любом пространстве имен).
- Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings) для символа с необязательным префиксом `T:`.

Примеры:

| Значение параметра | Итоги |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | Соответствует всем типам с именем `MyType` и всем их производным типам. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | Соответствует всем типам с именем `MyType1` или `MyType2` и всем их производным типам. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | Соответствует конкретному типу `MyType` с заданным полным именем и всем производным от него типам. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | Соответствует конкретным типам `MyType1` и `MyType2` с заданным полным именем и всем производным от них типам. |
