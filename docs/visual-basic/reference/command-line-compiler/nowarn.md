---
description: 'Дополнительные сведения: -nowarn'
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 4fb7d39aef48ff1443c342367f9e20bb37f9c5e0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434866"
---
# <a name="-nowarn"></a><span data-ttu-id="26336-103">-nowarn</span><span class="sxs-lookup"><span data-stu-id="26336-103">-nowarn</span></span>

<span data-ttu-id="26336-104">Отключает возможность компилятора создавать предупреждения.</span><span class="sxs-lookup"><span data-stu-id="26336-104">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26336-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26336-105">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="26336-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="26336-106">Arguments</span></span>  
  
|<span data-ttu-id="26336-107">Термин</span><span class="sxs-lookup"><span data-stu-id="26336-107">Term</span></span>|<span data-ttu-id="26336-108">Определение</span><span class="sxs-lookup"><span data-stu-id="26336-108">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="26336-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="26336-109">Optional.</span></span> <span data-ttu-id="26336-110">Разделенный запятыми список с идентификаторами предупреждений, которые должен подавлять компилятор.</span><span class="sxs-lookup"><span data-stu-id="26336-110">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="26336-111">Если идентификаторы предупреждений не указаны, подавляются все предупреждения.</span><span class="sxs-lookup"><span data-stu-id="26336-111">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26336-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="26336-112">Remarks</span></span>  

 <span data-ttu-id="26336-113">Параметр `-nowarn` указывает компилятору не генерировать предупреждения.</span><span class="sxs-lookup"><span data-stu-id="26336-113">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="26336-114">Чтобы подавить отдельное предупреждение, укажите идентификатор предупреждения в параметре `-nowarn` после двоеточия.</span><span class="sxs-lookup"><span data-stu-id="26336-114">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="26336-115">Можно указать несколько кодов предупреждений, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="26336-115">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="26336-116">Указывайте только числовую часть идентификатора предупреждения.</span><span class="sxs-lookup"><span data-stu-id="26336-116">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="26336-117">Например, если вы хотите подавить предупреждение BC42024, которое создается для неиспользуемых локальных переменных, укажите `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="26336-117">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="26336-118">Дополнительные сведения о идентификаторах предупреждений см. в статье [Настройка предупреждений в Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26336-118">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="26336-119">Задание параметра -nowarn в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26336-119">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="26336-120">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="26336-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="26336-121">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="26336-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="26336-122">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="26336-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="26336-123">3.  Установите флажок **Выключить все предупреждения**, чтобы полностью отключить предупреждения.</span><span class="sxs-lookup"><span data-stu-id="26336-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="26336-124">-или-</span><span class="sxs-lookup"><span data-stu-id="26336-124">- or -</span></span><br />     <span data-ttu-id="26336-125">Чтобы отключить конкретное предупреждение, выберите **Нет** из раскрывающегося списка рядом с предупреждением.</span><span class="sxs-lookup"><span data-stu-id="26336-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="26336-126">Пример</span><span class="sxs-lookup"><span data-stu-id="26336-126">Example</span></span>  

 <span data-ttu-id="26336-127">Следующий код компилирует `T2.vb` и не отображает никаких предупреждений.</span><span class="sxs-lookup"><span data-stu-id="26336-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="26336-128">Пример</span><span class="sxs-lookup"><span data-stu-id="26336-128">Example</span></span>  

 <span data-ttu-id="26336-129">Следующий код компилирует `T2.vb` и не отображает предупреждений о неиспользуемых локальных переменных (42024).</span><span class="sxs-lookup"><span data-stu-id="26336-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="26336-130">См. также</span><span class="sxs-lookup"><span data-stu-id="26336-130">See also</span></span>

- [<span data-ttu-id="26336-131">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="26336-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="26336-132">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="26336-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="26336-133">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26336-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
