---
description: -unsafe (параметры компилятора C#)
title: -unsafe (параметры компилятора C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89140845"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="6bc74-103">-unsafe (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="6bc74-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="6bc74-104">Параметр **-unsafe** разрешает компилировать код, в котором используется ключевое слово [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="6bc74-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc74-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6bc74-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="6bc74-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="6bc74-106">Remarks</span></span>

<span data-ttu-id="6bc74-107">Дополнительные сведения см. в разделе [Небезопасный код и указатели](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bc74-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6bc74-108">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6bc74-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6bc74-109">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="6bc74-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6bc74-110">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="6bc74-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6bc74-111">Установите флажок **Разрешить небезопасный код**.</span><span class="sxs-lookup"><span data-stu-id="6bc74-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="6bc74-112">Добавление этого параметра в CSPROJ-файл</span><span class="sxs-lookup"><span data-stu-id="6bc74-112">To add this option in a csproj file</span></span>

<span data-ttu-id="6bc74-113">Откройте CSPROJ-файл проекта и добавьте следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="6bc74-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="6bc74-114">Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bc74-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc74-115">Пример</span><span class="sxs-lookup"><span data-stu-id="6bc74-115">Example</span></span>

<span data-ttu-id="6bc74-116">Скомпилируйте `in.cs` для небезопасного режима:</span><span class="sxs-lookup"><span data-stu-id="6bc74-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bc74-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6bc74-117">See also</span></span>

- [<span data-ttu-id="6bc74-118">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="6bc74-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="6bc74-119">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="6bc74-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
