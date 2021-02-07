---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: Клеарунманажедбреакпоинт'
title: Метод ICorDebugProcess2::ClearUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: fba31a479e9bac525109e14c02995e78918d4c17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746637"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="d8229-103">Метод ICorDebugProcess2::ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d8229-103">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="d8229-104">Удаляет ранее установленную точку останова по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="d8229-104">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8229-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8229-105">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8229-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8229-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="d8229-107">окне `CORDB_ADDRESS` Значение типа, указывающее адрес, по которому была задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="d8229-107">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8229-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8229-108">Remarks</span></span>  

 <span data-ttu-id="d8229-109">Указанная точка останова была ранее задана предыдущим вызовом метода [ICorDebugProcess2:: сетунманажедбреакпоинт](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8229-109">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="d8229-110">`ClearUnmanagedBreakpoint`Метод может быть вызван во время выполнения отлаживаемого процесса.</span><span class="sxs-lookup"><span data-stu-id="d8229-110">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="d8229-111">`ClearUnmanagedBreakpoint`Метод возвращает код ошибки, если отладчик присоединен в режиме «только управляемый» или если в указанном адресе не существует точки останова.</span><span class="sxs-lookup"><span data-stu-id="d8229-111">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8229-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d8229-112">Requirements</span></span>  

 <span data-ttu-id="d8229-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8229-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8229-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8229-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8229-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8229-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8229-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8229-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
