---
description: 'Дополнительные сведения о: Аргумент NPer должен быть больше нуля'
title: Аргумент NPer должен быть больше нуля
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: ece5e775e2f05f757b2af53594c626f5a023161e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433412"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="10926-103">Аргумент NPer должен быть больше нуля</span><span class="sxs-lookup"><span data-stu-id="10926-103">Argument 'NPer' must be greater than zero</span></span>

<span data-ttu-id="10926-104">Функция `NPer` , которая возвращает значение `Double` , определяющее количество периодов для ежегодного дохода на основе периодических фиксированных выплат и фиксированной процентной ставки, требует аргумент, значение которого больше нуля.</span><span class="sxs-lookup"><span data-stu-id="10926-104">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10926-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="10926-105">To correct this error</span></span>  
  
- <span data-ttu-id="10926-106">Проверьте правильность написания аргументов в выражении.</span><span class="sxs-lookup"><span data-stu-id="10926-106">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="10926-107">Неправильно написанное имя переменной может привести к неявному созданию числовой переменной, которая инициализируется нулевым значением.</span><span class="sxs-lookup"><span data-stu-id="10926-107">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="10926-108">Проверьте предыдущие операции с переменными в выражении, в особенности те, которые передавались в процедуру как аргументы из других процедур.</span><span class="sxs-lookup"><span data-stu-id="10926-108">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10926-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="10926-109">See also</span></span>

- [<span data-ttu-id="10926-110">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="10926-110">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
