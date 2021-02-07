---
description: Дополнительные сведения о перечислении Цеесектионаттр
title: Перечисление CeeSectionAttr
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 13cfb635aaa606905745146d7c3caae3f9162e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678878"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="aae2e-103">Перечисление CeeSectionAttr</span><span class="sxs-lookup"><span data-stu-id="aae2e-103">CeeSectionAttr Enumeration</span></span>

<span data-ttu-id="aae2e-104">Предоставляет значения, указывающие атрибуты раздела для использования интерфейсом [ICeeGen](iceegen-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="aae2e-104">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aae2e-105">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="aae2e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="aae2e-106">Members</span></span>  
  
|<span data-ttu-id="aae2e-107">Член</span><span class="sxs-lookup"><span data-stu-id="aae2e-107">Member</span></span>|<span data-ttu-id="aae2e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="aae2e-108">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="aae2e-109">Раздел не имеет атрибутов.</span><span class="sxs-lookup"><span data-stu-id="aae2e-109">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="aae2e-110">Раздел содержит инициализированные данные, которые могут быть только считаны, но не обновлены.</span><span class="sxs-lookup"><span data-stu-id="aae2e-110">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="aae2e-111">Раздел содержит инициализированные данные, которые могут быть считаны или обновлены.</span><span class="sxs-lookup"><span data-stu-id="aae2e-111">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="aae2e-112">Раздел содержит исполняемый код, который может быть прочитан и выполнен.</span><span class="sxs-lookup"><span data-stu-id="aae2e-112">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aae2e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="aae2e-113">Requirements</span></span>  

 <span data-ttu-id="aae2e-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae2e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae2e-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="aae2e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aae2e-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aae2e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aae2e-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aae2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae2e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="aae2e-118">See also</span></span>

- [<span data-ttu-id="aae2e-119">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="aae2e-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
