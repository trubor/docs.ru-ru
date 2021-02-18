---
description: 'Дополнительные сведения: -highentropyva (Visual Basic)'
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 90fc3713ae4f9a073a63a57c5b35114548e26cbb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470269"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="1e921-103">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e921-103">-highentropyva (Visual Basic)</span></span>

<span data-ttu-id="1e921-104">Указывает, что 64-разрядный исполняемый файл или исполняемый файл, отмеченный параметром компилятора [-platform:anycpu](platform.md), поддерживает технологию Address Space Layout Randomization (ASLR) с высокой энтропией.</span><span class="sxs-lookup"><span data-stu-id="1e921-104">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e921-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e921-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e921-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="1e921-106">Arguments</span></span>  

 <span data-ttu-id="1e921-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1e921-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1e921-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e921-108">Optional.</span></span> <span data-ttu-id="1e921-109">Этот параметр выключен по умолчанию или если вы указываете `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="1e921-109">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="1e921-110">Параметр включен, если вы указываете `-highentropyva` или `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="1e921-110">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e921-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="1e921-111">Remarks</span></span>  

 <span data-ttu-id="1e921-112">Если этот параметр указан, совместимые версии ядра Windows могут использовать более высокие степени энтропии, когда ядро вносит элемент случайности в структуру адресного пространства процесса в рамках ASLR.</span><span class="sxs-lookup"><span data-stu-id="1e921-112">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="1e921-113">Если ядро использует более высокие степени энтропии, можно выделить больше адресов таким областям памяти, как стеки и кучи.</span><span class="sxs-lookup"><span data-stu-id="1e921-113">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="1e921-114">Из-за этого сложнее подобрать расположение определенной области памяти.</span><span class="sxs-lookup"><span data-stu-id="1e921-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="1e921-115">Если этот параметр включен, целевой исполняемый файл и все модули, от которых он зависит, должны быть способны обработать значения указателя, размер которых превышает 4 гигабайта (ГБ), когда они выполняются как 64-разрядный процесс.</span><span class="sxs-lookup"><span data-stu-id="1e921-115">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e921-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1e921-116">See also</span></span>

- [<span data-ttu-id="1e921-117">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="1e921-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1e921-118">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="1e921-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
