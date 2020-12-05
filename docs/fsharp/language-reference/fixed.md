---
title: Ключевое слово fixed
description: 'Узнайте, как можно закрепить локальную систему в стеке, чтобы предотвратить сбор с помощью ключевого слова F # fixed.'
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740358"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="cd714-103">Ключевое слово fixed</span><span class="sxs-lookup"><span data-stu-id="cd714-103">The fixed keyword</span></span>

<span data-ttu-id="cd714-104">`fixed`Ключевое слово позволяет «закрепить» локальную систему в стеке, чтобы предотвратить их сбор или перемещение во время сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="cd714-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="cd714-105">Он используется для сценариев низкого уровня программирования.</span><span class="sxs-lookup"><span data-stu-id="cd714-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd714-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd714-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="cd714-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd714-107">Remarks</span></span>

<span data-ttu-id="cd714-108">Это расширяет синтаксис выражений, позволяя извлекать указатель и привязать его к имени, которое не может быть собрано или перемещено во время сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="cd714-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="cd714-109">Указатель из выражения фиксируется с помощью `fixed` ключевого слова и привязывается к идентификатору с помощью `use` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="cd714-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="cd714-110">Семантика этого объекта аналогична управлению ресурсами с помощью `use` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="cd714-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="cd714-111">Указатель фиксирован, пока находится в области видимости, и, когда он выходит за пределы области, он больше не является фиксированным.</span><span class="sxs-lookup"><span data-stu-id="cd714-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="cd714-112">`fixed` не может использоваться вне контекста `use` привязки.</span><span class="sxs-lookup"><span data-stu-id="cd714-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="cd714-113">Необходимо привязать указатель к имени с помощью `use` .</span><span class="sxs-lookup"><span data-stu-id="cd714-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="cd714-114">Использование метода `fixed` должно выполняться в выражении в функции или в методе.</span><span class="sxs-lookup"><span data-stu-id="cd714-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="cd714-115">Его нельзя использовать в области действия уровня скрипта или модуля.</span><span class="sxs-lookup"><span data-stu-id="cd714-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="cd714-116">Как и все коды указателей, это незащищенная функция, которая выдает предупреждение при использовании.</span><span class="sxs-lookup"><span data-stu-id="cd714-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="cd714-117">Пример</span><span class="sxs-lookup"><span data-stu-id="cd714-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="cd714-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cd714-118">See also</span></span>

- [<span data-ttu-id="cd714-119">Модуль NativePtr</span><span class="sxs-lookup"><span data-stu-id="cd714-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
