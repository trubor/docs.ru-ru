---
description: 'Дополнительные сведения о операторе:  << (Visual Basic)'
title: Оператор <<
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 079af61e5c4ce3834db0877feace724c74c8169c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665631"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3bbcd-103">\<\< Оператор (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bbcd-103">\<\< Operator (Visual Basic)</span></span>

<span data-ttu-id="3bbcd-104">Выполняет арифметический сдвиг битового шаблона влево.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-104">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbcd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3bbcd-105">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3bbcd-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="3bbcd-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="3bbcd-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-107">Required.</span></span> <span data-ttu-id="3bbcd-108">Целое числовое значение.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-108">Integral numeric value.</span></span> <span data-ttu-id="3bbcd-109">Результат сдвига битового шаблона.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-109">The result of shifting the bit pattern.</span></span> <span data-ttu-id="3bbcd-110">Тип данных такой же, как для `pattern`.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-110">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="3bbcd-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-111">Required.</span></span> <span data-ttu-id="3bbcd-112">Целое числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-112">Integral numeric expression.</span></span> <span data-ttu-id="3bbcd-113">Битовый шаблон, подлежащий сдвигу.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-113">The bit pattern to be shifted.</span></span> <span data-ttu-id="3bbcd-114">Данные должны быть целого типа (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` или `ULong`).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-114">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3bbcd-115">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-115">Required.</span></span> <span data-ttu-id="3bbcd-116">Числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-116">Numeric expression.</span></span> <span data-ttu-id="3bbcd-117">Количество разрядов, на которое следует сдвинуть битовый шаблон.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-117">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="3bbcd-118">Данные должны относиться к типу `Integer` или допускать расширение до типа `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-118">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bbcd-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="3bbcd-119">Remarks</span></span>  

 <span data-ttu-id="3bbcd-120">Арифметические сдвиги не являются циклическими, то есть биты, сдвинутые за пределы результата, не переносятся на другой конец.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-120">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3bbcd-121">При выполнении арифметического сдвига влево биты, сдвинутые за пределы диапазона результирующего типа данных, отбрасываются, а позиции битов, освобожденные справа, устанавливаются в ноль.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-121">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="3bbcd-122">Чтобы предотвратить сдвиг на больше бит, чем может вместить результат, Visual Basic маскирует значение `amount` с маской размера, соответствующей типу данных `pattern` .</span><span class="sxs-lookup"><span data-stu-id="3bbcd-122">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="3bbcd-123">Двоичные значения и этих значений используются для величины сдвига.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-123">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="3bbcd-124">Ниже приведены маски размера.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-124">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="3bbcd-125">Тип данных `pattern`</span><span class="sxs-lookup"><span data-stu-id="3bbcd-125">Data type of `pattern`</span></span>|<span data-ttu-id="3bbcd-126">Маска размера (десятичная)</span><span class="sxs-lookup"><span data-stu-id="3bbcd-126">Size mask (decimal)</span></span>|<span data-ttu-id="3bbcd-127">Маска размера (шестнадцатеричная)</span><span class="sxs-lookup"><span data-stu-id="3bbcd-127">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="3bbcd-128">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="3bbcd-128">`SByte`, `Byte`</span></span>|<span data-ttu-id="3bbcd-129">7</span><span class="sxs-lookup"><span data-stu-id="3bbcd-129">7</span></span>|<span data-ttu-id="3bbcd-130">&H00000007</span><span class="sxs-lookup"><span data-stu-id="3bbcd-130">&H00000007</span></span>|  
|<span data-ttu-id="3bbcd-131">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="3bbcd-131">`Short`, `UShort`</span></span>|<span data-ttu-id="3bbcd-132">15</span><span class="sxs-lookup"><span data-stu-id="3bbcd-132">15</span></span>|<span data-ttu-id="3bbcd-133">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="3bbcd-133">&H0000000F</span></span>|  
|<span data-ttu-id="3bbcd-134">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="3bbcd-134">`Integer`, `UInteger`</span></span>|<span data-ttu-id="3bbcd-135">31</span><span class="sxs-lookup"><span data-stu-id="3bbcd-135">31</span></span>|<span data-ttu-id="3bbcd-136">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="3bbcd-136">&H0000001F</span></span>|  
|<span data-ttu-id="3bbcd-137">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="3bbcd-137">`Long`, `ULong`</span></span>|<span data-ttu-id="3bbcd-138">63</span><span class="sxs-lookup"><span data-stu-id="3bbcd-138">63</span></span>|<span data-ttu-id="3bbcd-139">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="3bbcd-139">&H0000003F</span></span>|  
  
 <span data-ttu-id="3bbcd-140">Если `amount` равен нулю, значение `result` идентично значению `pattern` .</span><span class="sxs-lookup"><span data-stu-id="3bbcd-140">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="3bbcd-141">Если `amount` имеет отрицательное значение, оно принимается в качестве значения без знака и маскируется с соответствующей маской размера.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-141">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="3bbcd-142">Арифметические сдвиги никогда не создают исключений переполнения.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-142">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bbcd-143">`<<`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-143">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3bbcd-144">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-144">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="3bbcd-145">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-145">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bbcd-146">Пример</span><span class="sxs-lookup"><span data-stu-id="3bbcd-146">Example</span></span>  

 <span data-ttu-id="3bbcd-147">В следующем примере оператор используется `<<` для выполнения арифметических сдвигов влево по целочисленным значениям.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-147">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="3bbcd-148">Результат всегда имеет тот же тип данных, что и выражение, для которого выполняется сдвиг.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-148">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="3bbcd-149">Результаты предыдущего примера выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3bbcd-149">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="3bbcd-150">`result1` — 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-150">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="3bbcd-151">`result2` — 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-151">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="3bbcd-152">`result3` — 32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-152">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="3bbcd-153">`result4` — 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-153">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="3bbcd-154">`result5` равно 0 (смещено 15 позиций влево).</span><span class="sxs-lookup"><span data-stu-id="3bbcd-154">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="3bbcd-155">Сумма сдвига для `result4` вычисляется как 17 и 15, что равно 1.</span><span class="sxs-lookup"><span data-stu-id="3bbcd-155">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbcd-156">См. также</span><span class="sxs-lookup"><span data-stu-id="3bbcd-156">See also</span></span>

- [<span data-ttu-id="3bbcd-157">Операторы сдвига битов</span><span class="sxs-lookup"><span data-stu-id="3bbcd-157">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="3bbcd-158">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="3bbcd-158">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="3bbcd-159"> Оператор<<=</span><span class="sxs-lookup"><span data-stu-id="3bbcd-159"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="3bbcd-160">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3bbcd-160">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3bbcd-161">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="3bbcd-161">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3bbcd-162">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3bbcd-162">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
