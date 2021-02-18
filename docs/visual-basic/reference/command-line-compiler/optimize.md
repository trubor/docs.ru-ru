---
description: 'Дополнительные сведения: -optimize'
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 812eaa544dd874fd3871e58f366a34ee8176273a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426703"
---
# <a name="-optimize"></a><span data-ttu-id="f91ec-103">-optimize</span><span class="sxs-lookup"><span data-stu-id="f91ec-103">-optimize</span></span>

<span data-ttu-id="f91ec-104">Разрешает или запрещает оптимизацию компилятора.</span><span class="sxs-lookup"><span data-stu-id="f91ec-104">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91ec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f91ec-105">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f91ec-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f91ec-106">Arguments</span></span>  
  
|<span data-ttu-id="f91ec-107">Термин</span><span class="sxs-lookup"><span data-stu-id="f91ec-107">Term</span></span>|<span data-ttu-id="f91ec-108">Определение</span><span class="sxs-lookup"><span data-stu-id="f91ec-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f91ec-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f91ec-109">`+` &#124; `-`</span></span>|<span data-ttu-id="f91ec-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f91ec-110">Optional.</span></span> <span data-ttu-id="f91ec-111">Параметр `-optimize-` запрещает оптимизацию компилятора.</span><span class="sxs-lookup"><span data-stu-id="f91ec-111">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="f91ec-112">Параметр `-optimize+` разрешает оптимизацию компилятора.</span><span class="sxs-lookup"><span data-stu-id="f91ec-112">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="f91ec-113">По умолчанию оптимизация отключена.</span><span class="sxs-lookup"><span data-stu-id="f91ec-113">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f91ec-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="f91ec-114">Remarks</span></span>  

 <span data-ttu-id="f91ec-115">Оптимизации компилятора делают код более быстрым, коротким и эффективным.</span><span class="sxs-lookup"><span data-stu-id="f91ec-115">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="f91ec-116">Но поскольку оптимизация изменяет порядок строк кода в файле вывода, `-optimize+` может осложнить процесс отладки.</span><span class="sxs-lookup"><span data-stu-id="f91ec-116">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="f91ec-117">Все модули, созданные с помощью `-target:module` для сборки, должны использовать те же параметры `-optimize`, что и сборка.</span><span class="sxs-lookup"><span data-stu-id="f91ec-117">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="f91ec-118">Дополнительные сведения см. в разделе [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="f91ec-118">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="f91ec-119">Параметры `-optimize` и `-debug` можно объединить.</span><span class="sxs-lookup"><span data-stu-id="f91ec-119">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="f91ec-120">Задание параметра -optimize в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f91ec-120">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f91ec-121">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="f91ec-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f91ec-122">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="f91ec-122">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="f91ec-123">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="f91ec-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f91ec-124">3.  Нажмите кнопку **Дополнительно** .</span><span class="sxs-lookup"><span data-stu-id="f91ec-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f91ec-125">4.  Установите флажок **Включить оптимизацию**.</span><span class="sxs-lookup"><span data-stu-id="f91ec-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f91ec-126">Пример</span><span class="sxs-lookup"><span data-stu-id="f91ec-126">Example</span></span>  

 <span data-ttu-id="f91ec-127">Следующий код компилирует `T2.vb` и включает оптимизацию компилятора.</span><span class="sxs-lookup"><span data-stu-id="f91ec-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="f91ec-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f91ec-128">See also</span></span>

- [<span data-ttu-id="f91ec-129">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="f91ec-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f91ec-130">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f91ec-130">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="f91ec-131">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="f91ec-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="f91ec-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f91ec-132">-target (Visual Basic)</span></span>](target.md)
