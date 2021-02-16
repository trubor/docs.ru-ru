---
description: 'Дополнительные сведения: используйте FileGetObject вместо "FileGet" при использовании аргумента типа "Object"'
title: При использовании аргумента типа Object используйте метод FileGetObject вместо метода FileGet
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 4481fdced961cacf0e652c141601efa13bec776b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471166"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="f006d-103">При использовании аргумента типа Object используйте метод FileGetObject вместо метода FileGet</span><span class="sxs-lookup"><span data-stu-id="f006d-103">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>

<span data-ttu-id="f006d-104">Метод `FileGet` включает аргумент типа `Object`.</span><span class="sxs-lookup"><span data-stu-id="f006d-104">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="f006d-105">Чтобы избежать неоднозначности, следует использовать`FileGetObject` вместо `FileGet` .</span><span class="sxs-lookup"><span data-stu-id="f006d-105">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="f006d-106">Обратите внимание, что функциональные возможности, предлагаемые `My.Computer.Filesystem` , проще в использовании и обеспечивают большую производительность, чем `FileGet` или `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="f006d-106">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f006d-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="f006d-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f006d-108">Замените `FileGet` на `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="f006d-108">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="f006d-109">Приведите аргумент `Object` к более конкретному типу.</span><span class="sxs-lookup"><span data-stu-id="f006d-109">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f006d-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f006d-110">See also</span></span>

- [<span data-ttu-id="f006d-111">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="f006d-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
