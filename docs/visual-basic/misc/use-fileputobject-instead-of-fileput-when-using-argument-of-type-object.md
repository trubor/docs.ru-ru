---
description: 'Дополнительные сведения: используйте "FilePutObject" вместо "FilePut" при использовании аргумента типа "Object"'
title: При использовании аргумента с типом Object применяйте FilePutObject вместо FilePut
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460102"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="28046-103">При использовании аргумента с типом Object применяйте FilePutObject вместо FilePut</span><span class="sxs-lookup"><span data-stu-id="28046-103">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="28046-104">Метод `FilePut` включает аргумент типа `Object`.</span><span class="sxs-lookup"><span data-stu-id="28046-104">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="28046-105">Чтобы избежать неоднозначности, следует использовать`FilePutObject` вместо `FilePut` .</span><span class="sxs-lookup"><span data-stu-id="28046-105">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28046-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="28046-106">To correct this error</span></span>  
  
- <span data-ttu-id="28046-107">Замените `FilePut` на `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="28046-107">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="28046-108">Приведите аргумент `Object` к более конкретному типу.</span><span class="sxs-lookup"><span data-stu-id="28046-108">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="28046-109">Используйте функциональность объекта `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="28046-109">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28046-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="28046-110">See also</span></span>

- [<span data-ttu-id="28046-111">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="28046-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="28046-112">My. Computer. FileSystem. WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="28046-112">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
