---
description: 'Дополнительные сведения о методе: IDebuggerInfo:: IsDebuggerAttached'
title: Метод IDebuggerInfo::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: a17a7f5f1cef1d0c7025f4051e59767ce09ec421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709814"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="6d588-103">Метод IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="6d588-103">IDebuggerInfo::IsDebuggerAttached Method</span></span>

<span data-ttu-id="6d588-104">Возвращает значение, указывающее, присоединен ли к этому процессу управляемый отладчик.</span><span class="sxs-lookup"><span data-stu-id="6d588-104">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d588-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d588-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d588-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6d588-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="6d588-107">заполняет Указатель на значение, равное, `true` Если управляемый отладчик присоединен к процессу; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="6d588-107">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d588-108">Требования</span><span class="sxs-lookup"><span data-stu-id="6d588-108">Requirements</span></span>  

 <span data-ttu-id="6d588-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d588-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d588-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d588-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d588-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d588-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d588-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d588-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d588-113">См. также</span><span class="sxs-lookup"><span data-stu-id="6d588-113">See also</span></span>

- [<span data-ttu-id="6d588-114">Интерфейс IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="6d588-114">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)
