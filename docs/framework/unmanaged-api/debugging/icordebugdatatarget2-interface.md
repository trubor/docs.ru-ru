---
description: 'Дополнительные сведения о: интерфейс метод icordebugdatatarget2'
title: Интерфейс ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 13a83ee99f0158f32f466f9ae29af3d917248f95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710469"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="b9335-103">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="b9335-103">ICorDebugDataTarget2 Interface</span></span>

<span data-ttu-id="b9335-104">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b9335-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9335-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b9335-105">Methods</span></span>  
  
|<span data-ttu-id="b9335-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b9335-106">Method</span></span>|<span data-ttu-id="b9335-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b9335-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9335-108">Метод CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="b9335-108">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="b9335-109">Создает новый элемент очистки стека, запускающий операцию очистки, начиная с исходного контекста (который не обязательно является концом потока).</span><span class="sxs-lookup"><span data-stu-id="b9335-109">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="b9335-110">Метод EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="b9335-110">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="b9335-111">Возвращает список идентификаторов активных потоков.</span><span class="sxs-lookup"><span data-stu-id="b9335-111">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="b9335-112">Метод GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="b9335-112">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="b9335-113">Возвращает базовый адрес и размер модуля из адреса в этом модуле.</span><span class="sxs-lookup"><span data-stu-id="b9335-113">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="b9335-114">Метод GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="b9335-114">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="b9335-115">Возвращает путь для модуля из базового адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="b9335-115">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="b9335-116">Метод GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="b9335-116">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="b9335-117">Возвращает поставщика символов для модуля из базового адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="b9335-117">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9335-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9335-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9335-119">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b9335-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b9335-120">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b9335-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9335-121">Требования</span><span class="sxs-lookup"><span data-stu-id="b9335-121">Requirements</span></span>  

 <span data-ttu-id="b9335-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9335-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9335-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9335-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9335-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9335-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9335-125">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9335-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9335-126">См. также</span><span class="sxs-lookup"><span data-stu-id="b9335-126">See also</span></span>

- [<span data-ttu-id="b9335-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b9335-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b9335-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="b9335-128">Debugging</span></span>](index.md)
