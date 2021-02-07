---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain2:: Жетаррайорпоинтертипе'
title: Метод ICorDebugAppDomain2::GetArrayOrPointerType
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754229"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="4a2d9-103">Метод ICorDebugAppDomain2::GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="4a2d9-103">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>

<span data-ttu-id="4a2d9-104">Возвращает массив указанного типа или указатель или ссылку на указанный тип.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-104">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2d9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a2d9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a2d9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a2d9-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="4a2d9-107">окне Значение перечисления Корелементтипе, которое указывает базовый собственный тип (массив, указатель или ссылка), который необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-107">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="4a2d9-108">окне Ранг (то есть количество измерений) массива.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-108">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="4a2d9-109">Это значение должно быть равно 0 `elementType` , если указывает тип указателя или ссылки.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-109">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="4a2d9-110">окне Указатель на объект ICorDebugType, представляющий тип создаваемого массива, указателя или ссылки.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-110">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="4a2d9-111">заполняет Указатель на адрес `ICorDebugType` объекта, представляющий сконструированный массив, тип указателя или ссылочный тип.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-111">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a2d9-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a2d9-112">Remarks</span></span>  

 <span data-ttu-id="4a2d9-113">Значение *ElementType* должно быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="4a2d9-113">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="4a2d9-114">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="4a2d9-114">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="4a2d9-115">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="4a2d9-115">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="4a2d9-116">ELEMENT_TYPE_ARRAY или ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="4a2d9-116">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="4a2d9-117">Если значение *ElementType* равно ELEMENT_TYPE_PTR или ELEMENT_TYPE_BYREF, *нранк* должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="4a2d9-117">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a2d9-118">Требования</span><span class="sxs-lookup"><span data-stu-id="4a2d9-118">Requirements</span></span>  

 <span data-ttu-id="4a2d9-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a2d9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a2d9-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a2d9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a2d9-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a2d9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a2d9-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a2d9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
