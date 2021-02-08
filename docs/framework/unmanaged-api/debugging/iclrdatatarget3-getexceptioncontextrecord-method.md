---
description: 'Дополнительные сведения о методе: метод iclrdatatarget3:: Жетексцептионконтекстрекорд'
title: Метод ICLRDataTarget3::GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: c722eaaf0f9935bc7adaa69a1792f934f631a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794836"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="aff82-103">Метод ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="aff82-103">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>

<span data-ttu-id="aff82-104">Вызывается службами доступа к данным среды CLR для извлечения записи контекста, связанной с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="aff82-104">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="aff82-105">Например, для целевого объекта дампа это будет эквивалентно записи контекста, передаваемой через `ExceptionParam` аргумент в функцию [Минидумпвритедумп](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) в библиотеке справки по отладке Windows (DBGHELP).</span><span class="sxs-lookup"><span data-stu-id="aff82-105">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff82-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aff82-106">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aff82-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="aff82-107">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="aff82-108">[в] Размер входного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="aff82-108">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="aff82-109">Он должен быть достаточно большим, чтобы вместить запись контекста.</span><span class="sxs-lookup"><span data-stu-id="aff82-109">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="aff82-110">[из] Указатель на тип `ULONG32`, который получает количество байтов, фактически записанных в буфер.</span><span class="sxs-lookup"><span data-stu-id="aff82-110">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="aff82-111">[из] Указатель на буфер памяти, который получает копию записи контекста.</span><span class="sxs-lookup"><span data-stu-id="aff82-111">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="aff82-112">Запись исключения возвращается как тип [контекста](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="aff82-112">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aff82-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="aff82-113">Return Value</span></span>  

 <span data-ttu-id="aff82-114">Возвращается значение `S_OK` при успешном выполнении или код ошибки `HRESULT` при сбое.</span><span class="sxs-lookup"><span data-stu-id="aff82-114">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="aff82-115">Коды `HRESULT` могут включать значения, приведенные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="aff82-115">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="aff82-116">Код возврата</span><span class="sxs-lookup"><span data-stu-id="aff82-116">Return code</span></span>|<span data-ttu-id="aff82-117">Описание</span><span class="sxs-lookup"><span data-stu-id="aff82-117">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="aff82-118">Метод успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="aff82-118">Method succeeded.</span></span> <span data-ttu-id="aff82-119">Запись контекста скопирована в буфер вывода.</span><span class="sxs-lookup"><span data-stu-id="aff82-119">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="aff82-120">Нет записей контекста, связанных с целевым объектом.</span><span class="sxs-lookup"><span data-stu-id="aff82-120">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="aff82-121">Размер входного буфера недостаточен для сохранения записи контекста.</span><span class="sxs-lookup"><span data-stu-id="aff82-121">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aff82-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="aff82-122">Remarks</span></span>  

 <span data-ttu-id="aff82-123">[Контекст](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) — это зависящая от платформы структура, определенная в заголовках, предоставляемых Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="aff82-123">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="aff82-124">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="aff82-124">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff82-125">Требования</span><span class="sxs-lookup"><span data-stu-id="aff82-125">Requirements</span></span>  

 <span data-ttu-id="aff82-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff82-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff82-127">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="aff82-127">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aff82-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aff82-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aff82-129">**Платформа .NET Framework версии:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aff82-129">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff82-130">См. также</span><span class="sxs-lookup"><span data-stu-id="aff82-130">See also</span></span>

- [<span data-ttu-id="aff82-131">Интерфейс ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="aff82-131">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="aff82-132">Метод GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="aff82-132">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="aff82-133">Метод GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="aff82-133">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
