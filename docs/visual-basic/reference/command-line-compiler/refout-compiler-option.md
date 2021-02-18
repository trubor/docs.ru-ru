---
description: 'Дополнительные сведения: -refout (Visual Basic)'
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 2760f7e60d950aaff90becad843824a2e2b4379f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474126"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="0cca2-103">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cca2-103">-refout (Visual Basic)</span></span>

<span data-ttu-id="0cca2-104">Параметр **-refout** указывает путь к файлу, в который нужно выводить базовую сборку.</span><span class="sxs-lookup"><span data-stu-id="0cca2-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="0cca2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0cca2-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="0cca2-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="0cca2-106">Arguments</span></span>

`filepath`  
<span data-ttu-id="0cca2-107">Путь и имя файла базовой сборки.</span><span class="sxs-lookup"><span data-stu-id="0cca2-107">The path and filename of the reference assembly.</span></span> <span data-ttu-id="0cca2-108">Обычно этот файл находится в подпапке основной сборки.</span><span class="sxs-lookup"><span data-stu-id="0cca2-108">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="0cca2-109">Согласно рекомендуемому соглашению (используемому в MSBuild), базовую сборку следует помещать во вложенную папку ref/ относительно основной сборки.</span><span class="sxs-lookup"><span data-stu-id="0cca2-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="0cca2-110">Все папки в пути `filepath` должны существовать; компилятор не создает их.</span><span class="sxs-lookup"><span data-stu-id="0cca2-110">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cca2-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="0cca2-111">Remarks</span></span>

<span data-ttu-id="0cca2-112">Поддержка параметра `-refout` в Visual Basic появилась в версии 15.3.</span><span class="sxs-lookup"><span data-stu-id="0cca2-112">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="0cca2-113">Базовые сборки являются особым типом сборки, которая содержит только минимальный объем метаданных, необходимый для представления общедоступного API-интерфейса библиотеки.</span><span class="sxs-lookup"><span data-stu-id="0cca2-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="0cca2-114">Такие сборки включают в себя объявления для всех элементов, которые важны при указании ссылки на сборку в средствах сборки, но исключают все реализации элементов, а также объявления закрытых элементов, не имеющих наблюдаемого влияния на их контракт API.</span><span class="sxs-lookup"><span data-stu-id="0cca2-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="0cca2-115">Дополнительные сведения см. в разделе [Базовые сборки](../../../standard/assembly/reference-assemblies.md) в руководстве по .NET.</span><span class="sxs-lookup"><span data-stu-id="0cca2-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="0cca2-116">Параметры `-refout` и [`-refonly`](refonly-compiler-option.md) являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="0cca2-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cca2-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0cca2-117">See also</span></span>

- [<span data-ttu-id="0cca2-118">/refonly</span><span class="sxs-lookup"><span data-stu-id="0cca2-118">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="0cca2-119">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="0cca2-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0cca2-120">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="0cca2-120">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
