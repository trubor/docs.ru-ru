---
description: 'Дополнительные сведения: User-Defined тип данных'
title: Тип данных, определенный пользователем
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 6eb94b38e2d29a4bbdfcf94de307bbe07a2c1b0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774971"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="cfc7b-103">Тип данных, определенный пользователем</span><span class="sxs-lookup"><span data-stu-id="cfc7b-103">User-Defined Data Type</span></span>

<span data-ttu-id="cfc7b-104">Хранит данные в определенном формате.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-104">Holds data in a format you define.</span></span> <span data-ttu-id="cfc7b-105">`Structure`Оператор определяет формат.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-105">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="cfc7b-106">Предыдущие версии Visual Basic поддерживают определяемый пользователем тип (UDT).</span><span class="sxs-lookup"><span data-stu-id="cfc7b-106">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="cfc7b-107">Текущая версия расширяет определяемый пользователем тип на *структуру*.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-107">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="cfc7b-108">Структура — это объединение одного или нескольких *элементов* различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-108">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="cfc7b-109">Visual Basic обрабатывает структуру как единое целое, хотя вы также можете обращаться к ее членам по отдельности.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-109">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfc7b-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="cfc7b-110">Remarks</span></span>

<span data-ttu-id="cfc7b-111">Определяйте и используйте тип данных Structure, если необходимо объединить различные типы данных в один блок или если ни один из простейших типов данных не подходит для ваших нужд.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-111">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="cfc7b-112">Значение по умолчанию для типа данных Structure состоит из сочетания значений по умолчанию для каждого из его элементов.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-112">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="cfc7b-113">Формат объявления</span><span class="sxs-lookup"><span data-stu-id="cfc7b-113">Declaration Format</span></span>

<span data-ttu-id="cfc7b-114">Объявление структуры начинается с [оператора Structure](../statements/structure-statement.md) и заканчивается `End Structure` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-114">A structure declaration starts with the [Structure Statement](../statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="cfc7b-115">`Structure`Инструкция предоставляет имя структуры, которая также является идентификатором типа данных, определяемого структурой.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-115">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="cfc7b-116">Другие части кода могут использовать этот идентификатор для объявления переменных, параметров и возвращаемых значений функций в качестве типа данных этой структуры.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-116">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="cfc7b-117">Объявления между `Structure` `End Structure` операторами и определяют элементы структуры.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-117">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="cfc7b-118">Уровни доступа к членам</span><span class="sxs-lookup"><span data-stu-id="cfc7b-118">Member Access Levels</span></span>

<span data-ttu-id="cfc7b-119">Каждый член необходимо объявить с помощью [оператора Dim](../statements/dim-statement.md) или оператора, определяющего уровень доступа, например [Public](../modifiers/public.md), [Friend](../modifiers/friend.md)или [Private](../modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="cfc7b-119">You must declare every member using a [Dim Statement](../statements/dim-statement.md) or a statement that specifies access level, such as [Public](../modifiers/public.md), [Friend](../modifiers/friend.md), or [Private](../modifiers/private.md).</span></span> <span data-ttu-id="cfc7b-120">При использовании `Dim` инструкции уровень доступа по умолчанию равен public.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-120">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="cfc7b-121">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="cfc7b-121">Programming Tips</span></span>

- <span data-ttu-id="cfc7b-122">**Потребление памяти.**</span><span class="sxs-lookup"><span data-stu-id="cfc7b-122">**Memory Consumption.**</span></span> <span data-ttu-id="cfc7b-123">Как и для всех составных типов данных, вы не можете безопасно вычислить общее потребление памяти для структуры, добавив в них номинальные объемы выделяемого пространства для его членов.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-123">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="cfc7b-124">Кроме того, нельзя безопасно предположить, что порядок хранения в памяти совпадает с порядком объявления.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-124">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="cfc7b-125">Если необходимо управлять структурой хранилища структуры, можно применить <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут к `Structure` оператору.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-125">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="cfc7b-126">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="cfc7b-126">**Interop Considerations.**</span></span> <span data-ttu-id="cfc7b-127">Если вы взаимодействуете с компонентами, которые не написаны для платформа .NET Framework, например автоматизации или COM-объекты, помните, что определяемые пользователем типы в других средах несовместимы с типами структуры Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-127">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="cfc7b-128">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="cfc7b-128">**Widening.**</span></span> <span data-ttu-id="cfc7b-129">Автоматическое преобразование в любой тип данных структуры или из него отсутствует.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-129">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="cfc7b-130">Операторы преобразования в структуре можно определить с помощью оператора [оператора](../statements/operator-statement.md), а каждый оператор преобразования можно объявить как `Widening` или `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="cfc7b-130">You can define conversion operators on your structure using the [Operator Statement](../statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="cfc7b-131">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="cfc7b-131">**Type Characters.**</span></span> <span data-ttu-id="cfc7b-132">Типы данных структуры не имеют символа литерального типа или символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-132">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="cfc7b-133">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="cfc7b-133">**Framework Type.**</span></span> <span data-ttu-id="cfc7b-134">В платформа .NET Framework нет соответствующего типа.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-134">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="cfc7b-135">Все структуры наследуют от класса платформа .NET Framework <xref:System.ValueType?displayProperty=nameWithType> , но никакая отдельная структура не соответствует <xref:System.ValueType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cfc7b-135">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="cfc7b-136">Пример</span><span class="sxs-lookup"><span data-stu-id="cfc7b-136">Example</span></span>

<span data-ttu-id="cfc7b-137">В следующей парадигме показана структура объявления структуры.</span><span class="sxs-lookup"><span data-stu-id="cfc7b-137">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="cfc7b-138">См. также</span><span class="sxs-lookup"><span data-stu-id="cfc7b-138">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="cfc7b-139">Типы данных</span><span class="sxs-lookup"><span data-stu-id="cfc7b-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="cfc7b-140">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="cfc7b-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="cfc7b-141">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="cfc7b-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="cfc7b-142">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="cfc7b-142">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="cfc7b-143">Widening</span><span class="sxs-lookup"><span data-stu-id="cfc7b-143">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="cfc7b-144">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cfc7b-144">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="cfc7b-145">Структуры</span><span class="sxs-lookup"><span data-stu-id="cfc7b-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cfc7b-146">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="cfc7b-146">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
