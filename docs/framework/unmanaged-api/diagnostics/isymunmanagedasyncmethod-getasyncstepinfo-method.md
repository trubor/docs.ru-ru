---
description: 'Дополнительные сведения о методе: Исимунманажедасинкмесод:: Жетасинкстепинфо'
title: Метод ISymUnmanagedAsyncMethod::GetAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: dc255323f103b3422b927b0489402b24767dcd92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737848"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="4e619-103">Метод ISymUnmanagedAsyncMethod::GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="4e619-103">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="4e619-104">См. раздел [метод дефинеасинкстепинфо](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4e619-104">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e619-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e619-105">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e619-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4e619-106">Parameters</span></span>  
  
|<span data-ttu-id="4e619-107">Параметр</span><span class="sxs-lookup"><span data-stu-id="4e619-107">Parameter</span></span>|<span data-ttu-id="4e619-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4e619-108">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4e619-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4e619-109">Return Value</span></span>  

 <span data-ttu-id="4e619-110">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4e619-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e619-111">Требования</span><span class="sxs-lookup"><span data-stu-id="4e619-111">Requirements</span></span>  

 <span data-ttu-id="4e619-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="4e619-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e619-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4e619-113">See also</span></span>

- [<span data-ttu-id="4e619-114">Интерфейс ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="4e619-114">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
