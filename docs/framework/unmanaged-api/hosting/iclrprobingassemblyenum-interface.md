---
description: 'Дополнительные сведения о: интерфейс ICLRProbingAssemblyEnum'
title: Интерфейс ICLRProbingAssemblyEnum
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: 1fd11e237f02bab85ec2b41df49d7d8a2f27e1e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716516"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="6396f-103">Интерфейс ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="6396f-103">ICLRProbingAssemblyEnum Interface</span></span>

<span data-ttu-id="6396f-104">Предоставляет методы, позволяющие узлу получить идентификаторы проверки сборки с помощью сведений об удостоверении сборки, которые являются внутренними для среды CLR, без необходимости создавать или понимать это удостоверение.</span><span class="sxs-lookup"><span data-stu-id="6396f-104">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6396f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6396f-105">Methods</span></span>  
  
|<span data-ttu-id="6396f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6396f-106">Method</span></span>|<span data-ttu-id="6396f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6396f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6396f-108">Метод Get</span><span class="sxs-lookup"><span data-stu-id="6396f-108">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="6396f-109">Возвращает удостоверение сборки по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="6396f-109">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6396f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="6396f-110">Remarks</span></span>  

 <span data-ttu-id="6396f-111">Методы, такие как [ICLRAssemblyIdentityManager:: жетпробингассемблиесфромреференце](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) , возвращают `ICLRProbingAssemblyEnum` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="6396f-111">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6396f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="6396f-112">Requirements</span></span>  

 <span data-ttu-id="6396f-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6396f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6396f-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6396f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6396f-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6396f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6396f-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6396f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6396f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6396f-117">See also</span></span>

- [<span data-ttu-id="6396f-118">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="6396f-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6396f-119">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6396f-119">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6396f-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="6396f-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
