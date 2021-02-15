---
description: 'Дополнительные сведения: Условная компиляция в Visual Basic'
title: Условная компиляция
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e9cb8a5af4dfbf2ffadef8edd8f6583614188391
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476141"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="365ef-103">Условная компиляция в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="365ef-103">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="365ef-104">В *условной компиляции* определенные блоки кода в программе компилируются выборочно, а другие игнорируются.</span><span class="sxs-lookup"><span data-stu-id="365ef-104">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="365ef-105">Например, может потребоваться написать инструкции отладки, которые сравнивают скорость различных подходов к одной задаче программирования, или вы можете локализовать приложение для нескольких языков.</span><span class="sxs-lookup"><span data-stu-id="365ef-105">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="365ef-106">Операторы условной компиляции предназначены для запуска во время компиляции, а не во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="365ef-106">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="365ef-107">Вы запишите блоки кода для условной компиляции с помощью `#If...Then...#Else` директивы.</span><span class="sxs-lookup"><span data-stu-id="365ef-107">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="365ef-108">Например, чтобы создать версии одного и того же приложения на французском и немецком языках из одного и того же исходного кода, необходимо внедрить в инструкции сегменты кода для конкретной платформы, `#If...Then` используя предопределенные константы `FrenchVersion` и `GermanVersion` .</span><span class="sxs-lookup"><span data-stu-id="365ef-108">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="365ef-109">В следующем примере показано, как:</span><span class="sxs-lookup"><span data-stu-id="365ef-109">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="365ef-110">Если `FrenchVersion` для константы условной компиляции задано значение `True` во время компиляции, то компилируется условный код для французской версии.</span><span class="sxs-lookup"><span data-stu-id="365ef-110">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="365ef-111">Если для константы задано значение `GermanVersion` `True` , компилятор использует немецкую версию.</span><span class="sxs-lookup"><span data-stu-id="365ef-111">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="365ef-112">Если ни один из них не имеет значение `True` , код в последнем `Else` блоке выполняется.</span><span class="sxs-lookup"><span data-stu-id="365ef-112">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="365ef-113">Автозаполнение не будет работать при редактировании кода и использовании директив условной компиляции, если код не является частью текущей ветви.</span><span class="sxs-lookup"><span data-stu-id="365ef-113">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="365ef-114">Объявление констант условной компиляции</span><span class="sxs-lookup"><span data-stu-id="365ef-114">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="365ef-115">Константы условной компиляции можно задать одним из трех способов:</span><span class="sxs-lookup"><span data-stu-id="365ef-115">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="365ef-116">В **конструкторе проектов**</span><span class="sxs-lookup"><span data-stu-id="365ef-116">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="365ef-117">В командной строке при использовании компилятора командной строки</span><span class="sxs-lookup"><span data-stu-id="365ef-117">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="365ef-118">В коде</span><span class="sxs-lookup"><span data-stu-id="365ef-118">In your code</span></span>  
  
 <span data-ttu-id="365ef-119">Константы условной компиляции имеют специальную область и недоступны из стандартного кода.</span><span class="sxs-lookup"><span data-stu-id="365ef-119">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="365ef-120">Область константы условной компиляции зависит от того, как она задана.</span><span class="sxs-lookup"><span data-stu-id="365ef-120">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="365ef-121">В следующей таблице перечислены области констант, объявленных с помощью каждого из трех описанных выше способов.</span><span class="sxs-lookup"><span data-stu-id="365ef-121">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="365ef-122">Как задается константа</span><span class="sxs-lookup"><span data-stu-id="365ef-122">How constant is set</span></span>|<span data-ttu-id="365ef-123">Область действия константы</span><span class="sxs-lookup"><span data-stu-id="365ef-123">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="365ef-124">**конструктор проектов**</span><span class="sxs-lookup"><span data-stu-id="365ef-124">**Project Designer**</span></span>|<span data-ttu-id="365ef-125">Открыт для всех файлов в проекте</span><span class="sxs-lookup"><span data-stu-id="365ef-125">Public to all files in the project</span></span>|  
|<span data-ttu-id="365ef-126">Командная строка</span><span class="sxs-lookup"><span data-stu-id="365ef-126">Command line</span></span>|<span data-ttu-id="365ef-127">Открытый для всех файлов, переданных компилятору командной строки</span><span class="sxs-lookup"><span data-stu-id="365ef-127">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="365ef-128">`#Const` оператор в коде</span><span class="sxs-lookup"><span data-stu-id="365ef-128">`#Const` statement in code</span></span>|<span data-ttu-id="365ef-129">Закрытый для файла, в котором он объявлен</span><span class="sxs-lookup"><span data-stu-id="365ef-129">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="365ef-130">Задание констант в конструкторе проектов</span><span class="sxs-lookup"><span data-stu-id="365ef-130">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="365ef-131">— Перед созданием исполняемого файла задайте константы в **конструкторе проектов** , выполнив действия, описанные в разделе [Управление свойствами проекта и решения](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="365ef-131">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="365ef-132">Задание констант в командной строке</span><span class="sxs-lookup"><span data-stu-id="365ef-132">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="365ef-133">— Используйте параметр **-d** , чтобы ввести константы условной компиляции, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="365ef-133">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="365ef-134">Между параметром **-d** и первой константой не должно быть пробелов.</span><span class="sxs-lookup"><span data-stu-id="365ef-134">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="365ef-135">Дополнительные сведения см. в разделе [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="365ef-135">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="365ef-136">Объявления из командной строки переопределяют объявления, указанные в **конструкторе проектов**, но не удаляют их.</span><span class="sxs-lookup"><span data-stu-id="365ef-136">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="365ef-137">Аргументы, заданные в **конструкторе проектов** , действуют для последующих компиляций.</span><span class="sxs-lookup"><span data-stu-id="365ef-137">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="365ef-138">При написании констант в самом коде нет никаких правил для их размещения, поскольку их областью действия является весь модуль, в котором они объявляются.</span><span class="sxs-lookup"><span data-stu-id="365ef-138">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="365ef-139">Задание констант в коде</span><span class="sxs-lookup"><span data-stu-id="365ef-139">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="365ef-140">-Поместите константы в блок объявления модуля, в котором они используются.</span><span class="sxs-lookup"><span data-stu-id="365ef-140">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="365ef-141">Это помогает организовать структурирование кода и облегчить его чтение.</span><span class="sxs-lookup"><span data-stu-id="365ef-141">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="365ef-142">См. также</span><span class="sxs-lookup"><span data-stu-id="365ef-142">Related Topics</span></span>  
  
|<span data-ttu-id="365ef-143">Заголовок</span><span class="sxs-lookup"><span data-stu-id="365ef-143">Title</span></span>|<span data-ttu-id="365ef-144">Описание</span><span class="sxs-lookup"><span data-stu-id="365ef-144">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="365ef-145">Соглашения о структуре программы и коде</span><span class="sxs-lookup"><span data-stu-id="365ef-145">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="365ef-146">Предоставляет рекомендации по упрощению чтения и сопровождения кода.</span><span class="sxs-lookup"><span data-stu-id="365ef-146">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="365ef-147">Справочник</span><span class="sxs-lookup"><span data-stu-id="365ef-147">Reference</span></span>  

 [<span data-ttu-id="365ef-148">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="365ef-148">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="365ef-149">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="365ef-149">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="365ef-150">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="365ef-150">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
