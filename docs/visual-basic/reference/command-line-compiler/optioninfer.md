---
description: 'Дополнительные сведения: -optioninfer'
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d45761914612a28788cc5c1a848d92238f05c162
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475920"
---
# <a name="-optioninfer"></a><span data-ttu-id="5420a-103">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5420a-103">-optioninfer</span></span>

<span data-ttu-id="5420a-104">Включает использование локального определения типов в различных объявлениях.</span><span class="sxs-lookup"><span data-stu-id="5420a-104">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5420a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5420a-105">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5420a-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5420a-106">Arguments</span></span>  
  
|<span data-ttu-id="5420a-107">Термин</span><span class="sxs-lookup"><span data-stu-id="5420a-107">Term</span></span>|<span data-ttu-id="5420a-108">Определение</span><span class="sxs-lookup"><span data-stu-id="5420a-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="5420a-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5420a-109">`+` &#124; `-`</span></span>|<span data-ttu-id="5420a-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="5420a-110">Optional.</span></span> <span data-ttu-id="5420a-111">Укажите `-optioninfer+`, чтобы включить локальное определение типов, или `-optioninfer-`, чтобы заблокировать его.</span><span class="sxs-lookup"><span data-stu-id="5420a-111">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="5420a-112">Параметр `-optioninfer`, для которого не указано значение, действует так же, как `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="5420a-112">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="5420a-113">Значение по умолчанию при отсутствии параметра `-optioninfer` также равно `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="5420a-113">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="5420a-114">Значение по умолчанию задается в файле ответов Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="5420a-114">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="5420a-115">Можно использовать параметр `-noconfig`, чтобы сохранить внутренние значения компилятора по умолчанию вместо использования значений, заданных в vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="5420a-115">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="5420a-116">Значение компилятора по умолчанию для этого параметра — `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="5420a-116">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5420a-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="5420a-117">Remarks</span></span>  

 <span data-ttu-id="5420a-118">Если файл исходного кода содержит [оператор Option Infer](../../language-reference/statements/option-infer-statement.md), этот оператор переопределяет параметр компилятора командной строки `-optioninfer`.</span><span class="sxs-lookup"><span data-stu-id="5420a-118">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="5420a-119">Порядок задания параметра -optioninfer в среде Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="5420a-119">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5420a-120">Выберите проект в **обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="5420a-120">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="5420a-121">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="5420a-121">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="5420a-122">На вкладке **Компиляция** измените значение в поле **Option infer**.</span><span class="sxs-lookup"><span data-stu-id="5420a-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5420a-123">Пример</span><span class="sxs-lookup"><span data-stu-id="5420a-123">Example</span></span>  

 <span data-ttu-id="5420a-124">Следующий код компилирует `test.vb` с включенным локальным определением типов.</span><span class="sxs-lookup"><span data-stu-id="5420a-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5420a-125">См. также</span><span class="sxs-lookup"><span data-stu-id="5420a-125">See also</span></span>

- [<span data-ttu-id="5420a-126">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="5420a-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5420a-127">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="5420a-127">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="5420a-128">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5420a-128">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="5420a-129">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="5420a-129">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="5420a-130">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="5420a-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="5420a-131">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="5420a-131">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="5420a-132">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="5420a-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="5420a-133">Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"</span><span class="sxs-lookup"><span data-stu-id="5420a-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="5420a-134">Страница "Компиляция" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5420a-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="5420a-135">-noconfig</span><span class="sxs-lookup"><span data-stu-id="5420a-135">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="5420a-136">Построение из командной строки</span><span class="sxs-lookup"><span data-stu-id="5420a-136">Building from the Command Line</span></span>](building-from-the-command-line.md)
