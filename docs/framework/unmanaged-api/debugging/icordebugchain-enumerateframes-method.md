---
description: 'Дополнительные сведения о методе: ICorDebugChain:: EnumerateFrames'
title: Метод ICorDebugChain::EnumerateFrames
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: 45bf69760eeccebada743d81e859a19e209b611a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711600"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="20d42-103">Метод ICorDebugChain::EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="20d42-103">ICorDebugChain::EnumerateFrames Method</span></span>

<span data-ttu-id="20d42-104">Возвращает перечислитель, содержащий все управляемые кадры стека в цепочке, начиная с самого последнего кадра.</span><span class="sxs-lookup"><span data-stu-id="20d42-104">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d42-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20d42-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20d42-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="20d42-106">Parameters</span></span>  

 `ppFrames`  
 <span data-ttu-id="20d42-107">заполняет Указатель на адрес объекта ICorDebugFrameEnum, который является перечислителем для кадров стека.</span><span class="sxs-lookup"><span data-stu-id="20d42-107">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20d42-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="20d42-108">Remarks</span></span>  

 <span data-ttu-id="20d42-109">Цепочка представляет физический стек вызовов для потока.</span><span class="sxs-lookup"><span data-stu-id="20d42-109">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="20d42-110">`EnumerateFrames`Метод должен вызываться только для управляемых цепочек.</span><span class="sxs-lookup"><span data-stu-id="20d42-110">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="20d42-111">API отладки не предоставляет методы для получения кадров, содержащихся в неуправляемых цепочках.</span><span class="sxs-lookup"><span data-stu-id="20d42-111">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="20d42-112">Для получения этих сведений отладчик должен использовать другие средства.</span><span class="sxs-lookup"><span data-stu-id="20d42-112">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d42-113">Требования</span><span class="sxs-lookup"><span data-stu-id="20d42-113">Requirements</span></span>  

 <span data-ttu-id="20d42-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20d42-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d42-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20d42-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20d42-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20d42-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20d42-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d42-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
