---
description: 'Дополнительные сведения о методе: ICorDebugDataTarget:: GetThreadContext'
title: Метод ICorDebugDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: cf40579aa0a495af4e5e775334d177ca6f3da86f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710638"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="14abc-103">Метод ICorDebugDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="14abc-103">ICorDebugDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="14abc-104">Возвращает текущий контекст потока для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="14abc-104">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14abc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14abc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14abc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="14abc-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="14abc-107">окне Идентификатор потока, контекст которого должен быть получен.</span><span class="sxs-lookup"><span data-stu-id="14abc-107">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="14abc-108">Идентификатор определяется операционной системой.</span><span class="sxs-lookup"><span data-stu-id="14abc-108">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="14abc-109">окне Побитовое сочетание флагов, зависящих от платформы, которые указывают, какие части контекста должны считываться.</span><span class="sxs-lookup"><span data-stu-id="14abc-109">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="14abc-110">[входной] Размер `pContext`.</span><span class="sxs-lookup"><span data-stu-id="14abc-110">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="14abc-111">заполняет Буфер, в котором будет храниться контекст потока.</span><span class="sxs-lookup"><span data-stu-id="14abc-111">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14abc-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="14abc-112">Remarks</span></span>  

 <span data-ttu-id="14abc-113">На платформах Windows `pContext` должна быть `CONTEXT` Структура (определенная в Winnt. h), подходящая для типа компьютера, указанного в методе [ICorDebugDataTarget::-Platform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14abc-113">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="14abc-114">`contextFlags` должны иметь те же значения, что и `ContextFlags` поле `CONTEXT` структуры.</span><span class="sxs-lookup"><span data-stu-id="14abc-114">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="14abc-115">`CONTEXT`Структура зависит от конкретного процессора; дополнительные сведения см. в файле WINNT. h.</span><span class="sxs-lookup"><span data-stu-id="14abc-115">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14abc-116">Требования</span><span class="sxs-lookup"><span data-stu-id="14abc-116">Requirements</span></span>  

 <span data-ttu-id="14abc-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14abc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14abc-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14abc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14abc-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14abc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14abc-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14abc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14abc-121">См. также</span><span class="sxs-lookup"><span data-stu-id="14abc-121">See also</span></span>

- [<span data-ttu-id="14abc-122">Интерфейс ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="14abc-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="14abc-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="14abc-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="14abc-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="14abc-124">Debugging</span></span>](index.md)
