---
description: 'Дополнительные сведения о: интерфейс Икордебуглоадедмодуле'
title: Интерфейс ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801232"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="5e340-103">Интерфейс ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="5e340-103">ICorDebugLoadedModule Interface</span></span>

<span data-ttu-id="5e340-104">Предоставляет сведения о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="5e340-104">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e340-105">Методы</span><span class="sxs-lookup"><span data-stu-id="5e340-105">Methods</span></span>  
  
|<span data-ttu-id="5e340-106">Метод</span><span class="sxs-lookup"><span data-stu-id="5e340-106">Method</span></span>|<span data-ttu-id="5e340-107">Описание</span><span class="sxs-lookup"><span data-stu-id="5e340-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e340-108">Метод GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="5e340-108">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="5e340-109">Получает базовый адрес загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="5e340-109">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="5e340-110">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="5e340-110">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="5e340-111">Получает имя загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="5e340-111">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="5e340-112">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="5e340-112">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="5e340-113">Возвращает размер в байтах загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="5e340-113">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e340-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="5e340-114">Remarks</span></span>  

 <span data-ttu-id="5e340-115">Интерфейс `ICorDebugLoadedModule` реализуется с помощью отладчика и используется интерфейсами отладки среды CLR для получения сведений о загруженном модуле из отладчика.</span><span class="sxs-lookup"><span data-stu-id="5e340-115">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e340-116">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5e340-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="5e340-117">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5e340-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e340-118">Требования</span><span class="sxs-lookup"><span data-stu-id="5e340-118">Requirements</span></span>  

 <span data-ttu-id="5e340-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e340-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e340-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e340-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e340-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e340-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e340-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e340-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e340-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5e340-123">See also</span></span>

- [<span data-ttu-id="5e340-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="5e340-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5e340-125">Отладка</span><span class="sxs-lookup"><span data-stu-id="5e340-125">Debugging</span></span>](index.md)
