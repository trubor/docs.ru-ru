---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedScope2'
title: Интерфейс ISymUnmanagedScope2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: a15094da68b00dbec454b2f6a642ac333f9a34ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763154"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="7d284-103">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="7d284-103">ISymUnmanagedScope2 Interface</span></span>

<span data-ttu-id="7d284-104">Представляет лексическую область внутри метода.</span><span class="sxs-lookup"><span data-stu-id="7d284-104">Represents a lexical scope within a method.</span></span> <span data-ttu-id="7d284-105">Этот интерфейс расширяет интерфейс [исимунманажедскопе](isymunmanagedscope-interface.md) с помощью методов, которые получают сведения о константах, определенных в области.</span><span class="sxs-lookup"><span data-stu-id="7d284-105">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d284-106">Методы</span><span class="sxs-lookup"><span data-stu-id="7d284-106">Methods</span></span>  
  
|<span data-ttu-id="7d284-107">Метод</span><span class="sxs-lookup"><span data-stu-id="7d284-107">Method</span></span>|<span data-ttu-id="7d284-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7d284-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d284-109">Метод GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="7d284-109">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="7d284-110">Возвращает число констант, определенных в этой области.</span><span class="sxs-lookup"><span data-stu-id="7d284-110">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="7d284-111">Метод GetConstants</span><span class="sxs-lookup"><span data-stu-id="7d284-111">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="7d284-112">Возвращает локальные константы, определенные в этой области.</span><span class="sxs-lookup"><span data-stu-id="7d284-112">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d284-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7d284-113">Requirements</span></span>  

 <span data-ttu-id="7d284-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="7d284-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d284-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7d284-115">See also</span></span>

- [<span data-ttu-id="7d284-116">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="7d284-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7d284-117">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="7d284-117">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
