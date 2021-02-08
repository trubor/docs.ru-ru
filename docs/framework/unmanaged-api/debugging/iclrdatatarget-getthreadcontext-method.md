---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: GetThreadContext'
title: Метод ICLRDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 210f4294aed31307557db419a0fb567cc71d4354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785696"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="11739-103">Метод ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="11739-103">ICLRDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="11739-104">Возвращает текущий контекст выполнения для данного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="11739-104">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="11739-105">Этот метод вызывается службами доступа к данным среды CLR.</span><span class="sxs-lookup"><span data-stu-id="11739-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11739-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11739-106">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11739-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="11739-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="11739-108">окне Идентификатор операционной системы потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="11739-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="11739-109">окне Флаги, указывающие, какие части контекста должны быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="11739-109">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="11739-110">Реализация возвратит по крайней мере эти части контекста.</span><span class="sxs-lookup"><span data-stu-id="11739-110">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="11739-111">окне Размер контекста.</span><span class="sxs-lookup"><span data-stu-id="11739-111">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="11739-112">заполняет Указатель на буфер, в который будет помещен контекст.</span><span class="sxs-lookup"><span data-stu-id="11739-112">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="11739-113">Данные в `context` буфере должны быть в формате `CONTEXT` структуры Win32.</span><span class="sxs-lookup"><span data-stu-id="11739-113">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="11739-114">Контекст задает зависящие от процессора данные регистров, поэтому определение `CONTEXT` структуры Win32 зависит от архитектуры процессора.</span><span class="sxs-lookup"><span data-stu-id="11739-114">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="11739-115">Описание структуры Win32 см. в файле заголовка WinNT. h `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="11739-115">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11739-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="11739-116">Remarks</span></span>  

 <span data-ttu-id="11739-117">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="11739-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11739-118">Требования</span><span class="sxs-lookup"><span data-stu-id="11739-118">Requirements</span></span>  

 <span data-ttu-id="11739-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11739-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11739-120">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="11739-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="11739-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11739-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11739-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11739-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11739-123">См. также</span><span class="sxs-lookup"><span data-stu-id="11739-123">See also</span></span>

- [<span data-ttu-id="11739-124">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="11739-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
