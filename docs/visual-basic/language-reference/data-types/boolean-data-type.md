---
description: 'Дополнительные сведения: логический тип данных (Visual Basic)'
title: Логический тип данных
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: cdda6bc0571eb0a2a9ee6a079ffd276bfc89a9b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731413"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="f6422-103">Тип данных Boolean (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6422-103">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="f6422-104">Содержит значения, которые могут быть только `True` или `False` .</span><span class="sxs-lookup"><span data-stu-id="f6422-104">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="f6422-105">Ключевые слова `True` и `False` соответствуют двум состояниям `Boolean` переменных.</span><span class="sxs-lookup"><span data-stu-id="f6422-105">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6422-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="f6422-106">Remarks</span></span>  

 <span data-ttu-id="f6422-107">Используйте [логический тип данных (Visual Basic)](boolean-data-type.md) для хранения двух значений, таких как true/false, да/нет или ON/OFF.</span><span class="sxs-lookup"><span data-stu-id="f6422-107">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="f6422-108">Значением свойства `Boolean` по умолчанию является `False`.</span><span class="sxs-lookup"><span data-stu-id="f6422-108">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="f6422-109">`Boolean` значения не хранятся в виде чисел, а хранимые значения не должны быть эквивалентны числам.</span><span class="sxs-lookup"><span data-stu-id="f6422-109">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="f6422-110">Никогда не следует писать код, основанный на эквивалентных числовых значениях для `True` и `False` .</span><span class="sxs-lookup"><span data-stu-id="f6422-110">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="f6422-111">Везде, где это возможно, следует ограничить использование `Boolean` переменных логическими значениями, для которых они предназначены.</span><span class="sxs-lookup"><span data-stu-id="f6422-111">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="f6422-112">Преобразования типов</span><span class="sxs-lookup"><span data-stu-id="f6422-112">Type Conversions</span></span>  

 <span data-ttu-id="f6422-113">Когда Visual Basic преобразует числовые значения типа данных в значение `Boolean` , значение 0 становится равным, `False` а все остальные значения становятся `True` .</span><span class="sxs-lookup"><span data-stu-id="f6422-113">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="f6422-114">Когда Visual Basic преобразует `Boolean` значения в числовые типы, преобразуется в `False` 0 и `True` преобразуется в значение-1.</span><span class="sxs-lookup"><span data-stu-id="f6422-114">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="f6422-115">При преобразовании между `Boolean` значениями и числовыми типами данных следует помнить, что методы преобразования платформа .NET Framework не всегда дают те же результаты, что и ключевые слова Visual Basicного преобразования.</span><span class="sxs-lookup"><span data-stu-id="f6422-115">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="f6422-116">Это обусловлено тем, что Visual Basicное преобразование поддерживает поведение, совместимое с предыдущими версиями.</span><span class="sxs-lookup"><span data-stu-id="f6422-116">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="f6422-117">Дополнительные сведения см. в разделе "неверное Преобразование логического типа в числовой тип" раздела [Устранение неполадок типов данных](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f6422-117">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="f6422-118">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="f6422-118">Programming Tips</span></span>  
  
- <span data-ttu-id="f6422-119">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="f6422-119">**Negative Numbers.**</span></span> <span data-ttu-id="f6422-120">`Boolean` не является числовым типом и не может представлять отрицательное значение.</span><span class="sxs-lookup"><span data-stu-id="f6422-120">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="f6422-121">В любом случае не следует использовать `Boolean` для хранения числовых значений.</span><span class="sxs-lookup"><span data-stu-id="f6422-121">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="f6422-122">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="f6422-122">**Type Characters.**</span></span> <span data-ttu-id="f6422-123">`Boolean` не имеет символа типа литерала или символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="f6422-123">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="f6422-124">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="f6422-124">**Framework Type.**</span></span> <span data-ttu-id="f6422-125">В .NET Framework данный тип соответствует структуре <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6422-125">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6422-126">Пример</span><span class="sxs-lookup"><span data-stu-id="f6422-126">Example</span></span>  

 <span data-ttu-id="f6422-127">В следующем примере `runningVB` — это `Boolean` переменная, в которой хранится простой параметр Да/нет.</span><span class="sxs-lookup"><span data-stu-id="f6422-127">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6422-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f6422-128">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="f6422-129">Типы данных</span><span class="sxs-lookup"><span data-stu-id="f6422-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="f6422-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="f6422-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="f6422-131">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="f6422-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="f6422-132">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="f6422-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="f6422-133">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="f6422-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f6422-134">CType Function</span><span class="sxs-lookup"><span data-stu-id="f6422-134">CType Function</span></span>](../functions/ctype-function.md)
