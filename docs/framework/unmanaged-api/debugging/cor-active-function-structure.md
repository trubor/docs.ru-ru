---
description: 'Дополнительные сведения: структура COR_ACTIVE_FUNCTION'
title: Структура COR_ACTIVE_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: 7cc4a314c11ca4e2cdb4fe2b4090c471bcda26d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747238"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="41c9d-103">Структура COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="41c9d-103">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="41c9d-104">Содержит сведения о функциях, которые в данный момент активны в кадрах потока.</span><span class="sxs-lookup"><span data-stu-id="41c9d-104">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="41c9d-105">Эта структура используется методом [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41c9d-105">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c9d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41c9d-106">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="41c9d-107">Члены</span><span class="sxs-lookup"><span data-stu-id="41c9d-107">Members</span></span>  
  
|<span data-ttu-id="41c9d-108">Член</span><span class="sxs-lookup"><span data-stu-id="41c9d-108">Member</span></span>|<span data-ttu-id="41c9d-109">Описание</span><span class="sxs-lookup"><span data-stu-id="41c9d-109">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="41c9d-110">Указатель на владельца домена приложения для `ilOffset` поля.</span><span class="sxs-lookup"><span data-stu-id="41c9d-110">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="41c9d-111">Указатель на владельца `ilOffset` поля.</span><span class="sxs-lookup"><span data-stu-id="41c9d-111">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="41c9d-112">Указатель на владельца функции `ilOffset` поля.</span><span class="sxs-lookup"><span data-stu-id="41c9d-112">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="41c9d-113">Смещение кадра на языке MSIL.</span><span class="sxs-lookup"><span data-stu-id="41c9d-113">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="41c9d-114">Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="41c9d-114">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41c9d-115">Требования</span><span class="sxs-lookup"><span data-stu-id="41c9d-115">Requirements</span></span>  

 <span data-ttu-id="41c9d-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c9d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c9d-117">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="41c9d-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="41c9d-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41c9d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c9d-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c9d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c9d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="41c9d-120">See also</span></span>

- [<span data-ttu-id="41c9d-121">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="41c9d-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="41c9d-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="41c9d-122">Debugging</span></span>](index.md)
