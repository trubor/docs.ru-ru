---
description: 'Дополнительные сведения: перечисление COR_PUB_ENUMPROCESS'
title: Перечисление COR_PUB_ENUMPROCESS
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: 66bbd08aabb9d2c93e385ed098bae54754a85b85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801791"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="d1edd-103">Перечисление COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="d1edd-103">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="d1edd-104">Идентифицирует тип процесса для перечисления.</span><span class="sxs-lookup"><span data-stu-id="d1edd-104">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1edd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d1edd-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="d1edd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="d1edd-106">Members</span></span>  
  
|<span data-ttu-id="d1edd-107">Имя участника</span><span class="sxs-lookup"><span data-stu-id="d1edd-107">Member name</span></span>|<span data-ttu-id="d1edd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d1edd-108">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="d1edd-109">Управляемый процесс.</span><span class="sxs-lookup"><span data-stu-id="d1edd-109">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1edd-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d1edd-110">Remarks</span></span>  

 <span data-ttu-id="d1edd-111">Текущая версия неуправляемого API отладки перечисляет только управляемые процессы.</span><span class="sxs-lookup"><span data-stu-id="d1edd-111">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1edd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d1edd-112">Requirements</span></span>  

 <span data-ttu-id="d1edd-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1edd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1edd-114">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="d1edd-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d1edd-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1edd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1edd-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1edd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1edd-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d1edd-117">See also</span></span>

- [<span data-ttu-id="d1edd-118">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="d1edd-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
