---
description: 'Дополнительные сведения о: интерфейс Икордебугмеморибуффер'
title: Интерфейс ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 94eeb0f31c0e1c053fabbd556768fa65dda2d328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754021"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="5f023-103">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="5f023-103">ICorDebugMemoryBuffer Interface</span></span>

<span data-ttu-id="5f023-104">Представляет буфер в памяти.</span><span class="sxs-lookup"><span data-stu-id="5f023-104">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f023-105">Методы</span><span class="sxs-lookup"><span data-stu-id="5f023-105">Methods</span></span>  
  
|<span data-ttu-id="5f023-106">Метод</span><span class="sxs-lookup"><span data-stu-id="5f023-106">Method</span></span>|<span data-ttu-id="5f023-107">Описание</span><span class="sxs-lookup"><span data-stu-id="5f023-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f023-108">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="5f023-108">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="5f023-109">Возвращает размер буфера памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="5f023-109">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="5f023-110">Метод GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="5f023-110">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="5f023-111">Возвращает начальный адрес буфера памяти.</span><span class="sxs-lookup"><span data-stu-id="5f023-111">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f023-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="5f023-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f023-113">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5f023-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="5f023-114">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5f023-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f023-115">Требования</span><span class="sxs-lookup"><span data-stu-id="5f023-115">Requirements</span></span>  

 <span data-ttu-id="5f023-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f023-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f023-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f023-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f023-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f023-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f023-119">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f023-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f023-120">См. также</span><span class="sxs-lookup"><span data-stu-id="5f023-120">See also</span></span>

- [<span data-ttu-id="5f023-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="5f023-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5f023-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="5f023-122">Debugging</span></span>](index.md)
