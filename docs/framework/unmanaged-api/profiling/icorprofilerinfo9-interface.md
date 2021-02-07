---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo9'
title: Интерфейс ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 954cb16d2b789359693f6a8fa3e0f6e19ad19b3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736912"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="cf42c-103">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="cf42c-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="cf42c-104">Подкласс [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , предоставляющий методы для запроса сведений о функциях с несколькими версиями машинного кода.</span><span class="sxs-lookup"><span data-stu-id="cf42c-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="cf42c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="cf42c-105">Methods</span></span>  

| <span data-ttu-id="cf42c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="cf42c-106">Method</span></span>|<span data-ttu-id="cf42c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cf42c-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="cf42c-108">Метод GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="cf42c-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="cf42c-109">При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют.</span><span class="sxs-lookup"><span data-stu-id="cf42c-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="cf42c-110">Метод GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="cf42c-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="cf42c-111">С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода.</span><span class="sxs-lookup"><span data-stu-id="cf42c-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="cf42c-112">Метод GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="cf42c-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="cf42c-113">При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код.</span><span class="sxs-lookup"><span data-stu-id="cf42c-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="cf42c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="cf42c-114">Requirements</span></span>  

<span data-ttu-id="cf42c-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="cf42c-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="cf42c-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf42c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="cf42c-117">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf42c-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cf42c-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cf42c-118">See also</span></span>

- [<span data-ttu-id="cf42c-119">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="cf42c-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
