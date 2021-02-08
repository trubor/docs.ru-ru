---
description: 'Дополнительные сведения: структура StackTrace_SimpleContext'
title: Структура StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 22a0acada5ef2d392dfdef5326953be137280d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800569"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="6cd88-103">Структура StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="6cd88-103">StackTrace_SimpleContext Structure</span></span>

<span data-ttu-id="6cd88-104">Обеспечивает простой контекст, который может использоваться вместо полной структуры `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="6cd88-104">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd88-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6cd88-105">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6cd88-106">Члены</span><span class="sxs-lookup"><span data-stu-id="6cd88-106">Members</span></span>  
  
|<span data-ttu-id="6cd88-107">Член</span><span class="sxs-lookup"><span data-stu-id="6cd88-107">Member</span></span>|<span data-ttu-id="6cd88-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6cd88-108">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="6cd88-109">Указатель стека или ввод указателя стека (ESP) на платформах x86.</span><span class="sxs-lookup"><span data-stu-id="6cd88-109">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="6cd88-110">Смещение кадра или регистр EBP на платформах x86.</span><span class="sxs-lookup"><span data-stu-id="6cd88-110">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="6cd88-111">Указатель инструкции или ввод указателя инструкции (EIP) на платформах x86.</span><span class="sxs-lookup"><span data-stu-id="6cd88-111">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cd88-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="6cd88-112">Remarks</span></span>  

 <span data-ttu-id="6cd88-113">Поскольку функции трассировки стека обычно должны возвращать только адрес, Смещение фрейма и адрес стека, при необходимости можно использовать `SimpleContext` структуру, а не большую `CONTEXT` структуру.</span><span class="sxs-lookup"><span data-stu-id="6cd88-113">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd88-114">Требования</span><span class="sxs-lookup"><span data-stu-id="6cd88-114">Requirements</span></span>  

 <span data-ttu-id="6cd88-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd88-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd88-116">**Заголовок:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="6cd88-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6cd88-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd88-118">См. также</span><span class="sxs-lookup"><span data-stu-id="6cd88-118">See also</span></span>

- [<span data-ttu-id="6cd88-119">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="6cd88-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="6cd88-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="6cd88-120">Debugging</span></span>](index.md)
