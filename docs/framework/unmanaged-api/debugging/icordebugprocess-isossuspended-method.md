---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: IsOSSuspended'
title: Метод ICorDebugProcess::IsOSSuspended
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: aa5e438418330d9fee51fcdb56a617421df06904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746775"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="dbc64-103">Метод ICorDebugProcess::IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="dbc64-103">ICorDebugProcess::IsOSSuspended Method</span></span>

<span data-ttu-id="dbc64-104">Возвращает значение, указывающее, был ли заданный поток приостановлен в результате остановки этого процесса отладчиком.</span><span class="sxs-lookup"><span data-stu-id="dbc64-104">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc64-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbc64-105">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc64-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dbc64-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="dbc64-107">окне Идентификатор рассматриваемого потока.</span><span class="sxs-lookup"><span data-stu-id="dbc64-107">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="dbc64-108">заполняет Указатель на логическое значение, равное, `true` если указанный поток был приостановлен; в противном случае `pbSuspended` — \* `false` .</span><span class="sxs-lookup"><span data-stu-id="dbc64-108">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbc64-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="dbc64-109">Remarks</span></span>  

 <span data-ttu-id="dbc64-110">Если указанный поток был приостановлен в результате остановки этого процесса отладчиком, счетчик приостановки Win32 указанного потока увеличивается на единицу.</span><span class="sxs-lookup"><span data-stu-id="dbc64-110">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="dbc64-111">Пользовательский интерфейс отладчика может захотеть использовать эту информацию при отображении счетчика приостановки операционной системы (ОС) для пользователя.</span><span class="sxs-lookup"><span data-stu-id="dbc64-111">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="dbc64-112">`IsOSSuspended`Метод имеет смысл только в контексте неуправляемой отладки.</span><span class="sxs-lookup"><span data-stu-id="dbc64-112">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="dbc64-113">Во время управляемой отладки потоки приостанавливаются совместно, а не с приостановленной ОС.</span><span class="sxs-lookup"><span data-stu-id="dbc64-113">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc64-114">Требования</span><span class="sxs-lookup"><span data-stu-id="dbc64-114">Requirements</span></span>  

 <span data-ttu-id="dbc64-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc64-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc64-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbc64-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbc64-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbc64-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbc64-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc64-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
