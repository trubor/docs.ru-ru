---
description: Дополнительные сведения о предложении Alias (Visual Basic)
title: Предложение Alias
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: bf0ee1c22105b29aedb99ce45a99ba866f4b93c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674081"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="6633b-103">Предложение Alias (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6633b-103">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="6633b-104">Указывает, что у внешней процедуры есть другое имя в своей библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="6633b-104">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6633b-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="6633b-105">Remarks</span></span>  

 <span data-ttu-id="6633b-106">`Alias`Ключевое слово можно использовать в следующем контексте:</span><span class="sxs-lookup"><span data-stu-id="6633b-106">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="6633b-107">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="6633b-107">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="6633b-108">В следующем примере `Alias` ключевое слово используется для предоставления имени функции в advapi32.dll, `GetUserNameA` , `getUserName` используемом вместо в этом примере.</span><span class="sxs-lookup"><span data-stu-id="6633b-108">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="6633b-109">Функция `getUserName` вызывается в подпрограмме `getUser` , которая отображает имя текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="6633b-109">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="6633b-110">См. также</span><span class="sxs-lookup"><span data-stu-id="6633b-110">See also</span></span>

- [<span data-ttu-id="6633b-111">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="6633b-111">Keywords</span></span>](../keywords/index.md)
