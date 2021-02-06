---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetAssemblyInfo'
title: Метод ICorProfilerInfo::GetAssemblyInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 64e94031e0e4fc5f768e94b83e4e97c3a9a7cb61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647860"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="c590f-103">Метод ICorProfilerInfo::GetAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c590f-103">ICorProfilerInfo::GetAssemblyInfo Method</span></span>

<span data-ttu-id="c590f-104">Принимает идентификатор сборки и возвращает имя сборки, а также идентификатор ее модуля манифеста.</span><span class="sxs-lookup"><span data-stu-id="c590f-104">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c590f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c590f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c590f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c590f-106">Parameters</span></span>  

 `assemblyId`  
 <span data-ttu-id="c590f-107">[in] Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="c590f-107">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c590f-108">[in] Длина `szName` в символах.</span><span class="sxs-lookup"><span data-stu-id="c590f-108">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c590f-109">[out] Указатель на общую длину имени сборки в символах.</span><span class="sxs-lookup"><span data-stu-id="c590f-109">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c590f-110">[out] Буфер расширенных символов, предоставленный вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="c590f-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="c590f-111">Когда функция возвращает значение, оно содержит имя сборки.</span><span class="sxs-lookup"><span data-stu-id="c590f-111">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="c590f-112">[out] Указатель на идентификатор домена приложения, содержащего эту сборку.</span><span class="sxs-lookup"><span data-stu-id="c590f-112">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="c590f-113">[out] Указатель на идентификатор модуля манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="c590f-113">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c590f-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="c590f-114">Remarks</span></span>  

 <span data-ttu-id="c590f-115">После возврата этого метода необходимо убедиться, что буфер `szName` был достаточно велик, чтобы вместить в себя полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="c590f-115">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="c590f-116">Для этого сравните значение, на которое указывает параметр `pcchName`, со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="c590f-116">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="c590f-117">Если параметр `pcchName` указывает на значение, превышающее значение `cchName`, выделите буфер `szName` большего размера, обновите параметр `cchName`, задав новый, больший размер, и вызовите метод `GetAssemblyInfo` снова.</span><span class="sxs-lookup"><span data-stu-id="c590f-117">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="c590f-118">Кроме того, сначала можно вызвать метод `GetAssemblyInfo` с буфером `szName` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="c590f-118">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c590f-119">Затем можно настроить размер буфера, исходя из значения, возвращенного в `pcchName`, и вызвать метод `GetAssemblyInfo` снова.</span><span class="sxs-lookup"><span data-stu-id="c590f-119">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c590f-120">Требования</span><span class="sxs-lookup"><span data-stu-id="c590f-120">Requirements</span></span>  

 <span data-ttu-id="c590f-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c590f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c590f-122">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c590f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c590f-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c590f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c590f-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c590f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c590f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="c590f-125">See also</span></span>

- [<span data-ttu-id="c590f-126">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c590f-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c590f-127">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c590f-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c590f-128">Профилирование</span><span class="sxs-lookup"><span data-stu-id="c590f-128">Profiling</span></span>](index.md)
