---
description: 'Дополнительные сведения о: Куотедпаирреадер Class'
title: Класс Куотедпаирреадер (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 810a7b02948a1b7aa542a179563af9a6d79dd763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699666"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="dfeea-103">Класс QuotedPairReader</span><span class="sxs-lookup"><span data-stu-id="dfeea-103">QuotedPairReader class</span></span>

<span data-ttu-id="dfeea-104">Определяет, какие символы в строке заключены в кавычки (экранированные).</span><span class="sxs-lookup"><span data-stu-id="dfeea-104">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="dfeea-105">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="dfeea-105">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="dfeea-106">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="dfeea-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dfeea-107">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="dfeea-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="dfeea-108">Метод Каунткуотедчарс</span><span class="sxs-lookup"><span data-stu-id="dfeea-108">CountQuotedChars method</span></span>

<span data-ttu-id="dfeea-109">Подсчитывает количество последовательных заключенных в кавычки символов, включая несколько предшествующих кавычек, в указанной строке.</span><span class="sxs-lookup"><span data-stu-id="dfeea-109">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="dfeea-110">Например, если задана строка `a\\\b` и индекс `4` , метод возвращает значение `4` , так как `b` заключено в кавычки и поэтому являются три предшествующих обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="dfeea-110">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="dfeea-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="dfeea-111">Parameters</span></span>

- <span data-ttu-id="dfeea-112">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="dfeea-112">`data` <xref:System.String></span></span>

  <span data-ttu-id="dfeea-113">Строка данных, в которой подсчитывается число последовательных символов в кавычках.</span><span class="sxs-lookup"><span data-stu-id="dfeea-113">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="dfeea-114">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="dfeea-114">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="dfeea-115">Строка в указанной строке до и включает в себя подсчет последовательных символов в кавычках.</span><span class="sxs-lookup"><span data-stu-id="dfeea-115">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="dfeea-116">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="dfeea-116">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="dfeea-117">`true` значение для запрета экранирования символов Юникода; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="dfeea-117">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="dfeea-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dfeea-118">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="dfeea-119">`0` значение, если символ по указанному индексу не экранирован; в противном случае — число последовательных символов в кавычках до символа, включая символ `index` .</span><span class="sxs-lookup"><span data-stu-id="dfeea-119">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="dfeea-120">Исключения</span><span class="sxs-lookup"><span data-stu-id="dfeea-120">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="dfeea-121">Escape-символ Юникода найден, но не разрешен.</span><span class="sxs-lookup"><span data-stu-id="dfeea-121">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfeea-122">Требования</span><span class="sxs-lookup"><span data-stu-id="dfeea-122">Requirements</span></span>

<span data-ttu-id="dfeea-123">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dfeea-123">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dfeea-124">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="dfeea-124">**Assembly:** System (in System.dll)</span></span>
