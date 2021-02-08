---
description: Дополнительные сведения о перечислении Корсавесизе
title: Перечисление CorSaveSize
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 47e2d4d77f58f8f1c2135da5867dfa47cedfd83d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784227"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="8adb8-103">Перечисление CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="8adb8-103">CorSaveSize Enumeration</span></span>

<span data-ttu-id="8adb8-104">Содержит значения, указывающие уровень точности, необходимый при запросе размера операции сохранения.</span><span class="sxs-lookup"><span data-stu-id="8adb8-104">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adb8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8adb8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="8adb8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8adb8-106">Members</span></span>  
  
|<span data-ttu-id="8adb8-107">Член</span><span class="sxs-lookup"><span data-stu-id="8adb8-107">Member</span></span>|<span data-ttu-id="8adb8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8adb8-108">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="8adb8-109">Указывает, что возвращаемое значение должно быть точным.</span><span class="sxs-lookup"><span data-stu-id="8adb8-109">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="8adb8-110">Указывает, что возвращаемое значение должно быть оценено.</span><span class="sxs-lookup"><span data-stu-id="8adb8-110">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="8adb8-111">Указывает, что удаляемые типы должны быть удалены.</span><span class="sxs-lookup"><span data-stu-id="8adb8-111">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8adb8-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8adb8-112">Requirements</span></span>  

 <span data-ttu-id="8adb8-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adb8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adb8-114">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="8adb8-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8adb8-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8adb8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8adb8-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adb8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8adb8-117">See also</span></span>

- [<span data-ttu-id="8adb8-118">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="8adb8-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
