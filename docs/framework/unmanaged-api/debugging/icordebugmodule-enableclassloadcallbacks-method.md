---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Енаблекласслоадкаллбаккс'
title: Метод ICorDebugModule::EnableClassLoadCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 16516cceae9a10288f8660fa69d8e0c018953777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801089"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="f4ea4-103">Метод ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="f4ea4-103">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>

<span data-ttu-id="f4ea4-104">Определяет, вызываются ли для этого модуля обратные вызовы [ICorDebugManagedCallback:: loadClass](icordebugmanagedcallback-loadclass-method.md) и [ICorDebugManagedCallback:: унлоадкласс](icordebugmanagedcallback-unloadclass-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f4ea4-104">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ea4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4ea4-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4ea4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f4ea4-106">Parameters</span></span>  

 `bClassLoadCallbacks`  
 <span data-ttu-id="f4ea4-107">окне Задайте это значение `true` , чтобы среда CLR вызывала `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` методы и при возникновении связанных с ними событий.</span><span class="sxs-lookup"><span data-stu-id="f4ea4-107">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="f4ea4-108">Значение по умолчанию — `false` для модулей, не являющихся динамическими.</span><span class="sxs-lookup"><span data-stu-id="f4ea4-108">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="f4ea4-109">Значение всегда используется `true` для динамических модулей и не может быть изменено.</span><span class="sxs-lookup"><span data-stu-id="f4ea4-109">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4ea4-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4ea4-110">Remarks</span></span>  

 <span data-ttu-id="f4ea4-111">`ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` Обратные вызовы и всегда включены для динамических модулей и не могут быть отключены.</span><span class="sxs-lookup"><span data-stu-id="f4ea4-111">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4ea4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f4ea4-112">Requirements</span></span>  

 <span data-ttu-id="f4ea4-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4ea4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4ea4-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4ea4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4ea4-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4ea4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4ea4-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4ea4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ea4-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f4ea4-117">See also</span></span>
