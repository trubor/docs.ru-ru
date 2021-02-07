---
description: Дополнительные сведения о перечислении CLRDataEnumMemoryFlags
title: Перечисление CLRDataEnumMemoryFlags
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
ms.openlocfilehash: 3522649c59177de8295416ce260c374df605efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662251"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="dcbe8-103">Перечисление CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="dcbe8-103">CLRDataEnumMemoryFlags Enumeration</span></span>

<span data-ttu-id="dcbe8-104">Указывает, к каким областям памяти должен быть вызван вызов метода [иклрдатаенуммеморирегионс:: енуммеморирегионс](iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dcbe8-104">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbe8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcbe8-105">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dcbe8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="dcbe8-106">Members</span></span>  
  
|<span data-ttu-id="dcbe8-107">Член</span><span class="sxs-lookup"><span data-stu-id="dcbe8-107">Member</span></span>|<span data-ttu-id="dcbe8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="dcbe8-108">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="dcbe8-109">Мини-дамп, то есть дамп разреженной памяти.</span><span class="sxs-lookup"><span data-stu-id="dcbe8-109">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="dcbe8-110">Полный дамп кучи.</span><span class="sxs-lookup"><span data-stu-id="dcbe8-110">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcbe8-111">Требования</span><span class="sxs-lookup"><span data-stu-id="dcbe8-111">Requirements</span></span>  

 <span data-ttu-id="dcbe8-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbe8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbe8-113">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="dcbe8-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dcbe8-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcbe8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcbe8-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbe8-116">См. также</span><span class="sxs-lookup"><span data-stu-id="dcbe8-116">See also</span></span>

- [<span data-ttu-id="dcbe8-117">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="dcbe8-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
