---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: Сетдефаултстартупфлагс'
title: Метод ICLRRuntimeInfo::SetDefaultStartupFlags
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: eb839b2ff71836adc1b3858092f7caf5787275b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785046"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="f3cb4-103">Метод ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="f3cb4-103">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>

<span data-ttu-id="f3cb4-104">Задает флаги запуска и файл конфигурации узла, который будет использоваться для запуска среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-104">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="f3cb4-105">Этот метод заменяет использование `startupFlags` параметра в функциях [CorBindToRuntimeEx](corbindtoruntimeex-function.md) и [корбиндторунтимехост](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f3cb4-105">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3cb4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3cb4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3cb4-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f3cb4-107">Parameters</span></span>  

 `dwStartupFlags`  
 <span data-ttu-id="f3cb4-108">окне Заданные флаги запуска узла.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-108">[in] The host startup flags to set.</span></span> <span data-ttu-id="f3cb4-109">Используйте те же флаги, что и для функций [CorBindToRuntimeEx](corbindtoruntimeex-function.md) и [корбиндторунтимехост](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f3cb4-109">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="f3cb4-110">окне Путь к каталогу устанавливаемого файла конфигурации узла.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-110">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3cb4-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f3cb4-111">Return Value</span></span>  

 <span data-ttu-id="f3cb4-112">Этот метод возвращает следующее конкретное значение HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f3cb4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3cb4-113">HRESULT</span></span>|<span data-ttu-id="f3cb4-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="f3cb4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3cb4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3cb4-115">S_OK</span></span>|<span data-ttu-id="f3cb4-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3cb4-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3cb4-117">Remarks</span></span>  

 <span data-ttu-id="f3cb4-118">Многопоточный узел должен синхронизировать вызовы этого метода.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-118">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="f3cb4-119">В противном случае поток A может вызвать `SetStartupFlags` метод после того, как поток б завершит вызов `SetStartupFlags` и до того, как поток b запустит среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-119">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3cb4-120">Требования</span><span class="sxs-lookup"><span data-stu-id="f3cb4-120">Requirements</span></span>  

 <span data-ttu-id="f3cb4-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3cb4-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3cb4-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="f3cb4-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f3cb4-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3cb4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3cb4-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3cb4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cb4-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f3cb4-125">See also</span></span>

- [<span data-ttu-id="f3cb4-126">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="f3cb4-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f3cb4-127">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f3cb4-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f3cb4-128">Размещение</span><span class="sxs-lookup"><span data-stu-id="f3cb4-128">Hosting</span></span>](index.md)
