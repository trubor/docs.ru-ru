---
description: 'Дополнительные сведения о методе: ICorDebugDebugEvent:: GetEventKind'
title: Метод ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 9e15eb82195fae8aa3797ea47cb04d0bb407d2ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764324"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="75e0e-103">Метод ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="75e0e-103">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="75e0e-104">Указывает тип события, который представляет этот объект `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="75e0e-104">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e0e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="75e0e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e0e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="75e0e-106">Parameters</span></span>  

 <span data-ttu-id="75e0e-107">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="75e0e-107">pDebugEventKind</span></span>  
 <span data-ttu-id="75e0e-108">Указатель на элемент перечисления [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , указывающий тип события.</span><span class="sxs-lookup"><span data-stu-id="75e0e-108">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75e0e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="75e0e-109">Remarks</span></span>  

 <span data-ttu-id="75e0e-110">На основе значения `pDebugEventKind` можно вызвать `QueryInterface`, чтобы получить более точный интерфейс событий отладки, содержащий дополнительные данные.</span><span class="sxs-lookup"><span data-stu-id="75e0e-110">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75e0e-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="75e0e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e0e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="75e0e-112">Requirements</span></span>  

 <span data-ttu-id="75e0e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75e0e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e0e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75e0e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75e0e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75e0e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75e0e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e0e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e0e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="75e0e-117">See also</span></span>

- [<span data-ttu-id="75e0e-118">Интерфейс ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="75e0e-118">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="75e0e-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="75e0e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
