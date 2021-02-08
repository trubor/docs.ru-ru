---
description: 'Дополнительные сведения о: BC31393: Expression имеет тип " <typename> ", который является ограниченным типом и не может использоваться для доступа к членам, унаследованным от "Object" или "ValueType"'
title: Выражение имеет тип <typename> который является ограниченным и не может использоваться для доступа к членам, унаследованным от Object или ValueType
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 3b5f9bbb85d1645936286ea0e907e3e25764f69a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796383"
---
# <a name="bc31393-expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="6541c-103">BC31393: выражение имеет тип " \<typename> ", который является ограниченным типом и не может использоваться для доступа к членам, унаследованным от "Object" или "ValueType"</span><span class="sxs-lookup"><span data-stu-id="6541c-103">BC31393: Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>

<span data-ttu-id="6541c-104">Выражение принимает тип, который не может быть упакован средой CLR, но обращается к члену, для которого требуется упаковка-преобразование.</span><span class="sxs-lookup"><span data-stu-id="6541c-104">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>

 <span data-ttu-id="6541c-105">*Упаковкой-преобразованием* называется обработка, необходимая для преобразования типа в `Object` или, в некоторых случаях, в <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6541c-105">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="6541c-106">Среда CLR не может быть Box для определенных типов структуры, например <xref:System.ArgIterator> , <xref:System.RuntimeArgumentHandle> и <xref:System.TypedReference> .</span><span class="sxs-lookup"><span data-stu-id="6541c-106">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>

 <span data-ttu-id="6541c-107">Это выражение пытается использовать ограниченный тип для вызова метода, унаследованного от <xref:System.Object> или <xref:System.ValueType> , например <xref:System.Object.GetHashCode%2A> или <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="6541c-107">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="6541c-108">Для доступа к этому методу Visual Basic предпринималась попытка неявного преобразования упаковки, которое вызывает эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="6541c-108">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>

 <span data-ttu-id="6541c-109">**Идентификатор ошибки:** BC31393</span><span class="sxs-lookup"><span data-stu-id="6541c-109">**Error ID:** BC31393</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6541c-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6541c-110">To correct this error</span></span>

1. <span data-ttu-id="6541c-111">Найдите выражение, которое оценивается в указанный тип.</span><span class="sxs-lookup"><span data-stu-id="6541c-111">Locate the expression that evaluates to the cited type.</span></span>

2. <span data-ttu-id="6541c-112">Находит часть инструкции, которая пытается вызвать метод, наследуемый от <xref:System.Object> или <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="6541c-112">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>

3. <span data-ttu-id="6541c-113">Перепишите инструкцию, чтобы избежать вызова метода.</span><span class="sxs-lookup"><span data-stu-id="6541c-113">Rewrite the statement to avoid the method call.</span></span>

## <a name="see-also"></a><span data-ttu-id="6541c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6541c-114">See also</span></span>

- [<span data-ttu-id="6541c-115">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="6541c-115">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
