---
description: 'Дополнительные сведения о: BC42107: свойство " <propertyname> " не возвращает значение для всех ветвей кода'
title: Свойство ''<propertyname>'' возвращает значение не для всех ветвей кода
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 9aa0d6fea1feeaf7503f5f8831fbd3de910a4822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774893"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="47c57-103">BC42107: свойство " \<propertyname> " не возвращает значение для всех ветвей кода</span><span class="sxs-lookup"><span data-stu-id="47c57-103">BC42107: Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="47c57-104">Свойство " \<propertyname> " не возвращает значение для всех ветвей кода.</span><span class="sxs-lookup"><span data-stu-id="47c57-104">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="47c57-105">Во время выполнения может возникнуть исключение, связанное с пустой ссылкой, когда используется результат.</span><span class="sxs-lookup"><span data-stu-id="47c57-105">A null reference exception could occur at run time when the result is used.</span></span>

<span data-ttu-id="47c57-106">Процедура свойства `Get` имеет по крайней мере один возможный путь в коде, который не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="47c57-106">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="47c57-107">Получить значение из процедуры свойства можно `Get` одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="47c57-107">You can return a value from a property `Get` procedure in any of the following ways:</span></span>

- <span data-ttu-id="47c57-108">Присвойте значение имени свойства, а затем выполните `Exit Property` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="47c57-108">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>

- <span data-ttu-id="47c57-109">Присвойте значение имени свойства, а затем выполните `End Get` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="47c57-109">Assign the value to the property name and then perform the `End Get` statement.</span></span>

- <span data-ttu-id="47c57-110">Включите значение в [оператор return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47c57-110">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

<span data-ttu-id="47c57-111">Если элемент управления передается в `Exit Property` или `End Get` и вы не присвоили какое бы то ни было значение имени свойства, `Get` процедура возвращает значение по умолчанию для типа данных свойства.</span><span class="sxs-lookup"><span data-stu-id="47c57-111">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="47c57-112">Дополнительные сведения см. в разделе «поведение» в [операторе Function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47c57-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

<span data-ttu-id="47c57-113">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="47c57-113">By default, this message is a warning.</span></span> <span data-ttu-id="47c57-114">Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="47c57-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="47c57-115">**Идентификатор ошибки:** BC42107</span><span class="sxs-lookup"><span data-stu-id="47c57-115">**Error ID:** BC42107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="47c57-116">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="47c57-116">To correct this error</span></span>

- <span data-ttu-id="47c57-117">Проверьте логику потока управления и убедитесь, что значение присваивается перед каждой инструкцией, которая вызывает возврат.</span><span class="sxs-lookup"><span data-stu-id="47c57-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

  <span data-ttu-id="47c57-118">Проще гарантировать, что каждый возврат из процедуры возвращает значение, если всегда используется `Return` оператор.</span><span class="sxs-lookup"><span data-stu-id="47c57-118">It's easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="47c57-119">В этом случае последняя инструкция `End Get` должна быть `Return` оператором.</span><span class="sxs-lookup"><span data-stu-id="47c57-119">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="47c57-120">См. также</span><span class="sxs-lookup"><span data-stu-id="47c57-120">See also</span></span>

- [<span data-ttu-id="47c57-121">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="47c57-121">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="47c57-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="47c57-122">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="47c57-123">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="47c57-123">Get Statement</span></span>](../statements/get-statement.md)
