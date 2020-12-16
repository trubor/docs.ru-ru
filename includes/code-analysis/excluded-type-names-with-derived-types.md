---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97531887"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="9499b-101">Исключить определенные типы и их производные типы</span><span class="sxs-lookup"><span data-stu-id="9499b-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="9499b-102">Из анализа можно исключить определенные типы и их производные типы.</span><span class="sxs-lookup"><span data-stu-id="9499b-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="9499b-103">Например, чтобы указать, что правило не должно выполняться для каких-либо методов в типах с именем `MyType` и производных типов, добавьте следующую пару "ключ-значение" в *editorconfig* -файл в проекте:</span><span class="sxs-lookup"><span data-stu-id="9499b-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="9499b-104">Допустимые форматы имен символов в значении параметра (разделенные `|` ):</span><span class="sxs-lookup"><span data-stu-id="9499b-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="9499b-105">Только имя типа (включает все типы с именем, независимо от содержащего его типа или пространства имен).</span><span class="sxs-lookup"><span data-stu-id="9499b-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="9499b-106">Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)символа с дополнительным `T:` префиксом.</span><span class="sxs-lookup"><span data-stu-id="9499b-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="9499b-107">Примеры:</span><span class="sxs-lookup"><span data-stu-id="9499b-107">Examples:</span></span>

| <span data-ttu-id="9499b-108">Значение параметра</span><span class="sxs-lookup"><span data-stu-id="9499b-108">Option Value</span></span> | <span data-ttu-id="9499b-109">Итоги</span><span class="sxs-lookup"><span data-stu-id="9499b-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="9499b-110">Соответствует всем типам с именем `MyType` и всем их производным типам.</span><span class="sxs-lookup"><span data-stu-id="9499b-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="9499b-111">Соответствует всем типам с именами `MyType1` или `MyType2` и всем производным от него типам.</span><span class="sxs-lookup"><span data-stu-id="9499b-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="9499b-112">Соответствует определенному типу `MyType` с заданным полным именем и всеми производными от него типами.</span><span class="sxs-lookup"><span data-stu-id="9499b-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="9499b-113">Соответствует конкретным типам `MyType1` и `MyType2` с соответствующими полными именами и всем их производным типам.</span><span class="sxs-lookup"><span data-stu-id="9499b-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |
