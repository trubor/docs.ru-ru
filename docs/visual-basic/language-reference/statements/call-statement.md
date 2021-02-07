---
description: 'Дополнительные сведения о вызываемом операторе: Call (Visual Basic)'
title: Оператор Call
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 70e6c109621c3710ad9476a952e9c384a142ba3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674016"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="c402b-103">Оператор Call (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c402b-103">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="c402b-104">Передает управление в `Function` процедуру, `Sub` или в библиотеку динамической КОМПОНОВКИ (DLL).</span><span class="sxs-lookup"><span data-stu-id="c402b-104">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c402b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c402b-105">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c402b-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="c402b-106">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="c402b-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c402b-107">Required.</span></span> <span data-ttu-id="c402b-108">Имя вызываемой процедуры.</span><span class="sxs-lookup"><span data-stu-id="c402b-108">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="c402b-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c402b-109">Optional.</span></span> <span data-ttu-id="c402b-110">Список переменных или выражений, представляющих аргументы, которые передаются в процедуру при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="c402b-110">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="c402b-111">Несколько аргументов разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="c402b-111">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="c402b-112">Если включить `argumentList` , необходимо заключить его в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="c402b-112">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="c402b-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c402b-113">Remarks</span></span>

 <span data-ttu-id="c402b-114">`Call`При вызове процедуры можно использовать ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="c402b-114">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="c402b-115">Для большинства вызовов процедур использовать это ключевое слово не обязательно.</span><span class="sxs-lookup"><span data-stu-id="c402b-115">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="c402b-116">Обычно используется `Call` ключевое слово, если вызванное выражение не начинается с идентификатора.</span><span class="sxs-lookup"><span data-stu-id="c402b-116">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="c402b-117">Использование `Call` ключевого слова для других целей не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c402b-117">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="c402b-118">Если процедура возвращает значение, `Call` инструкция отклоняет ее.</span><span class="sxs-lookup"><span data-stu-id="c402b-118">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="c402b-119">Пример</span><span class="sxs-lookup"><span data-stu-id="c402b-119">Example</span></span>

 <span data-ttu-id="c402b-120">В следующем коде показаны два примера, где `Call` ключевое слово требуется для вызова процедуры.</span><span class="sxs-lookup"><span data-stu-id="c402b-120">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="c402b-121">В обоих примерах вызванное выражение не начинается с идентификатора.</span><span class="sxs-lookup"><span data-stu-id="c402b-121">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="c402b-122">См. также</span><span class="sxs-lookup"><span data-stu-id="c402b-122">See also</span></span>

- [<span data-ttu-id="c402b-123">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c402b-123">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="c402b-124">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c402b-124">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c402b-125">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c402b-125">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="c402b-126">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="c402b-126">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
