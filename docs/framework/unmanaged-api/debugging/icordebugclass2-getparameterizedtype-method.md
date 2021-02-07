---
description: 'Дополнительные сведения о методе: ICorDebugClass2:: GetParameterizedType'
title: Метод ICorDebugClass2::GetParameterizedType
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 4810e10e88af9256a466579ee607c0ef314d984b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765042"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="4c411-103">Метод ICorDebugClass2::GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="4c411-103">ICorDebugClass2::GetParameterizedType Method</span></span>

<span data-ttu-id="4c411-104">Возвращает объявление типа для этого класса.</span><span class="sxs-lookup"><span data-stu-id="4c411-104">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c411-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c411-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c411-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4c411-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="4c411-107">окне Значение перечисления Корелементтипе, указывающее тип элемента для этого класса: задайте для этого параметра значение ELEMENT_TYPE_VALUETYPE, если этот ICorDebugClass2 представляет тип значения.</span><span class="sxs-lookup"><span data-stu-id="4c411-107">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="4c411-108">Присвойте этому параметру значение ELEMENT_TYPE_CLASS, если оно `ICorDebugClass2` представляет сложный тип.</span><span class="sxs-lookup"><span data-stu-id="4c411-108">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="4c411-109">окне Число параметров типа, если тип является универсальным.</span><span class="sxs-lookup"><span data-stu-id="4c411-109">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="4c411-110">Количество параметров типа (если таковое имеется) должно совпадать с числом, необходимым для класса.</span><span class="sxs-lookup"><span data-stu-id="4c411-110">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="4c411-111">окне Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий параметр типа.</span><span class="sxs-lookup"><span data-stu-id="4c411-111">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="4c411-112">Если класс не является универсальным, это значение равно null.</span><span class="sxs-lookup"><span data-stu-id="4c411-112">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="4c411-113">заполняет Указатель на адрес `ICorDebugType` объекта, который представляет объявление типа.</span><span class="sxs-lookup"><span data-stu-id="4c411-113">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="4c411-114">Этот объект эквивалентен <xref:System.Type> объекту в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="4c411-114">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c411-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c411-115">Remarks</span></span>  

 <span data-ttu-id="4c411-116">Если класс не является универсальным, то есть если он не имеет параметров типа, `GetParameterizedType` просто получает объект типа среды выполнения, соответствующий классу.</span><span class="sxs-lookup"><span data-stu-id="4c411-116">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="4c411-117">`elementType`Для параметра необходимо задать правильный тип элемента для класса: ELEMENT_TYPE_VALUETYPE, если класс является типом значения; в противном случае — ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="4c411-117">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="4c411-118">Если класс принимает параметры типа (например, `ArrayList<T>` ), можно использовать `GetParameterizedType` для создания объекта типа для экземпляра такого типа, как `ArrayList<int>` .</span><span class="sxs-lookup"><span data-stu-id="4c411-118">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="4c411-119">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="4c411-119">Background Information</span></span>  

 <span data-ttu-id="4c411-120">В платформа .NET Framework версиях 1,0 и 1,1 каждый тип в метаданных можно напрямую сопоставить с типом в выполняемом процессе.</span><span class="sxs-lookup"><span data-stu-id="4c411-120">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="4c411-121">Таким словами, тип метаданных и тип среды выполнения имеют одно представление в выполняющемся процессе.</span><span class="sxs-lookup"><span data-stu-id="4c411-121">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="4c411-122">Однако один универсальный тип в метаданных может быть сопоставлен с множеством различных экземпляров типа в выполняющемся процессе.</span><span class="sxs-lookup"><span data-stu-id="4c411-122">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="4c411-123">Например, тип метаданных `SortedList<K,V>` может сопоставляться с `SortedList<String, EmployeeRecord>` , `SortedList<Int32, String>` , `SortedList<String,Array<Int32>>` и т. д.</span><span class="sxs-lookup"><span data-stu-id="4c411-123">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="4c411-124">Таким образом, необходим способ для управления созданием экземпляров типа.</span><span class="sxs-lookup"><span data-stu-id="4c411-124">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="4c411-125">В платформа .NET Framework версии 2,0 появился `ICorDebugType` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4c411-125">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="4c411-126">Для универсального типа `ICorDebugClass` объект или представляет тип, не являющийся `ICorDebugClass2` экземпляром ( `SortedList<K,V>` ), а `ICorDebugType` объект представляет различные экземпляры типов.</span><span class="sxs-lookup"><span data-stu-id="4c411-126">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="4c411-127">При наличии `ICorDebugClass` `ICorDebugClass2` объекта или можно создать `ICorDebugType` объект для любого экземпляра, вызвав `ICorDebugClass2::GetParameterizedType` метод.</span><span class="sxs-lookup"><span data-stu-id="4c411-127">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="4c411-128">Можно также создать `ICorDebugType` объект для простого типа, например Int32, или для неуниверсального типа.</span><span class="sxs-lookup"><span data-stu-id="4c411-128">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="4c411-129">Введение `ICorDebugType` объекта, представляющего представление времени выполнения типа, оказывает воздействие на весь интерфейс API.</span><span class="sxs-lookup"><span data-stu-id="4c411-129">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="4c411-130">Функции, которые ранее принимали `ICorDebugClass` `ICorDebugClass2` объект или или даже `CorElementType` значение, обобщены для получения `ICorDebugType` объекта.</span><span class="sxs-lookup"><span data-stu-id="4c411-130">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c411-131">Требования</span><span class="sxs-lookup"><span data-stu-id="4c411-131">Requirements</span></span>  

 <span data-ttu-id="4c411-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c411-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c411-133">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c411-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c411-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c411-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c411-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c411-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
