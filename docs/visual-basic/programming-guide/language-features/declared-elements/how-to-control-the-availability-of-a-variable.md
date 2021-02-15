---
description: Дополнительные сведения см. в статье как управлять доступностью переменной (Visual Basic).
title: Практическое руководство. Управление доступностью переменной
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 3fa21a804008f31da9003aa847752f749154d602
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429888"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="ceb38-103">Практическое руководство. Управление доступностью переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceb38-103">How to: Control the Availability of a Variable (Visual Basic)</span></span>

<span data-ttu-id="ceb38-104">Для управления доступностью переменной можно указать ее *уровень доступа*.</span><span class="sxs-lookup"><span data-stu-id="ceb38-104">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="ceb38-105">Уровень доступа определяет, какой код имеет разрешение на чтение или запись в переменную.</span><span class="sxs-lookup"><span data-stu-id="ceb38-105">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="ceb38-106">*Переменные-члены* (определенные на уровне модуля и вне любой процедуры) по умолчанию имеют открытый доступ, что означает любой код, который может видеть, что они имеют доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="ceb38-106">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="ceb38-107">Это можно изменить, указав модификатор доступа.</span><span class="sxs-lookup"><span data-stu-id="ceb38-107">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="ceb38-108">*Локальные переменные* (определенные внутри процедуры) номинально имеют общий доступ, хотя доступ к ним могут получить только код внутри их процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-108">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="ceb38-109">Нельзя изменить уровень доступа локальной переменной, но можно изменить уровень доступа процедуры, содержащей ее.</span><span class="sxs-lookup"><span data-stu-id="ceb38-109">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="ceb38-110">Дополнительные сведения см. [в разделе уровни доступа в Visual Basic](access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ceb38-110">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="ceb38-111">Частный и открытый доступ</span><span class="sxs-lookup"><span data-stu-id="ceb38-111">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="ceb38-112">Предоставление доступа к переменной только внутри модуля, класса или структуры</span><span class="sxs-lookup"><span data-stu-id="ceb38-112">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="ceb38-113">Поместите [оператор Dim](../../../language-reference/statements/dim-statement.md) для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-113">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ceb38-114">Включите в оператор ключевое слово [Private](../../../language-reference/modifiers/private.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-114">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ceb38-115">Можно выполнять чтение или запись в переменную из любого места внутри модуля, класса или структуры, но не за ее пределами.</span><span class="sxs-lookup"><span data-stu-id="ceb38-115">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="ceb38-116">Чтобы сделать переменную доступной из любого кода, который может ее увидеть</span><span class="sxs-lookup"><span data-stu-id="ceb38-116">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="ceb38-117">Для переменной-члена поместите `Dim` оператор для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-117">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ceb38-118">Включите в оператор ключевое слово [Public](../../../language-reference/modifiers/public.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-118">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ceb38-119">Можно выполнять чтение или запись в переменную из любого кода, который взаимодействует со сборкой.</span><span class="sxs-lookup"><span data-stu-id="ceb38-119">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="ceb38-120">-или-</span><span class="sxs-lookup"><span data-stu-id="ceb38-120">-or-</span></span>  
  
1. <span data-ttu-id="ceb38-121">Для локальной переменной поместите `Dim` инструкцию для переменной внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-121">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="ceb38-122">Не включайте `Public` ключевое слово в `Dim` оператор.</span><span class="sxs-lookup"><span data-stu-id="ceb38-122">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ceb38-123">Можно выполнять чтение или запись в переменную из любого места внутри процедуры, но не за ее пределами.</span><span class="sxs-lookup"><span data-stu-id="ceb38-123">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="ceb38-124">Защищенный и дружественный доступ</span><span class="sxs-lookup"><span data-stu-id="ceb38-124">Protected and Friend Access</span></span>  

 <span data-ttu-id="ceb38-125">Уровень доступа переменной можно ограничить своим классом и любыми производными классами или сборкой.</span><span class="sxs-lookup"><span data-stu-id="ceb38-125">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="ceb38-126">Можно также указать объединение этих ограничений, которое разрешает доступ из кода в любом производном классе или в любом другом месте в одной сборке.</span><span class="sxs-lookup"><span data-stu-id="ceb38-126">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="ceb38-127">Это объединение можно указать, объединив `Protected` `Friend` Ключевые слова и в том же объявлении.</span><span class="sxs-lookup"><span data-stu-id="ceb38-127">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="ceb38-128">Предоставление доступа к переменной только внутри ее класса и любых производных классов</span><span class="sxs-lookup"><span data-stu-id="ceb38-128">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="ceb38-129">Поместите `Dim` оператор для переменной внутри класса, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-129">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ceb38-130">Включите в оператор ключевое слово [protected](../../../language-reference/modifiers/protected.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-130">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ceb38-131">Можно выполнять чтение или запись в переменную из любого места внутри класса, а также из любого класса, производного от него, но не за пределами класса в цепочке наследования.</span><span class="sxs-lookup"><span data-stu-id="ceb38-131">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="ceb38-132">Предоставление переменной доступа только из той же сборки</span><span class="sxs-lookup"><span data-stu-id="ceb38-132">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="ceb38-133">Поместите `Dim` оператор для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="ceb38-133">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="ceb38-134">Включите в оператор ключевое слово [Friend](../../../language-reference/modifiers/friend.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-134">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ceb38-135">Можно выполнять чтение или запись в переменную из любого места внутри модуля, класса или структуры, а также из любого кода в той же сборке, но не за пределами сборки.</span><span class="sxs-lookup"><span data-stu-id="ceb38-135">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceb38-136">Пример</span><span class="sxs-lookup"><span data-stu-id="ceb38-136">Example</span></span>  

 <span data-ttu-id="ceb38-137">В следующем примере показаны объявления переменных с `Public` `Protected` `Friend` `Protected Friend` уровнями доступа,,, и `Private` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-137">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="ceb38-138">Обратите внимание, что если `Dim` инструкция задает уровень доступа, ключевое слово включать не нужно `Dim` .</span><span class="sxs-lookup"><span data-stu-id="ceb38-138">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="ceb38-139">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ceb38-139">.NET Framework Security</span></span>  

 <span data-ttu-id="ceb38-140">Чем более ограниченный уровень доступа переменной, тем меньше вероятность того, что вредоносный код может неправильно использовать его.</span><span class="sxs-lookup"><span data-stu-id="ceb38-140">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb38-141">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ceb38-141">See also</span></span>

- [<span data-ttu-id="ceb38-142">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ceb38-142">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="ceb38-143">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="ceb38-143">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="ceb38-144">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="ceb38-144">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="ceb38-145">Защищенный</span><span class="sxs-lookup"><span data-stu-id="ceb38-145">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="ceb38-146">Friend</span><span class="sxs-lookup"><span data-stu-id="ceb38-146">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="ceb38-147">Частная</span><span class="sxs-lookup"><span data-stu-id="ceb38-147">Private</span></span>](../../../language-reference/modifiers/private.md)
