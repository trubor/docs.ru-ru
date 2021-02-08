---
description: 'Дополнительные сведения о операторе:  >> (Visual Basic)'
title: '>> Оператор'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 125b93f129734d196bd1f7f9c4fde86ab5d66319
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795304"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b0cc2-103">Оператор >> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0cc2-103">>> Operator (Visual Basic)</span></span>

<span data-ttu-id="b0cc2-104">Выполняет арифметический сдвиг битового шаблона вправо.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-104">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0cc2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0cc2-105">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b0cc2-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b0cc2-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="b0cc2-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-107">Required.</span></span> <span data-ttu-id="b0cc2-108">Целое числовое значение.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-108">Integral numeric value.</span></span> <span data-ttu-id="b0cc2-109">Результат сдвига битового шаблона.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-109">The result of shifting the bit pattern.</span></span> <span data-ttu-id="b0cc2-110">Тип данных такой же, как для `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-110">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="b0cc2-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-111">Required.</span></span> <span data-ttu-id="b0cc2-112">Целое числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-112">Integral numeric expression.</span></span> <span data-ttu-id="b0cc2-113">Битовый шаблон, подлежащий сдвигу.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-113">The bit pattern to be shifted.</span></span> <span data-ttu-id="b0cc2-114">Данные должны быть целого типа (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` или `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-114">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b0cc2-115">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-115">Required.</span></span> <span data-ttu-id="b0cc2-116">Числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-116">Numeric expression.</span></span> <span data-ttu-id="b0cc2-117">Количество разрядов, на которое следует сдвинуть битовый шаблон.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-117">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="b0cc2-118">Данные должны относиться к типу `Integer` или допускать расширение до типа `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-118">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0cc2-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0cc2-119">Remarks</span></span>  

 <span data-ttu-id="b0cc2-120">Арифметические сдвиги не являются циклическими, то есть биты, сдвинутые за пределы результата, не переносятся на другой конец.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-120">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b0cc2-121">При арифметическом сдвиге вправо биты, сдвинутые за пределы крайней правой позиции, отбрасываются, а самый левый бит (знак) распространяется на биты, освобожденные слева.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-121">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="b0cc2-122">Это означает, что если `pattern` имеет отрицательное значение, освобождаемые позиции задаются как один; в противном случае — значение 0.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-122">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="b0cc2-123">Обратите внимание, что типы данных `Byte` ,, `UShort` и не `UInteger` `ULong` подписаны, поэтому для распространения нет бита знака.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-123">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="b0cc2-124">Если `pattern` имеет любой тип без знака, освобождаемые позиции всегда устанавливаются в ноль.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-124">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="b0cc2-125">Чтобы предотвратить сдвиг на большее количество битов, чем может вместить результат, Visual Basic маскирует значение `amount` с маской размера, соответствующей типу данных `pattern` .</span><span class="sxs-lookup"><span data-stu-id="b0cc2-125">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="b0cc2-126">Двоичные значения и этих значений используются для величины сдвига.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-126">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="b0cc2-127">Ниже приведены маски размера.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-127">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="b0cc2-128">Тип данных `pattern`</span><span class="sxs-lookup"><span data-stu-id="b0cc2-128">Data type of `pattern`</span></span>|<span data-ttu-id="b0cc2-129">Маска размера (десятичная)</span><span class="sxs-lookup"><span data-stu-id="b0cc2-129">Size mask (decimal)</span></span>|<span data-ttu-id="b0cc2-130">Маска размера (шестнадцатеричная)</span><span class="sxs-lookup"><span data-stu-id="b0cc2-130">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="b0cc2-131">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="b0cc2-131">`SByte`, `Byte`</span></span>|<span data-ttu-id="b0cc2-132">7</span><span class="sxs-lookup"><span data-stu-id="b0cc2-132">7</span></span>|<span data-ttu-id="b0cc2-133">&H00000007</span><span class="sxs-lookup"><span data-stu-id="b0cc2-133">&H00000007</span></span>|  
|<span data-ttu-id="b0cc2-134">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="b0cc2-134">`Short`, `UShort`</span></span>|<span data-ttu-id="b0cc2-135">15</span><span class="sxs-lookup"><span data-stu-id="b0cc2-135">15</span></span>|<span data-ttu-id="b0cc2-136">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="b0cc2-136">&H0000000F</span></span>|  
|<span data-ttu-id="b0cc2-137">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="b0cc2-137">`Integer`, `UInteger`</span></span>|<span data-ttu-id="b0cc2-138">31</span><span class="sxs-lookup"><span data-stu-id="b0cc2-138">31</span></span>|<span data-ttu-id="b0cc2-139">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="b0cc2-139">&H0000001F</span></span>|  
|<span data-ttu-id="b0cc2-140">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="b0cc2-140">`Long`, `ULong`</span></span>|<span data-ttu-id="b0cc2-141">63</span><span class="sxs-lookup"><span data-stu-id="b0cc2-141">63</span></span>|<span data-ttu-id="b0cc2-142">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="b0cc2-142">&H0000003F</span></span>|  
  
 <span data-ttu-id="b0cc2-143">Если `amount` равен нулю, значение `result` идентично значению `pattern` .</span><span class="sxs-lookup"><span data-stu-id="b0cc2-143">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="b0cc2-144">Если `amount` имеет отрицательное значение, оно принимается в качестве значения без знака и маскируется с соответствующей маской размера.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-144">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="b0cc2-145">Арифметические сдвиги никогда не создают исключений переполнения.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-145">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b0cc2-146">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="b0cc2-146">Overloading</span></span>  

 <span data-ttu-id="b0cc2-147">`>>`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-147">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b0cc2-148">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-148">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b0cc2-149">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-149">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0cc2-150">Пример</span><span class="sxs-lookup"><span data-stu-id="b0cc2-150">Example</span></span>  

 <span data-ttu-id="b0cc2-151">В следующем примере оператор используется `>>` для выполнения арифметических сдвигов в целочисленных значениях вправо.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-151">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="b0cc2-152">Результат всегда имеет тот же тип данных, что и выражение, для которого выполняется сдвиг.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-152">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="b0cc2-153">Ниже приведены результаты предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-153">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="b0cc2-154">`result1` — 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-154">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="b0cc2-155">`result2` — 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-155">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="b0cc2-156">`result3` равно 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-156">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="b0cc2-157">`result4` — 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-157">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="b0cc2-158">`result5` равно 0 (смещено 15 позиций вправо).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-158">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="b0cc2-159">Сумма сдвига для вычисляется `result4` как 18 и 15, что равно 2.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-159">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="b0cc2-160">В следующем примере показаны арифметические сдвиги для отрицательного значения.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-160">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="b0cc2-161">Ниже приведены результаты предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-161">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="b0cc2-162">`negresult1` — 512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-162">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="b0cc2-163">`negresult2` равно-1 (бит подписи распространяется);</span><span class="sxs-lookup"><span data-stu-id="b0cc2-163">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cc2-164">См. также</span><span class="sxs-lookup"><span data-stu-id="b0cc2-164">See also</span></span>

- [<span data-ttu-id="b0cc2-165">Операторы сдвига битов</span><span class="sxs-lookup"><span data-stu-id="b0cc2-165">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="b0cc2-166">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="b0cc2-166">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="b0cc2-167"> Оператор>>=</span><span class="sxs-lookup"><span data-stu-id="b0cc2-167">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="b0cc2-168">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0cc2-168">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b0cc2-169">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="b0cc2-169">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b0cc2-170">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0cc2-170">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
