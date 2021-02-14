---
description: Дополнительные сведения см. в разделе как передавать аргументы в процедуру (Visual Basic).
title: Практическое руководство. Передача аргументов в процедуру
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: e4dcdac19699c4b4b1f88327034a9e9d4364f040
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434333"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="92e8f-103">Практическое руководство. Передача аргументов в процедуру (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92e8f-103">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>

<span data-ttu-id="92e8f-104">При вызове процедуры необходимо следовать имени процедуры со списком аргументов в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="92e8f-104">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="92e8f-105">Укажите аргумент, соответствующий каждому обязательному параметру, определяемому процедурой, и при необходимости можно указать аргументы для `Optional` параметров.</span><span class="sxs-lookup"><span data-stu-id="92e8f-105">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="92e8f-106">Если `Optional` в вызове не указан параметр, необходимо включить запятую, чтобы пометить ее место в списке аргументов, если вы предоставляете последующие аргументы.</span><span class="sxs-lookup"><span data-stu-id="92e8f-106">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="92e8f-107">Если предполагается передать аргумент типа данных, отличный от того, который имеет соответствующий параметр, например, `Byte` `String` можно установить параметр проверки типов ([оператор Option строго](../../../language-reference/statements/option-strict-statement.md)) в значение `Off` .</span><span class="sxs-lookup"><span data-stu-id="92e8f-107">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="92e8f-108">Если `Option Strict` имеет значение `On` , необходимо использовать расширяющие преобразования или ключевые слова явного преобразования.</span><span class="sxs-lookup"><span data-stu-id="92e8f-108">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="92e8f-109">Дополнительные сведения см. в разделе [расширяющие и сужающие преобразования](../data-types/widening-and-narrowing-conversions.md) и [функции преобразования типов](../../../language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="92e8f-109">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="92e8f-110">Дополнительные сведения см. в разделе [Параметры и аргументы процедуры](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="92e8f-110">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="92e8f-111">Передача одного или нескольких аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="92e8f-111">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="92e8f-112">В операторе вызова используйте имя процедуры с круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="92e8f-112">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="92e8f-113">Внутри круглых скобок вставьте список аргументов.</span><span class="sxs-lookup"><span data-stu-id="92e8f-113">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="92e8f-114">Включите аргумент для каждого обязательного параметра, определяемого процедурой, и разделите аргументы запятыми.</span><span class="sxs-lookup"><span data-stu-id="92e8f-114">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="92e8f-115">Убедитесь, что каждый аргумент является допустимым выражением, результатом которого является тип данных, преобразуемый в тип, определяемый процедурой для соответствующего параметра.</span><span class="sxs-lookup"><span data-stu-id="92e8f-115">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="92e8f-116">Если параметр определен как [необязательный](../../../language-reference/modifiers/optional.md), его можно включить в список аргументов или опустить.</span><span class="sxs-lookup"><span data-stu-id="92e8f-116">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="92e8f-117">Если опустить его, процедура использует значение по умолчанию, определенное для этого параметра.</span><span class="sxs-lookup"><span data-stu-id="92e8f-117">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="92e8f-118">Если опустить аргумент для `Optional` параметра и в списке параметров есть другой параметр, можно пометить место пропущенного аргумента на дополнительную запятую в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="92e8f-118">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="92e8f-119">В следующем примере вызывается <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> функция Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="92e8f-119">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="92e8f-120">В предыдущем примере предоставляется обязательный первый аргумент, который представляет собой отображаемую строку сообщения.</span><span class="sxs-lookup"><span data-stu-id="92e8f-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="92e8f-121">Он опускает аргумент для необязательного второго параметра, который указывает кнопки, отображаемые в окне сообщения.</span><span class="sxs-lookup"><span data-stu-id="92e8f-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="92e8f-122">Поскольку вызов не предоставляет значение, `MsgBox` использует значение по умолчанию, `MsgBoxStyle.OKOnly` которое отображает только кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="92e8f-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="92e8f-123">Вторая запятая в списке аргументов отмечает место пропущенного второго аргумента, а последняя строка передается необязательному третьему параметру `MsgBox` , который является текстом, отображаемым в заголовке окна.</span><span class="sxs-lookup"><span data-stu-id="92e8f-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e8f-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="92e8f-124">See also</span></span>

- [<span data-ttu-id="92e8f-125">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="92e8f-125">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="92e8f-126">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="92e8f-126">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="92e8f-127">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="92e8f-127">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="92e8f-128">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="92e8f-128">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="92e8f-129">Практическое руководство. Определение параметра для процедуры</span><span class="sxs-lookup"><span data-stu-id="92e8f-129">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="92e8f-130">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="92e8f-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="92e8f-131">Рекурсивные процедуры</span><span class="sxs-lookup"><span data-stu-id="92e8f-131">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="92e8f-132">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="92e8f-132">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="92e8f-133">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="92e8f-133">Objects and Classes</span></span>](../objects-and-classes/index.md)
- <span data-ttu-id="92e8f-134">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md) (Объектно-ориентированное программирование на языке Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92e8f-134">[Object-Oriented Programming (Visual Basic)](../../concepts/object-oriented-programming.md)</span></span>
