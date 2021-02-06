---
description: 'Дополнительные сведения о методе ICorDebugType:: Енумератетипепараметерс'
title: Метод ICorDebugType::EnumerateTypeParameters
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: 5189394cbb39cd133ebce494107f4ca65660bb5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658416"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="12a2a-103">Метод ICorDebugType::EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="12a2a-103">ICorDebugType::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="12a2a-104">Возвращает указатель интерфейса на ICorDebugTypeEnum, содержащий <xref:System.Type> Параметры класса, на который ссылается этот объект ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="12a2a-104">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a2a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12a2a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12a2a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="12a2a-106">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="12a2a-107">заполняет Указатель на адрес объекта `ICorDebugTypeEnum` , который содержит параметры типа.</span><span class="sxs-lookup"><span data-stu-id="12a2a-107">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12a2a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="12a2a-108">Remarks</span></span>  

 <span data-ttu-id="12a2a-109">Можно использовать, `EnumerateTypeParameters` Если значение корелементтипе, возвращаемое методом [ICorDebugType:: GetType](icordebugtype-gettype-method.md) , равно ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR или ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="12a2a-109">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="12a2a-110">Количество параметров и их порядок зависит от типа:</span><span class="sxs-lookup"><span data-stu-id="12a2a-110">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="12a2a-111">ELEMENT_TYPE_CLASS или ELEMENT_TYPE_VALUETYPE: количество параметров типа, содержащихся в, `ICorDebugTypeEnum` которые возвращает этот метод, будет зависеть от числа формальных параметров типа для соответствующего класса.</span><span class="sxs-lookup"><span data-stu-id="12a2a-111">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="12a2a-112">Например, если тип — `class Dict<String,int32>` , то `EnumerateTypeParameters` возвратит объект `ICorDebugTypeEnum` , содержащий объекты, представляющие `String` и `int32` в последовательности.</span><span class="sxs-lookup"><span data-stu-id="12a2a-112">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="12a2a-113">ELEMENT_TYPE_FNPTR: количество параметров типа, содержащихся в, `ICorDebugTypeEnum` будет больше, чем число аргументов, принимаемых функцией.</span><span class="sxs-lookup"><span data-stu-id="12a2a-113">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="12a2a-114">Первый параметр типа, содержащийся в, `ICorDebugTypeEnum` является типом возвращаемого значения для функции, а последующие параметры типа — параметрами функции.</span><span class="sxs-lookup"><span data-stu-id="12a2a-114">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="12a2a-115">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF или ELEMENT_TYPE_PTR: будет возвращен один параметр типа.</span><span class="sxs-lookup"><span data-stu-id="12a2a-115">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="12a2a-116">Например, если тип является массивом типа, таким как `int32[]` , `EnumerateTypeParameters` возвращает объект `ICorDebugTypeEnum` , содержащий объект, представляющий `int32` .</span><span class="sxs-lookup"><span data-stu-id="12a2a-116">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a2a-117">Требования</span><span class="sxs-lookup"><span data-stu-id="12a2a-117">Requirements</span></span>  

 <span data-ttu-id="12a2a-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a2a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a2a-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12a2a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12a2a-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12a2a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12a2a-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a2a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
