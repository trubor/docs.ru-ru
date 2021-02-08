---
description: 'Дополнительные сведения: перечисление CLSID_RESOLUTION_FLAGS'
title: Перечисление CLSID_RESOLUTION_FLAGS
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 54d334147e13217f8ce20dae1b139cdc6d11a3b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799880"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="40dce-103">Перечисление CLSID_RESOLUTION_FLAGS</span><span class="sxs-lookup"><span data-stu-id="40dce-103">CLSID_RESOLUTION_FLAGS Enumeration</span></span>

<span data-ttu-id="40dce-104">Содержит значения, которые указывают, как общеязыковая среда выполнения (CLR) должна разрешать `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="40dce-104">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40dce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40dce-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="40dce-106">Члены</span><span class="sxs-lookup"><span data-stu-id="40dce-106">Members</span></span>  
  
|<span data-ttu-id="40dce-107">Член</span><span class="sxs-lookup"><span data-stu-id="40dce-107">Member</span></span>|<span data-ttu-id="40dce-108">Описание</span><span class="sxs-lookup"><span data-stu-id="40dce-108">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="40dce-109">Указывает поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="40dce-109">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="40dce-110">Указывает, что среда выполнения выполняет поиск в реестре и применяет политику оболочки совместимости.</span><span class="sxs-lookup"><span data-stu-id="40dce-110">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40dce-111">Требования</span><span class="sxs-lookup"><span data-stu-id="40dce-111">Requirements</span></span>  

 <span data-ttu-id="40dce-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40dce-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40dce-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40dce-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40dce-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40dce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dce-115">См. также</span><span class="sxs-lookup"><span data-stu-id="40dce-115">See also</span></span>

- [<span data-ttu-id="40dce-116">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="40dce-116">Hosting Enumerations</span></span>](hosting-enumerations.md)
