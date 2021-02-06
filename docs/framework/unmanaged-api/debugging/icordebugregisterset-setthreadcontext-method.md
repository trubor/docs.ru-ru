---
description: 'Дополнительные сведения о методе: ICorDebugRegisterSet:: SetThreadContext'
title: Метод ICorDebugRegisterSet::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 8d874b1864e85e477260632ad6012dbbf10aefb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637694"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="64275-103">Метод ICorDebugRegisterSet::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="64275-103">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="64275-104">`SetThreadContext` не реализован в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="64275-104">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="64275-105">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="64275-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64275-106">Используйте операцию более высокого уровня [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) , чтобы задать контекст потока.</span><span class="sxs-lookup"><span data-stu-id="64275-106">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64275-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64275-107">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="64275-108">Требования</span><span class="sxs-lookup"><span data-stu-id="64275-108">Requirements</span></span>  

 <span data-ttu-id="64275-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64275-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64275-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64275-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64275-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64275-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64275-112">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="64275-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64275-113">См. также</span><span class="sxs-lookup"><span data-stu-id="64275-113">See also</span></span>

- [<span data-ttu-id="64275-114">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="64275-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="64275-115">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="64275-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
