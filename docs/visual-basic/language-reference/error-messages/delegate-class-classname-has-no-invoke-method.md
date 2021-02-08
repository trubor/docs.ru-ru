---
description: 'Дополнительные сведения о: BC30220: класс делегата " <classname> " не имеет метода Invoke, поэтому выражение этого типа не может быть целевым объектом вызова метода'
title: В делегируемом классе <classname> отсутствует метод Invoke, поэтому выражение этого типа не может быть вызвано посредством метода
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: c0d3f6e352a98e194b2c2ddca04bfa7254ec37a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796630"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="386fb-103">BC30220: класс делегата " \<classname> " не имеет метода Invoke, поэтому выражение этого типа не может быть целевым объектом вызова метода</span><span class="sxs-lookup"><span data-stu-id="386fb-103">BC30220: Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="386fb-104">Вызов `Invoke` через делегат завершился неудачей, поскольку `Invoke` не реализован в классе делегата.</span><span class="sxs-lookup"><span data-stu-id="386fb-104">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>

 <span data-ttu-id="386fb-105">**Идентификатор ошибки:** BC30220</span><span class="sxs-lookup"><span data-stu-id="386fb-105">**Error ID:** BC30220</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="386fb-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="386fb-106">To correct this error</span></span>

1. <span data-ttu-id="386fb-107">Убедитесь, что экземпляр класса делегата был создан с помощью `Dim` оператора и что процедура была назначена экземпляру делегата с помощью `AddressOf` оператора.</span><span class="sxs-lookup"><span data-stu-id="386fb-107">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>

2. <span data-ttu-id="386fb-108">Выберите код, реализующий класс делегата, и убедитесь, что он реализует `Invoke` процедуру.</span><span class="sxs-lookup"><span data-stu-id="386fb-108">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="386fb-109">См. также</span><span class="sxs-lookup"><span data-stu-id="386fb-109">See also</span></span>

- [<span data-ttu-id="386fb-110">Делегаты</span><span class="sxs-lookup"><span data-stu-id="386fb-110">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="386fb-111">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="386fb-111">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="386fb-112">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="386fb-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="386fb-113">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="386fb-113">Dim Statement</span></span>](../statements/dim-statement.md)
