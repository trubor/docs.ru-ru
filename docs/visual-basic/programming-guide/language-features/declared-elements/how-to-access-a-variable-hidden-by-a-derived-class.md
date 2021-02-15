---
description: Дополнительные сведения см. в статье как получить доступ к переменной, скрытой производным классом (Visual Basic)
title: Практическое руководство. Доступ к переменной, скрытой производным классом
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 5ac1dd8afc8c32c91b748c8316d035d69468d887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430057"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="7a0fd-103">Практическое руководство. Доступ к переменной, скрытой производным классом (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a0fd-103">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="7a0fd-104">Когда код в производном классе получает доступ к переменной, компилятор обычно разрешает ссылку на ближайшую доступную версию, то есть доступную версию с минимальными производными шагами назад от класса доступа.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-104">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="7a0fd-105">Если переменная определена в производном классе, код обычно получает доступ к определению.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-105">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="7a0fd-106">Если переменная производного класса затеняет переменную в базовом классе, она скрывает версию базового класса.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-106">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="7a0fd-107">Однако можно получить доступ к переменной базового класса, указав ее с помощью `MyBase` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-107">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="7a0fd-108">Доступ к переменной базового класса, скрытой производным классом</span><span class="sxs-lookup"><span data-stu-id="7a0fd-108">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="7a0fd-109">В выражении или операторе присваивания перед именем переменной следует `MyBase` указать ключевое слово и точку ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="7a0fd-109">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="7a0fd-110">Компилятор разрешает ссылку на версию базового класса переменной.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-110">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="7a0fd-111">В следующем примере показано затенение с помощью наследования.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-111">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="7a0fd-112">Он делает две ссылки — одну, которая обращается к переменной с тенью, и одну, которая обходит затенение.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-112">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="7a0fd-113">В предыдущем примере переменная объявляется `shadowString` в базовом классе и переобъявляется в производном классе.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-113">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="7a0fd-114">Процедура `showStrings` в производном классе отображает версию строки с тенью, если ее имя `shadowString` не является полным.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-114">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="7a0fd-115">После этого она отображает затененную версию, если `shadowString` дополнена `MyBase`  ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-115">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="7a0fd-116">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="7a0fd-116">Robust Programming</span></span>

<span data-ttu-id="7a0fd-117">Чтобы снизить риск обращения к непреднамеренной версии затененной переменной, можно полностью определить все ссылки на затененную переменную.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-117">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="7a0fd-118">При затенении введено более одной версии переменной с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-118">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="7a0fd-119">Если инструкция Code ссылается на имя переменной, версия, на которую компилятор разрешает ссылку, зависит от таких факторов, как расположение инструкции Code и наличие подходящих строк.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-119">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="7a0fd-120">Это может увеличить риск обращения к неверной версии переменной.</span><span class="sxs-lookup"><span data-stu-id="7a0fd-120">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a0fd-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7a0fd-121">See also</span></span>

- [<span data-ttu-id="7a0fd-122">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="7a0fd-122">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="7a0fd-123">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a0fd-123">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="7a0fd-124">Различия между удаленным управлением и переопределением</span><span class="sxs-lookup"><span data-stu-id="7a0fd-124">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="7a0fd-125">Практическое руководство. Сокрытие переменной с тем же именем, что и ваша переменная</span><span class="sxs-lookup"><span data-stu-id="7a0fd-125">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="7a0fd-126">Практическое руководство. Сокрытие наследуемой переменной</span><span class="sxs-lookup"><span data-stu-id="7a0fd-126">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="7a0fd-127">Shadows</span><span class="sxs-lookup"><span data-stu-id="7a0fd-127">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="7a0fd-128">Переопределения</span><span class="sxs-lookup"><span data-stu-id="7a0fd-128">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="7a0fd-129">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="7a0fd-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="7a0fd-130">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="7a0fd-130">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
