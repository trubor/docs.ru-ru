---
description: -target:module (параметры компилятора C#)
title: -target:module (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193612"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="85045-103">-target:module (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="85045-103">-target:module (C# Compiler Options)</span></span>

<span data-ttu-id="85045-104">Этот параметр указывает компилятору не создавать манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="85045-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85045-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85045-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="85045-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="85045-106">Remarks</span></span>  

 <span data-ttu-id="85045-107">По умолчанию выходной файл, созданный при компиляции с этим параметром, имеет расширение .netmodule.</span><span class="sxs-lookup"><span data-stu-id="85045-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="85045-108">Файл без манифеста сборки не может быть загружен в общеязыковую среду выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="85045-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="85045-109">Тем не менее его можно включить в манифест сборки с помощью параметра [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="85045-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="85045-110">Если в рамках одной процедуры компиляции создается несколько модулей, типы [internal](../keywords/internal.md) из одного модуля будут доступны для других модулей, компилируемых вместе с ним.</span><span class="sxs-lookup"><span data-stu-id="85045-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="85045-111">Если код одного модуля ссылается на типы `internal` в другом модуле, оба модуля нужно включить в манифест сборки с помощью параметра **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="85045-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="85045-112">Создание модуля в среде разработки Visual Studio не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="85045-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="85045-113">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="85045-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85045-114">Пример</span><span class="sxs-lookup"><span data-stu-id="85045-114">Example</span></span>  

 <span data-ttu-id="85045-115">Компиляция файла`in.cs`, создание модуля `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="85045-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="85045-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="85045-116">See also</span></span>

- [<span data-ttu-id="85045-117">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="85045-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="85045-118">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="85045-118">C# Compiler Options</span></span>](./index.md)
