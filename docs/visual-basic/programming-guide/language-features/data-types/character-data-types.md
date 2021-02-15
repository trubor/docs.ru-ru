---
description: 'Дополнительные сведения: символьные типы данных (Visual Basic)'
title: Символьные типы данных
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 2197c0210cb0c2287baff9856889334f5f95bd4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466397"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="45e9f-103">Символьные типы данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45e9f-103">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="45e9f-104">Visual Basic предоставляет *символьные типы данных* для работы с печатными и отображаемыми символами.</span><span class="sxs-lookup"><span data-stu-id="45e9f-104">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="45e9f-105">Несмотря на то, что они работают с символами Юникода, `Char` содержит один символ, тогда как `String` содержит неопределенное число символов.</span><span class="sxs-lookup"><span data-stu-id="45e9f-105">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="45e9f-106">Для таблицы, отображающей параллельное сравнение типов данных Visual Basic, см. в разделе [типы данных](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="45e9f-106">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="45e9f-107">Тип char</span><span class="sxs-lookup"><span data-stu-id="45e9f-107">Char Type</span></span>  

 <span data-ttu-id="45e9f-108">`Char`Тип данных — это один двухбайтовый (16-разрядный) символ Юникода.</span><span class="sxs-lookup"><span data-stu-id="45e9f-108">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="45e9f-109">Если переменная всегда хранит ровно один символ, объявите ее как `Char` .</span><span class="sxs-lookup"><span data-stu-id="45e9f-109">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="45e9f-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="45e9f-110">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="45e9f-111">Каждое возможное значение в `Char` переменной или `String` является кодовой *точкой* или кодом символа в кодировке Юникода.</span><span class="sxs-lookup"><span data-stu-id="45e9f-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="45e9f-112">Символы Юникода включают в себя основную кодировку ASCII, различные буквы, цифры, символы валют, дроби, диакритические знаки, математические и технические символы.</span><span class="sxs-lookup"><span data-stu-id="45e9f-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45e9f-113">Набор символов Юникода резервирует кодовые точки D800 до DFFF (от 55296 до 55551 десятичного) для *пар символов-заместителей*, для которых требуются 2 16-разрядные значения для представления одной кодовой точки.</span><span class="sxs-lookup"><span data-stu-id="45e9f-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="45e9f-114">`Char`Переменная не может содержать суррогатную пару, а `String` для хранения такой пары используется две позиции.</span><span class="sxs-lookup"><span data-stu-id="45e9f-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="45e9f-115">Дополнительные сведения см. в разделе [тип данных char](../../../language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="45e9f-115">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="45e9f-116">Тип строки</span><span class="sxs-lookup"><span data-stu-id="45e9f-116">String Type</span></span>  

 <span data-ttu-id="45e9f-117">`String`Тип данных — это последовательность из нуля или более двухбайтовых (16-разрядных) символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="45e9f-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="45e9f-118">Если переменная может содержать неопределенное число символов, объявите ее как `String` .</span><span class="sxs-lookup"><span data-stu-id="45e9f-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="45e9f-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="45e9f-119">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="45e9f-120">Дополнительные сведения см. в разделе [тип данных String](../../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="45e9f-120">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e9f-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="45e9f-121">See also</span></span>

- [<span data-ttu-id="45e9f-122">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="45e9f-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="45e9f-123">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="45e9f-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="45e9f-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45e9f-124">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="45e9f-125">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="45e9f-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="45e9f-126">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45e9f-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="45e9f-127">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="45e9f-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="45e9f-128">Символы типов</span><span class="sxs-lookup"><span data-stu-id="45e9f-128">Type Characters</span></span>](type-characters.md)
