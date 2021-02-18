---
description: 'Дополнительные сведения: -out (Visual Basic)'
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 82fb43ecf2239c38245f3afe7cacef8bad573175
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475894"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="1565e-103">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1565e-103">-out (Visual Basic)</span></span>

<span data-ttu-id="1565e-104">Задает имя выходного файла.</span><span class="sxs-lookup"><span data-stu-id="1565e-104">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1565e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1565e-105">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1565e-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="1565e-106">Arguments</span></span>  
  
|<span data-ttu-id="1565e-107">Термин</span><span class="sxs-lookup"><span data-stu-id="1565e-107">Term</span></span>|<span data-ttu-id="1565e-108">Определение</span><span class="sxs-lookup"><span data-stu-id="1565e-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="1565e-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="1565e-109">Required.</span></span> <span data-ttu-id="1565e-110">Имя выходного файла, создаваемого компилятором.</span><span class="sxs-lookup"><span data-stu-id="1565e-110">The name of the output file the compiler creates.</span></span> <span data-ttu-id="1565e-111">Если имя файла содержит пробел, заключите его в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="1565e-111">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1565e-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="1565e-112">Remarks</span></span>  

 <span data-ttu-id="1565e-113">Укажите полное имя и расширение создаваемого файла.</span><span class="sxs-lookup"><span data-stu-id="1565e-113">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="1565e-114">В противном случае этот EXE-файл именуется по файлу исходного кода, содержащему процедуру `Sub Main`, а DLL-файл именуется по первому файлу исходного кода.</span><span class="sxs-lookup"><span data-stu-id="1565e-114">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="1565e-115">Если указать имя файла без расширения EXE или DLL, компилятор автоматически добавляет расширение в зависимости от значения, указанного для параметра компилятора `-target`.</span><span class="sxs-lookup"><span data-stu-id="1565e-115">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="1565e-116">Настройка параметра -out в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1565e-116">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1565e-117">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="1565e-117">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1565e-118">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="1565e-118">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1565e-119">2.  Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="1565e-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1565e-120">3.  Измените значение в поле **Имя сборки**.</span><span class="sxs-lookup"><span data-stu-id="1565e-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1565e-121">Пример</span><span class="sxs-lookup"><span data-stu-id="1565e-121">Example</span></span>  

 <span data-ttu-id="1565e-122">Следующий код компилирует `T2.vb` и создает выходной файл `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="1565e-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="1565e-123">См. также</span><span class="sxs-lookup"><span data-stu-id="1565e-123">See also</span></span>

- [<span data-ttu-id="1565e-124">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="1565e-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1565e-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1565e-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="1565e-126">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="1565e-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
