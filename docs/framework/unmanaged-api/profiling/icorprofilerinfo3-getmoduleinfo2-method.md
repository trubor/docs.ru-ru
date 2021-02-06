---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetModuleInfo2'
title: Метод ICorProfilerInfo3::GetModuleInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
ms.openlocfilehash: 94a1159db9388e23fe244788dca0b2cf557c6cae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646742"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="ec83c-103">Метод ICorProfilerInfo3::GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="ec83c-103">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>

<span data-ttu-id="ec83c-104">Возвращает имя файла модуля, идентификатор родительской сборки модуля и битовую маску, описывающую свойства модуля, по идентификатору модуля.</span><span class="sxs-lookup"><span data-stu-id="ec83c-104">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec83c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec83c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec83c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ec83c-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="ec83c-107">[in] Идентификатор модуля, для которого будут извлекаться сведения.</span><span class="sxs-lookup"><span data-stu-id="ec83c-107">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="ec83c-108">[out] Базовый адрес, по которому модуль был загружен.</span><span class="sxs-lookup"><span data-stu-id="ec83c-108">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ec83c-109">[in] Длина буфера возврата `szName` в символах.</span><span class="sxs-lookup"><span data-stu-id="ec83c-109">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ec83c-110">[out] Указатель на общую длину возвращаемого имени файла модуля в символах.</span><span class="sxs-lookup"><span data-stu-id="ec83c-110">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="ec83c-111">[out] Буфер расширенных символов, предоставленный вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="ec83c-111">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="ec83c-112">При возврате метода этот буфер содержит имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="ec83c-112">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="ec83c-113">[out] Указатель на идентификатор родительской сборки модуля.</span><span class="sxs-lookup"><span data-stu-id="ec83c-113">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="ec83c-114">заполняет Битовая маска значений из перечисления [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) , определяющая свойства модуля.</span><span class="sxs-lookup"><span data-stu-id="ec83c-114">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec83c-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="ec83c-115">Remarks</span></span>  

 <span data-ttu-id="ec83c-116">Для динамических модулей параметр `szName` является именем метаданных модуля, а базовый адрес равен 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="ec83c-116">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="ec83c-117">Имя метаданных — это значение в столбце Name таблицы Module в метаданных.</span><span class="sxs-lookup"><span data-stu-id="ec83c-117">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="ec83c-118">Это также предоставляется в качестве <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> свойства управляемого кода, а также в качестве `szName` параметра метода [IMetaDataImport:: жетскопепропс](../metadata/imetadataimport-getscopeprops-method.md) для кода клиента неуправляемого метаданных.</span><span class="sxs-lookup"><span data-stu-id="ec83c-118">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="ec83c-119">Несмотря на то, что `GetModuleInfo2` метод может вызываться сразу после существования идентификатора модуля, идентификатор родительской сборки будет недоступен до тех пор, пока профилировщик не получит обратный вызов [ICorProfilerCallback:: модулеаттачедтоассембли](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ec83c-119">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="ec83c-120">После возврата метода `GetModuleInfo2` необходимо убедиться, что буфер `szName` был достаточно велик, чтобы вместить в себя полное имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="ec83c-120">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="ec83c-121">Для этого сравните значение, на которое указывает параметр `pcchName`, со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="ec83c-121">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ec83c-122">Если параметр `pcchName` указывает на значение, превышающее значение `cchName`, выделите буфер `szName` большего размера, обновите параметр `cchName`, задав новый, больший размер, и вызовите метод `GetModuleInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="ec83c-122">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="ec83c-123">Кроме того, сначала можно вызвать метод `GetModuleInfo2` с буфером `szName` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="ec83c-123">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ec83c-124">Затем можно задать размер буфера равным значению, возвращенному в параметре `pcchName`, и вызвать метод `GetModuleInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="ec83c-124">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec83c-125">Требования</span><span class="sxs-lookup"><span data-stu-id="ec83c-125">Requirements</span></span>  

 <span data-ttu-id="ec83c-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec83c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec83c-127">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec83c-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec83c-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec83c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec83c-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec83c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec83c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="ec83c-130">See also</span></span>

- [<span data-ttu-id="ec83c-131">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ec83c-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ec83c-132">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ec83c-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ec83c-133">Профилирование</span><span class="sxs-lookup"><span data-stu-id="ec83c-133">Profiling</span></span>](index.md)
