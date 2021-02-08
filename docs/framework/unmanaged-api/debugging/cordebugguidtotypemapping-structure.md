---
description: 'Дополнительные сведения о: структура Кордебуггуидтотипемаппинг'
title: Структура CorDebugGuidToTypeMapping
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: 5f6e99a17483b4fc16eb36ebb5fb5fd81380944b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801622"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="76821-103">Структура CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="76821-103">CorDebugGuidToTypeMapping Structure</span></span>

<span data-ttu-id="76821-104">Сопоставляет идентификатор GUID среда выполнения Windows с соответствующим объектом ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="76821-104">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76821-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76821-105">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="76821-106">Члены</span><span class="sxs-lookup"><span data-stu-id="76821-106">Members</span></span>  
  
|<span data-ttu-id="76821-107">Член</span><span class="sxs-lookup"><span data-stu-id="76821-107">Member</span></span>|<span data-ttu-id="76821-108">Описание</span><span class="sxs-lookup"><span data-stu-id="76821-108">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="76821-109">Идентификатор GUID кэшированного типа среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="76821-109">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="76821-110">Указатель на объект ICorDebugType, предоставляющий сведения о кэшированном типе.</span><span class="sxs-lookup"><span data-stu-id="76821-110">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76821-111">Требования</span><span class="sxs-lookup"><span data-stu-id="76821-111">Requirements</span></span>  

 <span data-ttu-id="76821-112">**Платформы:** среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="76821-112">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="76821-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76821-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76821-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76821-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76821-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76821-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76821-116">См. также</span><span class="sxs-lookup"><span data-stu-id="76821-116">See also</span></span>

- [<span data-ttu-id="76821-117">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="76821-117">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="76821-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="76821-118">Debugging</span></span>](index.md)
