---
description: Дополнительные сведения о перечислении Коревентаттр
title: Перечисление CorEventAttr
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: 70f05eacf2cc7c7975b9b52d402cceb60bbea426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784513"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="198fd-103">Перечисление CorEventAttr</span><span class="sxs-lookup"><span data-stu-id="198fd-103">CorEventAttr Enumeration</span></span>

<span data-ttu-id="198fd-104">Содержит значения, описывающие метаданные события.</span><span class="sxs-lookup"><span data-stu-id="198fd-104">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="198fd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="198fd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="198fd-106">Members</span></span>  
  
|<span data-ttu-id="198fd-107">Член</span><span class="sxs-lookup"><span data-stu-id="198fd-107">Member</span></span>|<span data-ttu-id="198fd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="198fd-108">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="198fd-109">Указывает, что событие является специальным, и что его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="198fd-109">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="198fd-110">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="198fd-110">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="198fd-111">Указывает, что среда CLR должна проверять кодировку имени события.</span><span class="sxs-lookup"><span data-stu-id="198fd-111">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="198fd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="198fd-112">Requirements</span></span>  

 <span data-ttu-id="198fd-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="198fd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198fd-114">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="198fd-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="198fd-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198fd-116">См. также</span><span class="sxs-lookup"><span data-stu-id="198fd-116">See also</span></span>

- [<span data-ttu-id="198fd-117">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="198fd-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
