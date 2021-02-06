---
description: Дополнительные сведения <returns> (Visual Basic)
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: ba5f1e231502a67e86ffbb92cf8868c3aecb05d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640385"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="de096-103">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de096-103">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="de096-104">Задает возвращаемое значение свойства или функции.</span><span class="sxs-lookup"><span data-stu-id="de096-104">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de096-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de096-105">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="de096-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="de096-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="de096-107">Описание возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="de096-107">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de096-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="de096-108">Remarks</span></span>  

 <span data-ttu-id="de096-109">Используйте `<returns>` тег в комментарии для объявления метода, чтобы описать возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="de096-109">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="de096-110">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="de096-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de096-111">Пример</span><span class="sxs-lookup"><span data-stu-id="de096-111">Example</span></span>  

 <span data-ttu-id="de096-112">В этом примере `<returns>` тег используется для объяснения того, что `DoesRecordExist` возвращает функция.</span><span class="sxs-lookup"><span data-stu-id="de096-112">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="de096-113">См. также</span><span class="sxs-lookup"><span data-stu-id="de096-113">See also</span></span>

- [<span data-ttu-id="de096-114">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="de096-114">XML Comment Tags</span></span>](index.md)
