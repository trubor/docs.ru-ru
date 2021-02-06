---
description: Дополнительные сведения <remarks> (Visual Basic)
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 4b0584abbe85a7ecc73e25dd1f6ec321962b88a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640411"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="2e6c4-103">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e6c4-103">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="2e6c4-104">Задает раздел примечаний для элемента.</span><span class="sxs-lookup"><span data-stu-id="2e6c4-104">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6c4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2e6c4-105">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e6c4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2e6c4-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="2e6c4-107">Описание элемента.</span><span class="sxs-lookup"><span data-stu-id="2e6c4-107">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e6c4-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="2e6c4-108">Remarks</span></span>  

 <span data-ttu-id="2e6c4-109">Используйте `<remarks>` тег, чтобы добавить сведения о типе, добавив сведения, указанные в параметре [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="2e6c4-109">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="2e6c4-110">Эти сведения отображаются в обозревателе объектов.</span><span class="sxs-lookup"><span data-stu-id="2e6c4-110">This information appears in the Object Browser.</span></span> <span data-ttu-id="2e6c4-111">Дополнительные сведения об обозревателе объектов см. [в разделе Просмотр структуры кода](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="2e6c4-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2e6c4-112">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="2e6c4-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e6c4-113">Пример</span><span class="sxs-lookup"><span data-stu-id="2e6c4-113">Example</span></span>  

 <span data-ttu-id="2e6c4-114">В этом примере `<remarks>` тег используется для объяснения того, что `UpdateRecord` делает метод.</span><span class="sxs-lookup"><span data-stu-id="2e6c4-114">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2e6c4-115">См. также</span><span class="sxs-lookup"><span data-stu-id="2e6c4-115">See also</span></span>

- [<span data-ttu-id="2e6c4-116">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="2e6c4-116">XML Comment Tags</span></span>](index.md)
