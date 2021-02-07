---
description: 'Дополнительные сведения о методе: ICorDebugEnum:: NOCOUNT'
title: Метод ICorDebugEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 38fa85958ea0c6945a5575d12700701ed355891d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694563"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="ea94a-103">Метод ICorDebugEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="ea94a-103">ICorDebugEnum::GetCount Method</span></span>

<span data-ttu-id="ea94a-104">Возвращает число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="ea94a-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea94a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ea94a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea94a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea94a-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="ea94a-107">заполняет Указатель на число элементов в перечислении.</span><span class="sxs-lookup"><span data-stu-id="ea94a-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea94a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ea94a-108">Requirements</span></span>  

 <span data-ttu-id="ea94a-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea94a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea94a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea94a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea94a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea94a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea94a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea94a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
