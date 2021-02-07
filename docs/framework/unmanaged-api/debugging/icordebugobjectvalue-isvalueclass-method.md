---
description: 'Дополнительные сведения о методе: ICorDebugObjectValue:: IsValueClass'
title: Метод ICorDebugObjectValue::IsValueClass
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
ms.openlocfilehash: bf3ce94a06092209507fd1ff737e09a77b5d0c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728929"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="f03a7-103">Метод ICorDebugObjectValue::IsValueClass</span><span class="sxs-lookup"><span data-stu-id="f03a7-103">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="f03a7-104">Возвращает значение, указывающее, является ли значение этого объекта типом значения.</span><span class="sxs-lookup"><span data-stu-id="f03a7-104">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f03a7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f03a7-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f03a7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f03a7-106">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="f03a7-107">заполняет Указатель на логическое значение, равное, `true` Если значение объекта, представленное этим "ICorDebugObjectValue", является типом значения, а не ссылочным типом; в противном случае `pbIsValueClass` — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="f03a7-107">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f03a7-108">Требования</span><span class="sxs-lookup"><span data-stu-id="f03a7-108">Requirements</span></span>  

 <span data-ttu-id="f03a7-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f03a7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f03a7-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f03a7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f03a7-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f03a7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f03a7-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f03a7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03a7-113">См. также</span><span class="sxs-lookup"><span data-stu-id="f03a7-113">See also</span></span>
