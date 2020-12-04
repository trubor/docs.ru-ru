---
title: Выражение with в справочнике по C#
description: Сведения о выражении with, которое выполняет обратимое изменение записей C#
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: d7d3758c8c5da7859974b5b50b63d2a5ca16b24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702229"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="7f10f-103">Выражение with (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="7f10f-103">with expression (C# reference)</span></span>

<span data-ttu-id="7f10f-104">Выражение `with`, доступное в C# 9.0 и более поздних версиях, создает копию операнда [record](../../whats-new/csharp-9.md#record-types) с измененными заданными свойствами и полями:</span><span class="sxs-lookup"><span data-stu-id="7f10f-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="7f10f-105">Как показано в предыдущем примере, для указания элементов для изменения и их новых значений используется синтаксис [инициализатора объектов](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="7f10f-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="7f10f-106">В выражении `with` левый операнд должен иметь тип записи.</span><span class="sxs-lookup"><span data-stu-id="7f10f-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="7f10f-107">Результат выражения `with` имеет тот же тип среды выполнения, что и операнд выражения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="7f10f-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="7f10f-108">В случае с членом ссылочного типа при копировании записи копируется только ссылка на экземпляр.</span><span class="sxs-lookup"><span data-stu-id="7f10f-108">In the case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="7f10f-109">Как скопированный, так и исходный экземпляр записи имеют доступ к одному и тому же экземпляру ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="7f10f-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="7f10f-110">В следующем примере продемонстрировано такое поведение.</span><span class="sxs-lookup"><span data-stu-id="7f10f-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="7f10f-111">Любой тип записи имеет *конструктор копии*.</span><span class="sxs-lookup"><span data-stu-id="7f10f-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="7f10f-112">Это конструктор с одним параметром содержащего типа записи.</span><span class="sxs-lookup"><span data-stu-id="7f10f-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="7f10f-113">Он копирует состояние своего аргумента в новый экземпляр записи.</span><span class="sxs-lookup"><span data-stu-id="7f10f-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="7f10f-114">При вычислении выражения `with` вызывается конструктор копий для создания нового экземпляра записи на основе исходной записи.</span><span class="sxs-lookup"><span data-stu-id="7f10f-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="7f10f-115">После этого новый экземпляр обновляется в соответствии с указанными изменениями.</span><span class="sxs-lookup"><span data-stu-id="7f10f-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="7f10f-116">По умолчанию конструктор копий является неявным, то есть созданным компилятором.</span><span class="sxs-lookup"><span data-stu-id="7f10f-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="7f10f-117">Если необходимо настроить семантику копирования записей, явно объявите конструктор копии с требуемым поведением.</span><span class="sxs-lookup"><span data-stu-id="7f10f-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="7f10f-118">В следующем примере предыдущий пример обновляется явным образом с помощью конструктора копии.</span><span class="sxs-lookup"><span data-stu-id="7f10f-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="7f10f-119">Новое поведение копирования записи заключается в копировании элементов списка вместо ссылки на список:</span><span class="sxs-lookup"><span data-stu-id="7f10f-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="7f10f-120">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="7f10f-120">C# language specification</span></span>

<span data-ttu-id="7f10f-121">Дополнительные сведения см. в следующих разделах [примечания к предлагаемой функции записи](~/_csharplang/proposals/csharp-9.0/records.md):</span><span class="sxs-lookup"><span data-stu-id="7f10f-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="7f10f-122">Выражение `with`</span><span class="sxs-lookup"><span data-stu-id="7f10f-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="7f10f-123">Копирование и клонирование членов</span><span class="sxs-lookup"><span data-stu-id="7f10f-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="7f10f-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7f10f-124">See also</span></span>

- [<span data-ttu-id="7f10f-125">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="7f10f-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7f10f-126">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="7f10f-126">C# operators and expressions</span></span>](index.md)
