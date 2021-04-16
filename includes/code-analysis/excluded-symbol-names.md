---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97366822"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="d1be4-101">Исключение определенных символов</span><span class="sxs-lookup"><span data-stu-id="d1be4-101">Exclude specific symbols</span></span>

<span data-ttu-id="d1be4-102">Вы можете исключить из анализа определенные символы, например типы и методы.</span><span class="sxs-lookup"><span data-stu-id="d1be4-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="d1be4-103">Например, чтобы указать, что правило не должно выполняться для какого-либо кода в типах с именем `MyType`, добавьте следующую пару "ключ-значение" в файл *EDITORCONFIG* в своем проекте:</span><span class="sxs-lookup"><span data-stu-id="d1be4-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="d1be4-104">Допустимые форматы имени символа в значении параметра (разделенные `|`):</span><span class="sxs-lookup"><span data-stu-id="d1be4-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="d1be4-105">Только имя символа (включает все символы с этим именем, любого типа и в любом пространстве имен).</span><span class="sxs-lookup"><span data-stu-id="d1be4-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="d1be4-106">Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings) для символа.</span><span class="sxs-lookup"><span data-stu-id="d1be4-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="d1be4-107">Для каждого имени символа требуется префикс в виде символа, например `M:` для методов, `T:` для типов и `N:` для пространств имен.</span><span class="sxs-lookup"><span data-stu-id="d1be4-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="d1be4-108">`.ctor` используется для конструкторов, а `.cctor` — для статических конструкторов.</span><span class="sxs-lookup"><span data-stu-id="d1be4-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="d1be4-109">Примеры:</span><span class="sxs-lookup"><span data-stu-id="d1be4-109">Examples:</span></span>

| <span data-ttu-id="d1be4-110">Значение параметра</span><span class="sxs-lookup"><span data-stu-id="d1be4-110">Option Value</span></span> | <span data-ttu-id="d1be4-111">Итоги</span><span class="sxs-lookup"><span data-stu-id="d1be4-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="d1be4-112">Соответствует всем символам с именем `MyType`.</span><span class="sxs-lookup"><span data-stu-id="d1be4-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="d1be4-113">Соответствует всем символам с именем `MyType1` или `MyType2`.</span><span class="sxs-lookup"><span data-stu-id="d1be4-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="d1be4-114">Соответствует конкретному методу `MyMethod` с заданной полной сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="d1be4-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="d1be4-115">Соответствует конкретным методам `MyMethod1` и `MyMethod2` с соответствующими полными сигнатурами.</span><span class="sxs-lookup"><span data-stu-id="d1be4-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
