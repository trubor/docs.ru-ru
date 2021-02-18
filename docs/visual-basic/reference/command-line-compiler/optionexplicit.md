---
description: 'Дополнительные сведения: -optionexplicit'
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 4d1ab14bbf9de176de17fb5077f4bb919f5472b4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433566"
---
# <a name="-optionexplicit"></a><span data-ttu-id="d9555-103">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="d9555-103">-optionexplicit</span></span>

<span data-ttu-id="d9555-104">Заставляет компилятор сообщать об ошибках, если переменные не объявляются до их использования.</span><span class="sxs-lookup"><span data-stu-id="d9555-104">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9555-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9555-105">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9555-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d9555-106">Arguments</span></span>  

 <span data-ttu-id="d9555-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d9555-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d9555-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="d9555-108">Optional.</span></span> <span data-ttu-id="d9555-109">Чтобы сделать явное объявление переменных обязательным, укажите `-optionexplicit+`.</span><span class="sxs-lookup"><span data-stu-id="d9555-109">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="d9555-110">Параметр `-optionexplicit+` используется по умолчанию и аналогичен параметру `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="d9555-110">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="d9555-111">Используйте параметр `-optionexplicit-`, чтобы разрешить неявное объявление переменных.</span><span class="sxs-lookup"><span data-stu-id="d9555-111">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9555-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="d9555-112">Remarks</span></span>  

 <span data-ttu-id="d9555-113">Если файл исходного кода содержит [оператор Option Explicit](../../language-reference/statements/option-explicit-statement.md), этот оператор переопределяет параметр компилятора командной строки `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="d9555-113">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="d9555-114">Как задать параметр -optionexplicit в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9555-114">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="d9555-115">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="d9555-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d9555-116">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="d9555-116">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="d9555-117">Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="d9555-117">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="d9555-118">Измените значение в поле **Option Explicit**.</span><span class="sxs-lookup"><span data-stu-id="d9555-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9555-119">Пример</span><span class="sxs-lookup"><span data-stu-id="d9555-119">Example</span></span>  

 <span data-ttu-id="d9555-120">Следующий код компилируется, когда используется параметр `-optionexplicit-`.</span><span class="sxs-lookup"><span data-stu-id="d9555-120">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d9555-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d9555-121">See also</span></span>

- [<span data-ttu-id="d9555-122">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="d9555-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d9555-123">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="d9555-123">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="d9555-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="d9555-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="d9555-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d9555-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="d9555-126">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="d9555-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="d9555-127">Оператор Option Explicit</span><span class="sxs-lookup"><span data-stu-id="d9555-127">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="d9555-128">Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"</span><span class="sxs-lookup"><span data-stu-id="d9555-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
