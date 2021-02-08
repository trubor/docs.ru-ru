---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome::/Register'
title: 'Метод ICorDebugVariableHome::'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: c394d455048cf7451b8320ed72a6aa7adfb3518e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790663"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="ba822-103">Метод ICorDebugVariableHome::</span><span class="sxs-lookup"><span data-stu-id="ba822-103">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="ba822-104">Возвращает регистр, содержащий переменную с типом расположения `VLT_REGISTER` , и базовый регистр для переменной с типом расположения `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="ba822-104">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba822-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba822-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba822-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ba822-106">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="ba822-107">заполняет Значение перечисления CorDebugRegister, указывающее регистр для переменной с типом расположения `VLT_REGISTER` и базовый регистр для переменной с типом расположения `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="ba822-107">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba822-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ba822-108">Return Value</span></span>  

 <span data-ttu-id="ba822-109">Метод возвращает следующие значения:</span><span class="sxs-lookup"><span data-stu-id="ba822-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="ba822-110">Значение</span><span class="sxs-lookup"><span data-stu-id="ba822-110">Value</span></span>|<span data-ttu-id="ba822-111">Описание</span><span class="sxs-lookup"><span data-stu-id="ba822-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ba822-112">Переменная находится в регистре, указанном `pRegister` аргументом.</span><span class="sxs-lookup"><span data-stu-id="ba822-112">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ba822-113">Переменная не находится в регистре или расположении, относительно регистра.</span><span class="sxs-lookup"><span data-stu-id="ba822-113">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba822-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ba822-114">Requirements</span></span>  

 <span data-ttu-id="ba822-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba822-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba822-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba822-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba822-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba822-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba822-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba822-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba822-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ba822-119">See also</span></span>

- [<span data-ttu-id="ba822-120">Перечисление VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="ba822-120">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="ba822-121">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="ba822-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
