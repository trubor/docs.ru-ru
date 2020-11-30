---
title: Выполнение строковых операций, не зависящих от языка и региональных параметров
ms.date: 08/22/2018
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: a418432dfaba9ab070ddb6dc862dcbd798c16343
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732220"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="27393-102">Выполнение строковых операций, не зависящих от языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="27393-102">Performing culture-insensitive string operations</span></span>

<span data-ttu-id="27393-103">Большинство методов .NET, которые выполняют операции со строками с учетом языка и региональных параметров, по умолчанию предоставляют перегрузки, позволяющие явно указать используемые язык и региональные параметры, указав соответствующий параметр <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="27393-103">Most .NET methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="27393-104">Эти перегрузки позволяют устранить различия в сопоставлении регистров и правилах сортировки, вызванные различием языка и региональных параметров, и получить результаты, которые не зависят от языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="27393-105">В этом разделе содержатся следующие статьи, в которых показано, как выполнять операции со строками без учета языка и региональных параметров с помощью методов .NET, которые по умолчанию учитывают язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="27393-105">This section provides the following articles to demonstrate how to perform culture-insensitive string operations using .NET methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27393-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="27393-106">In this section</span></span>  

 [<span data-ttu-id="27393-107">Сравнение строк без учета языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="27393-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="27393-108">Описывает использование методов <xref:System.String.Compare%2A?displayProperty=nameWithType> и <xref:System.String.CompareTo%2A?displayProperty=nameWithType> для сравнения строк без учета языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="27393-109">Изменение регистра без учета языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="27393-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="27393-110">Описывает использование методов <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> и <xref:System.Char.ToLower%2A?displayProperty=nameWithType> для изменения регистра символов без учета языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="27393-111">Выполнение строковых операций без учета языка и региональных параметров в коллекциях</span><span class="sxs-lookup"><span data-stu-id="27393-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="27393-112">Описывает использование <xref:System.Collections.CaseInsensitiveComparer>, класса <xref:System.Collections.CaseInsensitiveHashCodeProvider>, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> и <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> для сравнения коллекций без учета языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="27393-113">Выполнение строковых операций без учета языка и региональных параметров в массивах</span><span class="sxs-lookup"><span data-stu-id="27393-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="27393-114">Описывает использование методов <xref:System.Array.Sort%2A?displayProperty=nameWithType> и <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> для операций над массивами без учета языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27393-115">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="27393-115">Related sections</span></span>  

 [<span data-ttu-id="27393-116">Операции со строками без учета языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="27393-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="27393-117">Описывает, почему следует иметь в виду язык и региональные параметры при выполнении операций над строками, и содержит указания о том, когда следует выполнять операции с учетом и без учета языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="27393-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="27393-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="27393-118">See also</span></span>

- [<span data-ttu-id="27393-119">Таблицы весовых коэффициентов сортировки (для .NET в ОС Windows)</span><span class="sxs-lookup"><span data-stu-id="27393-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="27393-120">Таблица параметров сортировки по умолчанию для элементов Юникод (для .NET Core в Linux и macOS)</span><span class="sxs-lookup"><span data-stu-id="27393-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
