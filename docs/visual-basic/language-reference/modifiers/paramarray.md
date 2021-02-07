---
description: 'Дополнительные сведения о: ParamArray (Visual Basic)'
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: 064bad8a558308ee3361c11d07020e0e3bf40c13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730399"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="70b17-103">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70b17-103">ParamArray (Visual Basic)</span></span>

<span data-ttu-id="70b17-104">Указывает, что параметр процедуры принимает необязательный массив элементов указанного типа.</span><span class="sxs-lookup"><span data-stu-id="70b17-104">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="70b17-105">`ParamArray` может использоваться только в последнем параметре списка параметров.</span><span class="sxs-lookup"><span data-stu-id="70b17-105">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70b17-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="70b17-106">Remarks</span></span>  

 <span data-ttu-id="70b17-107">`ParamArray` позволяет передавать процедуре произвольное число аргументов.</span><span class="sxs-lookup"><span data-stu-id="70b17-107">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="70b17-108">`ParamArray`Параметр всегда объявляется с помощью [ByVal](byval.md).</span><span class="sxs-lookup"><span data-stu-id="70b17-108">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="70b17-109">Можно указать один или несколько аргументов для параметра, `ParamArray` передав массив соответствующего типа данных, список значений с разделителями-запятыми или ничего вообще.</span><span class="sxs-lookup"><span data-stu-id="70b17-109">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="70b17-110">Дополнительные сведения см. в разделе «вызов ParamArray» в [массивах параметров](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="70b17-110">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="70b17-111">Всякий раз при работе с массивом, который может быть неограниченным большим, существует риск перегрузки внутренней емкости приложения.</span><span class="sxs-lookup"><span data-stu-id="70b17-111">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="70b17-112">Если вы принимаете массив параметров из вызывающего кода, следует проверить его длину и предпринять соответствующие шаги, если оно слишком велико для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="70b17-112">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="70b17-113">Модификатор `ParamArray` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="70b17-113">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="70b17-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="70b17-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="70b17-115">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="70b17-115">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="70b17-116">Property Statement</span><span class="sxs-lookup"><span data-stu-id="70b17-116">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="70b17-117">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="70b17-117">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="70b17-118">См. также</span><span class="sxs-lookup"><span data-stu-id="70b17-118">See also</span></span>

- [<span data-ttu-id="70b17-119">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="70b17-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="70b17-120">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="70b17-120">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
