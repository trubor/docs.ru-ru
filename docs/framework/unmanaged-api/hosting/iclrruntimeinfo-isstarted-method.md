---
description: 'Дополнительные сведения о методе ICLRRuntimeInfo:: OnStarted'
title: Метод ICLRRuntimeInfo::IsStarted
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 22059ecbded9eae9659cdaae8b9b92f2d7df0650
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753852"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="b25bd-103">Метод ICLRRuntimeInfo::IsStarted</span><span class="sxs-lookup"><span data-stu-id="b25bd-103">ICLRRuntimeInfo::IsStarted Method</span></span>

<span data-ttu-id="b25bd-104">Указывает, была ли запущена среда выполнения (т. е. был ли вызван [метод ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) и он был успешно выполнен).</span><span class="sxs-lookup"><span data-stu-id="b25bd-104">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25bd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b25bd-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b25bd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b25bd-106">Parameters</span></span>  

 `pbStarted`  
 <span data-ttu-id="b25bd-107">[out] `true` значение, если среда выполнения запущена; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="b25bd-107">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="b25bd-108">заполняет Возвращает флаги, которые использовались для запуска среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b25bd-108">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b25bd-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b25bd-109">Return Value</span></span>  

 <span data-ttu-id="b25bd-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="b25bd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b25bd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b25bd-111">HRESULT</span></span>|<span data-ttu-id="b25bd-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="b25bd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b25bd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b25bd-113">S_OK</span></span>|<span data-ttu-id="b25bd-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="b25bd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b25bd-115">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b25bd-115">E_NOTIMPL</span></span>|<span data-ttu-id="b25bd-116">Версия среды CLR предшествует версии CLR в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b25bd-116">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b25bd-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b25bd-117">Remarks</span></span>  

 <span data-ttu-id="b25bd-118">Этот метод не работает с версиями CLR, предшествующими версии CLR в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b25bd-118">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25bd-119">Требования</span><span class="sxs-lookup"><span data-stu-id="b25bd-119">Requirements</span></span>  

 <span data-ttu-id="b25bd-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b25bd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25bd-121">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="b25bd-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b25bd-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b25bd-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b25bd-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25bd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25bd-124">См. также</span><span class="sxs-lookup"><span data-stu-id="b25bd-124">See also</span></span>

- [<span data-ttu-id="b25bd-125">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="b25bd-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b25bd-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="b25bd-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b25bd-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="b25bd-127">Hosting</span></span>](index.md)
