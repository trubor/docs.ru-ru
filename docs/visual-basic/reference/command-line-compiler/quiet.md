---
description: 'Дополнительные сведения: -quiet'
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 23e1b6472e80ac6ca2ecea5c4390b43722ccebb6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432732"
---
# <a name="-quiet"></a><span data-ttu-id="a7ca8-103">-quiet</span><span class="sxs-lookup"><span data-stu-id="a7ca8-103">-quiet</span></span>

<span data-ttu-id="a7ca8-104">Запрещает компилятору показывать код синтаксических ошибок и предупреждений.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-104">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7ca8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7ca8-105">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="a7ca8-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="a7ca8-106">Remarks</span></span>

<span data-ttu-id="a7ca8-107">По умолчанию `-quiet` не действует.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-107">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="a7ca8-108">Когда компилятор сообщает об ошибке или предупреждении, связанных с синтаксисом, он также выводит соответствующую строку из исходного кода.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-108">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="a7ca8-109">Для приложений, анализирующих выходные данные компилятора, может быть удобнее, чтобы компилятор выводил только текстовую часть диагностической информации.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-109">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="a7ca8-110">В следующем примере `Module1` выводит ошибку, включающую в себя исходный код, при компиляции без `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-110">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="a7ca8-111">Результат</span><span class="sxs-lookup"><span data-stu-id="a7ca8-111">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="a7ca8-112">При компиляции с `-quiet` компилятор выводит только следующие данные:</span><span class="sxs-lookup"><span data-stu-id="a7ca8-112">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="a7ca8-113">Параметр `-quiet` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="a7ca8-113">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a7ca8-114">Пример</span><span class="sxs-lookup"><span data-stu-id="a7ca8-114">Example</span></span>

<span data-ttu-id="a7ca8-115">Следующий код компилирует `T2.vb` и не отображает код для диагностической информации компилятора, связанной с синтаксисом:</span><span class="sxs-lookup"><span data-stu-id="a7ca8-115">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a7ca8-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a7ca8-116">See also</span></span>

- [<span data-ttu-id="a7ca8-117">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="a7ca8-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a7ca8-118">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="a7ca8-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
