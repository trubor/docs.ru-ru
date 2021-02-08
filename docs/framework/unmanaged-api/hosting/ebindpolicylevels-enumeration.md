---
description: Дополнительные сведения о перечислении EBindPolicyLevels
title: Перечисление EBindPolicyLevels
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 00e10cff79cdd782e8d9ab8e9b7e1e3f388fb1ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785618"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="0af1c-103">Перечисление EBindPolicyLevels</span><span class="sxs-lookup"><span data-stu-id="0af1c-103">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="0af1c-104">Предоставляет флаги для указания уровня применения или изменения политики сборки.</span><span class="sxs-lookup"><span data-stu-id="0af1c-104">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af1c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0af1c-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="0af1c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="0af1c-106">Members</span></span>  
  
|<span data-ttu-id="0af1c-107">Член</span><span class="sxs-lookup"><span data-stu-id="0af1c-107">Member</span></span>|<span data-ttu-id="0af1c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0af1c-108">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="0af1c-109">Указывает, что политику следует применять на уровне администратора.</span><span class="sxs-lookup"><span data-stu-id="0af1c-109">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="0af1c-110">Указывает, что политику следует применять на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="0af1c-110">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="0af1c-111">Указывает, что политику следует применять на уровне узла.</span><span class="sxs-lookup"><span data-stu-id="0af1c-111">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="0af1c-112">Указывает отсутствие флагов уровня политики.</span><span class="sxs-lookup"><span data-stu-id="0af1c-112">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="0af1c-113">Указывает, что политика должна применяться на уровне издателя.</span><span class="sxs-lookup"><span data-stu-id="0af1c-113">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="0af1c-114">Указывает, что политика должна быть применима на уровнях переменных.</span><span class="sxs-lookup"><span data-stu-id="0af1c-114">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="0af1c-115">Указывает, что политика должна поддерживать переносимость между реализациями сборки платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0af1c-115">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="0af1c-116">См [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) . элемент файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0af1c-116">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="0af1c-117">Указывает, что политика должна быть унифицированной для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0af1c-117">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af1c-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="0af1c-118">Remarks</span></span>  

 <span data-ttu-id="0af1c-119">Это перечисление передается методам интерфейса [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) для указания изменений в политике приложения.</span><span class="sxs-lookup"><span data-stu-id="0af1c-119">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af1c-120">Требования</span><span class="sxs-lookup"><span data-stu-id="0af1c-120">Requirements</span></span>  

 <span data-ttu-id="0af1c-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0af1c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0af1c-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0af1c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0af1c-123">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0af1c-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0af1c-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0af1c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af1c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="0af1c-125">See also</span></span>

- [<span data-ttu-id="0af1c-126">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="0af1c-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0af1c-127">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="0af1c-127">Hosting Enumerations</span></span>](hosting-enumerations.md)
