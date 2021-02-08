---
description: 'Дополнительные сведения: Директива #Region'
title: '#Директива Region'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4ba1645cfc51a69d39e6a60b5ea236dd65883e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797228"
---
# <a name="region-directive"></a><span data-ttu-id="2d586-103">Директива #Region</span><span class="sxs-lookup"><span data-stu-id="2d586-103">#Region Directive</span></span>

<span data-ttu-id="2d586-104">Сворачивает и скрывает разделы кода в файлах Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d586-104">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d586-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d586-105">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="2d586-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="2d586-106">Parts</span></span>  
  
|<span data-ttu-id="2d586-107">Термин</span><span class="sxs-lookup"><span data-stu-id="2d586-107">Term</span></span>|<span data-ttu-id="2d586-108">Определение</span><span class="sxs-lookup"><span data-stu-id="2d586-108">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="2d586-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2d586-109">Required.</span></span> <span data-ttu-id="2d586-110">Строка, которая выступает в качестве заголовка области, если он свернут.</span><span class="sxs-lookup"><span data-stu-id="2d586-110">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="2d586-111">По умолчанию области свернуты.</span><span class="sxs-lookup"><span data-stu-id="2d586-111">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="2d586-112">Завершает блок `#Region`.</span><span class="sxs-lookup"><span data-stu-id="2d586-112">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d586-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="2d586-113">Remarks</span></span>  

 <span data-ttu-id="2d586-114">Используйте директиву `#Region`, чтобы указать блок кода, который можно разворачивать и сворачивать с помощью функции структурирования в редакторе кода Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d586-114">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="2d586-115">Вы можете разместить или *вложить* области внутри других регионов, чтобы сгруппировать похожие регионы.</span><span class="sxs-lookup"><span data-stu-id="2d586-115">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d586-116">Пример</span><span class="sxs-lookup"><span data-stu-id="2d586-116">Example</span></span>  

 <span data-ttu-id="2d586-117">В этом примере используется директива `#Region`.</span><span class="sxs-lookup"><span data-stu-id="2d586-117">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2d586-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2d586-118">See also</span></span>

- [<span data-ttu-id="2d586-119">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="2d586-119">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="2d586-120">Структура</span><span class="sxs-lookup"><span data-stu-id="2d586-120">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="2d586-121">Практическое руководство. Сворачивание и скрытие частей кода</span><span class="sxs-lookup"><span data-stu-id="2d586-121">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
