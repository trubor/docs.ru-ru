---
description: 'Дополнительные сведения о методе: Икордебугсреаденум:: Next'
title: Метод ICorDebugThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 2cfb651d65eaf0f5797444ea1bec587cebdde2f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658429"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="bd461-103">Метод ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="bd461-103">ICorDebugThreadEnum::Next Method</span></span>

<span data-ttu-id="bd461-104">Возвращает число указанных экземпляров ICorDebugThread из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="bd461-104">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd461-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd461-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd461-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bd461-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="bd461-107">окне Число `ICorDebugThread` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="bd461-107">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="bd461-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugThread` объект, представляющий поток.</span><span class="sxs-lookup"><span data-stu-id="bd461-108">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bd461-109">заполняет Указатель на число `ICorDebugThread` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="bd461-109">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="bd461-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="bd461-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd461-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bd461-111">Requirements</span></span>  

 <span data-ttu-id="bd461-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd461-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd461-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd461-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd461-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd461-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd461-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd461-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
