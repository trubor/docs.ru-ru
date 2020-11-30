---
description: -reference (параметры компилятора C#)
title: -reference (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: cd7346ae4094a84a398306394f771e040dd7b72f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193794"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="39cf5-103">-reference (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="39cf5-103">-reference (C# Compiler Options)</span></span>

<span data-ttu-id="39cf5-104">Параметр **-reference** предписывает компилятору импортировать сведения типа [public](../keywords/public.md) из указанного файла в текущий проект. Это позволяет ссылаться на метаданные из указанных файлов сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-104">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cf5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39cf5-105">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="39cf5-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="39cf5-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="39cf5-107">Имя файла, содержащего манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-107">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="39cf5-108">Чтобы импортировать данные из нескольких файлов, включите отдельный параметр **-reference** для каждого файла.</span><span class="sxs-lookup"><span data-stu-id="39cf5-108">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="39cf5-109">Допустимый идентификатор C#, который представляет корневое пространство имен, содержащее все пространства имен сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-109">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39cf5-110">Комментарии</span><span class="sxs-lookup"><span data-stu-id="39cf5-110">Remarks</span></span>  

 <span data-ttu-id="39cf5-111">Чтобы импортировать данные из нескольких файлов, включите параметр **-reference** для каждого файла.</span><span class="sxs-lookup"><span data-stu-id="39cf5-111">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="39cf5-112">Импортируемые файлы должны содержать манифест; выходной файл следует компилировать с одним из параметров [-target](./target-compiler-option.md), отличных от [-target:module](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="39cf5-112">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="39cf5-113">**-r** является краткой формой **-reference**.</span><span class="sxs-lookup"><span data-stu-id="39cf5-113">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="39cf5-114">Для импорта метаданных из выходного файла, который не содержит манифест сборки, используется параметр [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="39cf5-114">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="39cf5-115">При ссылке на сборку (сборку А), которая, в свою очередь, ссылается на другую сборку (сборку Б), необходимо ссылаться на сборку Б в указанных ниже случаях.</span><span class="sxs-lookup"><span data-stu-id="39cf5-115">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="39cf5-116">Используемый в сборке A тип наследует от типа сборки Б или реализует интерфейс из этой сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-116">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="39cf5-117">Вызывается поле, свойство, событие или метод, которые имеют тип возвращаемых данных или тип параметра из сборки Б.</span><span class="sxs-lookup"><span data-stu-id="39cf5-117">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="39cf5-118">Для указания каталога, где находится одна или несколько ссылок на сборки, используется параметр [-lib](./lib-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="39cf5-118">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="39cf5-119">В разделе, посвященном параметру **-lib**, также рассматриваются каталоги, в которых компилятор ищет сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-119">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="39cf5-120">Чтобы компилятор мог распознавать тип в сборке (не в модуле), ему следует указать принудительно разрешать типы. Это можно сделать, определив экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="39cf5-120">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="39cf5-121">Возможны и другие способы разрешения компилятором имен типов в сборке. Например, если тип наследуется от типа в сборке, его имя будет распознаваться компилятором.</span><span class="sxs-lookup"><span data-stu-id="39cf5-121">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="39cf5-122">Иногда бывает необходимо сослаться на две различные версии одного компонента из одной сборки.</span><span class="sxs-lookup"><span data-stu-id="39cf5-122">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="39cf5-123">Для этого следует использовать подпараметр псевдонима для параметра **-reference** для каждого файла, чтобы различать два этих файла.</span><span class="sxs-lookup"><span data-stu-id="39cf5-123">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="39cf5-124">Этот псевдоним используется в качестве квалификатора имени компонента и разрешается в компонент в одном из файлов.</span><span class="sxs-lookup"><span data-stu-id="39cf5-124">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="39cf5-125">Файл ответов csc (RSP-файл), который ссылается на часто используемые сборки .NET Framework, используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="39cf5-125">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="39cf5-126">Параметр [-noconfig](./noconfig-compiler-option.md) позволяет запретить компилятору использовать файл csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="39cf5-126">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39cf5-127">В Visual Studio используйте диалоговое окно **Добавление ссылки**.</span><span class="sxs-lookup"><span data-stu-id="39cf5-127">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="39cf5-128">Для получения дополнительной информации см. [Практическое руководство. Добавление и удаление ссылок с помощью диспетчера ссылок](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="39cf5-128">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="39cf5-129">Чтобы обеспечить эквивалентное поведение при добавлении ссылок с помощью `-reference` и диалогового окна **Добавление ссылки**, свойству **Внедрить типы взаимодействия** добавляемой сборки должно быть задано значение **False**.</span><span class="sxs-lookup"><span data-stu-id="39cf5-129">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="39cf5-130">**True** является значением по умолчанию для этого свойства.</span><span class="sxs-lookup"><span data-stu-id="39cf5-130">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39cf5-131">Пример</span><span class="sxs-lookup"><span data-stu-id="39cf5-131">Example</span></span>  

 <span data-ttu-id="39cf5-132">В этом примере показано, как использовать [псевдоним extern](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="39cf5-132">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="39cf5-133">В примере компилируется файл исходного кода и импортируются метаданные из сборок `grid.dll` и `grid20.dll`, которые были скомпилированы ранее.</span><span class="sxs-lookup"><span data-stu-id="39cf5-133">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="39cf5-134">Два DLL-файла содержат разные версии одного компонента, поэтому для компиляции файла исходного кода используются два параметра **-reference** с подпараметрами псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="39cf5-134">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="39cf5-135">Параметры выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="39cf5-135">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="39cf5-136">При этом устанавливаются внешние псевдонимы `GridV1` и `GridV2`, которые используются посредством оператора `extern`.</span><span class="sxs-lookup"><span data-stu-id="39cf5-136">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="39cf5-137">После выполнения описанных выше действий можно ссылаться на элемент управления "сетка" из файла `grid.dll`, предваряя имя элемента управления префиксом `GridV1`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="39cf5-137">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="39cf5-138">Кроме того, можно ссылаться на элемент управления "сетка" из файла `grid20.dll`, предваряя имя элемента управления префиксом `GridV2`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="39cf5-138">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="39cf5-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="39cf5-139">See also</span></span>

- [<span data-ttu-id="39cf5-140">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="39cf5-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="39cf5-141">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="39cf5-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
