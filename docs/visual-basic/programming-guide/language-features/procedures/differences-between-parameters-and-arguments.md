---
description: Дополнительные сведения см. в статье различия между параметрами и аргументами (Visual Basic)
title: Различия между параметрами и аргументами
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: 01efc7dc3f451d6aae20cfd091355f531af4431c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438766"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="0c9e8-103">Различия между параметрами и аргументами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9e8-103">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="0c9e8-104">В большинстве случаев процедура должна иметь некоторую информацию о обстоятельствах, в которых она была вызвана.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-104">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="0c9e8-105">Процедура, выполняющая повторяющиеся или общие задачи, использует разные сведения для каждого вызова.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="0c9e8-106">Эти сведения состоят из переменных, констант и выражений, которые передаются в процедуру при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="0c9e8-107">Чтобы передать эти сведения в процедуру, процедура определяет *параметр*, а вызывающий код передает *аргумент* в этот параметр.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-107">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="0c9e8-108">Параметр можно представить как место парковки, а аргумент — как автомобиль.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-108">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="0c9e8-109">Так же, как различные функции автомобильной связи могут приостановиться в пространстве стоянки в разное время, вызывающий код может передать другой аргумент одному параметру при каждом вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-109">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="0c9e8-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c9e8-110">Parameters</span></span>  

 <span data-ttu-id="0c9e8-111">*Параметр* представляет значение, которое процедура предполагает передать при ее вызове.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-111">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="0c9e8-112">В объявлении процедуры определяются ее параметры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-112">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="0c9e8-113">При определении `Function` `Sub` процедуры или необходимо указать *список параметров* в круглых скобках сразу после имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-113">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="0c9e8-114">Для каждого параметра указывается имя, тип данных и механизм передачи ([ByVal](../../../language-reference/modifiers/byval.md) или [ByRef](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="0c9e8-114">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="0c9e8-115">Можно также указать, что параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-115">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="0c9e8-116">Это означает, что вызывающему коду не обязательно передавать значение для него.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-116">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="0c9e8-117">Имя каждого параметра служит в качестве *локальной переменной* в процедуре.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-117">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="0c9e8-118">Имя параметра можно использовать так же, как и любую другую переменную.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-118">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="0c9e8-119">Аргументы</span><span class="sxs-lookup"><span data-stu-id="0c9e8-119">Arguments</span></span>  

 <span data-ttu-id="0c9e8-120">*Аргумент* представляет значение, которое передается в параметр процедуры при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-120">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="0c9e8-121">Вызывающий код предоставляет аргументы при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-121">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="0c9e8-122">При вызове `Function` процедуры или `Sub` вы включаете *список аргументов* в круглые скобки сразу после имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-122">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="0c9e8-123">Каждый аргумент соответствует параметру в том же положении в списке.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-123">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="0c9e8-124">В отличие от определения параметра, аргументы не имеют имен.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-124">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="0c9e8-125">Каждый аргумент является выражением, которое может содержать ноль или более переменных, констант и литералов.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-125">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="0c9e8-126">Тип данных вычисляемого выражения обычно должен соответствовать типу данных, определенному для соответствующего параметра, и в любом случае он должен быть преобразован в тип параметра.</span><span class="sxs-lookup"><span data-stu-id="0c9e8-126">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9e8-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0c9e8-127">See also</span></span>

- [<span data-ttu-id="0c9e8-128">Процедуры</span><span class="sxs-lookup"><span data-stu-id="0c9e8-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0c9e8-129">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="0c9e8-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0c9e8-130">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="0c9e8-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0c9e8-131">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="0c9e8-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0c9e8-132">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="0c9e8-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0c9e8-133">Практическое руководство. Определение параметра для процедуры</span><span class="sxs-lookup"><span data-stu-id="0c9e8-133">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="0c9e8-134">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="0c9e8-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="0c9e8-135">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="0c9e8-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0c9e8-136">Рекурсивные процедуры</span><span class="sxs-lookup"><span data-stu-id="0c9e8-136">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="0c9e8-137">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="0c9e8-137">Procedure Overloading</span></span>](./procedure-overloading.md)
