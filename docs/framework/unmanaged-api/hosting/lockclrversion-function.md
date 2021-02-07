---
description: Дополнительные сведения о функции Локкклрверсион
title: Функция LockClrVersion
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 268c08cdd24a826ba92cc8865dfd036f544febcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679929"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="65918-103">Функция LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="65918-103">LockClrVersion Function</span></span>

<span data-ttu-id="65918-104">Позволяет узлу определить, какая версия среды CLR будет использоваться в процессе перед явной инициализацией среды CLR.</span><span class="sxs-lookup"><span data-stu-id="65918-104">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="65918-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="65918-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65918-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65918-106">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65918-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="65918-107">Parameters</span></span>  

 `hostCallback`  
 <span data-ttu-id="65918-108">окне Функция, вызываемая средой CLR при инициализации.</span><span class="sxs-lookup"><span data-stu-id="65918-108">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="65918-109">окне Функция, вызываемая узлом для информирования среды CLR о начале инициализации.</span><span class="sxs-lookup"><span data-stu-id="65918-109">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="65918-110">окне Функция, вызываемая узлом для информирования среды CLR о завершении инициализации.</span><span class="sxs-lookup"><span data-stu-id="65918-110">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65918-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="65918-111">Return Value</span></span>  

 <span data-ttu-id="65918-112">Этот метод возвращает стандартные коды ошибок COM, как определено в файле WinError. h, а также следующие значения.</span><span class="sxs-lookup"><span data-stu-id="65918-112">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="65918-113">Код возврата</span><span class="sxs-lookup"><span data-stu-id="65918-113">Return code</span></span>|<span data-ttu-id="65918-114">Описание</span><span class="sxs-lookup"><span data-stu-id="65918-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="65918-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="65918-115">S_OK</span></span>|<span data-ttu-id="65918-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="65918-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="65918-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="65918-117">E_INVALIDARG</span></span>|<span data-ttu-id="65918-118">Один или несколько аргументов имеют значение null.</span><span class="sxs-lookup"><span data-stu-id="65918-118">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65918-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="65918-119">Remarks</span></span>  

 <span data-ttu-id="65918-120">Узел вызывает `LockClrVersion` перед инициализацией среды CLR.</span><span class="sxs-lookup"><span data-stu-id="65918-120">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="65918-121">`LockClrVersion` принимает три параметра, все из которых являются обратными вызовами типа [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="65918-121">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="65918-122">Этот тип определяется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="65918-122">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="65918-123">При инициализации среды выполнения выполняются следующие действия.</span><span class="sxs-lookup"><span data-stu-id="65918-123">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="65918-124">Узел вызывает [CorBindToRuntimeEx](corbindtoruntimeex-function.md) или одну из других функций инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="65918-124">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="65918-125">Кроме того, узел может инициализировать среду выполнения с помощью активации объекта COM.</span><span class="sxs-lookup"><span data-stu-id="65918-125">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="65918-126">Среда выполнения вызывает функцию, указанную `hostCallback` параметром.</span><span class="sxs-lookup"><span data-stu-id="65918-126">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="65918-127">Функция, указанная с помощью, `hostCallback` выполняет следующую последовательность вызовов:</span><span class="sxs-lookup"><span data-stu-id="65918-127">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="65918-128">Функция, заданная `pBeginHostSetup` параметром.</span><span class="sxs-lookup"><span data-stu-id="65918-128">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="65918-129">`CorBindToRuntimeEx` (или другую функцию инициализации среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="65918-129">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="65918-130">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="65918-130">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="65918-131">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="65918-131">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="65918-132">Функция, заданная `pEndHostSetup` параметром.</span><span class="sxs-lookup"><span data-stu-id="65918-132">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="65918-133">Все вызовы из `pBeginHostSetup` в `pEndHostSetup` должны выполняться в одном потоке или Fiber с одним и тем же логическим стеком.</span><span class="sxs-lookup"><span data-stu-id="65918-133">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="65918-134">Этот поток может отличаться от потока, в котором `hostCallback` вызывается.</span><span class="sxs-lookup"><span data-stu-id="65918-134">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65918-135">Требования</span><span class="sxs-lookup"><span data-stu-id="65918-135">Requirements</span></span>  

 <span data-ttu-id="65918-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65918-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65918-137">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65918-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65918-138">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65918-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65918-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65918-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65918-140">См. также</span><span class="sxs-lookup"><span data-stu-id="65918-140">See also</span></span>

- [<span data-ttu-id="65918-141">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="65918-141">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
