---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo8'
title: Интерфейс ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4538c9d314283c67ab0bfe6af3f3768062cffda4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646547"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="e1615-103">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="e1615-103">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="e1615-104">Подкласс [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , предоставляющий методы для запроса сведений о динамических методах.</span><span class="sxs-lookup"><span data-stu-id="e1615-104">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="e1615-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e1615-105">Methods</span></span>  

| <span data-ttu-id="e1615-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e1615-106">Method</span></span>|<span data-ttu-id="e1615-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e1615-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="e1615-108">Метод IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="e1615-108">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="e1615-109">Определяет, имеет ли функция связанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="e1615-109">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="e1615-110">Метод GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="e1615-110">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="e1615-111">Сопоставляет указатель инструкции управляемого кода с FunctionID.</span><span class="sxs-lookup"><span data-stu-id="e1615-111">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="e1615-112">Этот метод работает как с динамическими, так и с нединамическими методами.</span><span class="sxs-lookup"><span data-stu-id="e1615-112">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="e1615-113">Метод GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="e1615-113">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="e1615-114">Извлекает сведения о динамических методах.</span><span class="sxs-lookup"><span data-stu-id="e1615-114">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e1615-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e1615-115">Requirements</span></span>  

<span data-ttu-id="e1615-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1615-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e1615-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1615-117">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="e1615-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e1615-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e1615-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e1615-119">See also</span></span>

- [<span data-ttu-id="e1615-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e1615-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
