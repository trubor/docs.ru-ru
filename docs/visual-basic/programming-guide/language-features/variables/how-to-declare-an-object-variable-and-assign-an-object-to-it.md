---
description: Дополнительные сведения см. в статье как объявить объектную переменную и присвоить ей объект в Visual Basic
title: Практическое руководство. Объявление объектной переменной и присвоение ей объекта
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: f79cda4507a3dbf2a6946dee7d909b6d1b10802d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481952"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="633dc-103">Практическое руководство. Объявление объектной переменной в Visual Basic и присвоение ей объекта</span><span class="sxs-lookup"><span data-stu-id="633dc-103">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="633dc-104">Переменная [типа данных Object](../../../language-reference/data-types/object-data-type.md) объявляется путем указания `As Object` в [операторе Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="633dc-104">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="633dc-105">Вы назначаете объект такой переменной, помещая объект после знака равенства ( `=` ) в операторе присваивания или предложении инициализации.</span><span class="sxs-lookup"><span data-stu-id="633dc-105">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="633dc-106">Пример</span><span class="sxs-lookup"><span data-stu-id="633dc-106">Example</span></span>

<span data-ttu-id="633dc-107">В следующем примере объявляется `Object` переменная и назначается ей текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="633dc-107">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="633dc-108">Объявление и присваивание можно объединить, инициализируя переменную как часть ее объявления.</span><span class="sxs-lookup"><span data-stu-id="633dc-108">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="633dc-109">Следующий пример эквивалентен предыдущему примеру.</span><span class="sxs-lookup"><span data-stu-id="633dc-109">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="633dc-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="633dc-110">Compile the code</span></span>

<span data-ttu-id="633dc-111">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="633dc-111">This example requires:</span></span>

- <span data-ttu-id="633dc-112">ссылка на пространство имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="633dc-112">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="633dc-113">Класс, структура или модуль, в котором будет размещена `Dim` инструкция.</span><span class="sxs-lookup"><span data-stu-id="633dc-113">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="633dc-114">Процедура, в которой следует разместить оператор присваивания.</span><span class="sxs-lookup"><span data-stu-id="633dc-114">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="633dc-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="633dc-115">See also</span></span>

- [<span data-ttu-id="633dc-116">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="633dc-116">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="633dc-117">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="633dc-117">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="633dc-118">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="633dc-118">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="633dc-119">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="633dc-119">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="633dc-120">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="633dc-120">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="633dc-121">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="633dc-121">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="633dc-122">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="633dc-122">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
