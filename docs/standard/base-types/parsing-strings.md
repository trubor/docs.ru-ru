---
title: Преобразование строк в типы
description: Общие сведения об анализе строк в .NET. Операция анализа преобразует строку, представляющую базовый тип .NET, в этот базовый тип. Анализ является операцией, обратной форматированию.
ms.date: 03/30/2017
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: a5c38c29a45a9ce6f8aed7205c5bd44bebb023c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683724"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="e0077-105">Анализ строк в .NET</span><span class="sxs-lookup"><span data-stu-id="e0077-105">Parse strings in .NET</span></span>

<span data-ttu-id="e0077-106">Операция *синтаксического анализа* преобразует строку, представляющую базовый тип .NET, в этот базовый тип.</span><span class="sxs-lookup"><span data-stu-id="e0077-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="e0077-107">Например, операция синтаксического анализа используется для преобразования строки в число с плавающей запятой или в значение даты и времени.</span><span class="sxs-lookup"><span data-stu-id="e0077-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="e0077-108">Чаще всего для выполнения операции синтаксического разбора используется метод `Parse`.</span><span class="sxs-lookup"><span data-stu-id="e0077-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="e0077-109">Поскольку разбор — это операция, обратная форматированию (которое подразумевает преобразование базового типа в строковое представление), то применимы многие схожие правила и условия.</span><span class="sxs-lookup"><span data-stu-id="e0077-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="e0077-110">Подобно тому, как при форматировании используется объект, реализующий интерфейс <xref:System.IFormatProvider> для предоставления зависящей от языка и региональных параметров информации форматирования, точно так же и при синтаксическом разборе используется объект, реализующий интерфейс <xref:System.IFormatProvider>, чтобы определить, как интерпретировать строковое представление.</span><span class="sxs-lookup"><span data-stu-id="e0077-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="e0077-111">Дополнительные сведения см. в статье [Типы форматирования в .NET](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e0077-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e0077-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="e0077-112">In This Section</span></span>

 <span data-ttu-id="e0077-113">[Анализ числовых строк](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="e0077-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="e0077-114">Описание преобразования строк в числовые типы .NET.</span><span class="sxs-lookup"><span data-stu-id="e0077-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="e0077-115">[Анализ строк даты и времени](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="e0077-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="e0077-116">Описание преобразования строк в типы **даты и времени** .NET.</span><span class="sxs-lookup"><span data-stu-id="e0077-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="e0077-117">[Анализ других строк](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="e0077-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="e0077-118">Описание преобразования строк в типы **Char**, **Boolean** и **Enum**.</span><span class="sxs-lookup"><span data-stu-id="e0077-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e0077-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="e0077-119">Related Sections</span></span>

 <span data-ttu-id="e0077-120">[Типы форматирования](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="e0077-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="e0077-121">Описание базовых концепций форматирования, таких как описатели формата и поставщики формата.</span><span class="sxs-lookup"><span data-stu-id="e0077-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="e0077-122">[Преобразование типов в .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="e0077-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="e0077-123">Описание процесса преобразования типов.</span><span class="sxs-lookup"><span data-stu-id="e0077-123">Describes how to convert types.</span></span>
