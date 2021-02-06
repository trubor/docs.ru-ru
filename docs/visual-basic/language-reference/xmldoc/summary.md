---
description: Дополнительные сведения <summary> (Visual Basic)
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 4d4b1ecf0fa054eb625c1a3cf09c1cab4e661ef2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640294"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="18772-103">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18772-103">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="18772-104">Указывает сводку элемента.</span><span class="sxs-lookup"><span data-stu-id="18772-104">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18772-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18772-105">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="18772-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="18772-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="18772-107">Сводка объекта.</span><span class="sxs-lookup"><span data-stu-id="18772-107">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18772-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="18772-108">Remarks</span></span>  

 <span data-ttu-id="18772-109">Используйте `<summary>` тег для описания типа или члена типа.</span><span class="sxs-lookup"><span data-stu-id="18772-109">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="18772-110">Чтобы добавить дополнительную информацию в описание типа, используйте [\<remarks>](remarks.md).</span><span class="sxs-lookup"><span data-stu-id="18772-110">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="18772-111">Текст для `<summary>` тега — единственный источник сведений о типе в IntelliSense, который также отображается в обозревателе объектов.</span><span class="sxs-lookup"><span data-stu-id="18772-111">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="18772-112">Дополнительные сведения об обозревателе объектов см. [в разделе Просмотр структуры кода](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="18772-112">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="18772-113">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="18772-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18772-114">Пример</span><span class="sxs-lookup"><span data-stu-id="18772-114">Example</span></span>  

 <span data-ttu-id="18772-115">В этом примере используется `<summary>` тег для описания `ResetCounter` метода и `Counter` Свойства.</span><span class="sxs-lookup"><span data-stu-id="18772-115">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18772-116">См. также</span><span class="sxs-lookup"><span data-stu-id="18772-116">See also</span></span>

- [<span data-ttu-id="18772-117">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="18772-117">XML Comment Tags</span></span>](index.md)
