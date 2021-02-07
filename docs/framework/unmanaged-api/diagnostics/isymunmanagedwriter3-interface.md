---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedWriter3'
title: Интерфейс ISymUnmanagedWriter3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 586220af85f193b43acf0578706d9f67e3e83386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761737"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="beff0-103">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="beff0-103">ISymUnmanagedWriter3 Interface</span></span>

<span data-ttu-id="beff0-104">Представляет средство записи символов и предоставляет методы для определения документов, точек следования, лексических областей и переменных.</span><span class="sxs-lookup"><span data-stu-id="beff0-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="beff0-105">Этот интерфейс расширяет интерфейс [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="beff0-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="beff0-106">Методы</span><span class="sxs-lookup"><span data-stu-id="beff0-106">Methods</span></span>  
  
|<span data-ttu-id="beff0-107">Метод</span><span class="sxs-lookup"><span data-stu-id="beff0-107">Method</span></span>|<span data-ttu-id="beff0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="beff0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="beff0-109">Метод Commit</span><span class="sxs-lookup"><span data-stu-id="beff0-109">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="beff0-110">Фиксирует изменения, записанные на данный момент в поток.</span><span class="sxs-lookup"><span data-stu-id="beff0-110">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="beff0-111">Метод OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="beff0-111">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="beff0-112">Открывает метод и предоставляет его фактическое смещение раздела в изображении.</span><span class="sxs-lookup"><span data-stu-id="beff0-112">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="beff0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="beff0-113">Requirements</span></span>  

 <span data-ttu-id="beff0-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="beff0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beff0-115">См. также</span><span class="sxs-lookup"><span data-stu-id="beff0-115">See also</span></span>

- [<span data-ttu-id="beff0-116">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="beff0-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="beff0-117">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="beff0-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="beff0-118">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="beff0-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
