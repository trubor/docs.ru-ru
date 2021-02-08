---
description: 'Дополнительные сведения о методе: ICLRDebugManager:: SetSymbolReadingPolicy'
title: Метод ICLRDebugManager::SetSymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
ms.openlocfilehash: 2c0862f3c572808ffbf418b275e1ad1c62c2ac89
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781952"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="3a9fe-103">Метод ICLRDebugManager::SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="3a9fe-103">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>

<span data-ttu-id="3a9fe-104">Задает политику чтения файлов базы данных программы (PDB).</span><span class="sxs-lookup"><span data-stu-id="3a9fe-104">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="3a9fe-105">Политика определяет, включаются ли в стеки вызовов сведения о номерах строк и файлах.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-105">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9fe-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a9fe-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a9fe-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="3a9fe-107">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="3a9fe-108">окне Член перечисления [есимболреадингполици](esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3a9fe-108">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a9fe-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3a9fe-109">Return Value</span></span>  
  
|<span data-ttu-id="3a9fe-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a9fe-110">HRESULT</span></span>|<span data-ttu-id="3a9fe-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a9fe-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a9fe-112">S_OK</span></span>|<span data-ttu-id="3a9fe-113">`SetSymbolReadingPolicy` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-113">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="3a9fe-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a9fe-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a9fe-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a9fe-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a9fe-116">E_FAIL</span></span>|<span data-ttu-id="3a9fe-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a9fe-118">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-118">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a9fe-119">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a9fe-120">Требования</span><span class="sxs-lookup"><span data-stu-id="3a9fe-120">Requirements</span></span>  

 <span data-ttu-id="3a9fe-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a9fe-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a9fe-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3a9fe-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a9fe-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a9fe-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a9fe-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a9fe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9fe-125">См. также</span><span class="sxs-lookup"><span data-stu-id="3a9fe-125">See also</span></span>

- [<span data-ttu-id="3a9fe-126">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="3a9fe-126">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
