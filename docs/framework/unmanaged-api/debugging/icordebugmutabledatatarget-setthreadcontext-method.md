---
description: 'Дополнительные сведения о методе: Икордебугмутабледататаржет:: SetThreadContext'
title: Метод ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 4674df92b72b44e19eff663c9a17dd8ca4b5a1b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722481"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="8da11-103">Метод ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="8da11-103">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="8da11-104">Задает контекст (значения регистра) для потока.</span><span class="sxs-lookup"><span data-stu-id="8da11-104">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8da11-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8da11-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8da11-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8da11-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="8da11-107">[in] Идентификатор потока, определяемый операционной системой.</span><span class="sxs-lookup"><span data-stu-id="8da11-107">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8da11-108">[in] Размер буфера `pContext` для записи.</span><span class="sxs-lookup"><span data-stu-id="8da11-108">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="8da11-109">[in] Указатель на байты, которые требуется записать.</span><span class="sxs-lookup"><span data-stu-id="8da11-109">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8da11-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="8da11-110">Remarks</span></span>  

 <span data-ttu-id="8da11-111">Метод `SetThreadContext` обновляет текущий контекст для потока, указанного аргументом `dwThreadID`, который задается операционной системой.</span><span class="sxs-lookup"><span data-stu-id="8da11-111">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="8da11-112">Формат записи контекста определяется платформой, указанной в методе [ICorDebugDataTarget::-Platform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8da11-112">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="8da11-113">В Windows это структура [контекста](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="8da11-113">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8da11-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8da11-114">Requirements</span></span>  

 <span data-ttu-id="8da11-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8da11-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8da11-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8da11-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8da11-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8da11-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8da11-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8da11-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da11-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8da11-119">See also</span></span>

- [<span data-ttu-id="8da11-120">Интерфейс ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="8da11-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="8da11-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8da11-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
