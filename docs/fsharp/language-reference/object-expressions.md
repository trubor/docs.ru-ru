---
title: Выражения объекта
description: 'Узнайте, как использовать выражения объекта F #, если нужно избежать дополнительного кода и издержек, необходимых для создания нового именованного типа.'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740306"
---
# <a name="object-expressions"></a><span data-ttu-id="9d37f-103">Выражения объекта</span><span class="sxs-lookup"><span data-stu-id="9d37f-103">Object Expressions</span></span>

<span data-ttu-id="9d37f-104">*Выражение объекта* — это выражение, которое создает новый экземпляр динамически созданного анонимного типа объекта, основанного на существующем базовом типе, интерфейсе или наборе интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="9d37f-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d37f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d37f-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="9d37f-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="9d37f-106">Remarks</span></span>

<span data-ttu-id="9d37f-107">В предыдущем синтаксисе *TypeName* представляет существующий тип класса или тип интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9d37f-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="9d37f-108">*type-params* описывает необязательные параметры универсального типа.</span><span class="sxs-lookup"><span data-stu-id="9d37f-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="9d37f-109">*Аргументы* используются только для типов классов, для которых требуются параметры конструктора.</span><span class="sxs-lookup"><span data-stu-id="9d37f-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="9d37f-110">*Определения членов* — это переопределения методов базового класса или реализации абстрактных методов из базового класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9d37f-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="9d37f-111">В следующем примере показаны несколько различных типов выражений объекта.</span><span class="sxs-lookup"><span data-stu-id="9d37f-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="9d37f-112">Использование выражений объектов</span><span class="sxs-lookup"><span data-stu-id="9d37f-112">Using Object Expressions</span></span>

<span data-ttu-id="9d37f-113">Выражения объектов используются, если нужно избежать дополнительного кода и издержек, необходимых для создания нового именованного типа.</span><span class="sxs-lookup"><span data-stu-id="9d37f-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="9d37f-114">При использовании выражений объектов для уменьшения числа типов, созданных в программе, можно уменьшить число строк кода и предотвратить ненужные возможности распространения типов.</span><span class="sxs-lookup"><span data-stu-id="9d37f-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="9d37f-115">Вместо того чтобы создавать много типов только для обработки конкретных ситуаций, можно использовать объектное выражение, которое настраивает существующий тип или предоставляет соответствующую реализацию интерфейса для конкретного случая.</span><span class="sxs-lookup"><span data-stu-id="9d37f-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d37f-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9d37f-116">See also</span></span>

- [<span data-ttu-id="9d37f-117">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="9d37f-117">F# Language Reference</span></span>](index.md)
