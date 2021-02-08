---
description: 'Дополнительные сведения: перечисление HOST_TYPE'
title: Перечисление HOST_TYPE
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 6a0baf3050f99885953ddec06342cbe19accfef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785241"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="e663c-103">Перечисление HOST_TYPE</span><span class="sxs-lookup"><span data-stu-id="e663c-103">HOST_TYPE Enumeration</span></span>

<span data-ttu-id="e663c-104">Содержит значения, указывающие тип узла, запускающего приложение.</span><span class="sxs-lookup"><span data-stu-id="e663c-104">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e663c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e663c-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e663c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="e663c-106">Members</span></span>  
  
|<span data-ttu-id="e663c-107">Член</span><span class="sxs-lookup"><span data-stu-id="e663c-107">Member</span></span>|<span data-ttu-id="e663c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e663c-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="e663c-109">Запустите приложение из AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="e663c-109">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="e663c-110">Используйте это значение для частично доверенных приложений.</span><span class="sxs-lookup"><span data-stu-id="e663c-110">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="e663c-111">Запустите приложение напрямую.</span><span class="sxs-lookup"><span data-stu-id="e663c-111">Launch the application directly.</span></span> <span data-ttu-id="e663c-112">То есть запустите приложение из собственного EXE-файла.</span><span class="sxs-lookup"><span data-stu-id="e663c-112">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="e663c-113">Используйте это значение для полностью доверенных приложений.</span><span class="sxs-lookup"><span data-stu-id="e663c-113">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="e663c-114">То же, что и HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="e663c-114">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e663c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e663c-115">Requirements</span></span>  

 <span data-ttu-id="e663c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e663c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e663c-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e663c-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e663c-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e663c-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e663c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e663c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e663c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e663c-120">See also</span></span>

- [<span data-ttu-id="e663c-121">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="e663c-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
