---
description: 'Дополнительные сведения о: BC30451: имя " <name> " не объявлено'
title: Имя <name> не объявлено
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 8d76bcfd18b277a5f542f363cb906496680bae29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795746"
---
# <a name="bc30451-name-name-is-not-declared"></a><span data-ttu-id="5aa5c-103">BC30451: имя " \<name> " не объявлено</span><span class="sxs-lookup"><span data-stu-id="5aa5c-103">BC30451: Name '\<name>' is not declared</span></span>

<span data-ttu-id="5aa5c-104">Оператор ссылается на программный элемент, но компилятор не может найти элемент с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-104">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>

 <span data-ttu-id="5aa5c-105">**Идентификатор ошибки:** BC30451</span><span class="sxs-lookup"><span data-stu-id="5aa5c-105">**Error ID:** BC30451</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5aa5c-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="5aa5c-106">To correct this error</span></span>

1. <span data-ttu-id="5aa5c-107">Проверьте правильность написания в ссылающемся операторе.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-107">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="5aa5c-108">Visual Basic не учитывает регистр, но любые другие вариации в написании считаются совершенно разными именами.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-108">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="5aa5c-109">Обратите внимание, что символ подчеркивания (`_`) является частью имени и, следовательно, частью орфографии.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-109">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>

2. <span data-ttu-id="5aa5c-110">Убедитесь, что у вас есть оператор доступа к членам ( `.` ) между объектом и его членом.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-110">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="5aa5c-111">Например, если у вас есть элемент управления <xref:System.Windows.Forms.TextBox> с именем `TextBox1`, то для доступа к его свойству <xref:System.Windows.Forms.TextBoxBase.Text%2A> следует ввести `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-111">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="5aa5c-112">Если вместо этого ввести `TextBox1Text`, будет создано другое имя.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-112">If instead you type `TextBox1Text`, you have created a different name.</span></span>

3. <span data-ttu-id="5aa5c-113">Если орфография верна и синтаксис любого доступного члена объекта правильный, убедитесь, что элемент был объявлен.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-113">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="5aa5c-114">Дополнительные сведения см. в разделе [объявленные элементы](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5c-114">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>

4. <span data-ttu-id="5aa5c-115">Если элемент программирования был объявлен, убедитесь, что он находится в области.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-115">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="5aa5c-116">Если инструкция, ссылающаяся на инструкцию, находится за пределами области, объявляющего программный элемент, может потребоваться уточнение имени элемента.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-116">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="5aa5c-117">Для получения дополнительной информации см. [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5c-117">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>

5. <span data-ttu-id="5aa5c-118">Если вы не используете полностью определенный тип или тип и имя члена (например, код ссылается на свойство, как `MethodInfo.Name` вместо `System.Reflection.MethodInfo.Name` ), добавьте [оператор Imports](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5c-118">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="5aa5c-119">Если вы пытаетесь скомпилировать проект в стиле пакета SDK (проект с \* VBPROJ-файлом, который начинается со строки `<Project Sdk="Microsoft.NET.Sdk">` ), а сообщение об ошибке ссылается на тип или член сборки Microsoft.VisualBasic.dll, настройте приложение для компиляции со ссылкой на библиотеку времени выполнения Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-119">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="5aa5c-120">По умолчанию подмножество библиотеки внедряется в сборку в проекте в стиле пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-120">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="5aa5c-121">Например, следующий пример не удается скомпилировать, так как <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> не удается найти метод.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-121">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="5aa5c-122">Он не внедряется в подмножество Visual Basic среды выполнения, входящей в состав приложения.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-122">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="5aa5c-123">Чтобы устранить эту ошибку, добавьте `<VBRuntime>Default</VBRuntime>` элемент в раздел Projects `<PropertyGroup>` , как показано в следующем Visual Basic файле проекта.</span><span class="sxs-lookup"><span data-stu-id="5aa5c-123">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="5aa5c-124">См. также</span><span class="sxs-lookup"><span data-stu-id="5aa5c-124">See also</span></span>

- [<span data-ttu-id="5aa5c-125">Сводка по объявлениям и константам</span><span class="sxs-lookup"><span data-stu-id="5aa5c-125">Declarations and Constants Summary</span></span>](../keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="5aa5c-126">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5aa5c-126">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="5aa5c-127">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="5aa5c-127">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="5aa5c-128">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="5aa5c-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
