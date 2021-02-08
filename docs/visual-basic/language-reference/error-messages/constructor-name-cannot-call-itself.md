---
description: 'Дополнительные сведения о: BC30298: конструктор " <name> " не может вызвать сам себя'
title: Конструктор <name> не может вызывать сам себя
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 486495eb822e3e3008382232091fe3923851f97c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796721"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a><span data-ttu-id="07a35-103">BC30298: конструктор " \<name> " не может вызвать сам себя</span><span class="sxs-lookup"><span data-stu-id="07a35-103">BC30298: Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="07a35-104">`Sub New`Процедура в классе или структуре вызывает саму себя.</span><span class="sxs-lookup"><span data-stu-id="07a35-104">A `Sub New` procedure in a class or structure calls itself.</span></span>

 <span data-ttu-id="07a35-105">Назначение конструктора заключается в инициализации экземпляра класса или структуры при первом создании.</span><span class="sxs-lookup"><span data-stu-id="07a35-105">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="07a35-106">Класс или структура может иметь несколько конструкторов, при условии, что все они имеют разные списки параметров.</span><span class="sxs-lookup"><span data-stu-id="07a35-106">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="07a35-107">Конструктору разрешено вызывать другой конструктор для выполнения его функциональных возможностей в дополнение к собственным.</span><span class="sxs-lookup"><span data-stu-id="07a35-107">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="07a35-108">Однако конструктор не имеет смысла вызывать сам себя, и на самом деле это может привести к бесконечной рекурсии, если это разрешено.</span><span class="sxs-lookup"><span data-stu-id="07a35-108">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>

 <span data-ttu-id="07a35-109">**Идентификатор ошибки:** BC30298</span><span class="sxs-lookup"><span data-stu-id="07a35-109">**Error ID:** BC30298</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="07a35-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="07a35-110">To correct this error</span></span>

1. <span data-ttu-id="07a35-111">Проверьте список параметров вызываемого конструктора.</span><span class="sxs-lookup"><span data-stu-id="07a35-111">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="07a35-112">Он должен отличаться от конструктора, выполняющего вызов.</span><span class="sxs-lookup"><span data-stu-id="07a35-112">It should be different from that of the constructor making the call.</span></span>

2. <span data-ttu-id="07a35-113">Если вы не планируете вызывать другой конструктор, удалите `Sub New` вызов полностью.</span><span class="sxs-lookup"><span data-stu-id="07a35-113">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>

## <a name="see-also"></a><span data-ttu-id="07a35-114">См. также</span><span class="sxs-lookup"><span data-stu-id="07a35-114">See also</span></span>

- [<span data-ttu-id="07a35-115">Время существования: создание и уничтожение объектов</span><span class="sxs-lookup"><span data-stu-id="07a35-115">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
