---
description: 'Дополнительные сведения о методе: ICorDebugEval:: Креатевалуе'
title: Метод ICorDebugEval::CreateValue
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: f5ea753b5b95c68136e7b799aad88eee5845ea82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694166"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="77dab-103">Метод ICorDebugEval::CreateValue</span><span class="sxs-lookup"><span data-stu-id="77dab-103">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="77dab-104">Создает значение указанного типа с начальным значением нуль или null.</span><span class="sxs-lookup"><span data-stu-id="77dab-104">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="77dab-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="77dab-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="77dab-106">Вместо этого используйте [ICorDebugEval2:: креатевалуефортипе](icordebugeval2-createvaluefortype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77dab-106">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dab-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77dab-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77dab-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="77dab-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="77dab-109">окне Значение перечисления [корелементтипе](../metadata/corelementtype-enumeration.md) , указывающее тип значения.</span><span class="sxs-lookup"><span data-stu-id="77dab-109">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="77dab-110">окне Указатель на объект [ICorDebugClass](icordebugclass-interface.md) , указывающий класс значения, если тип не является типом-примитивом.</span><span class="sxs-lookup"><span data-stu-id="77dab-110">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="77dab-111">заполняет Указатель на адрес объекта "ICorDebugValue", представляющего значение.</span><span class="sxs-lookup"><span data-stu-id="77dab-111">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77dab-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="77dab-112">Remarks</span></span>  

 <span data-ttu-id="77dab-113">`CreateValue` создает `ICorDebugValue` объект данного типа для единственной цели использования в вычислении функции.</span><span class="sxs-lookup"><span data-stu-id="77dab-113">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="77dab-114">Этот объект значения можно использовать для передачи пользовательских констант в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="77dab-114">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="77dab-115">Если тип значения является типом-примитивом, его начальное значение равно нулю или null.</span><span class="sxs-lookup"><span data-stu-id="77dab-115">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="77dab-116">Используйте [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) , чтобы задать значение типа-примитива.</span><span class="sxs-lookup"><span data-stu-id="77dab-116">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="77dab-117">Если значение `elementType` равно ELEMENT_TYPE_CLASS, вы получаете "ICorDebugReferenceValue" (возвращаемый в), `ppValue` представляющий ссылку на пустой объект.</span><span class="sxs-lookup"><span data-stu-id="77dab-117">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="77dab-118">Этот объект можно использовать для передачи значения NULL в вычисление функции, имеющей параметры ссылки на объект.</span><span class="sxs-lookup"><span data-stu-id="77dab-118">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="77dab-119">Нельзя задать значение, которое `ICorDebugValue` всегда будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="77dab-119">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77dab-120">Требования</span><span class="sxs-lookup"><span data-stu-id="77dab-120">Requirements</span></span>  

 <span data-ttu-id="77dab-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77dab-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77dab-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77dab-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77dab-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77dab-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77dab-124">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="77dab-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77dab-125">См. также</span><span class="sxs-lookup"><span data-stu-id="77dab-125">See also</span></span>

- [<span data-ttu-id="77dab-126">Метод CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="77dab-126">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="77dab-127">Интерфейс ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="77dab-127">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
