---
description: 'Дополнительные сведения о методе ICorDebugType:: Жетфирсттипепараметер'
title: Метод ICorDebugType::GetFirstTypeParameter
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4c37217f34f80c916d618d88e4917eab794a1d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658286"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="6c9a1-103">Метод ICorDebugType::GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="6c9a1-103">ICorDebugType::GetFirstTypeParameter Method</span></span>

<span data-ttu-id="6c9a1-104">Возвращает указатель интерфейса на объект ICorDebugType, представляющий первый <xref:System.Type> параметр типа, представленного этим объектом `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="6c9a1-104">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c9a1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9a1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6c9a1-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="6c9a1-107">заполняет Указатель на адрес `ICorDebugType` объекта, представляющий первый параметр.</span><span class="sxs-lookup"><span data-stu-id="6c9a1-107">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9a1-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c9a1-108">Remarks</span></span>  

 <span data-ttu-id="6c9a1-109">`GetFirstTypeParameter` может вызываться в случаях, когда дополнительные сведения о типе в большинстве случаев входят в один параметр типа.</span><span class="sxs-lookup"><span data-stu-id="6c9a1-109">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="6c9a1-110">В частности, его можно использовать, если тип является ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF или ELEMENT_TYPE_PTR, как показано в методе [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9a1-110">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9a1-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6c9a1-111">Requirements</span></span>  

 <span data-ttu-id="6c9a1-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9a1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9a1-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c9a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c9a1-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9a1-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
