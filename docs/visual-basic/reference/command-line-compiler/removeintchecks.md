---
description: 'Дополнительные сведения: -removeintchecks'
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: 1dc484e1538718b68fe9f0cc450fa2480dc52412
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474100"
---
# <a name="-removeintchecks"></a><span data-ttu-id="68c61-103">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="68c61-103">-removeintchecks</span></span>

<span data-ttu-id="68c61-104">Включает и отключает проверку условий переполнения для целочисленных операций.</span><span class="sxs-lookup"><span data-stu-id="68c61-104">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c61-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68c61-105">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="68c61-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="68c61-106">Arguments</span></span>  
  
|<span data-ttu-id="68c61-107">Термин</span><span class="sxs-lookup"><span data-stu-id="68c61-107">Term</span></span>|<span data-ttu-id="68c61-108">Определение</span><span class="sxs-lookup"><span data-stu-id="68c61-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="68c61-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="68c61-109">`+` &#124; `-`</span></span>|<span data-ttu-id="68c61-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="68c61-110">Optional.</span></span> <span data-ttu-id="68c61-111">Если задан параметр `-removeintchecks-`, компилятор проверяет условия переполнения всех целочисленных операций.</span><span class="sxs-lookup"><span data-stu-id="68c61-111">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="68c61-112">Значение по умолчанию — `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="68c61-112">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="68c61-113">Если задано `-removeintchecks` или `-removeintchecks+`, переполнение не проверяется и целочисленные вычисления выполняются быстрее.</span><span class="sxs-lookup"><span data-stu-id="68c61-113">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="68c61-114">Однако в случае переполнения типа данных при отключенной проверке переполнения могут сохраниться неверные результаты без отображения ошибки.</span><span class="sxs-lookup"><span data-stu-id="68c61-114">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="68c61-115">Задание параметра -removeintchecks в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68c61-115">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="68c61-116">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="68c61-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="68c61-117">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="68c61-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="68c61-118">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="68c61-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="68c61-119">3.  Нажмите кнопку **Дополнительно** .</span><span class="sxs-lookup"><span data-stu-id="68c61-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="68c61-120">4.  Установите флажок **Отключить проверку переполнения для целочисленных значений**.</span><span class="sxs-lookup"><span data-stu-id="68c61-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68c61-121">Пример</span><span class="sxs-lookup"><span data-stu-id="68c61-121">Example</span></span>  

 <span data-ttu-id="68c61-122">Следующий код компилирует `Test.vb` и отключает проверку переполнения целочисленных значений.</span><span class="sxs-lookup"><span data-stu-id="68c61-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="68c61-123">См. также</span><span class="sxs-lookup"><span data-stu-id="68c61-123">See also</span></span>

- [<span data-ttu-id="68c61-124">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="68c61-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="68c61-125">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="68c61-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
