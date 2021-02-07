---
description: 'Дополнительные сведения о: интерфейс ICorDebugEval2'
title: Интерфейс ICorDebugEval2
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: 2c279335bdd30b8dc2698f348d9537443b236a45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693763"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="6d422-103">Интерфейс ICorDebugEval2</span><span class="sxs-lookup"><span data-stu-id="6d422-103">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="6d422-104">Расширяет "ICorDebugEval" для обеспечения поддержки универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="6d422-104">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d422-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6d422-105">Methods</span></span>  
  
|<span data-ttu-id="6d422-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6d422-106">Method</span></span>|<span data-ttu-id="6d422-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6d422-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d422-108">Метод CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="6d422-108">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="6d422-109">Настраивает вызов указанного "ICorDebugFunction", который может быть вложен в тип, конструктор которого принимает параметры типа или сам может принимать параметры типа.</span><span class="sxs-lookup"><span data-stu-id="6d422-109">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="6d422-110">Метод CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="6d422-110">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="6d422-111">Возвращает указатель на новый "ICorDebugValue" указанного типа с начальным значением NULL или нулем.</span><span class="sxs-lookup"><span data-stu-id="6d422-111">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="6d422-112">Метод NewParameterizedArray</span><span class="sxs-lookup"><span data-stu-id="6d422-112">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="6d422-113">Выделяет новый массив указанного типа элемента и измерений.</span><span class="sxs-lookup"><span data-stu-id="6d422-113">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="6d422-114">Метод NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="6d422-114">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="6d422-115">Создает новый объект параметризованного типа и вызывает метод конструктора объекта.</span><span class="sxs-lookup"><span data-stu-id="6d422-115">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="6d422-116">Метод NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="6d422-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="6d422-117">Создает новый объект параметризованного типа указанного класса без попытки вызова метода конструктора</span><span class="sxs-lookup"><span data-stu-id="6d422-117">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="6d422-118">Метод NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="6d422-118">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="6d422-119">Создает новую строку указанной длины с указанным содержимым.</span><span class="sxs-lookup"><span data-stu-id="6d422-119">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="6d422-120">Метод RudeAbort</span><span class="sxs-lookup"><span data-stu-id="6d422-120">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="6d422-121">Прерывает вычисление, выполняемое `ICorDebugEval2` в данный момент.</span><span class="sxs-lookup"><span data-stu-id="6d422-121">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d422-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d422-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d422-123">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="6d422-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d422-124">Требования</span><span class="sxs-lookup"><span data-stu-id="6d422-124">Requirements</span></span>  

 <span data-ttu-id="6d422-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d422-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d422-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d422-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d422-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d422-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d422-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d422-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d422-129">См. также</span><span class="sxs-lookup"><span data-stu-id="6d422-129">See also</span></span>

- [<span data-ttu-id="6d422-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6d422-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
