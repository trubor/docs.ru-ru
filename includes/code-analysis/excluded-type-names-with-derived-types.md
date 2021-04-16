---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97531887"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="96824-101">Исключение определенных типов и их производных типов</span><span class="sxs-lookup"><span data-stu-id="96824-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="96824-102">Из анализа можно исключать определенные типы и их производные типы.</span><span class="sxs-lookup"><span data-stu-id="96824-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="96824-103">Например, чтобы указать, что правило не должно выполняться в каких-либо методах типов `MyType` и их производных типов, добавьте следующую пару "ключ-значение" в файл *.editorconfig* своего проекта:</span><span class="sxs-lookup"><span data-stu-id="96824-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="96824-104">Допустимые форматы имени символа в значении параметра (разделенные `|`):</span><span class="sxs-lookup"><span data-stu-id="96824-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="96824-105">Только имя типа (включает все типы с этим именем, любого типа и в любом пространстве имен).</span><span class="sxs-lookup"><span data-stu-id="96824-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="96824-106">Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings) для символа с необязательным префиксом `T:`.</span><span class="sxs-lookup"><span data-stu-id="96824-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="96824-107">Примеры:</span><span class="sxs-lookup"><span data-stu-id="96824-107">Examples:</span></span>

| <span data-ttu-id="96824-108">Значение параметра</span><span class="sxs-lookup"><span data-stu-id="96824-108">Option Value</span></span> | <span data-ttu-id="96824-109">Итоги</span><span class="sxs-lookup"><span data-stu-id="96824-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="96824-110">Соответствует всем типам с именем `MyType` и всем их производным типам.</span><span class="sxs-lookup"><span data-stu-id="96824-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="96824-111">Соответствует всем типам с именем `MyType1` или `MyType2` и всем их производным типам.</span><span class="sxs-lookup"><span data-stu-id="96824-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="96824-112">Соответствует конкретному типу `MyType` с заданным полным именем и всем производным от него типам.</span><span class="sxs-lookup"><span data-stu-id="96824-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="96824-113">Соответствует конкретным типам `MyType1` и `MyType2` с заданным полным именем и всем производным от них типам.</span><span class="sxs-lookup"><span data-stu-id="96824-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |
