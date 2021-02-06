---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Dynamic'
title: Метод ICorDebugModule::IsDynamic
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 06ecb7aaffbe73da29bbdbba9446839db54c58c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660106"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="b424c-103">Метод ICorDebugModule::IsDynamic</span><span class="sxs-lookup"><span data-stu-id="b424c-103">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="b424c-104">Возвращает значение, указывающее, является ли этот модуль динамическим.</span><span class="sxs-lookup"><span data-stu-id="b424c-104">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b424c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b424c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b424c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b424c-106">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="b424c-107">[out] `true` значение, если этот модуль является динамическим; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="b424c-107">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b424c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b424c-108">Remarks</span></span>  

 <span data-ttu-id="b424c-109">Динамический модуль может добавлять новые классы и удалять существующие классы даже после загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="b424c-109">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="b424c-110">Обратные вызовы [ICorDebugManagedCallback:: loadClass](icordebugmanagedcallback-loadclass-method.md) и [ICorDebugManagedCallback:: унлоадкласс](icordebugmanagedcallback-unloadclass-method.md) информируют отладчик о добавлении или удалении класса.</span><span class="sxs-lookup"><span data-stu-id="b424c-110">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b424c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b424c-111">Requirements</span></span>  

 <span data-ttu-id="b424c-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b424c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b424c-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b424c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b424c-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b424c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b424c-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b424c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
