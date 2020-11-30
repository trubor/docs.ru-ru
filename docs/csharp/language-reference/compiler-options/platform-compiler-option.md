---
description: -platform (параметры компилятора C#)
title: -platform (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 3fdb030dfc141b011f5faa827a4e4bb45ae38d19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89466018"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="34c31-103">-platform (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="34c31-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="34c31-104">Указывает, в какой версии среды CLR может запускаться сборка.</span><span class="sxs-lookup"><span data-stu-id="34c31-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="34c31-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="34c31-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="34c31-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="34c31-106">Parameters</span></span>

`string` \
<span data-ttu-id="34c31-107">anycpu (по умолчанию), anycpu32bitpreferred, ARM, x64, x86 или Itanium.</span><span class="sxs-lookup"><span data-stu-id="34c31-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="34c31-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="34c31-108">Remarks</span></span>

- <span data-ttu-id="34c31-109">**anycpu** (по умолчанию) позволяет компилировать сборку для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="34c31-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="34c31-110">Если возможно, приложение выполняется как 64-разрядный процесс, а если доступен только 32-разрядный режим, переключается на него.</span><span class="sxs-lookup"><span data-stu-id="34c31-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="34c31-111">**anycpu32bitpreferred** (по умолчанию) позволяет компилировать сборку для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="34c31-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="34c31-112">Приложение выполняется в 32-разрядном режиме в системах, поддерживающих и 64-разрядные, и 32-разрядные приложения.</span><span class="sxs-lookup"><span data-stu-id="34c31-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="34c31-113">Можно задать этот параметр только для проектов, предназначенных для .NET Framework 4.5 и выше.</span><span class="sxs-lookup"><span data-stu-id="34c31-113">You can specify this option only for projects that target .NET Framework 4.5 or later.</span></span>

- <span data-ttu-id="34c31-114">**ARM** компилирует сборку для выполнения на компьютере с процессором Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="34c31-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="34c31-115">**ARM64** компилирует сборку для выполнения 64-разрядной средой CLR на компьютере с процессором Advanced RISC Machine (ARM) с поддержкой набора инструкций А64.</span><span class="sxs-lookup"><span data-stu-id="34c31-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="34c31-116">**x64** компилирует сборку для запуска в 64-разрядной среде CLR на компьютере, поддерживающем набор инструкций AMD64 или EM64T.</span><span class="sxs-lookup"><span data-stu-id="34c31-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="34c31-117">**x86** компилирует сборку для запуска в 32-разрядной среде CLR с архитектурой x86.</span><span class="sxs-lookup"><span data-stu-id="34c31-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="34c31-118">**Itanium** компилирует сборку для запуска в 64-разрядной среде CLR на компьютере с процессором Itanium.</span><span class="sxs-lookup"><span data-stu-id="34c31-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="34c31-119">В 64-разрядной ОС Windows:</span><span class="sxs-lookup"><span data-stu-id="34c31-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="34c31-120">Сборки, скомпилированные с параметром **-platform:x86**, будут выполняться в 32-разрядной среде CLR с WOW64.</span><span class="sxs-lookup"><span data-stu-id="34c31-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="34c31-121">Библиотека DLL, скомпилированная с использованием параметра **-platform:anycpu**, выполняется в той же среде CLR, в которую загружается процесс.</span><span class="sxs-lookup"><span data-stu-id="34c31-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="34c31-122">Исполняемые файлы, скомпилированные с использованием параметра **-platform:anycpu**, выполняются в 64-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="34c31-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="34c31-123">Исполняемые файлы, скомпилированные с использованием параметра **-platform:anycpu32bitpreferred**, выполняются в 32-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="34c31-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="34c31-124">Параметр **anycpu32bitpreferred** является допустимым только для исполняемых файлов (.exe). Он используется только с .NET Framework 4.5 и выше.</span><span class="sxs-lookup"><span data-stu-id="34c31-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires .NET Framework 4.5 or later.</span></span>

<span data-ttu-id="34c31-125">Дополнительные сведения о разработке приложений для запуска в 64-разрядной операционной системе Windows см. в разделе [64-разрядные приложения](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="34c31-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="34c31-126">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34c31-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="34c31-127">Откройте страницу **свойств** для проекта.</span><span class="sxs-lookup"><span data-stu-id="34c31-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="34c31-128">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="34c31-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="34c31-129">Измените значение свойства **Целевая платформа**, а для проектов, предназначенных для .NET Framework 4.5 и выше, установите или снимите флажок **Предпочитать 32-разрядную**.</span><span class="sxs-lookup"><span data-stu-id="34c31-129">Modify the **Platform target** property and, for projects that target .NET Framework 4.5 or later, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="34c31-130">Параметр `-platform` недоступен в среде разработки в Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="34c31-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="34c31-131">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="34c31-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="34c31-132">Пример</span><span class="sxs-lookup"><span data-stu-id="34c31-132">Example</span></span>

<span data-ttu-id="34c31-133">В следующем примере показано использование параметра **-platform**, чтобы указать, что приложение должно выполняться в 64-разрядной среде CLR в 64-разрядной операционной системой Windows.</span><span class="sxs-lookup"><span data-stu-id="34c31-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="34c31-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="34c31-134">See also</span></span>

- [<span data-ttu-id="34c31-135">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="34c31-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="34c31-136">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="34c31-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
