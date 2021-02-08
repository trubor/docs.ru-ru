---
description: Дополнительные сведения о перечислении EInitializeNewDomainFlags
title: Перечисление EInitializeNewDomainFlags
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: b856d061e86c0c79b35f842975378307b79a37e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785469"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="b248b-103">Перечисление EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="b248b-103">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="b248b-104">Позволяет узлу предоставлять среде выполнения сведения об инициализации домена приложения.</span><span class="sxs-lookup"><span data-stu-id="b248b-104">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b248b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b248b-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b248b-106">Члены</span><span class="sxs-lookup"><span data-stu-id="b248b-106">Members</span></span>  
  
|<span data-ttu-id="b248b-107">Член</span><span class="sxs-lookup"><span data-stu-id="b248b-107">Member</span></span>|<span data-ttu-id="b248b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b248b-108">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="b248b-109">Флаги отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="b248b-109">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="b248b-110">Информирует среду CLR о том, что узел не будет вносить изменения в состояние безопасности домена приложения в <xref:System.AppDomainManager.InitializeNewDomain%2A> методе.</span><span class="sxs-lookup"><span data-stu-id="b248b-110">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b248b-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b248b-111">Remarks</span></span>  

 <span data-ttu-id="b248b-112">Метод [иклрдомаинманажер:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) принимает параметр типа `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="b248b-112">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b248b-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b248b-113">Requirements</span></span>  

 <span data-ttu-id="b248b-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b248b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b248b-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b248b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b248b-116">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b248b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b248b-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b248b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b248b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b248b-118">See also</span></span>

- [<span data-ttu-id="b248b-119">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="b248b-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="b248b-120">Метод SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="b248b-120">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
