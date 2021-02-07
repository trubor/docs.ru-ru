---
description: 'Дополнительные сведения о: интерфейс ICorDebugClass2'
title: Интерфейс ICorDebugClass2
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 80aa8e59ccc774141e7fcea130d1fc6a38fa37da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711478"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="d3309-103">Интерфейс ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="d3309-103">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="d3309-104">Представляет универсальный класс или класс параметром метода типа <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d3309-104">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d3309-105">Этот интерфейс расширяет [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d3309-105">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3309-106">Методы</span><span class="sxs-lookup"><span data-stu-id="d3309-106">Methods</span></span>  
  
|<span data-ttu-id="d3309-107">Метод</span><span class="sxs-lookup"><span data-stu-id="d3309-107">Method</span></span>|<span data-ttu-id="d3309-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d3309-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3309-109">Метод GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="d3309-109">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="d3309-110">Возвращает объявление типа для этого класса.</span><span class="sxs-lookup"><span data-stu-id="d3309-110">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="d3309-111">Метод SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="d3309-111">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="d3309-112">Для каждого метода этого класса задает значение, указывающее, является ли метод определяемым пользователем кодом.</span><span class="sxs-lookup"><span data-stu-id="d3309-112">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3309-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="d3309-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3309-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="d3309-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3309-115">Требования</span><span class="sxs-lookup"><span data-stu-id="d3309-115">Requirements</span></span>  

 <span data-ttu-id="d3309-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3309-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3309-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3309-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3309-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3309-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3309-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3309-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3309-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d3309-120">See also</span></span>

- [<span data-ttu-id="d3309-121">Интерфейс ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="d3309-121">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="d3309-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d3309-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
