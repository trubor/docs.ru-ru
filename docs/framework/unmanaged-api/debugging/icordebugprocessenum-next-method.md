---
description: 'Дополнительные сведения о методе: Икордебугпроцессенум:: Next'
title: Метод ICorDebugProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: e32ff2e67f3f8a0242e0a0f93ed00229fee9cc26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691176"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="96e74-103">Метод ICorDebugProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="96e74-103">ICorDebugProcessEnum::Next Method</span></span>

<span data-ttu-id="96e74-104">Возвращает указанное число экземпляров ICorDebugProcess из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="96e74-104">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e74-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96e74-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e74-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96e74-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="96e74-107">окне Число `ICorDebugProcess` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="96e74-107">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="96e74-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugProcess` объект, представляющий процесс.</span><span class="sxs-lookup"><span data-stu-id="96e74-108">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="96e74-109">заполняет Указатель на число `ICorDebugProcess` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="96e74-109">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="96e74-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="96e74-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e74-111">Требования</span><span class="sxs-lookup"><span data-stu-id="96e74-111">Requirements</span></span>  

 <span data-ttu-id="96e74-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e74-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e74-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96e74-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96e74-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96e74-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96e74-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e74-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
