---
description: Дополнительные сведения о перечислении Корнотификатионфортокенмовемент
title: Перечисление CorNotificationForTokenMovement
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 1975598b756499c9c0b017bf7eba9a134af5185f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784318"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="bdd82-103">Перечисление CorNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="bdd82-103">CorNotificationForTokenMovement Enumeration</span></span>

<span data-ttu-id="bdd82-104">Указывает уведомления, которые будут отправляться клиенту API метаданных при выполнении сопоставления маркеров.</span><span class="sxs-lookup"><span data-stu-id="bdd82-104">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd82-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdd82-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="bdd82-106">Члены</span><span class="sxs-lookup"><span data-stu-id="bdd82-106">Members</span></span>  
  
|<span data-ttu-id="bdd82-107">Член</span><span class="sxs-lookup"><span data-stu-id="bdd82-107">Member</span></span>|<span data-ttu-id="bdd82-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bdd82-108">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="bdd82-109">Уведомлять при `mdTypeRef` `mdMethodDef` `mdMemberRef` `mdFieldDef` перемещении токенов,, или.</span><span class="sxs-lookup"><span data-stu-id="bdd82-109">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="bdd82-110">Уведомлять при перемещении токена.</span><span class="sxs-lookup"><span data-stu-id="bdd82-110">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="bdd82-111">Не уведомлять при перемещении токенов.</span><span class="sxs-lookup"><span data-stu-id="bdd82-111">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="bdd82-112">Уведомлять при `mdMethodDef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-112">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="bdd82-113">Уведомлять при `mdMemberRef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-113">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="bdd82-114">Уведомлять при `mdFieldDef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-114">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="bdd82-115">Уведомлять при `mdTypeRef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-115">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="bdd82-116">Уведомлять при `mdTypeDef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-116">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="bdd82-117">Уведомлять при `mdParamDef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-117">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="bdd82-118">Уведомлять при `mdInterfaceImpl` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-118">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="bdd82-119">Уведомлять при `mdProperty` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-119">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="bdd82-120">Уведомлять при `mdEvent` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-120">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="bdd82-121">Уведомлять при `mdSignature` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-121">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="bdd82-122">Уведомлять при `mdTypeSpec` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-122">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="bdd82-123">Уведомлять при `mdCustomAttribute` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-123">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="bdd82-124">Уведомлять при `mdSecurityValue` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-124">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="bdd82-125">Уведомлять при `mdPermission` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-125">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="bdd82-126">Уведомлять при `mdModuleRef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-126">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="bdd82-127">Уведомлять при `mdNameSpace` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-127">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="bdd82-128">Уведомлять при `mdAssemblyRef` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-128">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="bdd82-129">Уведомлять при `mdFile` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-129">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="bdd82-130">Уведомлять при `mdExportedType` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-130">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="bdd82-131">Уведомлять при `mdManifestResource` перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="bdd82-131">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdd82-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdd82-132">Remarks</span></span>  

 <span data-ttu-id="bdd82-133">Маркер может быть повторно сопоставлен (т. е. перемещен) во время слияния метаданных.</span><span class="sxs-lookup"><span data-stu-id="bdd82-133">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd82-134">Требования</span><span class="sxs-lookup"><span data-stu-id="bdd82-134">Requirements</span></span>  

 <span data-ttu-id="bdd82-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd82-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd82-136">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="bdd82-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bdd82-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd82-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd82-138">См. также</span><span class="sxs-lookup"><span data-stu-id="bdd82-138">See also</span></span>

- [<span data-ttu-id="bdd82-139">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="bdd82-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
