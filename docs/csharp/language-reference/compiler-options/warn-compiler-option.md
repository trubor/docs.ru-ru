---
description: -warn (параметры компилятора C#)
title: -warn (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d59274423e6f9844d3ab22f3ac513ba1a05d7f07
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171355"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="982d7-103">-warn (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="982d7-103">-warn (C# Compiler Options)</span></span>

<span data-ttu-id="982d7-104">Параметр **-warn** задает уровень предупреждений, которые должны отображаться компилятором.</span><span class="sxs-lookup"><span data-stu-id="982d7-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="982d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="982d7-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="982d7-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="982d7-106">Arguments</span></span>  

 `option`  
 <span data-ttu-id="982d7-107">При меньших значениях уровня предупреждений отображаются только самые серьезные предупреждения. Чем выше значение, тем больше предупреждений будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="982d7-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="982d7-108">Значение должно быть больше нуля или равно ему.</span><span class="sxs-lookup"><span data-stu-id="982d7-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="982d7-109">Уровень предупреждений</span><span class="sxs-lookup"><span data-stu-id="982d7-109">Warning level</span></span>|<span data-ttu-id="982d7-110">Значение</span><span class="sxs-lookup"><span data-stu-id="982d7-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="982d7-111">0</span><span class="sxs-lookup"><span data-stu-id="982d7-111">0</span></span>|<span data-ttu-id="982d7-112">Отключает вывод всех предупреждающих сообщений.</span><span class="sxs-lookup"><span data-stu-id="982d7-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="982d7-113">1</span><span class="sxs-lookup"><span data-stu-id="982d7-113">1</span></span>|<span data-ttu-id="982d7-114">Отображает серьезные предупреждающие сообщения.</span><span class="sxs-lookup"><span data-stu-id="982d7-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="982d7-115">2</span><span class="sxs-lookup"><span data-stu-id="982d7-115">2</span></span>|<span data-ttu-id="982d7-116">Отображает предупреждения уровня 1, а также некоторые менее серьезные предупреждения, в том числе связанные со скрытием членов класса.</span><span class="sxs-lookup"><span data-stu-id="982d7-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="982d7-117">3</span><span class="sxs-lookup"><span data-stu-id="982d7-117">3</span></span>|<span data-ttu-id="982d7-118">Отображает предупреждения уровня 2, а также некоторые менее серьезные предупреждения, в том числе связанные с выражениями, которые всегда возвращают значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="982d7-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="982d7-119">4 (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="982d7-119">4 (the default)</span></span>|<span data-ttu-id="982d7-120">Отображает все предупреждения уровня 3, а также информационные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="982d7-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="982d7-121">5</span><span class="sxs-lookup"><span data-stu-id="982d7-121">5</span></span>|<span data-ttu-id="982d7-122">Отображает предупреждения уровня 4, а также [дополнительные предупреждения](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) от компилятора, поставляемого в составе C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="982d7-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="982d7-123">Больше 5</span><span class="sxs-lookup"><span data-stu-id="982d7-123">Greater than 5</span></span>|<span data-ttu-id="982d7-124">Любое значение больше 5 будет рассматриваться как 5.</span><span class="sxs-lookup"><span data-stu-id="982d7-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="982d7-125">Обычно требуется произвольное большое значение (например, `9999`), чтобы гарантировать постоянное наличие всех предупреждений, если компилятор обновляется с новыми уровнями предупреждений.</span><span class="sxs-lookup"><span data-stu-id="982d7-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="982d7-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="982d7-126">Remarks</span></span>  

 <span data-ttu-id="982d7-127">Чтобы получить сведения об ошибке или предупреждении, выполните поиск по соответствующему коду в указателе справочной системы.</span><span class="sxs-lookup"><span data-stu-id="982d7-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="982d7-128">Дополнительные сведения о других способах получить информацию об ошибках и предупреждениях см. в разделе [Ошибки компилятора C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="982d7-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="982d7-129">Параметр [-warnaserror](./warnaserror-compiler-option.md) позволяет обрабатывать все предупреждения как ошибки.</span><span class="sxs-lookup"><span data-stu-id="982d7-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="982d7-130">Параметр [-nowarn](./nowarn-compiler-option.md) позволяет отключать определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="982d7-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="982d7-131">**-w** является краткой формой **-warn**.</span><span class="sxs-lookup"><span data-stu-id="982d7-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="982d7-132">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="982d7-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="982d7-133">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="982d7-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="982d7-134">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="982d7-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="982d7-135">Измените свойство **Порог предупреждений**.</span><span class="sxs-lookup"><span data-stu-id="982d7-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="982d7-136">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="982d7-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="982d7-137">Пример</span><span class="sxs-lookup"><span data-stu-id="982d7-137">Example</span></span>  

 <span data-ttu-id="982d7-138">Компиляция файла `in.cs` с отображением только предупреждений уровня 1:</span><span class="sxs-lookup"><span data-stu-id="982d7-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="982d7-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="982d7-139">See also</span></span>

- [<span data-ttu-id="982d7-140">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="982d7-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="982d7-141">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="982d7-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
