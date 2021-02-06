---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetRuntimeInformation'
title: Метод ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: f615cc54e12b6f2f6eaa7335353f2f5f6a8ecfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646716"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="02f13-103">Метод ICorProfilerInfo3::GetRuntimeInformation</span><span class="sxs-lookup"><span data-stu-id="02f13-103">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>

<span data-ttu-id="02f13-104">Предоставляет сведения о версии для профилирования среды CLR.</span><span class="sxs-lookup"><span data-stu-id="02f13-104">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f13-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02f13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f13-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="02f13-106">Parameters</span></span>  

 `pClrInstanceId`  
 <span data-ttu-id="02f13-107">заполняет Репрезентативный идентификатор выполняющегося экземпляра среды CLR в процессе.</span><span class="sxs-lookup"><span data-stu-id="02f13-107">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="02f13-108">Это то же самое `ClrInstanceID` , что и отчеты о событиях запуска для трассировки событий Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="02f13-108">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="02f13-109">заполняет Тип среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="02f13-109">[out] The runtime type.</span></span> <span data-ttu-id="02f13-110">Этот параметр возвращает `COR_PRF_DESKTOP_CLR` для классической версии среды CLR или `COR_PRF_CORE_CLR` для основной версии среды CLR, используемой в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="02f13-110">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="02f13-111">заполняет Основной номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="02f13-111">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="02f13-112">заполняет Дополнительный номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="02f13-112">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="02f13-113">заполняет Номер версии сборки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="02f13-113">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="02f13-114">заполняет Номер версии среды CLR, связанной с обновлением программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="02f13-114">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="02f13-115">окне Длина (в символах) буфера, на который `szVersionString` указывает.</span><span class="sxs-lookup"><span data-stu-id="02f13-115">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="02f13-116">заполняет Длина в символах `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="02f13-116">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="02f13-117">заполняет Строка версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="02f13-117">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f13-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="02f13-118">Remarks</span></span>  

 <span data-ttu-id="02f13-119">Вы можете передать значение NULL для любого параметра.</span><span class="sxs-lookup"><span data-stu-id="02f13-119">You may pass null for any parameter.</span></span> <span data-ttu-id="02f13-120">Однако `pcchVersionString` не может иметь значение null, если `szVersionString` не равно null.</span><span class="sxs-lookup"><span data-stu-id="02f13-120">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f13-121">Требования</span><span class="sxs-lookup"><span data-stu-id="02f13-121">Requirements</span></span>  

 <span data-ttu-id="02f13-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f13-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f13-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02f13-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02f13-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f13-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f13-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f13-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f13-126">См. также</span><span class="sxs-lookup"><span data-stu-id="02f13-126">See also</span></span>

- [<span data-ttu-id="02f13-127">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="02f13-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="02f13-128">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="02f13-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="02f13-129">Профилирование</span><span class="sxs-lookup"><span data-stu-id="02f13-129">Profiling</span></span>](index.md)
