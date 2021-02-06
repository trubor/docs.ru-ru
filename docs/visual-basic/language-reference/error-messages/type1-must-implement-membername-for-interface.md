---
description: 'Дополнительные сведения о: BC30154: <type1> " <typename> " должен реализовывать " <membername> " для интерфейса "<interfacename>'
title: <type1>Тип <typename> должен реализовать <membername> для интерфейса <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: fc47aaef0477638e0e1a566bca23e9c35cf514f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641151"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="ec1a7-103">BC30154: \<type1> " \<typename> " должен реализовывать " \<membername> " для интерфейса " \<interfacename> "</span><span class="sxs-lookup"><span data-stu-id="ec1a7-103">BC30154: \<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="ec1a7-104">" \<typename> " должен реализовывать " \<membername> " для интерфейса " \<interfacename> ".</span><span class="sxs-lookup"><span data-stu-id="ec1a7-104">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="ec1a7-105">Реализация свойства должна иметь соответствующие описатели "ReadOnly"/"WriteOnly".</span><span class="sxs-lookup"><span data-stu-id="ec1a7-105">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>

 <span data-ttu-id="ec1a7-106">Класс или структура объявляет о необходимости реализации интерфейса, но не реализует процедуру, свойство или событие, определенные интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-106">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="ec1a7-107">Каждый член интерфейса должен быть реализован.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-107">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="ec1a7-108">**Идентификатор ошибки:** BC30154</span><span class="sxs-lookup"><span data-stu-id="ec1a7-108">**Error ID:** BC30154</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec1a7-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ec1a7-109">To correct this error</span></span>

1. <span data-ttu-id="ec1a7-110">Объявите член с таким же именем и сигнатурой, как определено в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-110">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="ec1a7-111">Обязательно включите по крайней мере `End Function` оператор, `End Sub` или `End Property` .</span><span class="sxs-lookup"><span data-stu-id="ec1a7-111">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>

2. <span data-ttu-id="ec1a7-112">Добавьте `Implements` предложение в конец `Function` оператора,, `Sub` `Property` или `Event` .</span><span class="sxs-lookup"><span data-stu-id="ec1a7-112">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="ec1a7-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="ec1a7-113">For example:</span></span>

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. <span data-ttu-id="ec1a7-114">При реализации свойства убедитесь, что `ReadOnly` или используется так `WriteOnly` же, как и в определении интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-114">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>

4. <span data-ttu-id="ec1a7-115">При реализации свойства, объявите `Get` и `Set` процедуры, если это уместно.</span><span class="sxs-lookup"><span data-stu-id="ec1a7-115">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec1a7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ec1a7-116">See also</span></span>

- [<span data-ttu-id="ec1a7-117">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="ec1a7-117">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="ec1a7-118">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ec1a7-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
