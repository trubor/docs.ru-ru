---
description: -noconfig (параметры компилятора C#)
title: -noconfig (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: d62f16a3926aaa78e79c25b1c9b8d84e4401795a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194080"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="12a50-103">-noconfig (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="12a50-103">-noconfig (C# Compiler Options)</span></span>

<span data-ttu-id="12a50-104">Параметр **-noconfig** указывает компилятору не выполнять компиляцию с использованием файла csc.rsp, который располагается в том же каталоге, что и файл csc.exe, и загружается оттуда.</span><span class="sxs-lookup"><span data-stu-id="12a50-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a50-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12a50-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="12a50-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="12a50-106">Remarks</span></span>  

 <span data-ttu-id="12a50-107">Файл csc.rsp содержит ссылки на все сборки, поставляемые вместе с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12a50-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="12a50-108">Фактические ссылки, которые включает среда разработки Visual Studio .NET, зависят от типа проекта.</span><span class="sxs-lookup"><span data-stu-id="12a50-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="12a50-109">Вы можете изменить файл csc.rsp и указать дополнительные параметры компилятора, которые нужно включать при каждой компиляции, из командной строки с помощью программы csc.exe (кроме параметра **-noconfig**).</span><span class="sxs-lookup"><span data-stu-id="12a50-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="12a50-110">Компилятор обрабатывает параметры, передаваемые в команду **csc**, последними.</span><span class="sxs-lookup"><span data-stu-id="12a50-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="12a50-111">Таким образом, любой параметр командной строки переопределяет значение аналогичного параметра в файле csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="12a50-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="12a50-112">Если не требуется, чтобы компилятор искал и использовал параметры в файле csc.rsp, укажите параметр **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="12a50-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="12a50-113">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="12a50-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a50-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="12a50-114">See also</span></span>

- [<span data-ttu-id="12a50-115">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="12a50-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="12a50-116">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="12a50-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
