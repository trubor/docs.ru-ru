---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: Енумератеинсталледрунтимес'
title: Метод ICLRMetaHost::EnumerateInstalledRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: a1c2fe46a64339e013df0f65dc073d183036a0fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689200"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="f978e-103">Метод ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="f978e-103">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="f978e-104">Возвращает перечисление, которое содержит допустимый интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) для каждой версии среды CLR, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f978e-104">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f978e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f978e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f978e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f978e-106">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="f978e-107">заполняет Перечисление интерфейсов [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , соответствующих каждой версии среды CLR, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f978e-107">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f978e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f978e-108">Return Value</span></span>  

 <span data-ttu-id="f978e-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="f978e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f978e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f978e-110">HRESULT</span></span>|<span data-ttu-id="f978e-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="f978e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f978e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f978e-112">S_OK</span></span>|<span data-ttu-id="f978e-113">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f978e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f978e-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f978e-114">E_POINTER</span></span>|<span data-ttu-id="f978e-115">Параметр `ppEnumerator` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="f978e-115">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f978e-116">Требования</span><span class="sxs-lookup"><span data-stu-id="f978e-116">Requirements</span></span>  

 <span data-ttu-id="f978e-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f978e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f978e-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="f978e-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f978e-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f978e-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f978e-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f978e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f978e-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f978e-121">See also</span></span>

- [<span data-ttu-id="f978e-122">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="f978e-122">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="f978e-123">Размещение</span><span class="sxs-lookup"><span data-stu-id="f978e-123">Hosting</span></span>](index.md)
