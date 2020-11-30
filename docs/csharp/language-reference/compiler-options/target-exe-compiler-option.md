---
description: -target:exe (параметры компилятора C#)
title: -target:exe (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: ae1706f1ecdd396e24711070d19420faa6d34761
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193767"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="67467-103">-target:exe (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="67467-103">-target:exe (C# Compiler Options)</span></span>

<span data-ttu-id="67467-104">Параметр **-target:exe** предписывает компилятору создать исполняемое (EXE) консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="67467-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67467-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="67467-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="67467-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="67467-106">Remarks</span></span>  

 <span data-ttu-id="67467-107">Параметр **-target:exe** действует по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="67467-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="67467-108">Исполняемый файл создается с расширением ЕХЕ.</span><span class="sxs-lookup"><span data-stu-id="67467-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="67467-109">Используйте параметр [-target:winexe](./target-winexe-compiler-option.md) для создания исполняемого файла программы Windows.</span><span class="sxs-lookup"><span data-stu-id="67467-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="67467-110">Если не указано иное с помощью параметра [-out](./out-compiler-option.md), имя выходного файла совпадает с именем входного файла, который содержит метод [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="67467-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="67467-111">Для создания EXE-файла используются все файлы, указанные в командной строке до следующего параметра **-out** или **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="67467-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="67467-112">В файлах исходного кода, который компилируется в EXE-файл, должен содержаться один и только один метод **Main**.</span><span class="sxs-lookup"><span data-stu-id="67467-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="67467-113">Если код содержит несколько классов с методом **Main**, то указать, какой класс содержит метод **Main**, можно с помощью параметра компилятора [-main](./main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="67467-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="67467-114">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67467-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="67467-115">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="67467-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="67467-116">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="67467-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="67467-117">Измените значение свойства **Тип выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="67467-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="67467-118">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="67467-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67467-119">Пример</span><span class="sxs-lookup"><span data-stu-id="67467-119">Example</span></span>  

 <span data-ttu-id="67467-120">В каждой из представленных ниже команд командной строки выполняется компиляция файла `in.cs` для создания файла `in.exe`.</span><span class="sxs-lookup"><span data-stu-id="67467-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="67467-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="67467-121">See also</span></span>

- [<span data-ttu-id="67467-122">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="67467-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="67467-123">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="67467-123">C# Compiler Options</span></span>](./index.md)
