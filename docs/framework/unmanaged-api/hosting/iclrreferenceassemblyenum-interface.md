---
description: 'Дополнительные сведения о: интерфейс ICLRReferenceAssemblyEnum'
title: Интерфейс ICLRReferenceAssemblyEnum
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
ms.openlocfilehash: a7e522623c254940a6dbb8d22bf7f2fec76a1072
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689005"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="3e889-103">Интерфейс ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="3e889-103">ICLRReferenceAssemblyEnum Interface</span></span>

<span data-ttu-id="3e889-104">Предоставляет методы, позволяющие основному приложению манипулировать набором сборок, на которые ссылается файл или поток, с помощью данных идентификации сборок, которые являются внутренними для среды CLR, не требуя создания или понимания этих удостоверений.</span><span class="sxs-lookup"><span data-stu-id="3e889-104">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e889-105">Методы</span><span class="sxs-lookup"><span data-stu-id="3e889-105">Methods</span></span>  
  
|<span data-ttu-id="3e889-106">Метод</span><span class="sxs-lookup"><span data-stu-id="3e889-106">Method</span></span>|<span data-ttu-id="3e889-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3e889-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e889-108">Метод Get</span><span class="sxs-lookup"><span data-stu-id="3e889-108">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="3e889-109">Возвращает удостоверение сборки по заданному индексу.</span><span class="sxs-lookup"><span data-stu-id="3e889-109">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e889-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3e889-110">Requirements</span></span>  

 <span data-ttu-id="3e889-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e889-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e889-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3e889-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e889-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e889-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e889-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e889-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e889-115">См. также</span><span class="sxs-lookup"><span data-stu-id="3e889-115">See also</span></span>

- [<span data-ttu-id="3e889-116">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="3e889-116">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3e889-117">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="3e889-117">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3e889-118">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="3e889-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
