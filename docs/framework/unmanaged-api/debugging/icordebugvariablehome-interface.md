---
description: 'Дополнительные сведения о: интерфейс ICorDebugVariableHome'
title: Интерфейс ICorDebugVariableHome
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: a1dcc959ba9aeffc0e511dcd2f5bb15f58445139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790637"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="51f05-103">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="51f05-103">ICorDebugVariableHome Interface</span></span>

<span data-ttu-id="51f05-104">Представляет локальную переменную или аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="51f05-104">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51f05-105">Методы</span><span class="sxs-lookup"><span data-stu-id="51f05-105">Methods</span></span>  
  
|<span data-ttu-id="51f05-106">Метод</span><span class="sxs-lookup"><span data-stu-id="51f05-106">Method</span></span>|<span data-ttu-id="51f05-107">Описание</span><span class="sxs-lookup"><span data-stu-id="51f05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51f05-108">Метод GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="51f05-108">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="51f05-109">Возвращает индекс аргумента функции.</span><span class="sxs-lookup"><span data-stu-id="51f05-109">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="51f05-110">Метод GetCode</span><span class="sxs-lookup"><span data-stu-id="51f05-110">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="51f05-111">Возвращает экземпляр "ICorDebugCode", который содержит этот `ICorDebugVariableHome` объект.</span><span class="sxs-lookup"><span data-stu-id="51f05-111">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="51f05-112">Метод GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="51f05-112">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="51f05-113">Возвращает собственный диапазон, в котором эта переменная находится в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="51f05-113">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="51f05-114">Метод GetLocationType</span><span class="sxs-lookup"><span data-stu-id="51f05-114">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="51f05-115">Возвращает тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="51f05-115">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="51f05-116">Метод GetOffset</span><span class="sxs-lookup"><span data-stu-id="51f05-116">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="51f05-117">Возвращает смещение от базового регистра для переменной.</span><span class="sxs-lookup"><span data-stu-id="51f05-117">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="51f05-118">Метод GetRegister</span><span class="sxs-lookup"><span data-stu-id="51f05-118">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="51f05-119">Возвращает регистр, содержащий переменную с типом расположения `VLT_REGISTER` , и базовый регистр для переменной с типом расположения `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="51f05-119">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="51f05-120">Метод GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="51f05-120">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="51f05-121">Возвращает управляемый индекс в виде слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="51f05-121">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51f05-122">Пример</span><span class="sxs-lookup"><span data-stu-id="51f05-122">Example</span></span>  

 <span data-ttu-id="51f05-123">В следующем фрагменте кода используется объект [ICorDebugCode4](icordebugcode4-interface.md) с именем `pCode4` .</span><span class="sxs-lookup"><span data-stu-id="51f05-123">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="51f05-124">Требования</span><span class="sxs-lookup"><span data-stu-id="51f05-124">Requirements</span></span>  

 <span data-ttu-id="51f05-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51f05-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51f05-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51f05-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51f05-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51f05-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51f05-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51f05-128">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f05-129">См. также</span><span class="sxs-lookup"><span data-stu-id="51f05-129">See also</span></span>

- [<span data-ttu-id="51f05-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="51f05-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="51f05-131">Интерфейс ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="51f05-131">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
