---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: Attach'
title: Метод ICorDebugAppDomain::Attach
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: 94448937a735b30d0403a207992dae29920a93bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754281"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="d4750-103">Метод ICorDebugAppDomain::Attach</span><span class="sxs-lookup"><span data-stu-id="d4750-103">ICorDebugAppDomain::Attach Method</span></span>

<span data-ttu-id="d4750-104">Присоединяет отладчик к домену приложения.</span><span class="sxs-lookup"><span data-stu-id="d4750-104">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4750-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4750-105">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4750-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4750-106">Remarks</span></span>  

 <span data-ttu-id="d4750-107">Отладчик должен быть присоединен к домену приложения для получения событий и включения отладки домена приложения.</span><span class="sxs-lookup"><span data-stu-id="d4750-107">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4750-108">Требования</span><span class="sxs-lookup"><span data-stu-id="d4750-108">Requirements</span></span>  

 <span data-ttu-id="d4750-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4750-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4750-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4750-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4750-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4750-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4750-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4750-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
