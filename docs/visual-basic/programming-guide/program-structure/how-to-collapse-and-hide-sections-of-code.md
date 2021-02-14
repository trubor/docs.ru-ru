---
description: Дополнительные сведения о том, как сворачивать и скрывать разделы кода (Visual Basic).
title: Практическое руководство. Сворачивание и скрытие частей кода
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: b93a2190bd6266c6f9fa5cb06eb249ca174c8067
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475972"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="17c34-103">Практическое руководство. Сворачивание и скрытие частей кода (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17c34-103">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="17c34-104">`#Region`Директива позволяет сворачивать и скрывать разделы кода в файлах Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="17c34-104">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="17c34-105">`#Region`Директива позволяет указать блок кода, который можно развернуть или свернуть при использовании редактора кода Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17c34-105">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="17c34-106">Возможность скрывать код выборочно делает файлы более управляемыми и удобочитаемыми.</span><span class="sxs-lookup"><span data-stu-id="17c34-106">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="17c34-107">Дополнительные сведения см. в разделе [Структура](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="17c34-107">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="17c34-108">`#Region` директивы поддерживают семантику блока кода, такую как `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="17c34-108">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="17c34-109">Это означает, что они не могут начинаться в одном блоке и заканчиваться другим; Начало и конец должны находиться в одном блоке.</span><span class="sxs-lookup"><span data-stu-id="17c34-109">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="17c34-110">`#Region` директивы не поддерживаются в функциях.</span><span class="sxs-lookup"><span data-stu-id="17c34-110">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="17c34-111">Сворачивание и скрытие раздела кода</span><span class="sxs-lookup"><span data-stu-id="17c34-111">To collapse and hide a section of code</span></span>

<span data-ttu-id="17c34-112">Поместите раздел кода между `#Region` `#End Region` операторами и, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="17c34-112">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="17c34-113">Этот `#Region` блок можно использовать несколько раз в файле кода, поэтому пользователи могут определять собственные блоки процедур и классов, которые, в свою очередь, могут быть свернуты.</span><span class="sxs-lookup"><span data-stu-id="17c34-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="17c34-114">`#Region` блоки также могут быть вложены в другие `#Region` блоки.</span><span class="sxs-lookup"><span data-stu-id="17c34-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="17c34-115">Скрытие кода не мешает его компиляции и не влияет на `#If...#End If` инструкции.</span><span class="sxs-lookup"><span data-stu-id="17c34-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="17c34-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="17c34-116">See also</span></span>

- [<span data-ttu-id="17c34-117">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="17c34-117">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="17c34-118">Директива #Region</span><span class="sxs-lookup"><span data-stu-id="17c34-118">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="17c34-119">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="17c34-119">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="17c34-120">Структура</span><span class="sxs-lookup"><span data-stu-id="17c34-120">Outlining</span></span>](/visualstudio/ide/outlining)
