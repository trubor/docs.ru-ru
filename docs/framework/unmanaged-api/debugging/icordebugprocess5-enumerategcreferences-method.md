---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Енумератегкреференцес'
title: Метод ICorDebugProcess5::EnumerateGCReferences
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 5145fd072b083ed107b874fe99403984915233ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746416"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="9e779-103">Метод ICorDebugProcess5::EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="9e779-103">ICorDebugProcess5::EnumerateGCReferences Method</span></span>

<span data-ttu-id="9e779-104">Возвращает перечислитель для всех объектов, которые должны быть собраны в процессе сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="9e779-104">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e779-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e779-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e779-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9e779-106">Parameters</span></span>  

 `enumerateWeakReferences`  
 <span data-ttu-id="9e779-107">окне Логическое значение, указывающее, будут ли также перечисляться слабые ссылки.</span><span class="sxs-lookup"><span data-stu-id="9e779-107">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="9e779-108">Если `enumerateWeakReferences` имеет значение `true` , `ppEnum` перечислитель включает как строгие ссылки, так и слабые ссылки.</span><span class="sxs-lookup"><span data-stu-id="9e779-108">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="9e779-109">Если `enumerateWeakReferences` имеет значение `false` , перечислитель включает только строгие ссылки.</span><span class="sxs-lookup"><span data-stu-id="9e779-109">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="9e779-110">заполняет Указатель на адрес [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) , который является перечислителем для объектов, которые должны быть собраны в мусор.</span><span class="sxs-lookup"><span data-stu-id="9e779-110">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e779-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e779-111">Remarks</span></span>  

 <span data-ttu-id="9e779-112">Этот метод предоставляет способ определения полной цепочки корневых объектов для любого управляемого объекта в процессе и может использоваться для определения причины, по которой объект остается в рабочем состоянии.</span><span class="sxs-lookup"><span data-stu-id="9e779-112">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e779-113">Требования</span><span class="sxs-lookup"><span data-stu-id="9e779-113">Requirements</span></span>  

 <span data-ttu-id="9e779-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e779-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e779-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e779-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e779-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e779-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e779-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e779-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e779-118">См. также</span><span class="sxs-lookup"><span data-stu-id="9e779-118">See also</span></span>

- [<span data-ttu-id="9e779-119">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="9e779-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="9e779-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9e779-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
