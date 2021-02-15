---
description: 'Дополнительные сведения: как скрыть унаследованную переменную (Visual Basic)'
title: Практическое руководство. Сокрытие наследуемой переменной
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: be2de980e27b318151c795ae36bd92a01d47d55e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429901"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="076e3-103">Практическое руководство. Сокрытие наследуемой переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="076e3-103">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="076e3-104">Производный класс наследует все определения своего базового класса.</span><span class="sxs-lookup"><span data-stu-id="076e3-104">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="076e3-105">Если необходимо определить переменную с тем же именем, что и у элемента базового класса, можно скрыть или *затенить* этот элемент базового класса при определении переменной в производном классе.</span><span class="sxs-lookup"><span data-stu-id="076e3-105">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="076e3-106">В этом случае код в производном классе получает доступ к переменной, если только явно не обходит механизм теневого копирования.</span><span class="sxs-lookup"><span data-stu-id="076e3-106">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="076e3-107">Другой причиной, по которой может потребоваться скрыть унаследованную переменную, является защита от редакции базового класса.</span><span class="sxs-lookup"><span data-stu-id="076e3-107">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="076e3-108">Базовый класс может повлиять на изменение, изменяющее элемент, который вы наследуете.</span><span class="sxs-lookup"><span data-stu-id="076e3-108">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="076e3-109">Если это происходит, `Shadows` Модификатор заставляет ссылки из производного класса разрешаться в переменную, а не в элемент базового класса.</span><span class="sxs-lookup"><span data-stu-id="076e3-109">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="076e3-110">Скрытие унаследованной переменной</span><span class="sxs-lookup"><span data-stu-id="076e3-110">To hide an inherited variable</span></span>

1. <span data-ttu-id="076e3-111">Убедитесь, что переменная, которую нужно скрыть, объявлена на уровне класса (вне любой процедуры).</span><span class="sxs-lookup"><span data-stu-id="076e3-111">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="076e3-112">В противном случае скрыть ее не нужно.</span><span class="sxs-lookup"><span data-stu-id="076e3-112">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="076e3-113">Внутри производного класса напишите [оператор Dim](../../../language-reference/statements/dim-statement.md) , объявляющий переменную.</span><span class="sxs-lookup"><span data-stu-id="076e3-113">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="076e3-114">Используйте то же имя, что и у унаследованной переменной.</span><span class="sxs-lookup"><span data-stu-id="076e3-114">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="076e3-115">Включите в объявление ключевое слово [Shadows](../../../language-reference/modifiers/shadows.md) .</span><span class="sxs-lookup"><span data-stu-id="076e3-115">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="076e3-116">Если код в производном классе ссылается на имя переменной, компилятор разрешает ссылку на переменную.</span><span class="sxs-lookup"><span data-stu-id="076e3-116">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="076e3-117">В следующем примере показано затенение наследуемой переменной.</span><span class="sxs-lookup"><span data-stu-id="076e3-117">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="076e3-118">В предыдущем примере переменная объявляется `shadowString` в базовом классе и переобъявляется в производном классе.</span><span class="sxs-lookup"><span data-stu-id="076e3-118">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="076e3-119">Процедура `ShowStrings` в производном классе отображает версию строки с тенью, если ее имя `shadowString` не является полным.</span><span class="sxs-lookup"><span data-stu-id="076e3-119">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="076e3-120">После этого она отображает затененную версию, если `shadowString` дополнена `MyBase` ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="076e3-120">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="076e3-121">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="076e3-121">Robust programming</span></span>

<span data-ttu-id="076e3-122">При затенении введено более одной версии переменной с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="076e3-122">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="076e3-123">Если инструкция Code ссылается на имя переменной, версия, на которую компилятор разрешает ссылку, зависит от таких факторов, как расположение инструкции Code и наличие подходящих строк.</span><span class="sxs-lookup"><span data-stu-id="076e3-123">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="076e3-124">Это может увеличить риск обращения к непреднамеренной версии затененной переменной.</span><span class="sxs-lookup"><span data-stu-id="076e3-124">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="076e3-125">Можно снизить этот риск, полностью подполняя все ссылки на затененную переменную.</span><span class="sxs-lookup"><span data-stu-id="076e3-125">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="076e3-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="076e3-126">See also</span></span>

- [<span data-ttu-id="076e3-127">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="076e3-127">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="076e3-128">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="076e3-128">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="076e3-129">Различия между удаленным управлением и переопределением</span><span class="sxs-lookup"><span data-stu-id="076e3-129">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="076e3-130">Практическое руководство. Сокрытие переменной с тем же именем, что и ваша переменная</span><span class="sxs-lookup"><span data-stu-id="076e3-130">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="076e3-131">Практическое руководство. Доступ к переменной, скрытой производным классом</span><span class="sxs-lookup"><span data-stu-id="076e3-131">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="076e3-132">Переопределения</span><span class="sxs-lookup"><span data-stu-id="076e3-132">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="076e3-133">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="076e3-133">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="076e3-134">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="076e3-134">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
