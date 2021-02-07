---
description: 'Дополнительные сведения о методе: ICorDebugBreakpointEnum:: Next'
title: Метод ICorDebugBreakpointEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: 966494bbabaca99b6b5168db6fb7616c15c537e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711678"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="5a795-103">Метод ICorDebugBreakpointEnum::Next</span><span class="sxs-lookup"><span data-stu-id="5a795-103">ICorDebugBreakpointEnum::Next Method</span></span>

<span data-ttu-id="5a795-104">Возвращает указанное число экземпляров Икордебугбреакпоинт из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="5a795-104">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a795-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a795-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a795-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a795-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="5a795-107">окне Число `ICorDebugBreakpoint` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="5a795-107">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="5a795-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugBreakpoint` объект, представляющий точку останова.</span><span class="sxs-lookup"><span data-stu-id="5a795-108">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5a795-109">заполняет Указатель на число `ICorDebugBreakpoint` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="5a795-109">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="5a795-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="5a795-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a795-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5a795-111">Requirements</span></span>  

 <span data-ttu-id="5a795-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a795-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a795-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a795-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a795-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a795-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a795-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a795-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
