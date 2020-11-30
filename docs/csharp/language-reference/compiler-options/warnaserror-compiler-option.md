---
description: -warnaserror (параметры компилятора C#)
title: -warnaserror (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 9c3b307668968865b401aedc04c79f95d4f32513
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171342"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="3f383-103">-warnaserror (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="3f383-103">-warnaserror (C# Compiler Options)</span></span>

<span data-ttu-id="3f383-104">Параметр **-warnaserror+** предписывает обрабатывать все предупреждения как ошибки</span><span class="sxs-lookup"><span data-stu-id="3f383-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f383-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f383-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f383-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="3f383-106">Remarks</span></span>  

 <span data-ttu-id="3f383-107">Все сообщения, которые до этого получали статус предупреждений, будут возвращаться как ошибки, в результате чего процесс построения прерывается без создания выходных файлов.</span><span class="sxs-lookup"><span data-stu-id="3f383-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="3f383-108">По умолчанию действует параметр **-warnaserror-**, при котором наличие предупреждений не препятствует созданию выходного файла.</span><span class="sxs-lookup"><span data-stu-id="3f383-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="3f383-109">Если задан параметр **-warnaserror** или эквивалентный ему **-warnaserror+**, все предупреждения обрабатываются как ошибки.</span><span class="sxs-lookup"><span data-stu-id="3f383-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="3f383-110">Если требуется обрабатывать как ошибки только конкретные предупреждения, укажите их номера через запятую.</span><span class="sxs-lookup"><span data-stu-id="3f383-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="3f383-111">Набор всех предупреждений о допустимости значений NULL можно указать с помощью сокращения **nullable**.</span><span class="sxs-lookup"><span data-stu-id="3f383-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="3f383-112">Параметр [-warn](./warn-compiler-option.md) позволяет указать уровень предупреждений, которые будет отображать компилятор.</span><span class="sxs-lookup"><span data-stu-id="3f383-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="3f383-113">Параметр [-nowarn](./nowarn-compiler-option.md) позволяет отключать определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="3f383-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3f383-114">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f383-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3f383-115">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="3f383-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3f383-116">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="3f383-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="3f383-117">Измените свойство **Обрабатывать предупреждения как ошибки**.</span><span class="sxs-lookup"><span data-stu-id="3f383-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="3f383-118">Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="3f383-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f383-119">Пример</span><span class="sxs-lookup"><span data-stu-id="3f383-119">Example</span></span>  

 <span data-ttu-id="3f383-120">Компиляция файла `in.cs` без отображения предупреждений:</span><span class="sxs-lookup"><span data-stu-id="3f383-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f383-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3f383-121">See also</span></span>

- [<span data-ttu-id="3f383-122">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="3f383-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3f383-123">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="3f383-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
