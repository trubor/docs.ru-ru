---
description: 'Дополнительные сведения о: BC36564: аргументы типа не могут быть выведены из делегата'
title: Аргументы типа не могут быть выведены от делегата
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1a83ee64df4523cee87d0d677ddafaeadfe5543d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666268"
---
# <a name="bc36564-type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="7a2b3-103">BC36564: аргументы типа не могут быть выведены из делегата</span><span class="sxs-lookup"><span data-stu-id="7a2b3-103">BC36564: Type arguments could not be inferred from the delegate</span></span>

<span data-ttu-id="7a2b3-104">Оператор назначения использует `AddressOf` для назначения делегату адреса универсальной процедуры, но он не предоставляет универсальной процедуре никакие аргументы типа.</span><span class="sxs-lookup"><span data-stu-id="7a2b3-104">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>

 <span data-ttu-id="7a2b3-105">Как правило, при вызове универсального типа указывается аргумент типа для каждого параметра типа, определяемого этим универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="7a2b3-105">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="7a2b3-106">Если вы не предоставляете никакие аргументы типов, компилятор пытается вывести типы, которые должны быть переданы в параметры типов.</span><span class="sxs-lookup"><span data-stu-id="7a2b3-106">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="7a2b3-107">Если контекст не предоставляет достаточно сведений, чтобы компилятор мог вывести типы, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="7a2b3-107">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>

 <span data-ttu-id="7a2b3-108">**Идентификатор ошибки:** BC36564</span><span class="sxs-lookup"><span data-stu-id="7a2b3-108">**Error ID:** BC36564</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7a2b3-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="7a2b3-109">To correct this error</span></span>

- <span data-ttu-id="7a2b3-110">Укажите аргументы типа для универсальной процедуры в выражении `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="7a2b3-110">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a2b3-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7a2b3-111">See also</span></span>

- [<span data-ttu-id="7a2b3-112">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a2b3-112">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7a2b3-113">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="7a2b3-113">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="7a2b3-114">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a2b3-114">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="7a2b3-115">Type List</span><span class="sxs-lookup"><span data-stu-id="7a2b3-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="7a2b3-116">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="7a2b3-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
