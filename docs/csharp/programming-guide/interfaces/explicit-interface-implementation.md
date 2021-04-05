---
title: Руководство по программированию на C#. Явная реализация интерфейса
description: Класс может реализовывать интерфейсы, которые содержат член с такой же сигнатурой в C#. Явная реализация создает член класса, относящийся к одному интерфейсу.
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610867"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="cd33c-104">Явная реализация интерфейса (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="cd33c-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="cd33c-105">Если [класс](../../language-reference/keywords/class.md) реализует два интерфейса, содержащих член с одинаковой сигнатурой, при реализации такого члена в классе оба интерфейса будут использовать этот член в качестве собственной реализации.</span><span class="sxs-lookup"><span data-stu-id="cd33c-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="cd33c-106">В следующем примере все вызовы `Paint` приводят к вызову одного и того же метода.</span><span class="sxs-lookup"><span data-stu-id="cd33c-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="cd33c-107">Первый пример определяет типы:</span><span class="sxs-lookup"><span data-stu-id="cd33c-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="cd33c-108">Следующий пример вызывает методы:</span><span class="sxs-lookup"><span data-stu-id="cd33c-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="cd33c-109">Но может потребоваться, чтобы одна и та же реализация вызывалась для обоих интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="cd33c-109">But you might not want the same implementation to be called for both interfaces.</span></span> <span data-ttu-id="cd33c-110">Чтобы вызывать разную реализацию в зависимости от используемого интерфейса, можно явно реализовать член интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-110">To call a different implementation depending on which interface is in use, you can implement an interface member explicitly.</span></span> <span data-ttu-id="cd33c-111">Явная реализация интерфейса — это член класса, который вызывается только через указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="cd33c-111">An explicit interface implementation is a class member that is only called through the specified interface.</span></span> <span data-ttu-id="cd33c-112">Укажите имя интерфейса и точку в качестве префикса в имени члена класса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-112">Name the class member by prefixing it with the name of the interface and a period.</span></span> <span data-ttu-id="cd33c-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="cd33c-113">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="cd33c-114">Член класса `IControl.Paint` доступен только через интерфейс `IControl`, а `ISurface.Paint` — только через интерфейс `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="cd33c-114">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="cd33c-115">Обе реализации метода будут разделены, и ни одна из них не будет доступна в классе напрямую.</span><span class="sxs-lookup"><span data-stu-id="cd33c-115">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="cd33c-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="cd33c-116">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="cd33c-117">Явная реализация также применяется в случаях, когда в каждом из двух интерфейсов объявляются разные члены (например, свойство и метод) с одинаковыми именами.</span><span class="sxs-lookup"><span data-stu-id="cd33c-117">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="cd33c-118">Чтобы реализовать оба интерфейса и избежать ошибок компилятора, класс должен использовать явную реализацию либо свойства `P`, либо метода `P`, либо одновременно обоих этих членов.</span><span class="sxs-lookup"><span data-stu-id="cd33c-118">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="cd33c-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="cd33c-119">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="cd33c-120">Явная реализация интерфейса не имеет модификатора доступа, так как она недоступна в качестве члена типа, в котором определена.</span><span class="sxs-lookup"><span data-stu-id="cd33c-120">An explicit interface implementation doesn't have an access modifier since it isn't accessible as a member of the type it's defined in.</span></span> <span data-ttu-id="cd33c-121">Вместо этого она доступна только при вызове через экземпляр интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-121">Instead, it's only accessible when called through an instance of the interface.</span></span> <span data-ttu-id="cd33c-122">При указании модификатора доступа для явной реализации интерфейса возникает ошибка компилятора [CS0106](../../language-reference/compiler-messages/cs0106.md).</span><span class="sxs-lookup"><span data-stu-id="cd33c-122">If you specify an access modifier for an explicit interface implementation, you get compiler error [CS0106](../../language-reference/compiler-messages/cs0106.md).</span></span> <span data-ttu-id="cd33c-123">Дополнительные сведения см. в разделе [`interface` (справочник по C#)](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="cd33c-123">For more information, see [`interface` (C# Reference)](../../language-reference/keywords/interface.md).</span></span>

<span data-ttu-id="cd33c-124">Начиная с версии [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), вы можете определять реализацию для членов, объявленных в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="cd33c-124">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="cd33c-125">Если класс наследует реализацию метода от интерфейса, этот метод доступен только через ссылку типа интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-125">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="cd33c-126">Наследуемый член не отображается как часть открытого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-126">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="cd33c-127">Следующий пример определяет реализацию по умолчанию для метода интерфейса:</span><span class="sxs-lookup"><span data-stu-id="cd33c-127">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="cd33c-128">Следующий пример вызывает реализацию по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="cd33c-128">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="cd33c-129">Любой класс, реализующий интерфейс `IControl`, может переопределить метод `Paint` по умолчанию либо в качестве открытого метода, либо в качестве реализации интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd33c-129">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd33c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="cd33c-130">See also</span></span>

- [<span data-ttu-id="cd33c-131">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="cd33c-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd33c-132">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="cd33c-132">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="cd33c-133">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="cd33c-133">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="cd33c-134">Наследование</span><span class="sxs-lookup"><span data-stu-id="cd33c-134">Inheritance</span></span>](../classes-and-structs/inheritance.md)
