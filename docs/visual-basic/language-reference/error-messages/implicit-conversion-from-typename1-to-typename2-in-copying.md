---
description: 'Дополнительные сведения о: BC41999: неявное преобразование из " <typename1> " в " <typename2> " при копировании значения параметра "ByRef" "" <parametername> обратно в соответствующий аргумент.'
title: Неявное приведение <typename1> к <typename2> при копировании значения параметра <parametername>, объявленного как ByRef, обратно в соответствующий аргумент.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: debe9d248a41d1b5c1f541392a1846b8598c126f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796084"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="58718-103">BC41999: неявное преобразование из " \<typename1> " в " \<typename2> " при копировании значения параметра "ByRef" " \<parametername> " обратно в соответствующий аргумент.</span><span class="sxs-lookup"><span data-stu-id="58718-103">BC41999: Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>

<span data-ttu-id="58718-104">Процедура вызывается с аргументом [ByRef](../modifiers/byref.md) , отличным от типа соответствующего параметра.</span><span class="sxs-lookup"><span data-stu-id="58718-104">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>

 <span data-ttu-id="58718-105">При передаче аргумента `ByRef` Visual Basic иногда копирует значение аргумента в локальную переменную в процедуре вместо передачи ссылки.</span><span class="sxs-lookup"><span data-stu-id="58718-105">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="58718-106">В этом случае, когда процедура возвращает, Visual Basic необходимо скопировать значение локальной переменной обратно в аргумент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="58718-106">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="58718-107">Если значение аргумента `ByRef` копируется в процедуру, а аргумент и параметр имеют один и тот же тип, то преобразование не требуется.</span><span class="sxs-lookup"><span data-stu-id="58718-107">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="58718-108">Но если типы различаются, Visual Basic должны быть преобразованы в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="58718-108">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="58718-109">Поскольку нельзя использовать `CType` или любые другие ключевые слова преобразования в аргументе или параметре процедуры, такое преобразование всегда является неявным.</span><span class="sxs-lookup"><span data-stu-id="58718-109">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>

 <span data-ttu-id="58718-110">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="58718-110">By default, this message is a warning.</span></span> <span data-ttu-id="58718-111">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="58718-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="58718-112">**Идентификатор ошибки:** BC41999</span><span class="sxs-lookup"><span data-stu-id="58718-112">**Error ID:** BC41999</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="58718-113">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="58718-113">To correct this error</span></span>

- <span data-ttu-id="58718-114">По возможности используйте аргумент вызова того же типа, что и параметр процедуры, поэтому Visual Basic не требуется выполнять преобразование.</span><span class="sxs-lookup"><span data-stu-id="58718-114">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="58718-115">Если необходимо вызвать процедуру с аргументом, тип которого отличается от типа параметра, но не требуется возвращать значение в аргумент вызова, то определите параметр как [ByVal](../modifiers/byval.md) , а не `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="58718-115">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

## <a name="see-also"></a><span data-ttu-id="58718-116">См. также</span><span class="sxs-lookup"><span data-stu-id="58718-116">See also</span></span>

- [<span data-ttu-id="58718-117">Процедуры</span><span class="sxs-lookup"><span data-stu-id="58718-117">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="58718-118">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="58718-118">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="58718-119">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="58718-119">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="58718-120">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="58718-120">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
