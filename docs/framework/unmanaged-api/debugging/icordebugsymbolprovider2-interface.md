---
description: 'Дополнительные сведения о: интерфейс ICorDebugSymbolProvider2'
title: Интерфейс ICorDebugSymbolProvider2
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: b4eaeb29c15da979a522fb20e33a56030889d0c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659521"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="ff38b-103">Интерфейс ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="ff38b-103">ICorDebugSymbolProvider2 Interface</span></span>

<span data-ttu-id="ff38b-104">Логически расширяет интерфейс [метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md) для получения дополнительных сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="ff38b-104">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff38b-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ff38b-105">Methods</span></span>  
  
|<span data-ttu-id="ff38b-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ff38b-106">Method</span></span>|<span data-ttu-id="ff38b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ff38b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff38b-108">Метод GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="ff38b-108">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="ff38b-109">Возвращает начальный относительный виртуальный адрес метода и родительского фрейма для указанного относительного виртуального адреса кода.</span><span class="sxs-lookup"><span data-stu-id="ff38b-109">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="ff38b-110">Метод GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="ff38b-110">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="ff38b-111">Получает универсальную карту словаря</span><span class="sxs-lookup"><span data-stu-id="ff38b-111">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff38b-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff38b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff38b-113">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ff38b-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ff38b-114">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ff38b-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff38b-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ff38b-115">Requirements</span></span>  

 <span data-ttu-id="ff38b-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff38b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff38b-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff38b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff38b-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff38b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff38b-119">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff38b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff38b-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ff38b-120">See also</span></span>

- [<span data-ttu-id="ff38b-121">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="ff38b-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ff38b-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ff38b-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ff38b-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="ff38b-123">Debugging</span></span>](index.md)
