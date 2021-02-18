---
description: Дополнительные сведения:-rootnamespace
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 0e034999a65bf5294e63c8f9cec1a4ce4de39a4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474087"
---
# <a name="-rootnamespace"></a><span data-ttu-id="529e4-103">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="529e4-103">-rootnamespace</span></span>

<span data-ttu-id="529e4-104">Задает пространство имен для всех объявлений типов.</span><span class="sxs-lookup"><span data-stu-id="529e4-104">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="529e4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="529e4-105">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="529e4-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="529e4-106">Arguments</span></span>  
  
|<span data-ttu-id="529e4-107">Термин</span><span class="sxs-lookup"><span data-stu-id="529e4-107">Term</span></span>|<span data-ttu-id="529e4-108">Определение</span><span class="sxs-lookup"><span data-stu-id="529e4-108">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="529e4-109">Имя пространства имен, в котором должны быть заключены все объявления типов для текущего проекта.</span><span class="sxs-lookup"><span data-stu-id="529e4-109">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="529e4-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="529e4-110">Remarks</span></span>  

 <span data-ttu-id="529e4-111">Если вы используете исполняемый файл Visual Studio (Devenv.exe) для компиляции проекта, созданного в интегрированной среде разработки Visual Studio, используйте `-rootnamespace`, чтобы указать значение свойства <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="529e4-111">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="529e4-112">Дополнительные сведения см. в разделе [Параметры командной строки для команды Devenv](/visualstudio/ide/reference/devenv-command-line-switches).</span><span class="sxs-lookup"><span data-stu-id="529e4-112">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="529e4-113">Используйте дизассемблер MSIL среды CLR (`Ildasm.exe`) для просмотра имен пространств имен в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="529e4-113">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="529e4-114">Задание параметра -rootnamespace в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="529e4-114">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="529e4-115">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="529e4-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="529e4-116">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="529e4-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="529e4-117">2.  Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="529e4-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="529e4-118">3.  Измените значение в поле **Корневое пространство имен**.</span><span class="sxs-lookup"><span data-stu-id="529e4-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="529e4-119">Пример</span><span class="sxs-lookup"><span data-stu-id="529e4-119">Example</span></span>  

 <span data-ttu-id="529e4-120">Следующий код компилирует `In.vb` и заключает все объявления типов в пространство имен `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="529e4-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="529e4-121">См. также</span><span class="sxs-lookup"><span data-stu-id="529e4-121">See also</span></span>

- [<span data-ttu-id="529e4-122">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="529e4-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="529e4-123">Ildasm.exe (дизассемблер IL)</span><span class="sxs-lookup"><span data-stu-id="529e4-123">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="529e4-124">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="529e4-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
