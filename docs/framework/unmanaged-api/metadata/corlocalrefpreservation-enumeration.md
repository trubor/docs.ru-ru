---
description: Дополнительные сведения о перечислении Корлокалрефпресерватион
title: Перечисление CorLocalRefPreservation
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: afcdf6ce22c5f786e8f728cc1e45ad3ca44e7ef5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784422"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="ece80-103">Перечисление CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="ece80-103">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="ece80-104">Содержит значения флага для обработки локальных ссылок.</span><span class="sxs-lookup"><span data-stu-id="ece80-104">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ece80-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="ece80-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ece80-106">Members</span></span>  
  
|<span data-ttu-id="ece80-107">Член</span><span class="sxs-lookup"><span data-stu-id="ece80-107">Member</span></span>|<span data-ttu-id="ece80-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ece80-108">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="ece80-109">Не сохранять локальные ссылки.</span><span class="sxs-lookup"><span data-stu-id="ece80-109">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="ece80-110">Сохранение ссылок на локальные типы.</span><span class="sxs-lookup"><span data-stu-id="ece80-110">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="ece80-111">Сохранение ссылок на локальные члены.</span><span class="sxs-lookup"><span data-stu-id="ece80-111">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ece80-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ece80-112">Requirements</span></span>  

 <span data-ttu-id="ece80-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ece80-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece80-114">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="ece80-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ece80-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ece80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece80-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ece80-116">See also</span></span>

- [<span data-ttu-id="ece80-117">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="ece80-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
