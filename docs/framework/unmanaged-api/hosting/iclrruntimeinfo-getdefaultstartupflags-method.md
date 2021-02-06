---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: Жетдефаултстартупфлагс'
title: Метод ICLRRuntimeInfo::GetDefaultStartupFlags
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: c6afb19319fd24d499c2c216f2ce0adc2e7a886c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637183"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="e1430-103">Метод ICLRRuntimeInfo::GetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="e1430-103">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>

<span data-ttu-id="e1430-104">Возвращает флаги запуска и файл конфигурации узла, которые будут использоваться для запуска среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e1430-104">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1430-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1430-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1430-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e1430-106">Parameters</span></span>  

 `pdwStartupFlags`  
 <span data-ttu-id="e1430-107">заполняет Указатель на установленные в данный момент флаги запуска узла.</span><span class="sxs-lookup"><span data-stu-id="e1430-107">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="e1430-108">заполняет Указатель на путь к каталогу текущего файла конфигурации узла.</span><span class="sxs-lookup"><span data-stu-id="e1430-108">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="e1430-109">[вход, выход] Во входных данных — размер `pwzHostConfigFile` , чтобы избежать переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="e1430-109">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="e1430-110">Если `pwzHostConfigFile` имеет значение null, метод возвращает требуемый размер `pwzHostConfigFile` для предварительного выделения.</span><span class="sxs-lookup"><span data-stu-id="e1430-110">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1430-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e1430-111">Return Value</span></span>  

 <span data-ttu-id="e1430-112">Этот метод возвращает следующее конкретное значение HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="e1430-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1430-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1430-113">HRESULT</span></span>|<span data-ttu-id="e1430-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="e1430-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1430-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1430-115">S_OK</span></span>|<span data-ttu-id="e1430-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="e1430-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1430-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="e1430-117">Remarks</span></span>  

 <span data-ttu-id="e1430-118">Этот метод возвращает значения флагов по умолчанию ( `STARTUP_CONCURRENT_GC` и `NULL` ) или значения, предоставленные предыдущим вызовом [метода ICLRRuntimeInfo:: сетдефаултстартупфлагс](iclrruntimeinfo-setdefaultstartupflags-method.md), или значения, заданные любыми `CorBind*` методами, если они привязаны к этой среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="e1430-118">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1430-119">Требования</span><span class="sxs-lookup"><span data-stu-id="e1430-119">Requirements</span></span>  

 <span data-ttu-id="e1430-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1430-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1430-121">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="e1430-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1430-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1430-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1430-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1430-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1430-124">См. также</span><span class="sxs-lookup"><span data-stu-id="e1430-124">See also</span></span>

- [<span data-ttu-id="e1430-125">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="e1430-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e1430-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="e1430-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e1430-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="e1430-127">Hosting</span></span>](index.md)
