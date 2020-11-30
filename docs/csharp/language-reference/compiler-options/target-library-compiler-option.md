---
description: -target:library (параметры компилятора C#)
title: -target:library (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193729"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="1085e-103">-target:library (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="1085e-103">-target:library (C# Compiler Options)</span></span>

<span data-ttu-id="1085e-104">Параметр **-target:library** заставляет компилятор создавать библиотеку динамической компоновки (DLL), а не исполняемый файл (EXE).</span><span class="sxs-lookup"><span data-stu-id="1085e-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1085e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1085e-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="1085e-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="1085e-106">Remarks</span></span>  

 <span data-ttu-id="1085e-107">Библиотека DLL создается с расширением DLL.</span><span class="sxs-lookup"><span data-stu-id="1085e-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="1085e-108">Выходной файл получает имя первого входного файла, если только с помощью параметра [-out](./out-compiler-option.md) не указано иное.</span><span class="sxs-lookup"><span data-stu-id="1085e-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="1085e-109">Для создания DLL-файла используются все файлы, указанные в командной строке до следующего параметра **-out** или **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="1085e-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="1085e-110">При построении библиотеки DLL метод [Main](../../programming-guide/main-and-command-args/index.md) не требуется.</span><span class="sxs-lookup"><span data-stu-id="1085e-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1085e-111">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1085e-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1085e-112">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="1085e-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1085e-113">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="1085e-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="1085e-114">Измените значение свойства **Тип выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="1085e-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="1085e-115">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1085e-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1085e-116">Пример</span><span class="sxs-lookup"><span data-stu-id="1085e-116">Example</span></span>  

 <span data-ttu-id="1085e-117">Компиляция файла`in.cs`, создание модуля `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="1085e-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1085e-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1085e-118">See also</span></span>

- [<span data-ttu-id="1085e-119">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="1085e-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="1085e-120">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="1085e-120">C# Compiler Options</span></span>](./index.md)
