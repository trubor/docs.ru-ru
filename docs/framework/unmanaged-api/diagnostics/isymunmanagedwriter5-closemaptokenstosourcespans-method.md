---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter5:: CloseMapTokensToSourceSpans'
title: Метод ISymUnmanagedWriter5::CloseMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 687a853441a4406c2eb0a9c4b3d5d59df3575e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761659"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="3d1ed-103">Метод ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="3d1ed-103">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="3d1ed-104">Закройте Специальный раздел настраиваемых данных, чтобы получить сведения о сопоставлении диапазона "токен-источник".</span><span class="sxs-lookup"><span data-stu-id="3d1ed-104">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="3d1ed-105">После закрытия не удается добавить дополнительные сведения о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="3d1ed-105">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d1ed-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d1ed-106">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3d1ed-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3d1ed-107">Return Value</span></span>  

 <span data-ttu-id="3d1ed-108">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="3d1ed-108">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d1ed-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3d1ed-109">Requirements</span></span>  

 <span data-ttu-id="3d1ed-110">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="3d1ed-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1ed-111">См. также</span><span class="sxs-lookup"><span data-stu-id="3d1ed-111">See also</span></span>

- [<span data-ttu-id="3d1ed-112">Интерфейс ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="3d1ed-112">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
