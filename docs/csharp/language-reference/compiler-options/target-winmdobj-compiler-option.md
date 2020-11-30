---
description: -target:winmdobj (параметры компилятора C#)
title: -target:winmdobj (параметры компилятора C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: a13e2da02698209a514e716d65c1df3508cf1508
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171407"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="20ff5-103">-target:winmdobj (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="20ff5-103">-target:winmdobj (C# Compiler Options)</span></span>

<span data-ttu-id="20ff5-104">Если используется параметр компилятора **-target:winmdobj**, компилятор создает промежуточный WINMDOBJ-файл, который можно преобразовать в двоичный WINMD-файл среды выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="20ff5-104">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="20ff5-105">Затем WINMD-файл можно использовать в программах на языках JavaScript и C++ в дополнение к программам, использующим управляемые языки.</span><span class="sxs-lookup"><span data-stu-id="20ff5-105">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ff5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20ff5-106">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="20ff5-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="20ff5-107">Remarks</span></span>  

 <span data-ttu-id="20ff5-108">Параметр **winmdobj** сигнализирует компилятору, что необходим промежуточный модуль.</span><span class="sxs-lookup"><span data-stu-id="20ff5-108">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="20ff5-109">В результате Visual Studio компилирует библиотеку классов C# в виде WINMDOBJ-файла.</span><span class="sxs-lookup"><span data-stu-id="20ff5-109">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="20ff5-110">Затем WINMDOBJ-файл можно обработать с помощью инструмента экспорта <xref:Microsoft.Build.Tasks.WinMDExp> для создания файла метаданных Windows (WINCMD-файл).</span><span class="sxs-lookup"><span data-stu-id="20ff5-110">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="20ff5-111">WINMD-файл содержит код из исходной библиотеки и метаданные WinMD, используемые JavaScript, C++ и средой выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="20ff5-111">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="20ff5-112">Выходные данные файла, скомпилированного с помощью параметра **-target:winmdobj**, предназначены только для использования в качестве входных данных инструментом экспорта WimMDExp (на WINMDOBJ-файл нет прямой ссылки).</span><span class="sxs-lookup"><span data-stu-id="20ff5-112">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="20ff5-113">Выходной файл получает имя первого входного файла, если только с помощью параметра [-out](./out-compiler-option.md) не указано иное.</span><span class="sxs-lookup"><span data-stu-id="20ff5-113">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="20ff5-114">Метод [Main](../../programming-guide/main-and-command-args/index.md) не требуется.</span><span class="sxs-lookup"><span data-stu-id="20ff5-114">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="20ff5-115">Если параметр -target:winmdobj указан в командной строке, все файлы до следующего параметра **-out** или [-target:module](./target-module-compiler-option.md) будут использоваться для создания программы Windows.</span><span class="sxs-lookup"><span data-stu-id="20ff5-115">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="20ff5-116">Установка данного параметра компилятора в интегрированной среде разработки Visual Studio для приложения для Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="20ff5-116">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="20ff5-117">В **обозревателе решений** откройте контекстное меню своего проекта и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="20ff5-117">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="20ff5-118">Перейдите на вкладку **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="20ff5-118">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="20ff5-119">В списке **Тип выходных данных** выберите **Файл WinMD**.</span><span class="sxs-lookup"><span data-stu-id="20ff5-119">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="20ff5-120">Параметр **Файл WinMD** доступен только для шаблонов приложений Магазина Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="20ff5-120">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="20ff5-121">Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="20ff5-121">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ff5-122">Пример</span><span class="sxs-lookup"><span data-stu-id="20ff5-122">Example</span></span>  

 <span data-ttu-id="20ff5-123">Следующая команда компилирует `filename.cs` в промежуточный WINMDOBJ-файл.</span><span class="sxs-lookup"><span data-stu-id="20ff5-123">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="20ff5-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="20ff5-124">See also</span></span>

- [<span data-ttu-id="20ff5-125">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="20ff5-125">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="20ff5-126">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="20ff5-126">C# Compiler Options</span></span>](./index.md)
