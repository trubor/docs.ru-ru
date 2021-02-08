---
description: 'Дополнительные сведения о: BC31103: метод доступа get свойства " <propertyname> " недоступен'
title: Метод доступа Get свойства <propertyname> недоступен
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 3517bc7ec512ec99909539eb4d7cf3fafe9016fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796136"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="5c11e-103">BC31103: метод доступа get свойства " \<propertyname> " недоступен</span><span class="sxs-lookup"><span data-stu-id="5c11e-103">BC31103: 'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="5c11e-104">Оператор пытается получить значение свойства, если оно не имеет доступа к `Get` процедуре свойства.</span><span class="sxs-lookup"><span data-stu-id="5c11e-104">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>

 <span data-ttu-id="5c11e-105">Если [Инструкция Get](../statements/get-statement.md) помечена более ограниченным уровнем доступа, чем его [Инструкция Property](../statements/property-statement.md), попытка чтения значения свойства может завершиться ошибкой в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="5c11e-105">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>

- <span data-ttu-id="5c11e-106">`Get`Инструкция помечена как [закрытая](../modifiers/private.md) , а вызывающий код находится за пределами класса или структуры, в которой определено свойство.</span><span class="sxs-lookup"><span data-stu-id="5c11e-106">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="5c11e-107">`Get`Инструкция помечена как [protected](../modifiers/protected.md) и вызывающий код не находится в классе или структуре, в которой определено свойство, и в производном классе.</span><span class="sxs-lookup"><span data-stu-id="5c11e-107">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="5c11e-108">`Get`Инструкция помечена как [Friend](../modifiers/friend.md) , а вызывающий код — не в той сборке, в которой определено свойство.</span><span class="sxs-lookup"><span data-stu-id="5c11e-108">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="5c11e-109">**Идентификатор ошибки:** BC31103</span><span class="sxs-lookup"><span data-stu-id="5c11e-109">**Error ID:** BC31103</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5c11e-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="5c11e-110">To correct this error</span></span>

- <span data-ttu-id="5c11e-111">Если вы управляете исходным кодом, определяющим свойство, попробуйте объявить `Get` процедуру с тем же уровнем доступа, что и само свойство.</span><span class="sxs-lookup"><span data-stu-id="5c11e-111">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="5c11e-112">Если у вас нет контроля над исходным кодом, определяющим свойство, или необходимо ограничить `Get` уровень доступа к процедуре больше, чем само свойство, попробуйте переместить инструкцию, считывающую значение свойства, в область кода, имеющую Улучшенный доступ к свойству.</span><span class="sxs-lookup"><span data-stu-id="5c11e-112">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c11e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5c11e-113">See also</span></span>

- [<span data-ttu-id="5c11e-114">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="5c11e-114">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="5c11e-115">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="5c11e-115">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
