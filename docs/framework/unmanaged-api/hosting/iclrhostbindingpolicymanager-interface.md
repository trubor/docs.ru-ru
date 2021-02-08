---
description: 'Дополнительные сведения о: интерфейс ICLRHostBindingPolicyManager'
title: Интерфейс ICLRHostBindingPolicyManager
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 07a18d622ff8d8483fe6dcb0242cb5f1ee284b14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789948"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="17643-103">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="17643-103">ICLRHostBindingPolicyManager Interface</span></span>

<span data-ttu-id="17643-104">Предоставляет основному приложению методы для вычисления текущей политики привязки и обмена изменениями политики для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="17643-104">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17643-105">Методы</span><span class="sxs-lookup"><span data-stu-id="17643-105">Methods</span></span>  
  
|<span data-ttu-id="17643-106">Метод</span><span class="sxs-lookup"><span data-stu-id="17643-106">Method</span></span>|<span data-ttu-id="17643-107">Описание</span><span class="sxs-lookup"><span data-stu-id="17643-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17643-108">Метод EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="17643-108">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="17643-109">Оценивает политику привязки от имени узла.</span><span class="sxs-lookup"><span data-stu-id="17643-109">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="17643-110">Метод ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="17643-110">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="17643-111">Изменяет политику привязки для указанной сборки и создает новую версию политики.</span><span class="sxs-lookup"><span data-stu-id="17643-111">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17643-112">Требования</span><span class="sxs-lookup"><span data-stu-id="17643-112">Requirements</span></span>  

 <span data-ttu-id="17643-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17643-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17643-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17643-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17643-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17643-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17643-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17643-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17643-117">См. также</span><span class="sxs-lookup"><span data-stu-id="17643-117">See also</span></span>

- [<span data-ttu-id="17643-118">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="17643-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="17643-119">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="17643-119">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="17643-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="17643-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
