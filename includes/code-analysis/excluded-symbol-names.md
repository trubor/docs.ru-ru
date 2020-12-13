---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366822"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="23431-101">Исключить конкретные символы</span><span class="sxs-lookup"><span data-stu-id="23431-101">Exclude specific symbols</span></span>

<span data-ttu-id="23431-102">Вы можете исключить из анализа определенные символы, например типы и методы.</span><span class="sxs-lookup"><span data-stu-id="23431-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="23431-103">Например, чтобы указать, что правило не должно выполняться в каком-либо коде в типах с именем `MyType` , добавьте следующую пару "ключ-значение" в *editorconfig* -файл в проекте:</span><span class="sxs-lookup"><span data-stu-id="23431-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="23431-104">Допустимые форматы имен символов в значении параметра (разделенные `|` ):</span><span class="sxs-lookup"><span data-stu-id="23431-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="23431-105">Только имя символа (включает все символы с именем, независимо от содержащего его типа или пространства имен).</span><span class="sxs-lookup"><span data-stu-id="23431-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="23431-106">Полные имена в [формате идентификатора документации](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)символа.</span><span class="sxs-lookup"><span data-stu-id="23431-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="23431-107">Для каждого имени символа требуется префикс типа символа, например `M:` для методов, `T:` для типов и `N:` для пространств имен.</span><span class="sxs-lookup"><span data-stu-id="23431-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="23431-108">`.ctor` для конструкторов и `.cctor` для статических конструкторов.</span><span class="sxs-lookup"><span data-stu-id="23431-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="23431-109">Примеры:</span><span class="sxs-lookup"><span data-stu-id="23431-109">Examples:</span></span>

| <span data-ttu-id="23431-110">Значение параметра</span><span class="sxs-lookup"><span data-stu-id="23431-110">Option Value</span></span> | <span data-ttu-id="23431-111">Сводка</span><span class="sxs-lookup"><span data-stu-id="23431-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="23431-112">Соответствует всем символам с именем `MyType` .</span><span class="sxs-lookup"><span data-stu-id="23431-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="23431-113">Соответствует всем символам с именем `MyType1` или `MyType2` .</span><span class="sxs-lookup"><span data-stu-id="23431-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="23431-114">Соответствует конкретному методу `MyMethod` с указанной полной сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="23431-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="23431-115">Соответствует конкретным методам `MyMethod1` и `MyMethod2` соответствующим полным сигнатурам.</span><span class="sxs-lookup"><span data-stu-id="23431-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
