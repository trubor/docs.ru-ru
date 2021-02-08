---
description: 'Дополнительные сведения: Директива #ExternalSource'
title: '#Директива ExternalSource'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 1f2e73aa152fbe2d97edcde912626696faacd5af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797241"
---
# <a name="externalsource-directive"></a><span data-ttu-id="df564-103">Директива #ExternalSource</span><span class="sxs-lookup"><span data-stu-id="df564-103">#ExternalSource Directive</span></span>

<span data-ttu-id="df564-104">Указывает сопоставление между конкретными строками исходного кода и текстом, внешним по отношению к источнику.</span><span class="sxs-lookup"><span data-stu-id="df564-104">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df564-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="df564-105">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="df564-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="df564-106">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="df564-107">Путь к внешнему источнику.</span><span class="sxs-lookup"><span data-stu-id="df564-107">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="df564-108">Номер строки первой строки внешнего источника.</span><span class="sxs-lookup"><span data-stu-id="df564-108">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="df564-109">Строка, в которой возникла ошибка во внешнем источнике.</span><span class="sxs-lookup"><span data-stu-id="df564-109">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="df564-110">Завершает блок `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="df564-110">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df564-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="df564-111">Remarks</span></span>  

 <span data-ttu-id="df564-112">Эта директива используется только компилятором и отладчиком.</span><span class="sxs-lookup"><span data-stu-id="df564-112">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="df564-113">Исходный файл может содержать директивы External Source, которые указывают на сопоставление между конкретными строками кода в исходном файле и внешним по отношению к источнику текстом, например ASPX-файлу.</span><span class="sxs-lookup"><span data-stu-id="df564-113">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="df564-114">Если во время компиляции обнаружены ошибки в указанном исходном коде, они определяются как поступающие из внешнего источника.</span><span class="sxs-lookup"><span data-stu-id="df564-114">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="df564-115">Директивы External Source не влияют на компиляцию и не могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="df564-115">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="df564-116">Они предназначены только для внутреннего использования приложением.</span><span class="sxs-lookup"><span data-stu-id="df564-116">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df564-117">См. также</span><span class="sxs-lookup"><span data-stu-id="df564-117">See also</span></span>

- [<span data-ttu-id="df564-118">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="df564-118">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
