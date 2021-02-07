---
description: 'Дополнительные сведения: метод ICorDebug:: SetManagedHandler'
title: Метод ICorDebug::SetManagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 5817bd39a2c4e7c71dc12ca8d2d9b1263d116ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754359"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="565bf-103">Метод ICorDebug::SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="565bf-103">ICorDebug::SetManagedHandler Method</span></span>

<span data-ttu-id="565bf-104">Указывает объект обработчика событий для управляемых событий.</span><span class="sxs-lookup"><span data-stu-id="565bf-104">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565bf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="565bf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="565bf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="565bf-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="565bf-107">окне Указатель на объект [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , который является объектом обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="565bf-107">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="565bf-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="565bf-108">Remarks</span></span>  

 <span data-ttu-id="565bf-109">`SetManagedHandler` должен вызываться во время создания.</span><span class="sxs-lookup"><span data-stu-id="565bf-109">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="565bf-110">Если `ICorDebugManagedCallback` реализация не содержит достаточных интерфейсов для работы с событиями отладки для отлаживаемого приложения, `SetManagedHandler` возвращает значение HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="565bf-110">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="565bf-111">Требования</span><span class="sxs-lookup"><span data-stu-id="565bf-111">Requirements</span></span>  

 <span data-ttu-id="565bf-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="565bf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="565bf-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="565bf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="565bf-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="565bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="565bf-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="565bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565bf-116">См. также</span><span class="sxs-lookup"><span data-stu-id="565bf-116">See also</span></span>

- [<span data-ttu-id="565bf-117">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="565bf-117">ICorDebug Interface</span></span>](icordebug-interface.md)
