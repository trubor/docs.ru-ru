---
description: 'Дополнительные сведения о: интерфейс ICorDebugAssembly3'
title: Интерфейс ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791508"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="0bd3b-103">Интерфейс ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="0bd3b-103">ICorDebugAssembly3 Interface</span></span>

<span data-ttu-id="0bd3b-104">Логически расширяет интерфейс ICorDebugAssembly для обеспечения поддержки контейнерных сборок и их вложенных сборок.</span><span class="sxs-lookup"><span data-stu-id="0bd3b-104">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bd3b-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0bd3b-105">Methods</span></span>  
  
|<span data-ttu-id="0bd3b-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0bd3b-106">Method</span></span>|<span data-ttu-id="0bd3b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0bd3b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bd3b-108">Метод EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="0bd3b-108">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="0bd3b-109">Получает перечислитель для сборок, содержащихся в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="0bd3b-109">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="0bd3b-110">Метод GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="0bd3b-110">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="0bd3b-111">Возвращает контейнерную сборку этого объекта `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="0bd3b-111">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bd3b-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="0bd3b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bd3b-113">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0bd3b-113">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0bd3b-114">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0bd3b-114">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd3b-115">Требования</span><span class="sxs-lookup"><span data-stu-id="0bd3b-115">Requirements</span></span>  

 <span data-ttu-id="0bd3b-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd3b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd3b-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bd3b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd3b-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd3b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd3b-119">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd3b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd3b-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0bd3b-120">See also</span></span>

- [<span data-ttu-id="0bd3b-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0bd3b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0bd3b-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="0bd3b-122">Debugging</span></span>](index.md)
