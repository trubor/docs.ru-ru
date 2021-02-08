---
description: 'См. Дополнительные сведения о методе ICLRRuntimeInfo:: Overloads'
title: Метод ICLRRuntimeInfo::IsLoadable
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: cf63212350bfbd18e2a312add72818b163c32d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789792"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="ff0bf-103">Метод ICLRRuntimeInfo::IsLoadable</span><span class="sxs-lookup"><span data-stu-id="ff0bf-103">ICLRRuntimeInfo::IsLoadable Method</span></span>

<span data-ttu-id="ff0bf-104">Указывает, можно ли загрузить среду выполнения, связанную с этим интерфейсом, в текущий процесс, принимая во внимание другие среды выполнения, которые уже могут быть загружены в процесс.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-104">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0bf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff0bf-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff0bf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ff0bf-106">Parameters</span></span>  

 `pbLoadable`  
 <span data-ttu-id="ff0bf-107">[out] `true` значение, если эту среду выполнения можно загрузить в текущий процесс; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="ff0bf-107">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff0bf-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ff0bf-108">Return Value</span></span>  

 <span data-ttu-id="ff0bf-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ff0bf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff0bf-110">HRESULT</span></span>|<span data-ttu-id="ff0bf-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="ff0bf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff0bf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff0bf-112">S_OK</span></span>|<span data-ttu-id="ff0bf-113">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ff0bf-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ff0bf-114">E_POINTER</span></span>|<span data-ttu-id="ff0bf-115">Параметр `pbLoadable` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-115">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff0bf-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff0bf-116">Remarks</span></span>  

 <span data-ttu-id="ff0bf-117">Если в процесс уже загружена другая среда выполнения, и среда выполнения, связанная с этим интерфейсом, может быть загружена для внутрипроцессного параллельного выполнения, `pbLoadable` возвращает `true` .</span><span class="sxs-lookup"><span data-stu-id="ff0bf-117">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="ff0bf-118">Если две среды выполнения не могут выполняться параллельно, `pbLoadable` возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="ff0bf-118">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="ff0bf-119">Например, общеязыковая среда выполнения (CLR) версии 4 может работать параллельно в том же процессе с CLR версии 2,0 или CLR версии 1,1.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-119">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="ff0bf-120">Однако среда CLR версии 1,1 и CLR версии 2,0 не могут выполняться параллельно в процессе.</span><span class="sxs-lookup"><span data-stu-id="ff0bf-120">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="ff0bf-121">Если в процесс не загружены среды выполнения, этот метод всегда возвращает значение `true` .</span><span class="sxs-lookup"><span data-stu-id="ff0bf-121">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0bf-122">Требования</span><span class="sxs-lookup"><span data-stu-id="ff0bf-122">Requirements</span></span>  

 <span data-ttu-id="ff0bf-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff0bf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff0bf-124">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="ff0bf-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ff0bf-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff0bf-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff0bf-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff0bf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0bf-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ff0bf-127">See also</span></span>

- [<span data-ttu-id="ff0bf-128">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="ff0bf-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ff0bf-129">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="ff0bf-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ff0bf-130">Размещение</span><span class="sxs-lookup"><span data-stu-id="ff0bf-130">Hosting</span></span>](index.md)
