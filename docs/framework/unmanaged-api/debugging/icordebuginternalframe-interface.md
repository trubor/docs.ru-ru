---
description: 'Дополнительные сведения о: интерфейс ICorDebugInternalFrame'
title: Интерфейс ICorDebugInternalFrame
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: 7143f270b97e10fb9664aa7f7387749ddecbbcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791144"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="33670-103">Интерфейс ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="33670-103">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="33670-104">Представляет внутренний кадр среды выполнения в стеке.</span><span class="sxs-lookup"><span data-stu-id="33670-104">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="33670-105">Этот интерфейс является подклассом интерфейса ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="33670-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33670-106">Методы</span><span class="sxs-lookup"><span data-stu-id="33670-106">Methods</span></span>  
  
|<span data-ttu-id="33670-107">Метод</span><span class="sxs-lookup"><span data-stu-id="33670-107">Method</span></span>|<span data-ttu-id="33670-108">Описание</span><span class="sxs-lookup"><span data-stu-id="33670-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33670-109">Метод GetFrameType</span><span class="sxs-lookup"><span data-stu-id="33670-109">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="33670-110">Возвращает тип этого внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="33670-110">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33670-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="33670-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33670-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="33670-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33670-113">Требования</span><span class="sxs-lookup"><span data-stu-id="33670-113">Requirements</span></span>  

 <span data-ttu-id="33670-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33670-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33670-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33670-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33670-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33670-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33670-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33670-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33670-118">См. также</span><span class="sxs-lookup"><span data-stu-id="33670-118">See also</span></span>

- [<span data-ttu-id="33670-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="33670-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
