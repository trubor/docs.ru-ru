---
description: 'Дополнительные сведения о методе: ICorDebugEval2:: Креатевалуефортипе'
title: Метод ICorDebugEval2::CreateValueForType
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 2a8cd129d6194a4870817eb64b79606c395cb055
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693919"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="ec862-103">Метод ICorDebugEval2::CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="ec862-103">ICorDebugEval2::CreateValueForType Method</span></span>

<span data-ttu-id="ec862-104">Возвращает указатель на новый объект ICorDebugValue указанного типа с начальным значением нуль или null.</span><span class="sxs-lookup"><span data-stu-id="ec862-104">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec862-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec862-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec862-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ec862-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="ec862-107">окне Указатель на объект ICorDebugType, представляющий тип.</span><span class="sxs-lookup"><span data-stu-id="ec862-107">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ec862-108">заполняет Указатель на адрес `ICorDebugValue` объекта, представляющий значение.</span><span class="sxs-lookup"><span data-stu-id="ec862-108">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec862-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ec862-109">Remarks</span></span>  

 <span data-ttu-id="ec862-110">`CreateValueForType` обобщает [ICorDebugEval:: креатевалуе](icordebugeval-createvalue-method.md) , позволяя указать произвольный тип объекта, включая сконструированные типы, такие как `List<int>` .</span><span class="sxs-lookup"><span data-stu-id="ec862-110">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="ec862-111">Единственная цель этого метода — создать значение, которое может быть передано в вычисление функции.</span><span class="sxs-lookup"><span data-stu-id="ec862-111">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="ec862-112">Тип должен быть классом или типом значения.</span><span class="sxs-lookup"><span data-stu-id="ec862-112">The type must be a class or a value type.</span></span> <span data-ttu-id="ec862-113">Этот метод нельзя использовать для создания значений массива или строковых значений.</span><span class="sxs-lookup"><span data-stu-id="ec862-113">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec862-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ec862-114">Requirements</span></span>  

 <span data-ttu-id="ec862-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec862-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec862-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec862-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec862-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec862-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec862-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec862-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
