---
description: -refonly (параметры компилятора C#)
title: -refonly (параметры компилятора C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89124751"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="9125f-103">-refonly (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="9125f-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="9125f-104">Параметр **-refonly** указывает на то, что в качестве основных выходных данных должна быть выведена базовая сборка, а не сборка реализации.</span><span class="sxs-lookup"><span data-stu-id="9125f-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="9125f-105">Параметр `-refonly` автоматически отключает вывод файлов PDB, так как базовые сборки не могут выполняться.</span><span class="sxs-lookup"><span data-stu-id="9125f-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="9125f-106">Этот параметр соответствует свойству проекта [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) в MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9125f-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="9125f-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9125f-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="9125f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9125f-108">Remarks</span></span>

<span data-ttu-id="9125f-109">Базовые сборки являются особым типом сборки, которая содержит только минимальный объем метаданных, необходимый для представления общедоступного API-интерфейса библиотеки.</span><span class="sxs-lookup"><span data-stu-id="9125f-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="9125f-110">Такие сборки включают в себя объявления для всех элементов, которые важны при указании ссылки на сборку в средствах сборки, но исключают все реализации элементов, а также объявления закрытых элементов, не имеющих наблюдаемого влияния на их контракт API.</span><span class="sxs-lookup"><span data-stu-id="9125f-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="9125f-111">Дополнительные сведения см. в разделе [Базовые сборки](../../../standard/assembly/reference-assemblies.md) в руководстве по .NET.</span><span class="sxs-lookup"><span data-stu-id="9125f-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="9125f-112">Параметры `-refonly` и [`-refout`](refout-compiler-option.md) являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="9125f-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="9125f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="9125f-113">See also</span></span>

- [<span data-ttu-id="9125f-114">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="9125f-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9125f-115">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="9125f-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
