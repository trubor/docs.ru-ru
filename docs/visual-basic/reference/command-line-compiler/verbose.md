---
description: 'Дополнительные сведения: -verbose'
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: ea222d4f284bcaf163b142269fe250a081b0ee4f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470140"
---
# <a name="-verbose"></a><span data-ttu-id="ed7ac-103">-verbose</span><span class="sxs-lookup"><span data-stu-id="ed7ac-103">-verbose</span></span>

<span data-ttu-id="ed7ac-104">Заставляет компилятор выдавать подробные сообщения о состоянии и ошибках.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-104">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed7ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed7ac-105">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed7ac-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="ed7ac-106">Arguments</span></span>  

 <span data-ttu-id="ed7ac-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ed7ac-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ed7ac-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-108">Optional.</span></span> <span data-ttu-id="ed7ac-109">Указание `-verbose` аналогично указанию `-verbose+` и приводит к тому, что компилятор выдает подробные сообщения.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-109">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="ed7ac-110">Значение этого параметра по умолчанию равно `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-110">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed7ac-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="ed7ac-111">Remarks</span></span>  

 <span data-ttu-id="ed7ac-112">Параметр `-verbose` отображает сведения об общем количестве ошибок, выданных компилятором, сообщает о том, какие сборки загружаются модулем, и показывает, какие файлы в данный момент компилируются.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-112">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed7ac-113">Параметр `-verbose` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-113">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed7ac-114">Пример</span><span class="sxs-lookup"><span data-stu-id="ed7ac-114">Example</span></span>  

 <span data-ttu-id="ed7ac-115">Следующий код компилирует `In.vb` и предписывает компилятору отображать подробные сведения о состоянии.</span><span class="sxs-lookup"><span data-stu-id="ed7ac-115">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed7ac-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ed7ac-116">See also</span></span>

- [<span data-ttu-id="ed7ac-117">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="ed7ac-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ed7ac-118">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="ed7ac-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
