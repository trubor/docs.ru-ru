---
description: Дополнительные сведения <typeparam> (Visual Basic)
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: efb4394ee2badcf52bac75d7d9e317c732789746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640268"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="c6afc-103">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6afc-103">\<typeparam> (Visual Basic)</span></span>

<span data-ttu-id="c6afc-104">Определяет имя и описание параметра типа.</span><span class="sxs-lookup"><span data-stu-id="c6afc-104">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6afc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6afc-105">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6afc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6afc-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c6afc-107">Имя параметра типа.</span><span class="sxs-lookup"><span data-stu-id="c6afc-107">The name of the type parameter.</span></span> <span data-ttu-id="c6afc-108">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="c6afc-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c6afc-109">Описание параметра типа.</span><span class="sxs-lookup"><span data-stu-id="c6afc-109">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6afc-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6afc-110">Remarks</span></span>  

 <span data-ttu-id="c6afc-111">Используйте `<typeparam>` тег в комментарии для объявления универсального типа или универсального члена, чтобы описать один из параметров типа.</span><span class="sxs-lookup"><span data-stu-id="c6afc-111">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="c6afc-112">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="c6afc-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6afc-113">Пример</span><span class="sxs-lookup"><span data-stu-id="c6afc-113">Example</span></span>  

 <span data-ttu-id="c6afc-114">В этом примере `<typeparam>` для описания параметра используется тег `id` .</span><span class="sxs-lookup"><span data-stu-id="c6afc-114">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="c6afc-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c6afc-115">See also</span></span>

- [<span data-ttu-id="c6afc-116">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="c6afc-116">XML Comment Tags</span></span>](index.md)
