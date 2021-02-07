---
description: 'Дополнительные сведения: перечисление METAHOST_CONFIG_FLAGS'
title: Перечисление METAHOST_CONFIG_FLAGS
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 56d70f50d3b4c48b7fbf1aa3be6fc11cda904638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679645"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="7637f-103">Перечисление METAHOST_CONFIG_FLAGS</span><span class="sxs-lookup"><span data-stu-id="7637f-103">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="7637f-104">Описывает возможные флаги, возвращаемые в `pdwConfigFlags` параметре метода [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , который указывает на присутствие и настройку `useLegacyV2RuntimeActivationPolicy` атрибута в [ \<startup> элементе](../../configure-apps/file-schema/startup/startup-element.md) файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7637f-104">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7637f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7637f-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7637f-106">Члены</span><span class="sxs-lookup"><span data-stu-id="7637f-106">Members</span></span>  
  
|<span data-ttu-id="7637f-107">Член</span><span class="sxs-lookup"><span data-stu-id="7637f-107">Member</span></span>|<span data-ttu-id="7637f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7637f-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="7637f-109">`useLegacyV2RuntimeActivationPolicy`Атрибут не присутствовал в [ \<startup> элементе](../../configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="7637f-109">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="7637f-110">`useLegacyV2RuntimeActivationPolicy`Атрибут присутствовал и имеет значение `true` .</span><span class="sxs-lookup"><span data-stu-id="7637f-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="7637f-111">`useLegacyV2RuntimeActivationPolicy`Атрибут присутствовал и имеет значение `false` .</span><span class="sxs-lookup"><span data-stu-id="7637f-111">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="7637f-112">Примените эту маску к значению, возвращенному в `pdwConfigFlags` , чтобы получить значения, относящиеся к `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="7637f-112">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7637f-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="7637f-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7637f-114">Требования</span><span class="sxs-lookup"><span data-stu-id="7637f-114">Requirements</span></span>  

 <span data-ttu-id="7637f-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7637f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7637f-116">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="7637f-116">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="7637f-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7637f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7637f-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7637f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7637f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="7637f-119">See also</span></span>

- [<span data-ttu-id="7637f-120">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="7637f-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="7637f-121">Метод GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="7637f-121">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="7637f-122">\<startup> Элемент</span><span class="sxs-lookup"><span data-stu-id="7637f-122">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
