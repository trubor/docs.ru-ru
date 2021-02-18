---
description: 'Дополнительные сведения: -platform (Visual Basic)'
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 51d7c7882c29310ef1e0c0f5790a63da3bfb91b8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432745"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="3cc1c-103">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cc1c-103">-platform (Visual Basic)</span></span>

<span data-ttu-id="3cc1c-104">Указывает, на какой версии платформы среды CLR может запускаться выходной файл.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-104">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc1c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3cc1c-105">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cc1c-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3cc1c-106">Arguments</span></span>  
  
|<span data-ttu-id="3cc1c-107">Термин</span><span class="sxs-lookup"><span data-stu-id="3cc1c-107">Term</span></span>|<span data-ttu-id="3cc1c-108">Определение</span><span class="sxs-lookup"><span data-stu-id="3cc1c-108">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="3cc1c-109">Компилирует сбору для запуска в 32-разрядной среде CLR с архитектурой x86.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-109">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="3cc1c-110">Компилирует сбору для запуска в 64-разрядной среде CLR на компьютере, поддерживающем набор инструкций AMD64 или EM64T.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-110">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="3cc1c-111">Компилирует сбору для запуска в 64-разрядной среде CLR на компьютере с процессором Itanium.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-111">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="3cc1c-112">Компилирует сбору для запуска на компьютере с процессором ARM.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-112">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="3cc1c-113">Компилирует сбору для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-113">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="3cc1c-114">Приложение будет выполняться как 32-разрядное приложение в 32-разрядных версиях Windows и как 64-разрядное приложение в 64-разрядных версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-114">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="3cc1c-115">Этот флаг — значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-115">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="3cc1c-116">Компилирует сбору для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-116">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="3cc1c-117">Приложение будет выполняться как 32-разрядное приложение в 32-разрядных и 64-разрядных версиях Windows.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-117">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="3cc1c-118">Этот флаг действителен только для исполняемых файлов (с расширением EXE). Для него требуется платформа .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-118">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cc1c-119">Примечания</span><span class="sxs-lookup"><span data-stu-id="3cc1c-119">Remarks</span></span>  

 <span data-ttu-id="3cc1c-120">Используйте параметр `-platform`, чтобы указать процессор назначения для выходного файла.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-120">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="3cc1c-121">В целом, сборки .NET Framework, написанные на Visual Basic, будут работать одинаково вне зависимости от платформы.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-121">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="3cc1c-122">Тем не менее, в некоторых случаях поведение программ на разных платформах может различаться.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-122">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="3cc1c-123">Вот эти случаи:</span><span class="sxs-lookup"><span data-stu-id="3cc1c-123">These common cases are:</span></span>  
  
- <span data-ttu-id="3cc1c-124">Структуры, содержащие члены, размер которых изменяется в зависимости от платформы, например, любые типы указателей.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-124">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="3cc1c-125">Арифметика указателя, содержащая постоянные размеры.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-125">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="3cc1c-126">Неверный вызов платформ или объявления СОМ, использующие дескрипторы `Integer` вместо <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-126">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="3cc1c-127">Приведение <xref:System.IntPtr> к `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-127">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="3cc1c-128">Использование вызов платформ или взаимодействия СОМ с компонентами, существующими не на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-128">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="3cc1c-129">Параметр **-platform** позволит устранить некоторые проблемы, если известна архитектура, в которой будет выполняться ваш код.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-129">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="3cc1c-130">В частности:</span><span class="sxs-lookup"><span data-stu-id="3cc1c-130">Specifically:</span></span>  
  
- <span data-ttu-id="3cc1c-131">Если целевой является 64-разрядная платформа, а приложение запущено на 32-разрядном компьютере, сообщение об ошибке появится гораздо раньше и будет более точным, чем сообщение об ошибке, которое появится без этого параметра.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-131">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="3cc1c-132">Если задать флаг `x86` для параметра, а потом запустить приложение на 64-разрядном компьютере, приложение будет запущено в подсистеме WOW, а не непосредственно.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-132">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="3cc1c-133">В 64-разрядной ОС Windows:</span><span class="sxs-lookup"><span data-stu-id="3cc1c-133">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="3cc1c-134">Сборки, скомпилированные с параметром `-platform:x86`, будут выполняться в 32-разрядной среде CLR с WOW64.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-134">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="3cc1c-135">Исполняемые файлы, скомпилированные с параметром `-platform:anycpu`, будут выполняться в 64-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-135">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="3cc1c-136">Библиотеки DLL, скомпилированные с параметром `-platform:anycpu`, будут выполняться в тоже де среде CLR, что и процесс, загрузивший эти библиотеки.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-136">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="3cc1c-137">Исполняемые файлы, скомпилированные с параметром `-platform:anycpu32bitpreferred`, будут выполняться в 32-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-137">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="3cc1c-138">Дополнительные сведения о разработке приложений для 64-разрядных версий Windows см. в разделе [64-разрядные приложения](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3cc1c-138">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="3cc1c-139">Как задать параметр -platform в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3cc1c-139">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="3cc1c-140">В **обозревателе решений** выберите проект, откройте меню **Проект** и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-140">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="3cc1c-141">На вкладке **Компиляция** установите или снимите флажок **Предпочитать 32-разрядн.** или выберите значение в списке **Целевой ЦП**.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="3cc1c-142">Дополнительные сведения см. в разделе [Страница приложения в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3cc1c-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc1c-143">Пример</span><span class="sxs-lookup"><span data-stu-id="3cc1c-143">Example</span></span>  

 <span data-ttu-id="3cc1c-144">В следующем примере показано использование параметра компилятора `-platform`.</span><span class="sxs-lookup"><span data-stu-id="3cc1c-144">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cc1c-145">См. также</span><span class="sxs-lookup"><span data-stu-id="3cc1c-145">See also</span></span>

- [<span data-ttu-id="3cc1c-146">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cc1c-146">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="3cc1c-147">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="3cc1c-147">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3cc1c-148">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="3cc1c-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
