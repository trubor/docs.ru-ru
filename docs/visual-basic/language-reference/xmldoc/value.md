---
description: Дополнительные сведения <value> (Visual Basic)
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 80a3ef875eea4418d28d60dac1818f3390c361ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640255"
---
# <a name="value-visual-basic"></a><span data-ttu-id="74c96-103">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74c96-103">\<value> (Visual Basic)</span></span>

<span data-ttu-id="74c96-104">Задает описание свойства.</span><span class="sxs-lookup"><span data-stu-id="74c96-104">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c96-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74c96-105">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c96-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="74c96-106">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="74c96-107">Описание свойства.</span><span class="sxs-lookup"><span data-stu-id="74c96-107">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74c96-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="74c96-108">Remarks</span></span>  

 <span data-ttu-id="74c96-109">Используйте `<value>` тег для описания свойства.</span><span class="sxs-lookup"><span data-stu-id="74c96-109">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="74c96-110">Обратите внимание, что при добавлении свойства с помощью мастера кода в среде разработки Visual Studio будет добавлен [\<summary>](summary.md) тег для нового свойства.</span><span class="sxs-lookup"><span data-stu-id="74c96-110">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="74c96-111">После этого следует вручную добавить тег `<value>` для описания значения, которое представляется свойством.</span><span class="sxs-lookup"><span data-stu-id="74c96-111">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="74c96-112">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="74c96-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c96-113">Пример</span><span class="sxs-lookup"><span data-stu-id="74c96-113">Example</span></span>  

 <span data-ttu-id="74c96-114">В этом примере `<value>` тег используется для описания значения, которое `Counter` содержит свойство.</span><span class="sxs-lookup"><span data-stu-id="74c96-114">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="74c96-115">См. также</span><span class="sxs-lookup"><span data-stu-id="74c96-115">See also</span></span>

- [<span data-ttu-id="74c96-116">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="74c96-116">XML Comment Tags</span></span>](index.md)
