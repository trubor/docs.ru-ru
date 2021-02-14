---
description: 'Дополнительные сведения: преобразования между строками и другими типами (Visual Basic)'
title: Преобразования значений между строковыми и другими типами
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: c0f7f7637d173d039d58b2516fba41ae55b990ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477220"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="a25e0-103">Преобразование значений между строковыми и другими типами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25e0-103">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="a25e0-104">Можно преобразовать числовое значение типа, `Boolean` или значения даты и времени в `String` .</span><span class="sxs-lookup"><span data-stu-id="a25e0-104">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="a25e0-105">Можно также преобразовать в обратном направлении — от строкового значения к числовому, `Boolean` или `Date` — при условии, что содержимое строки может интерпретироваться как допустимое значение целевого типа данных.</span><span class="sxs-lookup"><span data-stu-id="a25e0-105">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="a25e0-106">Если они не могут, возникает ошибка времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="a25e0-106">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="a25e0-107">Преобразования для всех этих назначений в любом направлении представляют собой сужающие преобразования.</span><span class="sxs-lookup"><span data-stu-id="a25e0-107">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="a25e0-108">Следует использовать ключевые слова преобразования типов (,,,,,,, `CBool` `CByte` ,,,, `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` `CStr` `CUInt` , `CULng` , `CUShort` и `CType` ).</span><span class="sxs-lookup"><span data-stu-id="a25e0-108">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="a25e0-109"><xref:Microsoft.VisualBasic.Strings.Format%2A>Функции и <xref:Microsoft.VisualBasic.Conversion.Val%2A> предоставляют дополнительный контроль над преобразованиями между строками и числами.</span><span class="sxs-lookup"><span data-stu-id="a25e0-109">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="a25e0-110">Если вы определили класс или структуру, можно определить операторы преобразования типов между `String` и типом класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a25e0-110">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="a25e0-111">Дополнительные сведения см. в разделе [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a25e0-111">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="a25e0-112">Преобразование чисел в строки</span><span class="sxs-lookup"><span data-stu-id="a25e0-112">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="a25e0-113">Функцию можно использовать `Format` для преобразования числа в отформатированную строку, которая может включать не только соответствующие цифры, но и символы форматирования, такие как знак валюты (например `$` ,), разделители тысяч или *символы группирования цифр* (например,), `,` и десятичный разделитель (например,) `.` .</span><span class="sxs-lookup"><span data-stu-id="a25e0-113">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="a25e0-114">`Format` автоматически использует соответствующие символы в соответствии с **региональными** параметрами, заданными на **панели управления** Windows.</span><span class="sxs-lookup"><span data-stu-id="a25e0-114">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="a25e0-115">Обратите внимание, что оператор конкатенации ( `&` ) может преобразовать число в строку неявным образом, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a25e0-115">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="a25e0-116">Преобразование строк в числа</span><span class="sxs-lookup"><span data-stu-id="a25e0-116">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="a25e0-117">Функцию можно использовать `Val` для явного преобразования цифр из строки в число.</span><span class="sxs-lookup"><span data-stu-id="a25e0-117">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="a25e0-118">`Val` считывает строку, пока не встретится символ, отличный от цифры, пробела, табуляции, перевода строки или точки.</span><span class="sxs-lookup"><span data-stu-id="a25e0-118">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="a25e0-119">Последовательности "&O" и "&H" изменяют основание системы счисления и завершают сканирование.</span><span class="sxs-lookup"><span data-stu-id="a25e0-119">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="a25e0-120">До тех пор пока не будет остановлено чтение, `Val` преобразует все соответствующие символы в числовое значение.</span><span class="sxs-lookup"><span data-stu-id="a25e0-120">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="a25e0-121">Например, следующая инструкция возвращает значение `141.825` .</span><span class="sxs-lookup"><span data-stu-id="a25e0-121">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="a25e0-122">Когда Visual Basic преобразует строку в числовое значение, она использует **региональные параметры** , заданные на **панели управления** Windows, для интерпретации разделителя групп разрядов, десятичного разделителя и символа валюты.</span><span class="sxs-lookup"><span data-stu-id="a25e0-122">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="a25e0-123">Это означает, что преобразование может быть выполнено в одном параметре, но не в другом.</span><span class="sxs-lookup"><span data-stu-id="a25e0-123">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="a25e0-124">Например, `"$14.20"` допустим в английской (США) национальной настройке, но не на французском языке.</span><span class="sxs-lookup"><span data-stu-id="a25e0-124">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25e0-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a25e0-125">See also</span></span>

- [<span data-ttu-id="a25e0-126">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a25e0-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="a25e0-127">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="a25e0-127">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="a25e0-128">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="a25e0-128">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a25e0-129">Практическое руководство. Преобразование объекта к другому типу в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a25e0-129">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="a25e0-130">Преобразования массивов</span><span class="sxs-lookup"><span data-stu-id="a25e0-130">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="a25e0-131">Типы данных</span><span class="sxs-lookup"><span data-stu-id="a25e0-131">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="a25e0-132">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="a25e0-132">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a25e0-133">Разработка глобализованных и локализованных приложений</span><span class="sxs-lookup"><span data-stu-id="a25e0-133">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
