---
description: 'Дополнительные сведения о: BC30149: <type1> " <typename> " должен реализовывать " <methodname> " для интерфейса " <interfacename> "'
title: <type1>Тип <typename> должен реализовать <methodname> для интерфейса <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: b2fb7f5ea019a86b18ea89456e353778e5246d2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473441"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="efb13-103">BC30149: \<type1> " \<typename> " должен реализовывать " \<methodname> " для интерфейса " \<interfacename> "</span><span class="sxs-lookup"><span data-stu-id="efb13-103">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="efb13-104">Класс или структура требует реализации интерфейса, но не реализует процедуру, определенную интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="efb13-104">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="efb13-105">Каждый член интерфейса должен быть реализован.</span><span class="sxs-lookup"><span data-stu-id="efb13-105">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="efb13-106">**Идентификатор ошибки:** BC30149</span><span class="sxs-lookup"><span data-stu-id="efb13-106">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="efb13-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="efb13-107">To correct this error</span></span>

1. <span data-ttu-id="efb13-108">Объявите процедуру с тем же именем и сигнатурой, как определено в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="efb13-108">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="efb13-109">Обязательно включите по крайней мере `End Function` оператор или `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="efb13-109">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="efb13-110">Добавьте `Implements` предложение в конец `Function` `Sub` оператора или.</span><span class="sxs-lookup"><span data-stu-id="efb13-110">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="efb13-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="efb13-111">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="efb13-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="efb13-112">See also</span></span>

- [<span data-ttu-id="efb13-113">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="efb13-113">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="efb13-114">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="efb13-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
