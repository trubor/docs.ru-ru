---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: Енумерателоадедрунтимес'
title: Метод ICLRMetaHost::EnumerateLoadedRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 508c4daca7e34366e0da35591f4e7a780301e823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789870"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="97dfb-103">Метод ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="97dfb-103">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>

<span data-ttu-id="97dfb-104">Возвращает перечисление, содержащее допустимый указатель интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) для каждой версии среды CLR, загруженной в заданный процесс.</span><span class="sxs-lookup"><span data-stu-id="97dfb-104">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="97dfb-105">Этот метод заменяет функцию [GetVersionFromProcess](getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="97dfb-105">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97dfb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="97dfb-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97dfb-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="97dfb-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="97dfb-108">окне Описатель процесса для проверки загруженных сред выполнения.</span><span class="sxs-lookup"><span data-stu-id="97dfb-108">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="97dfb-109">заполняет <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> Перечисление интерфейсов [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , соответствующих каждой среде CLR, загруженной процессом.</span><span class="sxs-lookup"><span data-stu-id="97dfb-109">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97dfb-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="97dfb-110">Return Value</span></span>  

 <span data-ttu-id="97dfb-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="97dfb-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="97dfb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97dfb-112">HRESULT</span></span>|<span data-ttu-id="97dfb-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="97dfb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97dfb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="97dfb-114">S_OK</span></span>|<span data-ttu-id="97dfb-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="97dfb-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="97dfb-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="97dfb-116">E_POINTER</span></span>|<span data-ttu-id="97dfb-117">Параметр `ppEnumerator` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="97dfb-117">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97dfb-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="97dfb-118">Remarks</span></span>  

 <span data-ttu-id="97dfb-119">Этот метод перечисляет все загруженные среды выполнения, даже если они были загружены с устаревшими функциями, такими как [CorBindToRuntime](corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="97dfb-119">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97dfb-120">Требования</span><span class="sxs-lookup"><span data-stu-id="97dfb-120">Requirements</span></span>  

 <span data-ttu-id="97dfb-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97dfb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97dfb-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="97dfb-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="97dfb-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97dfb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97dfb-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97dfb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dfb-125">См. также</span><span class="sxs-lookup"><span data-stu-id="97dfb-125">See also</span></span>

- [<span data-ttu-id="97dfb-126">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="97dfb-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="97dfb-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="97dfb-127">Hosting</span></span>](index.md)
