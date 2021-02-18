---
description: 'Дополнительные сведения: -refonly (Visual Basic)'
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 283aa75fceead38c62c4cf10c1ffe08151aeac9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474139"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="1f66f-103">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f66f-103">-refonly (Visual Basic)</span></span>

<span data-ttu-id="1f66f-104">Параметр **-refonly** указывает на то, что основными выходными данными должна быть базовая сборка, а не сборка реализации.</span><span class="sxs-lookup"><span data-stu-id="1f66f-104">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="1f66f-105">Параметр `-refonly` автоматически отключает вывод файлов PDB, так как базовые сборки не могут выполняться.</span><span class="sxs-lookup"><span data-stu-id="1f66f-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="1f66f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f66f-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="1f66f-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f66f-107">Remarks</span></span>

<span data-ttu-id="1f66f-108">Поддержка параметра `-refonly` в Visual Basic появилась в версии 15.3.</span><span class="sxs-lookup"><span data-stu-id="1f66f-108">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="1f66f-109">Базовые сборки являются особым типом сборки, которая содержит только минимальный объем метаданных, необходимый для представления общедоступного API-интерфейса библиотеки.</span><span class="sxs-lookup"><span data-stu-id="1f66f-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="1f66f-110">Такие сборки включают в себя объявления для всех элементов, которые важны при указании ссылки на сборку в средствах сборки, но исключают все реализации элементов, а также объявления закрытых элементов, не имеющих наблюдаемого влияния на их контракт API.</span><span class="sxs-lookup"><span data-stu-id="1f66f-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="1f66f-111">Дополнительные сведения см. в разделе [Базовые сборки](../../../standard/assembly/reference-assemblies.md) в руководстве по .NET.</span><span class="sxs-lookup"><span data-stu-id="1f66f-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="1f66f-112">Параметры `-refonly` и [`-refout`](refout-compiler-option.md) являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="1f66f-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f66f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="1f66f-113">See also</span></span>

- [<span data-ttu-id="1f66f-114">/refout</span><span class="sxs-lookup"><span data-stu-id="1f66f-114">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="1f66f-115">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="1f66f-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1f66f-116">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="1f66f-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
