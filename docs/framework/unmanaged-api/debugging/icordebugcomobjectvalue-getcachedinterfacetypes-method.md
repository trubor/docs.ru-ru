---
description: 'Дополнительные сведения о методе: Икордебугкомобжектвалуе:: Жеткачединтерфацетипес'
title: Метод ICorDebugComObjectValue::GetCachedInterfaceTypes
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: b1c65979895dfaeacae3d171adbcfd1455b7030d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764623"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="e2fb5-103">Метод ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="e2fb5-103">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>

<span data-ttu-id="e2fb5-104">Предоставляет перечислитель для типов интерфейса, которые текущий объект приводят к типу или используются в качестве.</span><span class="sxs-lookup"><span data-stu-id="e2fb5-104">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2fb5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e2fb5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2fb5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e2fb5-106">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="e2fb5-107">окне Значение, указывающее, возвращает ли метод только среда выполнения Windows интерфейсы ( `IInspectable` интерфейсы) или все COM-интерфейсы, кэшированные вызываемой оболочкой времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="e2fb5-107">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="e2fb5-108">заполняет Указатель на адрес перечислителя ICorDebugTypeEnum, который предоставляет доступ к объектам ICorDebugType, представляющим кэшированные типы интерфейсов, отфильтрованные в соответствии с `bIInspectableOnly` .</span><span class="sxs-lookup"><span data-stu-id="e2fb5-108">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2fb5-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e2fb5-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2fb5-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e2fb5-110">Requirements</span></span>  

 <span data-ttu-id="e2fb5-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2fb5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2fb5-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2fb5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2fb5-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2fb5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2fb5-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2fb5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fb5-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e2fb5-115">See also</span></span>

- [<span data-ttu-id="e2fb5-116">Интерфейс ICorDebugComObjectValue Interface</span><span class="sxs-lookup"><span data-stu-id="e2fb5-116">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="e2fb5-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e2fb5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
