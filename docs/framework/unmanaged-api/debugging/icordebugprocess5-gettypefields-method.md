---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Жеттипефиелдс'
title: Метод ICorDebugProcess5::GetTypeFields
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: bdbb0be76400262d83876b9fc37cc4f00eb34e43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649823"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="3bcd0-103">Метод ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="3bcd0-103">ICorDebugProcess5::GetTypeFields Method</span></span>

<span data-ttu-id="3bcd0-104">Предоставляет сведения о полях, принадлежащих типу.</span><span class="sxs-lookup"><span data-stu-id="3bcd0-104">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bcd0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3bcd0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bcd0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3bcd0-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="3bcd0-107">окне Идентификатор типа, сведения о поле которого извлекаются.</span><span class="sxs-lookup"><span data-stu-id="3bcd0-107">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="3bcd0-108">окне Число объектов [COR_FIELD](cor-field-structure.md) , сведения о полях которых нужно получить.</span><span class="sxs-lookup"><span data-stu-id="3bcd0-108">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="3bcd0-109">заполняет Массив объектов [COR_FIELD](cor-field-structure.md) , которые предоставляют сведения о полях, принадлежащих типу.</span><span class="sxs-lookup"><span data-stu-id="3bcd0-109">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="3bcd0-110">заполняет Указатель на число объектов [COR_FIELD](cor-field-structure.md) , включаемых в `fields` .</span><span class="sxs-lookup"><span data-stu-id="3bcd0-110">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bcd0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3bcd0-111">Remarks</span></span>  

 <span data-ttu-id="3bcd0-112">`celt`Параметр, указывающий количество полей, сведения о полях которых использует метод для заполнения `fields` , должно соответствовать значению `COR_TYPE_LAYOUT::numFields` поля.</span><span class="sxs-lookup"><span data-stu-id="3bcd0-112">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bcd0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="3bcd0-113">Requirements</span></span>  

 <span data-ttu-id="3bcd0-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bcd0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bcd0-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bcd0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bcd0-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bcd0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bcd0-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bcd0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcd0-118">См. также</span><span class="sxs-lookup"><span data-stu-id="3bcd0-118">See also</span></span>

- [<span data-ttu-id="3bcd0-119">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="3bcd0-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3bcd0-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3bcd0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
