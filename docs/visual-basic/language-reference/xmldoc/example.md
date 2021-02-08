---
description: Дополнительные сведения <example> (Visual Basic)
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787491"
---
# <a name="example-visual-basic"></a><span data-ttu-id="5beaa-103">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5beaa-103">\<example> (Visual Basic)</span></span>

<span data-ttu-id="5beaa-104">Указывает пример для элемента.</span><span class="sxs-lookup"><span data-stu-id="5beaa-104">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5beaa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5beaa-105">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5beaa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5beaa-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="5beaa-107">Описание примера кода.</span><span class="sxs-lookup"><span data-stu-id="5beaa-107">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5beaa-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="5beaa-108">Remarks</span></span>  

 <span data-ttu-id="5beaa-109">Тег `<example>` позволяет указать пример использования метода или другого элемента библиотеки.</span><span class="sxs-lookup"><span data-stu-id="5beaa-109">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="5beaa-110">Вместе с ним часто применяется тег [\<code>](code.md).</span><span class="sxs-lookup"><span data-stu-id="5beaa-110">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="5beaa-111">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="5beaa-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5beaa-112">Пример</span><span class="sxs-lookup"><span data-stu-id="5beaa-112">Example</span></span>  

 <span data-ttu-id="5beaa-113">В этом примере `<example>` тег используется для включения примера использования `ID` поля.</span><span class="sxs-lookup"><span data-stu-id="5beaa-113">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5beaa-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5beaa-114">See also</span></span>

- [<span data-ttu-id="5beaa-115">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="5beaa-115">XML Comment Tags</span></span>](index.md)
