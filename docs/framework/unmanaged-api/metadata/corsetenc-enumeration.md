---
description: Дополнительные сведения о перечислении CorSetENC
title: Перечисление CorSetENC
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 5ba3e41c10b082ceb2ce7d327f7ff7f857ca98a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707401"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="98c2b-103">Перечисление CorSetENC</span><span class="sxs-lookup"><span data-stu-id="98c2b-103">CorSetENC Enumeration</span></span>

<span data-ttu-id="98c2b-104">Содержит значения, используемые для оказания влияния на поведение во время создания метаданных.</span><span class="sxs-lookup"><span data-stu-id="98c2b-104">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c2b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98c2b-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="98c2b-106">Члены</span><span class="sxs-lookup"><span data-stu-id="98c2b-106">Members</span></span>  
  
|<span data-ttu-id="98c2b-107">Член</span><span class="sxs-lookup"><span data-stu-id="98c2b-107">Member</span></span>|<span data-ttu-id="98c2b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="98c2b-108">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="98c2b-109">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="98c2b-109">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="98c2b-110">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="98c2b-110">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="98c2b-111">Указывает, что в то время как метаданные могут быть обновлены, токены перемещаться нельзя.</span><span class="sxs-lookup"><span data-stu-id="98c2b-111">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="98c2b-112">Указывает, что токены можно перемещать во время обновлений.</span><span class="sxs-lookup"><span data-stu-id="98c2b-112">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="98c2b-113">Указывает, что обновления могут состоять только из добавлений.</span><span class="sxs-lookup"><span data-stu-id="98c2b-113">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="98c2b-114">Маркеры не могут быть перемещены.</span><span class="sxs-lookup"><span data-stu-id="98c2b-114">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="98c2b-115">Указывает, что компиляция является добавочной.</span><span class="sxs-lookup"><span data-stu-id="98c2b-115">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="98c2b-116">Указывает, что должны быть сохранены только измененные метаданные.</span><span class="sxs-lookup"><span data-stu-id="98c2b-116">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="98c2b-117">Включает `MDUpdateENC` , `MDUpdateFull` и `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="98c2b-117">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98c2b-118">Требования</span><span class="sxs-lookup"><span data-stu-id="98c2b-118">Requirements</span></span>  

 <span data-ttu-id="98c2b-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98c2b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c2b-120">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="98c2b-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="98c2b-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c2b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c2b-122">См. также</span><span class="sxs-lookup"><span data-stu-id="98c2b-122">See also</span></span>

- [<span data-ttu-id="98c2b-123">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="98c2b-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
