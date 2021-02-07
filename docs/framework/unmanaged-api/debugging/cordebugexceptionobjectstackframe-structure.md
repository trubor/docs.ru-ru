---
description: 'Дополнительные сведения о: структура Кордебужексцептионобжектстаккфраме'
title: Структура CorDebugExceptionObjectStackFrame
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: abeb5a9f6385c494745a34c6f37d6fbc1376ad7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662160"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="c3072-103">Структура CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="c3072-103">CorDebugExceptionObjectStackFrame Structure</span></span>

<span data-ttu-id="c3072-104">Представляет сведения о кадре стека из объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="c3072-104">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3072-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3072-105">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="c3072-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c3072-106">Members</span></span>  
  
|<span data-ttu-id="c3072-107">Член</span><span class="sxs-lookup"><span data-stu-id="c3072-107">Member</span></span>|<span data-ttu-id="c3072-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c3072-108">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="c3072-109">Указатель на объект ICorDebugModule для текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="c3072-109">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="c3072-110">Значение указателя инструкций (EIP/RIP) для текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="c3072-110">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="c3072-111">Токен метода для текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="c3072-111">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="c3072-112">Значение, указывающее, является ли кадр последним кадром во внешнем исключении.</span><span class="sxs-lookup"><span data-stu-id="c3072-112">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3072-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3072-113">Remarks</span></span>  

 <span data-ttu-id="c3072-114">Вызывающая сторона должна освободить указатель на объект ICorDebugModule, когда он больше не используется.</span><span class="sxs-lookup"><span data-stu-id="c3072-114">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3072-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c3072-115">Requirements</span></span>  

 <span data-ttu-id="c3072-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3072-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3072-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3072-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3072-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3072-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3072-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3072-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3072-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c3072-120">See also</span></span>

- [<span data-ttu-id="c3072-121">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="c3072-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c3072-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="c3072-122">Debugging</span></span>](index.md)
