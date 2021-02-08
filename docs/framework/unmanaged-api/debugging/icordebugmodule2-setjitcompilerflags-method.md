---
description: 'Дополнительные сведения о методе: ICorDebugModule2:: SetJITCompilerFlags'
title: Метод ICorDebugModule2::SetJITCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 72139c2fefc0eab7e76e38d07558e4386b47bc34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801076"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="977f1-103">Метод ICorDebugModule2::SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="977f1-103">ICorDebugModule2::SetJITCompilerFlags Method</span></span>

<span data-ttu-id="977f1-104">Задает флаги, управляющие JIT-компиляцией этого ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="977f1-104">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977f1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="977f1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="977f1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="977f1-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="977f1-107">окне Побитовое сочетание значений перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="977f1-107">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="977f1-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="977f1-108">Remarks</span></span>  

 <span data-ttu-id="977f1-109">Если `dwFlags` значение недопустимо, `SetJITCompilerFlags` метод завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="977f1-109">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="977f1-110">`SetJITCompilerFlags`Метод может быть вызван только в обратном вызове [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="977f1-110">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="977f1-111">Попытки вызвать его после `ICorDebugManagedCallback::LoadModule` доставки обратного вызова завершатся ошибкой.</span><span class="sxs-lookup"><span data-stu-id="977f1-111">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="977f1-112">"Изменить и продолжить" не поддерживается на платформах 64-разрядных или Win9x.</span><span class="sxs-lookup"><span data-stu-id="977f1-112">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="977f1-113">Поэтому при вызове `SetJITCompilerFlags` метода для любой из этих двух платформ с флагом CORDEBUG_JIT_ENABLE_ENC, установленным в `dwFlags` , `SetJITCompilerFlags` метод и все методы, относящиеся к Edit и Continue, такие как [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md), завершатся ошибкой.</span><span class="sxs-lookup"><span data-stu-id="977f1-113">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977f1-114">Требования</span><span class="sxs-lookup"><span data-stu-id="977f1-114">Requirements</span></span>  

 <span data-ttu-id="977f1-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="977f1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977f1-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="977f1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="977f1-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="977f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="977f1-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="977f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
