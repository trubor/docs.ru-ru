---
description: 'Дополнительные сведения о предложении: Implements (Visual Basic)'
title: Предложение Implements
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 360d8812a7c49d6462818246b1448e171dcd597f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769004"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="85be4-103">Предложение Implements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85be4-103">Implements Clause (Visual Basic)</span></span>

<span data-ttu-id="85be4-104">Указывает, что член класса или структуры предоставляет реализацию для члена, определенного в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="85be4-104">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85be4-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="85be4-105">Remarks</span></span>  

<span data-ttu-id="85be4-106">`Implements`Ключевое слово не совпадает с [оператором Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="85be4-106">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="85be4-107">`Implements`Инструкция используется для указания того, что класс или структура реализует один или несколько интерфейсов, а затем для каждого элемента используется `Implements` ключевое слово для указания интерфейса и члена, который он реализует.</span><span class="sxs-lookup"><span data-stu-id="85be4-107">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="85be4-108">Если класс или структура реализует интерфейс, он должен включать `Implements` инструкцию сразу после оператора [Class](class-statement.md) или [Structure](structure-statement.md), и она должна реализовывать все члены, определенные интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="85be4-108">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="85be4-109">Воссоздании</span><span class="sxs-lookup"><span data-stu-id="85be4-109">Reimplementation</span></span>  

<span data-ttu-id="85be4-110">В производном классе можно повторно реализовать член интерфейса, который уже реализован в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="85be4-110">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="85be4-111">Это отличается от переопределения члена базового класса в следующих отношениях.</span><span class="sxs-lookup"><span data-stu-id="85be4-111">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="85be4-112">Член базового класса не обязательно должен быть [переопределяемым](../modifiers/overridable.md) для повторной реализации.</span><span class="sxs-lookup"><span data-stu-id="85be4-112">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="85be4-113">Элемент можно повторно реализовать с другим именем.</span><span class="sxs-lookup"><span data-stu-id="85be4-113">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="85be4-114">`Implements`Ключевое слово можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="85be4-114">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="85be4-115">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="85be4-115">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="85be4-116">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="85be4-116">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="85be4-117">Property Statement</span><span class="sxs-lookup"><span data-stu-id="85be4-117">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="85be4-118">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="85be4-118">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="85be4-119">См. также</span><span class="sxs-lookup"><span data-stu-id="85be4-119">See also</span></span>

- [<span data-ttu-id="85be4-120">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="85be4-120">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="85be4-121">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="85be4-121">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="85be4-122">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="85be4-122">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="85be4-123">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="85be4-123">Structure Statement</span></span>](structure-statement.md)
