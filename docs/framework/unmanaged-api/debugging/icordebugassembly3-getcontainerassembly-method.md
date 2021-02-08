---
description: 'Дополнительные сведения о методе: ICorDebugAssembly3:: GetContainerAssembly'
title: Метод ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791521"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="95ad6-103">Метод ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="95ad6-103">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="95ad6-104">Возвращает контейнерную сборку этого объекта `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="95ad6-104">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ad6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95ad6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95ad6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="95ad6-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="95ad6-107">Указатель на адрес объекта ICorDebugAssembly, который представляет сборку контейнера, или **значение NULL** , если вызов метода завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="95ad6-107">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95ad6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="95ad6-108">Return Value</span></span>  

 <span data-ttu-id="95ad6-109">`S_OK` значение, если вызов метода выполнен. в противном случае, `S_FALSE` и `ppAssembly` имеет **значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="95ad6-109">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95ad6-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="95ad6-110">Remarks</span></span>  

 <span data-ttu-id="95ad6-111">Если эта сборка была объединена с другими сборками внутри одиночной контейнерной сборки, этот метод возвращает контейнерную сборку.</span><span class="sxs-lookup"><span data-stu-id="95ad6-111">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="95ad6-112">Дополнительные сведения и терминология см. в разделе [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="95ad6-112">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95ad6-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="95ad6-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95ad6-114">Требования</span><span class="sxs-lookup"><span data-stu-id="95ad6-114">Requirements</span></span>  

 <span data-ttu-id="95ad6-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95ad6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ad6-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95ad6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95ad6-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95ad6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95ad6-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ad6-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ad6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="95ad6-119">See also</span></span>

- [<span data-ttu-id="95ad6-120">Интерфейс ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="95ad6-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="95ad6-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="95ad6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
