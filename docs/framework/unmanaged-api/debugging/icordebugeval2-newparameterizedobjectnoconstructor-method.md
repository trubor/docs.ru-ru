---
description: 'Дополнительные сведения о методе: ICorDebugEval2:: Невпараметеризедобжектноконструктор'
title: Метод ICorDebugEval2::NewParameterizedObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 8300378facb38714b50d6507b19876b8721c6229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693594"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="65264-103">Метод ICorDebugEval2::NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="65264-103">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="65264-104">Создает новый объект параметризованного типа указанного класса без попытки вызова метода конструктора.</span><span class="sxs-lookup"><span data-stu-id="65264-104">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65264-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65264-105">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65264-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="65264-106">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="65264-107">окне Указатель на объект ICorDebugClass, представляющий класс объекта, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="65264-107">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="65264-108">окне Число переданных аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="65264-108">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="65264-109">окне Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий аргумент типа для объекта, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="65264-109">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65264-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="65264-110">Remarks</span></span>  

 <span data-ttu-id="65264-111">`NewParameterizedObjectNoConstructor`Метод завершится ошибкой, если передается неверное число аргументов типа или неправильные типы аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="65264-111">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65264-112">Требования</span><span class="sxs-lookup"><span data-stu-id="65264-112">Requirements</span></span>  

 <span data-ttu-id="65264-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65264-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65264-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65264-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65264-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65264-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65264-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65264-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
