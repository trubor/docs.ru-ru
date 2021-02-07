---
description: 'Дополнительные сведения о: ICorProfilerInfo7:: Реадинмеморисимболс'
title: 'ICorProfilerInfo7:: Реадинмеморисимболс'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 7f1a88d823e7cdfcc89aa140681f61cfbe3f63ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736990"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="a482c-103">ICorProfilerInfo7:: Реадинмеморисимболс</span><span class="sxs-lookup"><span data-stu-id="a482c-103">ICorProfilerInfo7::ReadInMemorySymbols</span></span>

<span data-ttu-id="a482c-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="a482c-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a482c-105">Считывает байты из потока символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="a482c-105">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a482c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a482c-106">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a482c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a482c-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="a482c-108">окне Идентификатор модуля, содержащего поток в памяти.</span><span class="sxs-lookup"><span data-stu-id="a482c-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="a482c-109">окне Смещение в потоке в памяти, с которого начинается чтение байтов.</span><span class="sxs-lookup"><span data-stu-id="a482c-109">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="a482c-110">заполняет Указатель на буфер, в который будут копироваться данные.</span><span class="sxs-lookup"><span data-stu-id="a482c-110">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="a482c-111">Буфер должен иметь `countSymbolBytes` доступное место.</span><span class="sxs-lookup"><span data-stu-id="a482c-111">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="a482c-112">окне Число байтов для копирования.</span><span class="sxs-lookup"><span data-stu-id="a482c-112">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="a482c-113">заполняет При возврате из метода содержит фактическое число считанных байтов.</span><span class="sxs-lookup"><span data-stu-id="a482c-113">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a482c-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a482c-114">Return Value</span></span>  

 <span data-ttu-id="a482c-115">`S_OK`значение, если было считано ненулевое число байтов.</span><span class="sxs-lookup"><span data-stu-id="a482c-115">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="a482c-116">`CORPROF_E_MODULE_IS_DYNAMIC`, если модуль был создан с помощью <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="a482c-116">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a482c-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="a482c-117">Remarks</span></span>  

 <span data-ttu-id="a482c-118">`ReadInMemorySymbols`Метод пытается выполнить чтение `countSymbolBytes` данных, начиная со смещения `symbolsReadOffset` в потоке в памяти.</span><span class="sxs-lookup"><span data-stu-id="a482c-118">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="a482c-119">Данные копируются в `pSymbolBytes` , что должно иметь `countSymbolBytes` доступное место.</span><span class="sxs-lookup"><span data-stu-id="a482c-119">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="a482c-120">`pCountSymbolsBytesRead` содержит фактическое число считанных байтов, которое может быть меньше, чем `countSymbolBytes` при достижении конца потока.</span><span class="sxs-lookup"><span data-stu-id="a482c-120">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a482c-121">Текущая реализация не поддерживает отражение. Emit.</span><span class="sxs-lookup"><span data-stu-id="a482c-121">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="a482c-122">Если модуль был создан с помощью отражения. Emit, метод возвращает значение `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="a482c-122">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a482c-123">Требования</span><span class="sxs-lookup"><span data-stu-id="a482c-123">Requirements</span></span>  

 <span data-ttu-id="a482c-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a482c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a482c-125">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a482c-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a482c-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a482c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a482c-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a482c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a482c-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a482c-128">See also</span></span>

- [<span data-ttu-id="a482c-129">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="a482c-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
