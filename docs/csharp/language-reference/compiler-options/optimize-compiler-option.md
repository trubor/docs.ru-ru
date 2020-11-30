---
description: -optimize (параметры компилятора C#)
title: -optimize (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 1862794e4d823e38ce19780300a0b04f4e57dc44
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193989"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="64126-103">-optimize (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="64126-103">-optimize (C# Compiler Options)</span></span>

<span data-ttu-id="64126-104">Параметр **-optimize** включает или отключает оптимизацию кода компилятором, чтобы сделать код более быстрым, коротким и эффективным.</span><span class="sxs-lookup"><span data-stu-id="64126-104">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64126-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64126-105">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="64126-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="64126-106">Remarks</span></span>  

 <span data-ttu-id="64126-107">Кроме того, параметр **-optimize** включает оптимизацию кода во время выполнения в общеязыковой среде выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="64126-107">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="64126-108">По умолчанию оптимизация отключена.</span><span class="sxs-lookup"><span data-stu-id="64126-108">By default, optimizations are disabled.</span></span> <span data-ttu-id="64126-109">Чтобы включить оптимизацию, укажите **-optimize+**.</span><span class="sxs-lookup"><span data-stu-id="64126-109">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="64126-110">При создании модуля для сборки используйте те же настройки параметра **-optimize**, что и для сборки.</span><span class="sxs-lookup"><span data-stu-id="64126-110">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="64126-111">**-o** является краткой формой параметра **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="64126-111">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="64126-112">Параметры **-optimize** и [-debug](./debug-compiler-option.md) можно объединять.</span><span class="sxs-lookup"><span data-stu-id="64126-112">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="64126-113">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64126-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="64126-114">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="64126-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="64126-115">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="64126-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="64126-116">Измените свойство **Оптимизировать код**.</span><span class="sxs-lookup"><span data-stu-id="64126-116">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="64126-117">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="64126-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64126-118">Пример</span><span class="sxs-lookup"><span data-stu-id="64126-118">Example</span></span>  

 <span data-ttu-id="64126-119">Скомпилируйте `t2.cs` и включите выполняемую компилятором оптимизацию:</span><span class="sxs-lookup"><span data-stu-id="64126-119">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="64126-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="64126-120">See also</span></span>

- [<span data-ttu-id="64126-121">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="64126-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="64126-122">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="64126-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
