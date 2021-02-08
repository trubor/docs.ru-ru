---
description: 'Дополнительные сведения: <c> (Visual Basic)'
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 350a5dbf2dee2911c356a7c76a9bafbab35fd71e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787517"
---
# <a name="c-visual-basic"></a><span data-ttu-id="65f2a-102">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65f2a-102">\<c> (Visual Basic)</span></span>

<span data-ttu-id="65f2a-103">Указывает, что текст в описании является кодом.</span><span class="sxs-lookup"><span data-stu-id="65f2a-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f2a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65f2a-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="65f2a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="65f2a-105">Parameters</span></span>  
  
|<span data-ttu-id="65f2a-106">Параметр</span><span class="sxs-lookup"><span data-stu-id="65f2a-106">Parameter</span></span>|<span data-ttu-id="65f2a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="65f2a-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="65f2a-108">Текст, который нужно указать в качестве кода.</span><span class="sxs-lookup"><span data-stu-id="65f2a-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65f2a-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="65f2a-109">Remarks</span></span>  

 <span data-ttu-id="65f2a-110">С помощью тега `<c>` можно указать, что текст в описании необходимо пометить как код.</span><span class="sxs-lookup"><span data-stu-id="65f2a-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="65f2a-111">Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](code.md).</span><span class="sxs-lookup"><span data-stu-id="65f2a-111">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="65f2a-112">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="65f2a-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65f2a-113">Пример</span><span class="sxs-lookup"><span data-stu-id="65f2a-113">Example</span></span>  

 <span data-ttu-id="65f2a-114">В этом примере `<c>` тег в разделе сводки используется для указания того, что `Counter` является кодом.</span><span class="sxs-lookup"><span data-stu-id="65f2a-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="65f2a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="65f2a-115">See also</span></span>

- [<span data-ttu-id="65f2a-116">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="65f2a-116">XML Comment Tags</span></span>](index.md)
