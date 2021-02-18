---
description: 'Дополнительные сведения: -moduleassemblyname'
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 1b5daac8fea264e86b7200f3cead4cb657641000
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434320"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="b364d-103">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="b364d-103">-moduleassemblyname</span></span>

<span data-ttu-id="b364d-104">Задает имя сборки, частью которой будет этот модуль.</span><span class="sxs-lookup"><span data-stu-id="b364d-104">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b364d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b364d-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b364d-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="b364d-106">Arguments</span></span>  
  
|<span data-ttu-id="b364d-107">Термин</span><span class="sxs-lookup"><span data-stu-id="b364d-107">Term</span></span>|<span data-ttu-id="b364d-108">Определение</span><span class="sxs-lookup"><span data-stu-id="b364d-108">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="b364d-109">Имя сборки, частью которой будет этот модуль.</span><span class="sxs-lookup"><span data-stu-id="b364d-109">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b364d-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="b364d-110">Remarks</span></span>  

 <span data-ttu-id="b364d-111">Компилятор обрабатывает параметр `-moduleassemblyname` только в том случае, если был указан параметр `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="b364d-111">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="b364d-112">В результате компилятор создает модуль.</span><span class="sxs-lookup"><span data-stu-id="b364d-112">This causes the compiler to create a module.</span></span> <span data-ttu-id="b364d-113">Модуль, созданный компилятором, действителен только для сборки, указанной с помощью параметра `-moduleassemblyname`.</span><span class="sxs-lookup"><span data-stu-id="b364d-113">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="b364d-114">Если разместить модуль в другой сборке, возникнут ошибки во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b364d-114">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="b364d-115">Параметр `-moduleassemblyname` требуется только в том случае, если выполняются следующие условия:</span><span class="sxs-lookup"><span data-stu-id="b364d-115">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="b364d-116">Для типа данных в модуле требуется доступ к типу `Friend` в сборке, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="b364d-116">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="b364d-117">Сборка, на которую указывает ссылка, предоставила дружественной сборке доступ к сборке, в которую будет встроен модуль.</span><span class="sxs-lookup"><span data-stu-id="b364d-117">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="b364d-118">Дополнительные сведения о создании модуля см. в разделе [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="b364d-118">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="b364d-119">Дополнительные сведения о дружественных сборках см. в разделе [Дружественные сборки](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="b364d-119">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b364d-120">Параметр `-moduleassemblyname` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="b364d-120">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b364d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b364d-121">See also</span></span>

- [<span data-ttu-id="b364d-122">Практическое руководство. Создание многофайловой сборки</span><span class="sxs-lookup"><span data-stu-id="b364d-122">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="b364d-123">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="b364d-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b364d-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b364d-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="b364d-125">-main</span><span class="sxs-lookup"><span data-stu-id="b364d-125">-main</span></span>](main.md)
- [<span data-ttu-id="b364d-126">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b364d-126">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="b364d-127">-addmodule</span><span class="sxs-lookup"><span data-stu-id="b364d-127">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="b364d-128">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="b364d-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="b364d-129">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="b364d-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="b364d-130">Дружественные сборки</span><span class="sxs-lookup"><span data-stu-id="b364d-130">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
