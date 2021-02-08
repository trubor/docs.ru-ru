---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: GetCurrentThreadID'
title: Метод ICLRDataTarget::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: ae1ef00fd6afbecf741d1e4ed215c816dcf6af8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801362"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="5a209-103">Метод ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="5a209-103">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="5a209-104">Возвращает идентификатор операционной системы для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="5a209-104">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a209-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a209-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a209-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a209-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="5a209-107">заполняет Указатель на идентификатор операционной системы текущего потока для целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="5a209-107">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a209-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="5a209-108">Remarks</span></span>  

 <span data-ttu-id="5a209-109">Если текущего потока для целевого процесса нет, `GetCurrentThreadID` метод может завершиться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5a209-109">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a209-110">Требования</span><span class="sxs-lookup"><span data-stu-id="5a209-110">Requirements</span></span>  

 <span data-ttu-id="5a209-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a209-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a209-112">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="5a209-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5a209-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a209-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a209-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a209-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a209-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5a209-115">See also</span></span>

- [<span data-ttu-id="5a209-116">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="5a209-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
