---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: Сетунманажедбреакпоинт'
title: Метод ICorDebugProcess2::SetUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 7989f0fc9908941513b7d099fde81c79cef82c5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746546"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="9f265-103">Метод ICorDebugProcess2::SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9f265-103">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="9f265-104">Задает неуправляемую точку останова в указанном смещении машинного образа.</span><span class="sxs-lookup"><span data-stu-id="9f265-104">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f265-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f265-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f265-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9f265-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="9f265-107">окне `CORDB_ADDRESS` Объект, указывающий смещение машинного образа.</span><span class="sxs-lookup"><span data-stu-id="9f265-107">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="9f265-108">окне Размер массива в байтах `buffer` .</span><span class="sxs-lookup"><span data-stu-id="9f265-108">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9f265-109">заполняет Массив, содержащий код операции, который заменяется точкой останова.</span><span class="sxs-lookup"><span data-stu-id="9f265-109">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="9f265-110">заполняет Указатель на число байтов, возвращенных в `buffer` массиве.</span><span class="sxs-lookup"><span data-stu-id="9f265-110">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f265-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9f265-111">Remarks</span></span>  

 <span data-ttu-id="9f265-112">Если смещение машинного образа находится в среде CLR, точка останова будет пропущена.</span><span class="sxs-lookup"><span data-stu-id="9f265-112">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="9f265-113">Это позволяет среде CLR избежать диспетчеризации точки останова по внешнему каналу, когда точка останова задается отладчиком.</span><span class="sxs-lookup"><span data-stu-id="9f265-113">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f265-114">Требования</span><span class="sxs-lookup"><span data-stu-id="9f265-114">Requirements</span></span>  

 <span data-ttu-id="9f265-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f265-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f265-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f265-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f265-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f265-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f265-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f265-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
