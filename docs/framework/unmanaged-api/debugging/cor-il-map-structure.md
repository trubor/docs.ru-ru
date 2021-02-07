---
description: 'Дополнительные сведения: структура COR_IL_MAP'
title: Структура COR_IL_MAP
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: ff3d636429f51119342baea5d71163eb9d764e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712328"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="64d64-103">Структура COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="64d64-103">COR_IL_MAP Structure</span></span>

<span data-ttu-id="64d64-104">Указывает изменения в относительном смещении функции.</span><span class="sxs-lookup"><span data-stu-id="64d64-104">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d64-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64d64-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="64d64-106">Члены</span><span class="sxs-lookup"><span data-stu-id="64d64-106">Members</span></span>  
  
|<span data-ttu-id="64d64-107">Член</span><span class="sxs-lookup"><span data-stu-id="64d64-107">Member</span></span>|<span data-ttu-id="64d64-108">Описание</span><span class="sxs-lookup"><span data-stu-id="64d64-108">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="64d64-109">Старый сдвиг на языке MSIL относительно начала функции.</span><span class="sxs-lookup"><span data-stu-id="64d64-109">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="64d64-110">Новое смещение MSIL относительно начала функции.</span><span class="sxs-lookup"><span data-stu-id="64d64-110">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="64d64-111">`true` значение, если сопоставление известно как точное; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="64d64-111">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d64-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="64d64-112">Remarks</span></span>  

 <span data-ttu-id="64d64-113">Формат схемы выглядит следующим образом: в отладчике предполагается, что `oldOffset` ссылается на смещение MSIL в исходном, неизмененном коде MSIL.</span><span class="sxs-lookup"><span data-stu-id="64d64-113">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="64d64-114">`newOffset`Параметр ссылается на соответствующее смещение MSIL в новом, инструментированном коде.</span><span class="sxs-lookup"><span data-stu-id="64d64-114">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="64d64-115">Чтобы пошаговая работа работала правильно, должны выполняться следующие требования:</span><span class="sxs-lookup"><span data-stu-id="64d64-115">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="64d64-116">Схема должна быть отсортирована в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="64d64-116">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="64d64-117">Не следует изменять порядок инструментированного кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="64d64-117">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="64d64-118">Исходный код MSIL не должен удаляться.</span><span class="sxs-lookup"><span data-stu-id="64d64-118">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="64d64-119">На карте должны содержаться записи, позволяющие сопоставлять все точки последовательности из файла базы данных программы (PDB).</span><span class="sxs-lookup"><span data-stu-id="64d64-119">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="64d64-120">На карте не выполняется интерполяция отсутствующих записей.</span><span class="sxs-lookup"><span data-stu-id="64d64-120">The map does not interpolate missing entries.</span></span> <span data-ttu-id="64d64-121">В следующем примере показана схема и ее результаты.</span><span class="sxs-lookup"><span data-stu-id="64d64-121">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="64d64-122">Таблица</span><span class="sxs-lookup"><span data-stu-id="64d64-122">Map:</span></span>  
  
- <span data-ttu-id="64d64-123">0 старое смещение, 0 новое смещение</span><span class="sxs-lookup"><span data-stu-id="64d64-123">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="64d64-124">5 старое смещение, 10 новых смещений</span><span class="sxs-lookup"><span data-stu-id="64d64-124">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="64d64-125">9 старое смещение, 20 новое смещение</span><span class="sxs-lookup"><span data-stu-id="64d64-125">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="64d64-126">Результат:</span><span class="sxs-lookup"><span data-stu-id="64d64-126">Results:</span></span>  
  
- <span data-ttu-id="64d64-127">Старое смещение 0, 1, 2, 3 или 4 будет сопоставлено с новым смещением, равным 0.</span><span class="sxs-lookup"><span data-stu-id="64d64-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="64d64-128">Старое смещение 5, 6, 7 или 8 будет сопоставлено с новым смещением 10.</span><span class="sxs-lookup"><span data-stu-id="64d64-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="64d64-129">Старое смещение 9 или выше будет сопоставлено с новым смещением 20.</span><span class="sxs-lookup"><span data-stu-id="64d64-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="64d64-130">Новое смещение 0, 1, 2, 3, 4, 5, 6, 7, 8 или 9 будет сопоставлено со старым смещением 0.</span><span class="sxs-lookup"><span data-stu-id="64d64-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="64d64-131">Новое смещение, равное 10, 11, 12, 13, 14, 15, 16, 17, 18 или 19, будет сопоставлено со старым смещением 5.</span><span class="sxs-lookup"><span data-stu-id="64d64-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="64d64-132">Новое смещение, равное 20 или выше, будет сопоставлено старому смещению 9.</span><span class="sxs-lookup"><span data-stu-id="64d64-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d64-133">Требования</span><span class="sxs-lookup"><span data-stu-id="64d64-133">Requirements</span></span>  

 <span data-ttu-id="64d64-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d64-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d64-135">**Заголовок:** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="64d64-135">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="64d64-136">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64d64-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d64-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d64-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d64-138">См. также</span><span class="sxs-lookup"><span data-stu-id="64d64-138">See also</span></span>

- [<span data-ttu-id="64d64-139">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="64d64-139">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="64d64-140">Отладка</span><span class="sxs-lookup"><span data-stu-id="64d64-140">Debugging</span></span>](index.md)
