---
description: 'Дополнительные сведения о: когда следует использовать перечисление (Visual Basic)'
title: Когда следует использовать перечисление
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: a29d0e3bb8ac99baf5d43827a8b58701eddcfbdd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480743"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="24d56-103">Когда следует использовать перечисление (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24d56-103">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="24d56-104">Перечисления предлагают простой способ работы с наборами связанных констант.</span><span class="sxs-lookup"><span data-stu-id="24d56-104">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="24d56-105">Перечисление или `Enum` является символическим именем для набора значений.</span><span class="sxs-lookup"><span data-stu-id="24d56-105">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="24d56-106">Перечисления обрабатываются как типы данных, и их можно использовать для создания наборов констант для использования с переменными и свойствами.</span><span class="sxs-lookup"><span data-stu-id="24d56-106">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="24d56-107">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="24d56-107">When to Use an Enumeration</span></span>  

 <span data-ttu-id="24d56-108">Если процедура принимает ограниченный набор переменных, рекомендуется использовать перечисление.</span><span class="sxs-lookup"><span data-stu-id="24d56-108">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="24d56-109">Перечисления делают более понятным и удобочитаемым кодом, особенно при использовании осмысленных имен.</span><span class="sxs-lookup"><span data-stu-id="24d56-109">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="24d56-110">Ниже перечислены преимущества использования перечислений.</span><span class="sxs-lookup"><span data-stu-id="24d56-110">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="24d56-111">Сокращает количество ошибок, вызванных перечислением или неотрицательным вводом чисел.</span><span class="sxs-lookup"><span data-stu-id="24d56-111">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="24d56-112">Упрощает изменение значений в будущем.</span><span class="sxs-lookup"><span data-stu-id="24d56-112">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="24d56-113">Упрощает чтение кода. Это означает, что менее вероятно, что ошибки будут отменяться.</span><span class="sxs-lookup"><span data-stu-id="24d56-113">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="24d56-114">Обеспечивает прямую совместимость.</span><span class="sxs-lookup"><span data-stu-id="24d56-114">Ensures forward compatibility.</span></span> <span data-ttu-id="24d56-115">При использовании перечислений код менее вероятен, если в будущем кто-то изменит значения, соответствующие именам элементов.</span><span class="sxs-lookup"><span data-stu-id="24d56-115">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="24d56-116">Перечисления именования</span><span class="sxs-lookup"><span data-stu-id="24d56-116">Naming Enumerations</span></span>  

 <span data-ttu-id="24d56-117">Используйте соглашение об именовании для членов перечисления.</span><span class="sxs-lookup"><span data-stu-id="24d56-117">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="24d56-118">Когда Visual Basic встречает имя члена перечисления, может возникнуть исключение, если другие библиотеки типов содержат одно и то же имя.</span><span class="sxs-lookup"><span data-stu-id="24d56-118">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="24d56-119">Используйте уникальный префикс, определяющий значения из приложения или компонента.</span><span class="sxs-lookup"><span data-stu-id="24d56-119">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="24d56-120">При ссылке на член перечисления необходимо уточнить имя члена с помощью имени перечисления или использовать `Imports` оператор.</span><span class="sxs-lookup"><span data-stu-id="24d56-120">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="24d56-121">Дополнительные сведения см. в разделе [перечисления и квалификация имени](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-121">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="24d56-122">Предопределенные перечисления</span><span class="sxs-lookup"><span data-stu-id="24d56-122">Predefined Enumerations</span></span>  

 <span data-ttu-id="24d56-123">Visual Basic предоставляет ряд предопределенных перечислений, таких как `FirstDayOfWeek` и `MsgBoxResult` , для упрощения кода.</span><span class="sxs-lookup"><span data-stu-id="24d56-123">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="24d56-124">Список этих элементов см. в разделе [константы и перечисления](../../../language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-124">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d56-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="24d56-125">See also</span></span>

- [<span data-ttu-id="24d56-126">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="24d56-126">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="24d56-127">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="24d56-127">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="24d56-128">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="24d56-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="24d56-129">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24d56-129">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="24d56-130">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="24d56-130">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="24d56-131">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="24d56-131">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="24d56-132">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="24d56-132">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
