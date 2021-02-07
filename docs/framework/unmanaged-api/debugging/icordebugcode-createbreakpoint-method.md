---
description: 'Дополнительные сведения: метод ICorDebugCode:: CreateBreakpoint'
title: Метод ICorDebugCode::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: a9285d59da3e3f34ea303413fca67bc39aff9e32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711379"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="46268-103">Метод ICorDebugCode::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="46268-103">ICorDebugCode::CreateBreakpoint Method</span></span>

<span data-ttu-id="46268-104">Создает точку останова в этом сегменте кода в указанном смещении.</span><span class="sxs-lookup"><span data-stu-id="46268-104">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46268-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46268-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46268-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="46268-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="46268-107">окне Смещение для создания точки останова.</span><span class="sxs-lookup"><span data-stu-id="46268-107">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="46268-108">заполняет Указатель на адрес объекта "ICorDebugFunctionBreakpoint", представляющего точку останова.</span><span class="sxs-lookup"><span data-stu-id="46268-108">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46268-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="46268-109">Remarks</span></span>  

 <span data-ttu-id="46268-110">Прежде чем точка останова станет активной, ее необходимо добавить в объект Process.</span><span class="sxs-lookup"><span data-stu-id="46268-110">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="46268-111">Если этот код является кодом на языке MSIL и имеется JIT-скомпилированная собственная версия кода, то точка останова будет применена и в JIT-скомпилированном коде.</span><span class="sxs-lookup"><span data-stu-id="46268-111">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="46268-112">(То же самое верно, если код компилируется позже.)</span><span class="sxs-lookup"><span data-stu-id="46268-112">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46268-113">Требования</span><span class="sxs-lookup"><span data-stu-id="46268-113">Requirements</span></span>  

 <span data-ttu-id="46268-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46268-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46268-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46268-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46268-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46268-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46268-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46268-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
