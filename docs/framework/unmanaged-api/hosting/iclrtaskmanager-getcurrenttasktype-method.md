---
description: 'Дополнительные сведения о методе: ICLRTaskManager:: GetCurrentTaskType'
title: Метод ICLRTaskManager::GetCurrentTaskType
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 984cc490123d6146737d3f018fdf712c7c528635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799490"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="99c8d-103">Метод ICLRTaskManager::GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="99c8d-103">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="99c8d-104">Возвращает тип выполняемой в данный момент задачи.</span><span class="sxs-lookup"><span data-stu-id="99c8d-104">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c8d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99c8d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99c8d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="99c8d-106">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="99c8d-107">заполняет Указатель на значение перечисления [етасктипе](etasktype-enumeration.md) , указывающее тип выполняемой в данный момент задачи.</span><span class="sxs-lookup"><span data-stu-id="99c8d-107">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c8d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="99c8d-108">Requirements</span></span>  

 <span data-ttu-id="99c8d-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99c8d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c8d-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99c8d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99c8d-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99c8d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c8d-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c8d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c8d-113">См. также</span><span class="sxs-lookup"><span data-stu-id="99c8d-113">See also</span></span>

- [<span data-ttu-id="99c8d-114">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="99c8d-114">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
