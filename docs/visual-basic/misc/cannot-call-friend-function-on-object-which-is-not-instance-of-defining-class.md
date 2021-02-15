---
description: 'Дополнительные сведения: невозможно вызвать дружественную функцию для объекта, который не является экземпляром определяющего класса'
title: Невозможно вызвать дружественную функцию для объекта, не являющегося экземпляром определяющего класса.
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: 612a169cf976881b82cb0bb0c44ac6c6e7f91755
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478702"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="d0eaf-103">Невозможно вызвать дружественную функцию для объекта, не являющегося экземпляром определяющего класса.</span><span class="sxs-lookup"><span data-stu-id="d0eaf-103">Cannot call friend function on object which is not an instance of defining class</span></span>

<span data-ttu-id="d0eaf-104">Предпринята попытка либо вызова процедуры `Friend` класса, либо получения доступа к дружественному ( `Friend` ) свойству или методу между процессами или между потоками.</span><span class="sxs-lookup"><span data-stu-id="d0eaf-104">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="d0eaf-105">Процедура `Friend` может вызываться из модуля вне класса, однако она является частью проекта, в котором определен класс.</span><span class="sxs-lookup"><span data-stu-id="d0eaf-105">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0eaf-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d0eaf-106">To correct this error</span></span>  
  
- <span data-ttu-id="d0eaf-107">Убедитесь, что вызов процедуры или доступ к процедуре выполняется из модуля, являющегося частью проекта, в котором определен класс.</span><span class="sxs-lookup"><span data-stu-id="d0eaf-107">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0eaf-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d0eaf-108">See also</span></span>

- [<span data-ttu-id="d0eaf-109">Friend</span><span class="sxs-lookup"><span data-stu-id="d0eaf-109">Friend</span></span>](../language-reference/modifiers/friend.md)
