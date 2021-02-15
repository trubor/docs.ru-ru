---
description: Дополнительные сведения см. в статье как управлять областью действия переменной (Visual Basic)
title: Практическое руководство. Управление областью действия переменной
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: c6da599f76883cba545efbdf9570aa05770602a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429875"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="536e6-103">Практическое руководство. Управление областью действия переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="536e6-103">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="536e6-104">Как правило, переменная находится в *области видимости* или видима для справки по всему региону, в котором она объявлена.</span><span class="sxs-lookup"><span data-stu-id="536e6-104">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="536e6-105">В некоторых случаях *уровень доступа* переменной может повлиять на ее область.</span><span class="sxs-lookup"><span data-stu-id="536e6-105">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="536e6-106">Для получения дополнительной информации см. [Scope in Visual Basic](scope.md).</span><span class="sxs-lookup"><span data-stu-id="536e6-106">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="536e6-107">Область на уровне блока или процедуры</span><span class="sxs-lookup"><span data-stu-id="536e6-107">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="536e6-108">Предоставление переменной видимой только внутри блока</span><span class="sxs-lookup"><span data-stu-id="536e6-108">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="536e6-109">Поместите [оператор Dim](../../../language-reference/statements/dim-statement.md) для переменной между операторами объявления и завершения этого блока, например между `For` `Next` операторами и `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="536e6-109">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="536e6-110">Ссылаться на переменную можно только внутри блока.</span><span class="sxs-lookup"><span data-stu-id="536e6-110">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="536e6-111">Предоставление переменной видимой только внутри процедуры</span><span class="sxs-lookup"><span data-stu-id="536e6-111">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="536e6-112">Поместите `Dim` оператор для переменной внутри процедуры, но вне любого блока (например, `With` блок... `End With` ).</span><span class="sxs-lookup"><span data-stu-id="536e6-112">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="536e6-113">Ссылаться на переменную можно только внутри процедуры, включая внутри любого блока, содержащегося в процедуре.</span><span class="sxs-lookup"><span data-stu-id="536e6-113">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="536e6-114">Область на уровне модуля или пространства имен</span><span class="sxs-lookup"><span data-stu-id="536e6-114">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="536e6-115">Для удобства *уровень модуля* единого термина применяется в равной степени к модулям, классам и структурам.</span><span class="sxs-lookup"><span data-stu-id="536e6-115">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="536e6-116">Уровень доступа переменной уровня модуля определяет ее область.</span><span class="sxs-lookup"><span data-stu-id="536e6-116">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="536e6-117">Пространство имен, содержащее модуль, класс или структуру, также влияет на область.</span><span class="sxs-lookup"><span data-stu-id="536e6-117">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="536e6-118">Чтобы сделать переменную видимой в пределах модуля, класса или структуры</span><span class="sxs-lookup"><span data-stu-id="536e6-118">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="536e6-119">Поместите `Dim` оператор для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="536e6-119">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="536e6-120">Включите в оператор ключевое слово [Private](../../../language-reference/modifiers/private.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="536e6-120">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="536e6-121">Можно ссылаться на переменную из любого места в модуле, классе или структуре, но не за ее пределами.</span><span class="sxs-lookup"><span data-stu-id="536e6-121">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="536e6-122">Как сделать переменную видимой во всем пространстве имен</span><span class="sxs-lookup"><span data-stu-id="536e6-122">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="536e6-123">Поместите `Dim` оператор для переменной внутри модуля, класса или структуры, но вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="536e6-123">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="536e6-124">Включите в инструкцию ключевое слово [Friend](../../../language-reference/modifiers/friend.md) или [Public](../../../language-reference/modifiers/public.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="536e6-124">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="536e6-125">Можно ссылаться на переменную из любого места в пространстве имен, содержащем модуль, класс или структуру.</span><span class="sxs-lookup"><span data-stu-id="536e6-125">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="536e6-126">Пример</span><span class="sxs-lookup"><span data-stu-id="536e6-126">Example</span></span>  

 <span data-ttu-id="536e6-127">В следующем примере объявляется переменная на уровне модуля и ограничивается ее видимость кодом внутри модуля.</span><span class="sxs-lookup"><span data-stu-id="536e6-127">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="536e6-128">В предыдущем примере все процедуры, определенные в модуле, `demonstrateScope` могут ссылаться на `String` переменную `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="536e6-128">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="536e6-129">При `usePrivateVariable` вызове процедуры она отображает содержимое строковой переменной `strMsg` в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="536e6-129">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="536e6-130">После выполнения следующей изменения в предыдущем примере строковая переменная `strMsg` может называться кодом в любом месте пространства имен его объявления.</span><span class="sxs-lookup"><span data-stu-id="536e6-130">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="536e6-131">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="536e6-131">Robust Programming</span></span>  

 <span data-ttu-id="536e6-132">Чем более узкие области переменной, тем меньше возможностей вы случайно ссылаетесь на нее вместо другой переменной с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="536e6-132">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="536e6-133">Можно также избежать проблем, связанных с сопоставлением ссылок.</span><span class="sxs-lookup"><span data-stu-id="536e6-133">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="536e6-134">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="536e6-134">.NET Framework Security</span></span>  

 <span data-ttu-id="536e6-135">Чем короче область переменной, тем меньше вероятность того, что вредоносный код может неправильно использовать его.</span><span class="sxs-lookup"><span data-stu-id="536e6-135">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536e6-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="536e6-136">See also</span></span>

- [<span data-ttu-id="536e6-137">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="536e6-137">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="536e6-138">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="536e6-138">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="536e6-139">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="536e6-139">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="536e6-140">Переменные</span><span class="sxs-lookup"><span data-stu-id="536e6-140">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="536e6-141">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="536e6-141">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="536e6-142">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="536e6-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
