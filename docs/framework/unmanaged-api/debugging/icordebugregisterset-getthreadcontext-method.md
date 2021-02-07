---
description: 'Дополнительные сведения о методе: ICorDebugRegisterSet:: GetThreadContext'
title: Метод ICorDebugRegisterSet::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: be6384562858d04b6e139eda83c172c09f2dfc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690812"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="b2afa-103">Метод ICorDebugRegisterSet::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="b2afa-103">ICorDebugRegisterSet::GetThreadContext Method</span></span>

<span data-ttu-id="b2afa-104">Возвращает контекст текущего потока.</span><span class="sxs-lookup"><span data-stu-id="b2afa-104">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2afa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2afa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2afa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b2afa-106">Parameters</span></span>  

 `contextSize`  
 <span data-ttu-id="b2afa-107">окне Размер массива в байтах `context` .</span><span class="sxs-lookup"><span data-stu-id="b2afa-107">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="b2afa-108">[вход, выход] Массив байтов, образующих `CONTEXT` структуру Win32 для текущей платформы.</span><span class="sxs-lookup"><span data-stu-id="b2afa-108">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2afa-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2afa-109">Remarks</span></span>  

 <span data-ttu-id="b2afa-110">Отладчик должен вызвать эту функцию вместо `GetThreadContext` функции Win32, так как поток может находиться в состоянии "перехвачено", в котором его контекст был временно изменен.</span><span class="sxs-lookup"><span data-stu-id="b2afa-110">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="b2afa-111">Возвращаемые данные представляют собой `CONTEXT` структуру Win32 для текущей платформы.</span><span class="sxs-lookup"><span data-stu-id="b2afa-111">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="b2afa-112">Для неконечных кадров клиенты должны проверить, какие регистры являются допустимыми с помощью [ICorDebugRegisterSet:: жетрегистерсаваилабле](icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="b2afa-112">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2afa-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b2afa-113">Requirements</span></span>  

 <span data-ttu-id="b2afa-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2afa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2afa-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2afa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2afa-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2afa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2afa-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2afa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2afa-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b2afa-118">See also</span></span>

- [<span data-ttu-id="b2afa-119">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="b2afa-119">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="b2afa-120">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="b2afa-120">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
