---
description: 'Дополнительные сведения: -win32icon'
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 32a46771012708a42beb5450d28daf2fbab3f1c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433553"
---
# <a name="-win32icon"></a><span data-ttu-id="0fba8-103">-win32icon</span><span class="sxs-lookup"><span data-stu-id="0fba8-103">-win32icon</span></span>

<span data-ttu-id="0fba8-104">Внедряет ICO-файл в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="0fba8-104">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="0fba8-105">Этот ICO-файл представляет выходной файл в **проводнике**.</span><span class="sxs-lookup"><span data-stu-id="0fba8-105">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fba8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fba8-106">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0fba8-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="0fba8-107">Arguments</span></span>  
  
|<span data-ttu-id="0fba8-108">Термин</span><span class="sxs-lookup"><span data-stu-id="0fba8-108">Term</span></span>|<span data-ttu-id="0fba8-109">Определение</span><span class="sxs-lookup"><span data-stu-id="0fba8-109">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="0fba8-110">ICO-файл, который требуется добавить в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="0fba8-110">The .ico file to add to your output file.</span></span> <span data-ttu-id="0fba8-111">Если имя файла содержит пробел, заключите это имя в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="0fba8-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fba8-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="0fba8-112">Remarks</span></span>  

 <span data-ttu-id="0fba8-113">Вы можете создать ICO-файл с помощью компилятора ресурсов Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="0fba8-113">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="0fba8-114">Компилятор ресурсов вызывается при компиляции программы Visual C++. При этом ICO-файл создается из RC-файла.</span><span class="sxs-lookup"><span data-stu-id="0fba8-114">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="0fba8-115">Параметры `-win32icon` и `-win32resource` являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="0fba8-115">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0fba8-116">Чтобы создать ссылку на файл ресурсов .NET Framework, см. раздел [-linkresource (Visual Basic)](linkresource.md). Чтобы присоединить файл ресурсов .NET, см. раздел [-resource (Visual Basic)](resource.md).</span><span class="sxs-lookup"><span data-stu-id="0fba8-116">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="0fba8-117">См. сведения об импорте RES-файла в разделе [-win32resource](win32resource.md).</span><span class="sxs-lookup"><span data-stu-id="0fba8-117">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="0fba8-118">Чтобы задать параметр -win32icon в Visual Studio IDE, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="0fba8-118">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="0fba8-119">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="0fba8-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0fba8-120">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="0fba8-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0fba8-121">2.  Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="0fba8-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="0fba8-122">3.  Измените значение в поле **Значок**.</span><span class="sxs-lookup"><span data-stu-id="0fba8-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fba8-123">Пример</span><span class="sxs-lookup"><span data-stu-id="0fba8-123">Example</span></span>  

 <span data-ttu-id="0fba8-124">Следующий код компилирует `In.vb` и присоединяет ICO-файл `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="0fba8-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fba8-125">См. также</span><span class="sxs-lookup"><span data-stu-id="0fba8-125">See also</span></span>

- [<span data-ttu-id="0fba8-126">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="0fba8-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0fba8-127">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="0fba8-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
