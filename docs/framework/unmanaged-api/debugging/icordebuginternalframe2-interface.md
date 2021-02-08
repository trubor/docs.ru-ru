---
description: 'Дополнительные сведения о: интерфейс ICorDebugInternalFrame2'
title: Интерфейс ICorDebugInternalFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: 3edc666c043513562b2fcece478b2879f294ce33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791105"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="fa044-103">Интерфейс ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="fa044-103">ICorDebugInternalFrame2 Interface</span></span>

<span data-ttu-id="fa044-104">Предоставляет сведения о внутренних кадрах, включая стековый адрес и положение относительно объектов ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="fa044-104">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa044-105">Методы</span><span class="sxs-lookup"><span data-stu-id="fa044-105">Methods</span></span>  
  
|<span data-ttu-id="fa044-106">Метод</span><span class="sxs-lookup"><span data-stu-id="fa044-106">Method</span></span>|<span data-ttu-id="fa044-107">Описание</span><span class="sxs-lookup"><span data-stu-id="fa044-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa044-108">Метод GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="fa044-108">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="fa044-109">Возвращает адрес стека внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="fa044-109">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="fa044-110">Метод IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="fa044-110">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="fa044-111">Проверяет, `this` находится ли внутренний кадр ближе к конечному объекту, чем указанный объект ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="fa044-111">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa044-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="fa044-112">Remarks</span></span>  

 <span data-ttu-id="fa044-113">Этот интерфейс расширяет интерфейс ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="fa044-113">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa044-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="fa044-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa044-115">Требования</span><span class="sxs-lookup"><span data-stu-id="fa044-115">Requirements</span></span>  

 <span data-ttu-id="fa044-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa044-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa044-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa044-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa044-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa044-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa044-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa044-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa044-120">См. также</span><span class="sxs-lookup"><span data-stu-id="fa044-120">See also</span></span>

- [<span data-ttu-id="fa044-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fa044-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fa044-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="fa044-122">Debugging</span></span>](index.md)
