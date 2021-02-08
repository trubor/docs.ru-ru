---
description: 'Дополнительные сведения о: интерфейс ICorDebugInstanceFieldSymbol'
title: Интерфейс ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: aa47c858ec5b4b0d04b851357fe81c0fc9b2e30a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791137"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="de49d-103">Интерфейс ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="de49d-103">ICorDebugInstanceFieldSymbol Interface</span></span>

<span data-ttu-id="de49d-104">Представляет сведения отладочного символа для поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="de49d-104">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de49d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="de49d-105">Methods</span></span>  
  
|<span data-ttu-id="de49d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="de49d-106">Method</span></span>|<span data-ttu-id="de49d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="de49d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de49d-108">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="de49d-108">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="de49d-109">Получает имя поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="de49d-109">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="de49d-110">Метод GetOffset</span><span class="sxs-lookup"><span data-stu-id="de49d-110">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="de49d-111">Возвращает смещение в байтах этого поля экземпляра в его родительском классе.</span><span class="sxs-lookup"><span data-stu-id="de49d-111">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="de49d-112">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="de49d-112">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="de49d-113">Получает размер поля экземпляра в байтах.</span><span class="sxs-lookup"><span data-stu-id="de49d-113">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de49d-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="de49d-114">Remarks</span></span>  

 <span data-ttu-id="de49d-115">Интерфейс `ICorDebugInstanceFieldSymbol` используется для получения сведений символа отладки для поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="de49d-115">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de49d-116">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="de49d-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="de49d-117">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="de49d-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de49d-118">Требования</span><span class="sxs-lookup"><span data-stu-id="de49d-118">Requirements</span></span>  

 <span data-ttu-id="de49d-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de49d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de49d-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de49d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de49d-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de49d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de49d-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de49d-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de49d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="de49d-123">See also</span></span>

- [<span data-ttu-id="de49d-124">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="de49d-124">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="de49d-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="de49d-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="de49d-126">Отладка</span><span class="sxs-lookup"><span data-stu-id="de49d-126">Debugging</span></span>](index.md)
