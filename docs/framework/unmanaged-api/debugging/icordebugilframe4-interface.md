---
description: 'Дополнительные сведения о: интерфейс ICorDebugILFrame4'
title: Интерфейс ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: f2d29229f039509ed7799399f0d4d701e8cafba7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791209"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="aedde-103">Интерфейс ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="aedde-103">ICorDebugILFrame4 Interface</span></span>

<span data-ttu-id="aedde-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="aedde-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="aedde-105">Предоставляет методы, обеспечивающие доступ к локальным переменным и коду в кадре стека кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="aedde-105">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="aedde-106">Параметр показывает, имеет ли отладчик доступ к переменным и коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="aedde-106">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aedde-107">Методы</span><span class="sxs-lookup"><span data-stu-id="aedde-107">Methods</span></span>  
  
|<span data-ttu-id="aedde-108">Метод</span><span class="sxs-lookup"><span data-stu-id="aedde-108">Method</span></span>|<span data-ttu-id="aedde-109">Описание</span><span class="sxs-lookup"><span data-stu-id="aedde-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aedde-110">Метод EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="aedde-110">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="aedde-111">Возвращает список локальных переменных, доступных в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="aedde-111">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="aedde-112">Метод GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="aedde-112">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="aedde-113">Возвращает код, который выполняется этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="aedde-113">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="aedde-114">Метод GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="aedde-114">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="aedde-115">Возвращает значение локальной переменной в кадре промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="aedde-115">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aedde-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="aedde-116">Remarks</span></span>  

 <span data-ttu-id="aedde-117">Эти методы предоставляют функциональные возможности в дополнение к [возможностям,](icordebugframe-getcode-method.md)предоставляемым методами [енумерателокалвариаблес](icordebugilframe-enumeratelocalvariables-method.md), [жетлокалвариабле](icordebugilframe-getlocalvariable-method.md) и.</span><span class="sxs-lookup"><span data-stu-id="aedde-117">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="aedde-118">Каждый метод включает параметр `flags`, определяющий видимость дополнительных локальных переменных или кода, определенных ReJIT-запросом профилировщика.</span><span class="sxs-lookup"><span data-stu-id="aedde-118">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedde-119">Требования</span><span class="sxs-lookup"><span data-stu-id="aedde-119">Requirements</span></span>  

 <span data-ttu-id="aedde-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aedde-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedde-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aedde-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aedde-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aedde-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aedde-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedde-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedde-124">См. также</span><span class="sxs-lookup"><span data-stu-id="aedde-124">See also</span></span>

- [<span data-ttu-id="aedde-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="aedde-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="aedde-126">Отладка</span><span class="sxs-lookup"><span data-stu-id="aedde-126">Debugging</span></span>](index.md)
