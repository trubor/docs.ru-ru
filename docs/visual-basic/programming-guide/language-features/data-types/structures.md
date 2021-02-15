---
description: 'Дополнительные сведения о структурах: структуры (Visual Basic)'
title: Структуры
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: c79ba7b4ea8e80aced6c2a280c4896ed9f8c9916
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427626"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="2c6c1-103">Структуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c6c1-103">Structures (Visual Basic)</span></span>

<span data-ttu-id="2c6c1-104">*Структура* представляет собой обобщение определяемого пользователем типа (UDT), поддерживаемого предыдущими версиями Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-104">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="2c6c1-105">В дополнение к полям, структуры могут предоставлять свойства, методы и события.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-105">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="2c6c1-106">Структура может реализовывать один или несколько интерфейсов, и можно объявить отдельные уровни доступа для каждого поля.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-106">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="2c6c1-107">Для создания структуры можно сочетать элементы данных различных типов.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-107">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="2c6c1-108">Структура связывает один или несколько *элементов* друг с другом и с самой структурой.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-108">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="2c6c1-109">При объявлении структуры она превращается в *составной тип данных*, и можно объявлять переменные этого типа.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-109">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="2c6c1-110">Структуры полезны, если требуется, чтобы одна переменная содержала несколько связанных частей информации.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-110">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="2c6c1-111">Например, может потребоваться одновременное отслеживание имени сотрудника, телефонного расширения и оклада.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-111">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="2c6c1-112">Для этой информации можно использовать несколько переменных или определить структуру и использовать ее для одной переменной сотрудника.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-112">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="2c6c1-113">Преимущество структуры станет очевидным, если у вас много сотрудников и, следовательно, много экземпляров переменной.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-113">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c6c1-114">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="2c6c1-114">In This Section</span></span>  

 [<span data-ttu-id="2c6c1-115">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="2c6c1-115">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)  
 <span data-ttu-id="2c6c1-116">Показывает, как объявить структуру и ее элементы.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-116">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="2c6c1-117">Переменные структуры</span><span class="sxs-lookup"><span data-stu-id="2c6c1-117">Structure Variables</span></span>](structure-variables.md)  
 <span data-ttu-id="2c6c1-118">Описывает назначение структуры переменной и доступ к ее элементам.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-118">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="2c6c1-119">Структуры и другие элементы программирования</span><span class="sxs-lookup"><span data-stu-id="2c6c1-119">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)  
 <span data-ttu-id="2c6c1-120">Описывает, как структуры взаимодействуют с массивами, объектами, процедурами и друг с другом.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-120">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="2c6c1-121">Структуры и классы</span><span class="sxs-lookup"><span data-stu-id="2c6c1-121">Structures and Classes</span></span>](structures-and-classes.md)  
 <span data-ttu-id="2c6c1-122">Описывает сходства и различия между структурами и классами.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-122">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c6c1-123">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="2c6c1-123">Related Sections</span></span>  

 [<span data-ttu-id="2c6c1-124">Типы данных</span><span class="sxs-lookup"><span data-stu-id="2c6c1-124">Data Types</span></span>](index.md)  
 <span data-ttu-id="2c6c1-125">Вводит Visual Basic типы данных и описывает, как их использовать.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-125">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="2c6c1-126">Типы данных</span><span class="sxs-lookup"><span data-stu-id="2c6c1-126">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="2c6c1-127">Содержит список простейших типов данных, предоставляемых Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2c6c1-127">Lists the elementary data types supplied by Visual Basic.</span></span>
