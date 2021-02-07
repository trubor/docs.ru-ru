---
description: 'Дополнительные сведения о методе: Икордебужексцептиондебужевент:: "Flags"'
title: Метод ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 54a6c9b0dff2346ca130f80e72fe06dbb3017f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693477"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="ab528-103">Метод ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="ab528-103">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="ab528-104">Возвращает флаг, указывающий, может ли исключение быть перехвачено.</span><span class="sxs-lookup"><span data-stu-id="ab528-104">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab528-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab528-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab528-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab528-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="ab528-107">заполняет Указатель на значение [кордебужексцептионфлагс](cordebugexceptionflags-enumeration.md) , указывающее, может ли быть перехвачено исключение.</span><span class="sxs-lookup"><span data-stu-id="ab528-107">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab528-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="ab528-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab528-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="ab528-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab528-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ab528-110">Requirements</span></span>  

 <span data-ttu-id="ab528-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab528-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab528-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab528-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab528-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab528-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab528-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab528-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab528-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ab528-115">See also</span></span>

- [<span data-ttu-id="ab528-116">Интерфейс ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ab528-116">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="ab528-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ab528-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
