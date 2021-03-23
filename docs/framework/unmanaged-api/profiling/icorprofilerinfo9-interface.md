---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo9'
title: Интерфейс ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 44e3d694b426f87ee4e4bc12181f46322b0d246f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805679"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="048df-103">Интерфейс ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="048df-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="048df-104">Подкласс [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , предоставляющий методы для запроса сведений о функциях с несколькими версиями машинного кода.</span><span class="sxs-lookup"><span data-stu-id="048df-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="048df-105">Методы</span><span class="sxs-lookup"><span data-stu-id="048df-105">Methods</span></span>  

| <span data-ttu-id="048df-106">Метод</span><span class="sxs-lookup"><span data-stu-id="048df-106">Method</span></span>|<span data-ttu-id="048df-107">Описание</span><span class="sxs-lookup"><span data-stu-id="048df-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="048df-108">Метод GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="048df-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="048df-109">При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют.</span><span class="sxs-lookup"><span data-stu-id="048df-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="048df-110">Метод GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="048df-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="048df-111">С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода.</span><span class="sxs-lookup"><span data-stu-id="048df-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="048df-112">Метод GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="048df-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="048df-113">При наличии начального адреса машинного кода возвращает блоки виртуальной памяти, в которых хранится этот код.</span><span class="sxs-lookup"><span data-stu-id="048df-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="048df-114">Требования</span><span class="sxs-lookup"><span data-stu-id="048df-114">Requirements</span></span>  

<span data-ttu-id="048df-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="048df-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="048df-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="048df-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="048df-117">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048df-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="048df-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="048df-118">See also</span></span>

- [<span data-ttu-id="048df-119">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="048df-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
