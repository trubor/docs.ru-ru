---
description: -bugreport (параметры компилятора C#)
title: -bugreport (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 1fb2efc9b12680e95767746c7e4e1ddacbdd2594
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "93281510"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="a4b65-103">-bugreport (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="a4b65-103">-bugreport (C# Compiler Options)</span></span>

<span data-ttu-id="a4b65-104">Указывает, что отладочную информацию следует поместить в файл для последующего анализа.</span><span class="sxs-lookup"><span data-stu-id="a4b65-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b65-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4b65-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4b65-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="a4b65-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="a4b65-107">Имя файла, который будет содержать отчет об ошибках.</span><span class="sxs-lookup"><span data-stu-id="a4b65-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4b65-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="a4b65-108">Remarks</span></span>  

 <span data-ttu-id="a4b65-109">Параметр **-bugreport** указывает, что в `file` нужно поместить следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="a4b65-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="a4b65-110">Копия всех файлов исходного кода, включенных в компиляцию.</span><span class="sxs-lookup"><span data-stu-id="a4b65-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="a4b65-111">Список параметров компилятора, используемых при компиляции.</span><span class="sxs-lookup"><span data-stu-id="a4b65-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="a4b65-112">Сведения о версии компилятора, среды выполнения и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="a4b65-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="a4b65-113">Сборки и модули, на которые задаются ссылки, в формате шестнадцатеричных чисел, за исключением сборок, поставляемых с .NET и .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="a4b65-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that are shipped with .NET and the .NET SDK.</span></span>  
  
- <span data-ttu-id="a4b65-114">Выходные данные компилятора (если есть).</span><span class="sxs-lookup"><span data-stu-id="a4b65-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="a4b65-115">Описание проблемы, которое вам потребуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="a4b65-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="a4b65-116">Описание предполагаемого способа разрешения проблемы, которое вам потребуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="a4b65-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="a4b65-117">Если этот параметр используется с параметром **-errorreport:prompt** или **-errorreport:send**, содержимое файла будет передано в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a4b65-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="a4b65-118">Поскольку в `file` будут помещены копии всех файлов исходного кода, рекомендуется воспроизводить предполагаемую ошибку в коде с использованием максимально короткой программы.</span><span class="sxs-lookup"><span data-stu-id="a4b65-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="a4b65-119">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="a4b65-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="a4b65-120">Обратите внимание, что содержимое созданного файла раскрывает исходный код, что может привести к непреднамеренному разглашению информации.</span><span class="sxs-lookup"><span data-stu-id="a4b65-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b65-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4b65-121">See also</span></span>

- [<span data-ttu-id="a4b65-122">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="a4b65-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a4b65-123">-errorreport (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="a4b65-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="a4b65-124">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="a4b65-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
