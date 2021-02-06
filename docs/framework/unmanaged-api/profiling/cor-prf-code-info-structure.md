---
description: 'Дополнительные сведения: структура COR_PRF_CODE_INFO'
title: Структура COR_PRF_CODE_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 11eae032424a039cac1136c08409b5b4712e6db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649251"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="c52a0-103">Структура COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="c52a0-103">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="c52a0-104">Представляет один непрерывный блок машинного кода, хранящийся в памяти.</span><span class="sxs-lookup"><span data-stu-id="c52a0-104">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52a0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c52a0-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c52a0-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c52a0-106">Members</span></span>  
  
|<span data-ttu-id="c52a0-107">Член</span><span class="sxs-lookup"><span data-stu-id="c52a0-107">Member</span></span>|<span data-ttu-id="c52a0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c52a0-108">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="c52a0-109">Начальный адрес непрерывного блока кода.</span><span class="sxs-lookup"><span data-stu-id="c52a0-109">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="c52a0-110">Размер блока.</span><span class="sxs-lookup"><span data-stu-id="c52a0-110">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c52a0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c52a0-111">Requirements</span></span>  

 <span data-ttu-id="c52a0-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c52a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c52a0-113">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="c52a0-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c52a0-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c52a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c52a0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c52a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52a0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c52a0-116">See also</span></span>

- [<span data-ttu-id="c52a0-117">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="c52a0-117">Profiling Structures</span></span>](profiling-structures.md)
