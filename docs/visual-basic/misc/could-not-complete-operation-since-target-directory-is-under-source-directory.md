---
description: 'Дополнительные сведения: не удалось завершить операцию, так как целевой каталог находится в исходном каталоге'
title: 'Невозможно завершить операцию: конечный каталог находится внутри исходного'
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 5fb0bf1d761faf9d3d0c64e8815e28e14841b1fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463524"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="3dfcf-103">Невозможно завершить операцию: конечный каталог находится внутри исходного</span><span class="sxs-lookup"><span data-stu-id="3dfcf-103">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="3dfcf-104">Циклическая операция не удалась.</span><span class="sxs-lookup"><span data-stu-id="3dfcf-104">A cyclic operation has failed.</span></span> <span data-ttu-id="3dfcf-105">Циклические операции являются бесконечными циклами и поэтому не могут завершиться.</span><span class="sxs-lookup"><span data-stu-id="3dfcf-105">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="3dfcf-106">Например, объект A может попытаться наследоваться от объекта B, который в свою очередь наследуется от объекта A.</span><span class="sxs-lookup"><span data-stu-id="3dfcf-106">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3dfcf-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="3dfcf-107">To correct this error</span></span>  
  
- <span data-ttu-id="3dfcf-108">При наследовании убедитесь в отсутствии циклических ссылок.</span><span class="sxs-lookup"><span data-stu-id="3dfcf-108">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfcf-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3dfcf-109">See also</span></span>

- [<span data-ttu-id="3dfcf-110">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="3dfcf-110">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="3dfcf-111">Использование точек останова в отладчике Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3dfcf-111">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
