---
description: 'Дополнительные сведения о методе ICLRDebugManager:: "DACL"'
title: Метод ICLRDebugManager::GetDacl
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.GetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::GetDacl
helpviewer_keywords:
- GetDacl method [.NET Framework hosting]
- ICLRDebugManager::GetDacl method [.NET Framework hosting]
ms.assetid: 7115e920-aaff-440a-824e-39497139c6f6
topic_type:
- apiref
ms.openlocfilehash: 8a1b747851d0c5104dbe18e5a66742d57b09aa22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649485"
---
# <a name="iclrdebugmanagergetdacl-method"></a><span data-ttu-id="f5f60-103">Метод ICLRDebugManager::GetDacl</span><span class="sxs-lookup"><span data-stu-id="f5f60-103">ICLRDebugManager::GetDacl Method</span></span>

<span data-ttu-id="f5f60-104">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="f5f60-104">This method is not implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f60-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5f60-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDacl (  
    [out] PACL* ppacl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f60-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f5f60-106">Parameters</span></span>  

 `ppacl`  
 <span data-ttu-id="f5f60-107">заполняет Указатель интерфейса на список управления доступом (ACL).</span><span class="sxs-lookup"><span data-stu-id="f5f60-107">[out] An interface pointer to the Access Control List (ACL).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5f60-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f5f60-108">Return Value</span></span>  
  
|<span data-ttu-id="f5f60-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5f60-109">HRESULT</span></span>|<span data-ttu-id="f5f60-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f5f60-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5f60-111">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f5f60-111">E_NOTIMPL</span></span>|<span data-ttu-id="f5f60-112">Метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="f5f60-112">The method is not implemented.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5f60-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f5f60-113">Requirements</span></span>  

 <span data-ttu-id="f5f60-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f60-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f60-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5f60-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5f60-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5f60-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5f60-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f60-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f60-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f5f60-118">See also</span></span>

- [<span data-ttu-id="f5f60-119">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="f5f60-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f5f60-120">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="f5f60-120">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="f5f60-121">Метод SetDacl</span><span class="sxs-lookup"><span data-stu-id="f5f60-121">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)
- [<span data-ttu-id="f5f60-122">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="f5f60-122">IHostControl Interface</span></span>](ihostcontrol-interface.md)
