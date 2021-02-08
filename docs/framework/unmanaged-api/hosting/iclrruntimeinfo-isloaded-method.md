---
description: 'Дополнительные сведения о методе ICLRRuntimeInfo:: Overloads'
title: Метод ICLRRuntimeInfo::IsLoaded
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: e6a5984dbd2340fe07af546dd48ae6760d5b4271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799710"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="20f84-103">Метод ICLRRuntimeInfo::IsLoaded</span><span class="sxs-lookup"><span data-stu-id="20f84-103">ICLRRuntimeInfo::IsLoaded Method</span></span>

<span data-ttu-id="20f84-104">Указывает, загружается ли в процесс общеязыковая среда выполнения (CLR), связанная с интерфейсом [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="20f84-104">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="20f84-105">Среду выполнения можно загрузить без запуска.</span><span class="sxs-lookup"><span data-stu-id="20f84-105">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f84-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20f84-106">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20f84-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="20f84-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="20f84-108">окне Обработчик процесса.</span><span class="sxs-lookup"><span data-stu-id="20f84-108">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="20f84-109">[out] `true` значение, если среда CLR загружена в процесс; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="20f84-109">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20f84-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="20f84-110">Return Value</span></span>  

 <span data-ttu-id="20f84-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="20f84-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="20f84-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20f84-112">HRESULT</span></span>|<span data-ttu-id="20f84-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="20f84-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20f84-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="20f84-114">S_OK</span></span>|<span data-ttu-id="20f84-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="20f84-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="20f84-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="20f84-116">E_POINTER</span></span>|<span data-ttu-id="20f84-117">Параметр `pbLoaded` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="20f84-117">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20f84-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="20f84-118">Remarks</span></span>  

 <span data-ttu-id="20f84-119">Этот метод обеспечивает обратную совместимость со следующими функциями и интерфейсами:</span><span class="sxs-lookup"><span data-stu-id="20f84-119">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="20f84-120">Интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) (в API размещения платформа .NET Framework версии 1).</span><span class="sxs-lookup"><span data-stu-id="20f84-120">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="20f84-121">Интерфейс [ICLRRuntimeHost](iclrruntimehost-interface.md) (в API размещения платформа .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="20f84-121">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="20f84-122">Устаревшие `CorBindTo*` функции (см. раздел [нерекомендуемые функции размещения CLR](deprecated-clr-hosting-functions.md) в API размещения платформа .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="20f84-122">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="20f84-123">Узел может вызвать одну из устаревших `CorBindTo*` функций, например функцию [CorBindToRuntime](corbindtoruntime-function.md) , для создания экземпляра конкретной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="20f84-123">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="20f84-124">Затем узел может вызвать метод [ICLRMetaHost::-Runtime](iclrmetahost-getruntime-method.md) и указать тот же номер версии для получения интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="20f84-124">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="20f84-125">Если узел затем вызывает `IsLoaded` метод для возвращенного интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` возвращает `true` ; в противном случае возвращается значение `false` .</span><span class="sxs-lookup"><span data-stu-id="20f84-125">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f84-126">Требования</span><span class="sxs-lookup"><span data-stu-id="20f84-126">Requirements</span></span>  

 <span data-ttu-id="20f84-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20f84-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f84-128">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="20f84-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20f84-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20f84-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20f84-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f84-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f84-131">См. также</span><span class="sxs-lookup"><span data-stu-id="20f84-131">See also</span></span>

- [<span data-ttu-id="20f84-132">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="20f84-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="20f84-133">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="20f84-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="20f84-134">Размещение</span><span class="sxs-lookup"><span data-stu-id="20f84-134">Hosting</span></span>](index.md)
