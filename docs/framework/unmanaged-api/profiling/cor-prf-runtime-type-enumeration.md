---
description: 'Дополнительные сведения: перечисление COR_PRF_RUNTIME_TYPE'
title: Перечисление COR_PRF_RUNTIME_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: 8f4b4a0c51c43b1db97b511387eaee1aee79f523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789051"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="d85dc-103">Перечисление COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="d85dc-103">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="d85dc-104">Содержит значения, указывающие версию среды CLR: Desktop или CoreCLR, которая используется в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d85dc-104">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d85dc-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d85dc-106">Члены</span><span class="sxs-lookup"><span data-stu-id="d85dc-106">Members</span></span>  
  
|<span data-ttu-id="d85dc-107">Член</span><span class="sxs-lookup"><span data-stu-id="d85dc-107">Member</span></span>|<span data-ttu-id="d85dc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d85dc-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="d85dc-109">Версия среды CLR для настольных систем.</span><span class="sxs-lookup"><span data-stu-id="d85dc-109">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="d85dc-110">Основная версия среды CLR, используемая в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d85dc-110">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d85dc-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d85dc-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85dc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d85dc-112">Requirements</span></span>  

 <span data-ttu-id="d85dc-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d85dc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d85dc-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d85dc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d85dc-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d85dc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d85dc-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d85dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85dc-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d85dc-117">See also</span></span>

- [<span data-ttu-id="d85dc-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="d85dc-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
