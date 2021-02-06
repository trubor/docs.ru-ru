---
description: 'Дополнительные сведения о методе: ICorDebugThread2:: Жетволатилеоссреадид'
title: Метод ICorDebugThread2::GetVolatileOSThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: 2c198577195c9b1e4a3a74fae686e405b22120eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658598"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="18b4b-103">Метод ICorDebugThread2::GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="18b4b-103">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>

<span data-ttu-id="18b4b-104">Возвращает идентификатор потока операционной системы для этого ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="18b4b-104">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b4b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18b4b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b4b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="18b4b-106">Parameters</span></span>  

 `pdwTid`  
 <span data-ttu-id="18b4b-107">заполняет Идентификатор потока операционной системы для этого потока.</span><span class="sxs-lookup"><span data-stu-id="18b4b-107">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b4b-108">Требования</span><span class="sxs-lookup"><span data-stu-id="18b4b-108">Requirements</span></span>  

 <span data-ttu-id="18b4b-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b4b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b4b-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18b4b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18b4b-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18b4b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b4b-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b4b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
