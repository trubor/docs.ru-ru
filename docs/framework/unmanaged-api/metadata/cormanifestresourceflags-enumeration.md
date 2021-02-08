---
description: Дополнительные сведения о перечислении Корманифестресаурцефлагс
title: Перечисление CorManifestResourceFlags
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: a863e1248bf5274e12fc16d2edea6b28dd493963
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784409"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="28ad3-103">Перечисление CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="28ad3-103">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="28ad3-104">Указывает видимость ресурсов, закодированных в манифесте сборки.</span><span class="sxs-lookup"><span data-stu-id="28ad3-104">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ad3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28ad3-105">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="28ad3-106">Члены</span><span class="sxs-lookup"><span data-stu-id="28ad3-106">Members</span></span>  
  
|<span data-ttu-id="28ad3-107">Член</span><span class="sxs-lookup"><span data-stu-id="28ad3-107">Member</span></span>|<span data-ttu-id="28ad3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="28ad3-108">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="28ad3-109">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="28ad3-109">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="28ad3-110">Ресурсы являются общедоступными.</span><span class="sxs-lookup"><span data-stu-id="28ad3-110">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="28ad3-111">Ресурсы являются частными.</span><span class="sxs-lookup"><span data-stu-id="28ad3-111">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28ad3-112">Требования</span><span class="sxs-lookup"><span data-stu-id="28ad3-112">Requirements</span></span>  

 <span data-ttu-id="28ad3-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28ad3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ad3-114">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="28ad3-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="28ad3-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ad3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ad3-116">См. также</span><span class="sxs-lookup"><span data-stu-id="28ad3-116">See also</span></span>

- [<span data-ttu-id="28ad3-117">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="28ad3-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
