---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain3:: GetCachedWinRTTypes'
title: Метод ICorDebugAppDomain3::GetCachedWinRTTypes
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
ms.openlocfilehash: 813fb6c05d5e1e5f119424c6e983b86b3ff5889d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772241"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="7cc2a-103">Метод ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="7cc2a-103">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>

<span data-ttu-id="7cc2a-104">Возвращает перечислитель для всех кэшированных среда выполнения Windowsных типов.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-104">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc2a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7cc2a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc2a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7cc2a-106">Parameters</span></span>  

 `ppGuidToTypeEnum`  
 <span data-ttu-id="7cc2a-107">заполняет Указатель на объект интерфейса [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) , который может перечислить управляемые представления среда выполнения Windows типов, загруженных в домен приложения в данный момент.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-107">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc2a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="7cc2a-108">Requirements</span></span>  

 <span data-ttu-id="7cc2a-109">**Платформы:** среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="7cc2a-109">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7cc2a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cc2a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cc2a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cc2a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cc2a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc2a-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7cc2a-113">See also</span></span>

- [<span data-ttu-id="7cc2a-114">Интерфейс ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="7cc2a-114">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
