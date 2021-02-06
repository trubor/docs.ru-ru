---
description: 'Дополнительные сведения о методе: ICorConfiguration:: Сетгчостконтрол'
title: Метод ICorConfiguration::SetGCHostControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 4d3d6e5e5275adf02f9d693234a5c8e77714fd03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636654"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="ed5d7-103">Метод ICorConfiguration::SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="ed5d7-103">ICorConfiguration::SetGCHostControl Method</span></span>

<span data-ttu-id="ed5d7-104">Задает интерфейс обратного вызова, используемый сборщиком мусора для запроса изменения ограничения виртуальной памяти на узле.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-104">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed5d7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed5d7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ed5d7-106">Parameters</span></span>  

 `pGCHostControl`  
 <span data-ttu-id="ed5d7-107">окне Указатель на объект [игчостконтрол](igchostcontrol-interface.md) , который позволяет сборщику мусора запрашивать у узла изменение ограничений виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="ed5d7-107">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed5d7-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ed5d7-108">Requirements</span></span>  

 <span data-ttu-id="ed5d7-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed5d7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed5d7-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed5d7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed5d7-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed5d7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed5d7-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed5d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5d7-113">См. также</span><span class="sxs-lookup"><span data-stu-id="ed5d7-113">See also</span></span>

- [<span data-ttu-id="ed5d7-114">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ed5d7-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
