---
description: 'Дополнительные сведения: -noconfig'
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: e97d44427b537e73a404a47d30db202e2c3b1f41
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481692"
---
# <a name="-noconfig"></a><span data-ttu-id="af357-103">-noconfig</span><span class="sxs-lookup"><span data-stu-id="af357-103">-noconfig</span></span>

<span data-ttu-id="af357-104">Указывает, что компилятор не должен автоматически ссылаться на часто используемые сборки .NET Framework и импортировать пространства имен `System` и `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="af357-104">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af357-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af357-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="af357-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="af357-106">Remarks</span></span>  

 <span data-ttu-id="af357-107">Параметр `-noconfig` указывает компилятору не выполнять сборку с использованием файла Vbc.rsp, который располагается в том же каталоге, что и файл Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="af357-107">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="af357-108">Файл Vbc.rsp ссылается на часто используемые сборки .NET Framework и импортирует пространства имен `System` и `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="af357-108">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="af357-109">Компилятор неявно ссылается на сборку System.dll, если не указан параметр `-nostdlib`.</span><span class="sxs-lookup"><span data-stu-id="af357-109">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="af357-110">Параметр `-nostdlib` указывает компилятору не выполнять сборку с использованием файла Vbc.rsp и не ссылаться на сборку System.dll автоматически.</span><span class="sxs-lookup"><span data-stu-id="af357-110">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af357-111">При этом компилятор всегда ссылается на сборки Mscorlib.dll и Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="af357-111">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="af357-112">Можно изменить файл Vbc.rsp, указав дополнительные параметры компилятора, которые должны включаться в каждую компиляцию Vbc.exe (за исключением случаев, когда указан параметр `-noconfig`).</span><span class="sxs-lookup"><span data-stu-id="af357-112">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="af357-113">Дополнительные сведения см. в документации синтаксиса [@ (указание файла ответа)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="af357-113">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="af357-114">Компилятор обрабатывает параметры, передаваемые в команду `vbc`, последними.</span><span class="sxs-lookup"><span data-stu-id="af357-114">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="af357-115">Таким образом, любой параметр командной строки переопределяет значение аналогичного параметра в файле Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="af357-115">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af357-116">Параметр `-noconfig` недоступен в среде разработки Visual Studio. Его можно использовать только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="af357-116">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af357-117">См. также</span><span class="sxs-lookup"><span data-stu-id="af357-117">See also</span></span>

- [<span data-ttu-id="af357-118">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af357-118">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="af357-119">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="af357-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="af357-120">@ (указание файла ответов)</span><span class="sxs-lookup"><span data-stu-id="af357-120">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="af357-121">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af357-121">-reference (Visual Basic)</span></span>](reference.md)
