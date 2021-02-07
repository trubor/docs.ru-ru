---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: GetObject'
title: Метод ICorDebugProcess5::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 4e295e1afc19cc5b9ca763b04b05097d48f0302c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746364"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="04ff4-103">Метод ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="04ff4-103">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="04ff4-104">Преобразует адрес объекта в объект "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="04ff4-104">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ff4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04ff4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ff4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="04ff4-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="04ff4-107">окне Адрес объекта.</span><span class="sxs-lookup"><span data-stu-id="04ff4-107">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="04ff4-108">заполняет Указатель на адрес объекта "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="04ff4-108">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ff4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="04ff4-109">Remarks</span></span>  

 <span data-ttu-id="04ff4-110">Если не `addr` указывает на допустимый управляемый объект, `GetObject` метод возвращает значение `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="04ff4-110">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ff4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="04ff4-111">Requirements</span></span>  

 <span data-ttu-id="04ff4-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ff4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ff4-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04ff4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ff4-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ff4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04ff4-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ff4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ff4-116">См. также</span><span class="sxs-lookup"><span data-stu-id="04ff4-116">See also</span></span>

- [<span data-ttu-id="04ff4-117">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="04ff4-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="04ff4-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="04ff4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
