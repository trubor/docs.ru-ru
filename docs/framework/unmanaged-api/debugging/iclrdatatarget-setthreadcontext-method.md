---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: SetThreadContext'
title: Метод ICLRDataTarget::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: fc428bc887f7ba10f3096cdf17a757fb252418f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738209"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="5e16f-103">Метод ICLRDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="5e16f-103">ICLRDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="5e16f-104">Задает текущий контекст указанного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="5e16f-104">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="5e16f-105">Этот метод вызывается службами доступа к данным среды CLR.</span><span class="sxs-lookup"><span data-stu-id="5e16f-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e16f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5e16f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e16f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="5e16f-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="5e16f-108">окне Идентификатор операционной системы потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="5e16f-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5e16f-109">окне Размер контекста.</span><span class="sxs-lookup"><span data-stu-id="5e16f-109">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="5e16f-110">окне Указатель на буфер, содержащий контекст.</span><span class="sxs-lookup"><span data-stu-id="5e16f-110">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="5e16f-111">Данные в `context` буфере будут иметь формат `CONTEXT` структуры Win32.</span><span class="sxs-lookup"><span data-stu-id="5e16f-111">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="5e16f-112">Контекст задает зависящие от процессора данные регистров, поэтому определение `CONTEXT` структуры Win32 зависит от архитектуры процессора.</span><span class="sxs-lookup"><span data-stu-id="5e16f-112">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="5e16f-113">Описание структуры Win32 см. в файле заголовка WinNT. h `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="5e16f-113">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e16f-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="5e16f-114">Remarks</span></span>  

 <span data-ttu-id="5e16f-115">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="5e16f-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e16f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="5e16f-116">Requirements</span></span>  

 <span data-ttu-id="5e16f-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e16f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e16f-118">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="5e16f-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5e16f-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e16f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e16f-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e16f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e16f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="5e16f-121">See also</span></span>

- [<span data-ttu-id="5e16f-122">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="5e16f-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
