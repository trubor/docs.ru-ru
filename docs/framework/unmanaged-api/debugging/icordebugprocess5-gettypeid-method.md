---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: TypeID'
title: Метод ICorDebugProcess5::GetTypeID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 564fc2819c9c370844111cf497d62e6d89cb28b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649719"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="fe2bb-103">Метод ICorDebugProcess5::GetTypeID</span><span class="sxs-lookup"><span data-stu-id="fe2bb-103">ICorDebugProcess5::GetTypeID Method</span></span>

<span data-ttu-id="fe2bb-104">Преобразует адрес объекта в идентификатор [COR_TYPEID](cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="fe2bb-104">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe2bb-105">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe2bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fe2bb-106">Parameters</span></span>  

 `obj`  
 <span data-ttu-id="fe2bb-107">окне Адрес объекта.</span><span class="sxs-lookup"><span data-stu-id="fe2bb-107">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="fe2bb-108">Указатель на значение [COR_TYPEID](cor-typeid-structure.md) , идентифицирующее объект.</span><span class="sxs-lookup"><span data-stu-id="fe2bb-108">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe2bb-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="fe2bb-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe2bb-110">Требования</span><span class="sxs-lookup"><span data-stu-id="fe2bb-110">Requirements</span></span>  

 <span data-ttu-id="fe2bb-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe2bb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe2bb-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe2bb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe2bb-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe2bb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe2bb-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe2bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2bb-115">См. также</span><span class="sxs-lookup"><span data-stu-id="fe2bb-115">See also</span></span>

- [<span data-ttu-id="fe2bb-116">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="fe2bb-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="fe2bb-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fe2bb-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
