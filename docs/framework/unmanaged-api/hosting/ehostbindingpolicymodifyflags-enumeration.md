---
description: Дополнительные сведения о перечислении Ехостбиндингполицимодифифлагс
title: Перечисление EHostBindingPolicyModifyFlags
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: be8a15cad49097d1ea2e206e01da2d5d5dcb165a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785488"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="687ac-103">Перечисление EHostBindingPolicyModifyFlags</span><span class="sxs-lookup"><span data-stu-id="687ac-103">EHostBindingPolicyModifyFlags Enumeration</span></span>

<span data-ttu-id="687ac-104">Позволяет узлу указать тип перенаправления, которое должна выполнять среда CLR при применении изменений политики из исходной сборки к целевой сборке.</span><span class="sxs-lookup"><span data-stu-id="687ac-104">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="687ac-105">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="687ac-106">Члены</span><span class="sxs-lookup"><span data-stu-id="687ac-106">Members</span></span>  
  
|<span data-ttu-id="687ac-107">Член</span><span class="sxs-lookup"><span data-stu-id="687ac-107">Member</span></span>|<span data-ttu-id="687ac-108">Описание</span><span class="sxs-lookup"><span data-stu-id="687ac-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="687ac-109">Указывает, что среда CLR будет связывать значения политики исходной сборки с целевыми сборками.</span><span class="sxs-lookup"><span data-stu-id="687ac-109">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="687ac-110">Указывает, что среда CLR будет выполнять действие по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="687ac-110">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="687ac-111">Указывает, что среда CLR будет задавать максимальные значения политики для целевой сборки.</span><span class="sxs-lookup"><span data-stu-id="687ac-111">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="687ac-112">Указывает, что среда CLR заменит значения политики целевой сборки значениями из исходной сборки.</span><span class="sxs-lookup"><span data-stu-id="687ac-112">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="687ac-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="687ac-113">Remarks</span></span>  

 <span data-ttu-id="687ac-114">Метод [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) принимает параметр типа `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="687ac-114">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="687ac-115">Требования</span><span class="sxs-lookup"><span data-stu-id="687ac-115">Requirements</span></span>  

 <span data-ttu-id="687ac-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="687ac-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="687ac-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="687ac-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="687ac-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="687ac-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="687ac-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="687ac-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687ac-120">См. также</span><span class="sxs-lookup"><span data-stu-id="687ac-120">See also</span></span>

- [<span data-ttu-id="687ac-121">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="687ac-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="687ac-122">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="687ac-122">Hosting Enumerations</span></span>](hosting-enumerations.md)
