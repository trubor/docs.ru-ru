---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97366822"
---
### <a name="exclude-specific-symbols"></a>Исключение определенных символов

Вы можете исключить из анализа определенные символы, например типы и методы. Например, чтобы указать, что правило не должно выполняться для какого-либо кода в типах с именем `MyType`, добавьте следующую пару "ключ-значение" в файл *EDITORCONFIG* в своем проекте:

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

Допустимые форматы имени символа в значении параметра (разделенные `|`):

- Только имя символа (включает все символы с этим именем, любого типа и в любом пространстве имен).
- Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings) для символа. Для каждого имени символа требуется префикс в виде символа, например `M:` для методов, `T:` для типов и `N:` для пространств имен.
- `.ctor` используется для конструкторов, а `.cctor` — для статических конструкторов.

Примеры:

| Значение параметра | Итоги |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | Соответствует всем символам с именем `MyType`. |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | Соответствует всем символам с именем `MyType1` или `MyType2`. |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | Соответствует конкретному методу `MyMethod` с заданной полной сигнатурой. |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | Соответствует конкретным методам `MyMethod1` и `MyMethod2` с соответствующими полными сигнатурами. |
