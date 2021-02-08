---
description: 'Дополнительные сведения о: BC32096: "For Each" в типе " <typename> " неоднозначно, так как тип реализует несколько экземпляров "System. Collections. Generic. IEnumerable" (Of T)'
title: Оператор For Each для типа <typename> неоднозначен, поскольку тип реализует несколько экземпляров System.Collections.Generic.IEnumerable (Of T)
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: c96bab40d4f7216f90368cf4c5526c7b4e5532f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796214"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="535cd-103">BC32096: "For Each" для типа " \<typename> " является неоднозначным, так как тип реализует несколько экземпляров "System. Collections. Generic. IEnumerable (Of T)"</span><span class="sxs-lookup"><span data-stu-id="535cd-103">BC32096: 'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="535cd-104">`For Each`Оператор указывает переменную-итератор, имеющую более одного <xref:System.Collections.IEnumerable.GetEnumerator%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="535cd-104">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>

 <span data-ttu-id="535cd-105">Переменная итератора должна иметь тип, реализующий <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> интерфейс или в одном из `Collections` пространств имен платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="535cd-105">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="535cd-106">Класс может реализовывать несколько сконструированных универсальных интерфейсов, используя разные аргументы типа для каждой конструкции.</span><span class="sxs-lookup"><span data-stu-id="535cd-106">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="535cd-107">Если класс, который выполняет это, используется для переменной-итератора, эта переменная имеет более одного <xref:System.Collections.IEnumerable.GetEnumerator%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="535cd-107">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="535cd-108">В этом случае Visual Basic не может выбрать метод для вызова.</span><span class="sxs-lookup"><span data-stu-id="535cd-108">In such a case, Visual Basic cannot choose which method to call.</span></span>

 <span data-ttu-id="535cd-109">**Идентификатор ошибки:** BC32096</span><span class="sxs-lookup"><span data-stu-id="535cd-109">**Error ID:** BC32096</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="535cd-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="535cd-110">To correct this error</span></span>

- <span data-ttu-id="535cd-111">Используйте [Оператор DirectCast](../operators/directcast-operator.md) или [Оператор TryCast](../operators/trycast-operator.md) для приведения типа переменной итератора к интерфейсу, определяющему <xref:System.Collections.IEnumerable.GetEnumerator%2A> метод, который вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="535cd-111">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>

## <a name="see-also"></a><span data-ttu-id="535cd-112">См. также</span><span class="sxs-lookup"><span data-stu-id="535cd-112">See also</span></span>

- [<span data-ttu-id="535cd-113">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="535cd-113">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="535cd-114">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="535cd-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
