---
description: 'Дополнительные сведения: -warnaserror (Visual Basic)'
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 38fc2d70f95228c715ef5ac4bfc9b4fdb6f67c0e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470101"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="dd216-103">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd216-103">-warnaserror (Visual Basic)</span></span>

<span data-ttu-id="dd216-104">Приводит к тому, что компилятор обрабатывает первое появление предупреждения как ошибку.</span><span class="sxs-lookup"><span data-stu-id="dd216-104">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd216-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd216-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd216-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="dd216-106">Arguments</span></span>  
  
|<span data-ttu-id="dd216-107">Термин</span><span class="sxs-lookup"><span data-stu-id="dd216-107">Term</span></span>|<span data-ttu-id="dd216-108">Определение</span><span class="sxs-lookup"><span data-stu-id="dd216-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="dd216-109">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="dd216-109">+ &#124; -</span></span>|<span data-ttu-id="dd216-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dd216-110">Optional.</span></span> <span data-ttu-id="dd216-111">Параметр `-warnaserror-` включен по умолчанию. Предупреждения не препятствуют созданию выходного файла компилятором.</span><span class="sxs-lookup"><span data-stu-id="dd216-111">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="dd216-112">Если задан параметр `-warnaserror` или эквивалентный ему `-warnaserror+`, все предупреждения обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd216-112">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="dd216-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dd216-113">Optional.</span></span> <span data-ttu-id="dd216-114">Разделенный запятыми список с номерами идентификаторов предупреждений, к которому применим параметр `-warnaserror`.</span><span class="sxs-lookup"><span data-stu-id="dd216-114">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="dd216-115">Если идентификатор предупреждения не указан, параметр `-warnaserror` применяется ко всем предупреждениям.</span><span class="sxs-lookup"><span data-stu-id="dd216-115">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd216-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="dd216-116">Remarks</span></span>  

 <span data-ttu-id="dd216-117">Параметр `-warnaserror` обрабатывает все предупреждения как ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd216-117">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="dd216-118">Все сообщения, которые до этого получали статус предупреждений, будут возвращаться как ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd216-118">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="dd216-119">Компилятор сообщает о последующих появлениях того же предупреждения как о предупреждениях.</span><span class="sxs-lookup"><span data-stu-id="dd216-119">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="dd216-120">Параметр `-warnaserror-` включен по умолчанию, в результате чего предупреждения имеют только информационный характер.</span><span class="sxs-lookup"><span data-stu-id="dd216-120">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="dd216-121">Если задан параметр `-warnaserror` или эквивалентный ему `-warnaserror+`, все предупреждения обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd216-121">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="dd216-122">Если требуется обрабатывать как ошибки только конкретные предупреждения, укажите их номера через запятую.</span><span class="sxs-lookup"><span data-stu-id="dd216-122">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd216-123">Параметр `-warnaserror` не управляет способом отображения предупреждений.</span><span class="sxs-lookup"><span data-stu-id="dd216-123">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="dd216-124">Используйте параметр [-nowarn](nowarn.md), чтобы отключить предупреждения.</span><span class="sxs-lookup"><span data-stu-id="dd216-124">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="dd216-125">Настройка параметра -warnaserror для обработки всех предупреждений как ошибок в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd216-125">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="dd216-126">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="dd216-126">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dd216-127">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="dd216-127">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="dd216-128">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="dd216-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dd216-129">3.  Убедитесь, что флажок **Выключить все предупреждения** снят.</span><span class="sxs-lookup"><span data-stu-id="dd216-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="dd216-130">4.  Проверьте флажок **Обрабатывать все предупреждения как ошибки**.</span><span class="sxs-lookup"><span data-stu-id="dd216-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="dd216-131">Настройка параметра -warnaserror для обработки конкретных предупреждений как ошибок в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd216-131">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="dd216-132">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="dd216-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dd216-133">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="dd216-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="dd216-134">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="dd216-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dd216-135">3.  Убедитесь, что флажок **Выключить все предупреждения** снят.</span><span class="sxs-lookup"><span data-stu-id="dd216-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="dd216-136">4.  Убедитесь, что флажок **Обрабатывать все предупреждения как ошибки** снят.</span><span class="sxs-lookup"><span data-stu-id="dd216-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="dd216-137">5.  Выберите **Ошибка** в столбце **Уведомления** рядом с предупреждением, которое должно обрабатываться как ошибка.</span><span class="sxs-lookup"><span data-stu-id="dd216-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dd216-138">Пример</span><span class="sxs-lookup"><span data-stu-id="dd216-138">Example</span></span>  

 <span data-ttu-id="dd216-139">Следующий код компилирует `In.vb` и настраивает компилятор на отображение ошибки при первом появлении каждого обнаруженного предупреждения.</span><span class="sxs-lookup"><span data-stu-id="dd216-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="dd216-140">Пример</span><span class="sxs-lookup"><span data-stu-id="dd216-140">Example</span></span>  

 <span data-ttu-id="dd216-141">Следующий код компилирует `T2.vb` и обрабатывает как ошибку только предупреждение о неиспользуемых локальных переменных (42024).</span><span class="sxs-lookup"><span data-stu-id="dd216-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd216-142">См. также</span><span class="sxs-lookup"><span data-stu-id="dd216-142">See also</span></span>

- [<span data-ttu-id="dd216-143">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="dd216-143">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="dd216-144">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="dd216-144">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="dd216-145">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd216-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
