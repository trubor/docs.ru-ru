---
description: -nowarn (параметры компилятора C#)
title: -nowarn (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194028"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="73372-103">-nowarn (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="73372-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="73372-104">Параметр **-nowarn** позволяет предотвратить отображение одного или нескольких предупреждений компилятором.</span><span class="sxs-lookup"><span data-stu-id="73372-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="73372-105">Разделяйте предупреждения запятыми.</span><span class="sxs-lookup"><span data-stu-id="73372-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73372-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73372-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="73372-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="73372-107">Arguments</span></span>  

 <span data-ttu-id="73372-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="73372-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="73372-109">Номер (номера) предупреждений, которые требуется отключить в компиляторе.</span><span class="sxs-lookup"><span data-stu-id="73372-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73372-110">Комментарии</span><span class="sxs-lookup"><span data-stu-id="73372-110">Remarks</span></span>  

 <span data-ttu-id="73372-111">Необходимо указать только числовую часть идентификатора предупреждения.</span><span class="sxs-lookup"><span data-stu-id="73372-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="73372-112">Например, если требуется отключить CS0028, можно указать `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="73372-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="73372-113">Компилятор просто пропустит номера предупреждений, переданные `-nowarn`, которые использовались в предыдущих версиях, но были удалены из компилятора.</span><span class="sxs-lookup"><span data-stu-id="73372-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="73372-114">Например, предупреждение CS0679 использовалось в компиляторе Visual Studio .NET 2002, но было удалено в последующих версиях.</span><span class="sxs-lookup"><span data-stu-id="73372-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="73372-115">Параметр `-nowarn` позволяет отключить следующие предупреждения:</span><span class="sxs-lookup"><span data-stu-id="73372-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="73372-116">Предупреждение компилятора (уровень 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="73372-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="73372-117">Предупреждение компилятора (уровень 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="73372-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="73372-118">Предупреждение компилятора (уровень 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="73372-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="73372-119">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73372-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="73372-120">Откройте страницу **свойств** для проекта.</span><span class="sxs-lookup"><span data-stu-id="73372-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="73372-121">Дополнительные сведения см. в разделе [Страница "Сборка", конструктор проектов (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="73372-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="73372-122">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="73372-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="73372-123">Измените свойство **Отключить предупреждения**.</span><span class="sxs-lookup"><span data-stu-id="73372-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="73372-124">Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="73372-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73372-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="73372-125">See also</span></span>

- [<span data-ttu-id="73372-126">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="73372-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="73372-127">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="73372-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="73372-128">Ошибки компилятора C#</span><span class="sxs-lookup"><span data-stu-id="73372-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
