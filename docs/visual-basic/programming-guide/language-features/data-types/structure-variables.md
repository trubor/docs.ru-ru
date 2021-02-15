---
description: 'Дополнительные сведения: переменные структуры (Visual Basic)'
title: Переменные структуры
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 64c53b06369bc7d7d0c46bc87d4c73ce90b4011f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484162"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="da14b-103">Переменные структуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da14b-103">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="da14b-104">После создания структуры можно объявить переменные уровня процедуры и модуля в качестве этого типа.</span><span class="sxs-lookup"><span data-stu-id="da14b-104">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="da14b-105">Например, можно создать структуру, которая записывает сведения о компьютерной системе.</span><span class="sxs-lookup"><span data-stu-id="da14b-105">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="da14b-106">В следующем примере это показано.</span><span class="sxs-lookup"><span data-stu-id="da14b-106">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="da14b-107">Теперь можно объявлять переменные этого типа.</span><span class="sxs-lookup"><span data-stu-id="da14b-107">You can now declare variables of that type.</span></span> <span data-ttu-id="da14b-108">Это показано в следующем объявлении.</span><span class="sxs-lookup"><span data-stu-id="da14b-108">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="da14b-109">В классах и модулях структуры, объявленные с помощью [инструкции Dim](../../../language-reference/statements/dim-statement.md) , по умолчанию имеют открытый доступ.</span><span class="sxs-lookup"><span data-stu-id="da14b-109">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="da14b-110">Если структура должна быть закрытой, убедитесь, что она объявлена с помощью ключевого слова [Private](../../../language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="da14b-110">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="da14b-111">Доступ к значениям структуры</span><span class="sxs-lookup"><span data-stu-id="da14b-111">Access to Structure Values</span></span>

<span data-ttu-id="da14b-112">Для присвоения и извлечения значений из элементов переменной структуры используется тот же синтаксис, что и при использовании для задания и получения свойств объекта.</span><span class="sxs-lookup"><span data-stu-id="da14b-112">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="da14b-113">Оператор доступа к членам () размещается `.` между именем переменной структуры и именем элемента.</span><span class="sxs-lookup"><span data-stu-id="da14b-113">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="da14b-114">В следующем примере осуществляется доступ к элементам переменных, ранее объявленных как тип `systemInfo` .</span><span class="sxs-lookup"><span data-stu-id="da14b-114">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="da14b-115">Присваивание переменных структуры</span><span class="sxs-lookup"><span data-stu-id="da14b-115">Assigning Structure Variables</span></span>

<span data-ttu-id="da14b-116">Можно также присвоить одну переменную другой, если оба имеют один и тот же тип структуры.</span><span class="sxs-lookup"><span data-stu-id="da14b-116">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="da14b-117">Все элементы одной структуры копируются в соответствующие элементы в другом.</span><span class="sxs-lookup"><span data-stu-id="da14b-117">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="da14b-118">Это показано в следующем объявлении.</span><span class="sxs-lookup"><span data-stu-id="da14b-118">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="da14b-119">Если элемент структуры является ссылочным типом, таким как массив типа `String` , `Object` или, то копируется указатель на данные.</span><span class="sxs-lookup"><span data-stu-id="da14b-119">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="da14b-120">В предыдущем примере, если `systemInfo` была включена объектная переменная, в предыдущем примере был скопирован указатель из `mySystem` в `yourSystem` , а изменение данных объекта через одну структуру вступит в действие при доступе через другую структуру.</span><span class="sxs-lookup"><span data-stu-id="da14b-120">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="da14b-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="da14b-121">See also</span></span>

- [<span data-ttu-id="da14b-122">Типы данных</span><span class="sxs-lookup"><span data-stu-id="da14b-122">Data Types</span></span>](index.md)
- [<span data-ttu-id="da14b-123">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="da14b-123">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="da14b-124">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="da14b-124">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="da14b-125">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="da14b-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="da14b-126">Структуры</span><span class="sxs-lookup"><span data-stu-id="da14b-126">Structures</span></span>](structures.md)
- [<span data-ttu-id="da14b-127">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="da14b-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="da14b-128">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="da14b-128">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="da14b-129">Структуры и другие элементы программирования</span><span class="sxs-lookup"><span data-stu-id="da14b-129">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="da14b-130">Структуры и классы</span><span class="sxs-lookup"><span data-stu-id="da14b-130">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="da14b-131">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="da14b-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
