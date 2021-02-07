---
description: 'Дополнительные сведения о: BC30149: <type1> " <typename> " должен реализовывать " <methodname> " для интерфейса "<interfacename>'
title: <type1>Тип <typename> должен реализовать <methodname> для интерфейса <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 34635cbe5b8736d273d5972a1bb83aa3d975490b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675017"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="41a8a-103">BC30149: \<type1> " \<typename> " должен реализовывать " \<methodname> " для интерфейса " \<interfacename> "</span><span class="sxs-lookup"><span data-stu-id="41a8a-103">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="41a8a-104">Класс или структура требует реализации интерфейса, но не реализует процедуру, определенную интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="41a8a-104">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="41a8a-105">Каждый член интерфейса должен быть реализован.</span><span class="sxs-lookup"><span data-stu-id="41a8a-105">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="41a8a-106">**Идентификатор ошибки:** BC30149</span><span class="sxs-lookup"><span data-stu-id="41a8a-106">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="41a8a-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="41a8a-107">To correct this error</span></span>

1. <span data-ttu-id="41a8a-108">Объявите процедуру с тем же именем и сигнатурой, как определено в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="41a8a-108">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="41a8a-109">Обязательно включите по крайней мере `End Function` оператор или `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="41a8a-109">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="41a8a-110">Добавьте `Implements` предложение в конец `Function` `Sub` оператора или.</span><span class="sxs-lookup"><span data-stu-id="41a8a-110">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="41a8a-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="41a8a-111">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="41a8a-112">См. также</span><span class="sxs-lookup"><span data-stu-id="41a8a-112">See also</span></span>

- [<span data-ttu-id="41a8a-113">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="41a8a-113">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="41a8a-114">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="41a8a-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
