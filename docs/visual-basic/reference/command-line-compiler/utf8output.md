---
description: 'Дополнительные сведения: -utf8output (Visual Basic)'
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 317c1be3f18150ae88bb8e95927d9f5faf0e4f3c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461896"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="634a1-103">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="634a1-103">-utf8output (Visual Basic)</span></span>

<span data-ttu-id="634a1-104">Отображает выходные данные компилятора в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="634a1-104">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="634a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="634a1-105">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="634a1-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="634a1-106">Arguments</span></span>  

 <span data-ttu-id="634a1-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="634a1-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="634a1-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="634a1-108">Optional.</span></span> <span data-ttu-id="634a1-109">Значением по умолчанию для этого параметра является `-utf8output-`, то есть выходные данные компилятора не используют кодировку UTF-8.</span><span class="sxs-lookup"><span data-stu-id="634a1-109">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="634a1-110">Указание `-utf8output` дает тот же результат, что и указание `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="634a1-110">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="634a1-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="634a1-111">Remarks</span></span>  

 <span data-ttu-id="634a1-112">В некоторых конфигурациях для различных языков выходные данные компилятора отображаются в консоли некорректно.</span><span class="sxs-lookup"><span data-stu-id="634a1-112">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="634a1-113">В таких ситуациях используйте `-utf8output` и перенаправьте выходные данные компилятора в файл.</span><span class="sxs-lookup"><span data-stu-id="634a1-113">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="634a1-114">Параметр `-utf8output` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="634a1-114">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="634a1-115">Пример</span><span class="sxs-lookup"><span data-stu-id="634a1-115">Example</span></span>  

 <span data-ttu-id="634a1-116">Следующий код компилирует `In.vb` и предписывает компилятору отобразить выходные данные с использованием кодировки UTF-8.</span><span class="sxs-lookup"><span data-stu-id="634a1-116">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="634a1-117">См. также</span><span class="sxs-lookup"><span data-stu-id="634a1-117">See also</span></span>

- [<span data-ttu-id="634a1-118">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="634a1-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="634a1-119">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="634a1-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
