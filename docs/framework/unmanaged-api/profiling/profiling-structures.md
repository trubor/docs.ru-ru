---
description: 'Дополнительные сведения: Профилирование структур'
title: Структуры профилирования
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 176830cac519f22864ba004b176cb575d80e50e2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760240"
---
# <a name="profiling-structures"></a><span data-ttu-id="7642d-103">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="7642d-103">Profiling Structures</span></span>

<span data-ttu-id="7642d-104">В этом разделе описаны неуправляемые структуры, которые использует API профилирования.</span><span class="sxs-lookup"><span data-stu-id="7642d-104">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7642d-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7642d-105">In This Section</span></span>  

 [<span data-ttu-id="7642d-106">Структура COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="7642d-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="7642d-107">Обеспечивает среду CLR информацией о ссылке на сборку, которую ей следует учитывать при выполнении обхода замыкания.</span><span class="sxs-lookup"><span data-stu-id="7642d-107">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="7642d-108">Структура COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="7642d-108">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="7642d-109">Представляет один непрерывный блок машинного кода, хранящийся в памяти.</span><span class="sxs-lookup"><span data-stu-id="7642d-109">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="7642d-110">Структура COR_PRF_EX_CLAUSE_INFO</span><span class="sxs-lookup"><span data-stu-id="7642d-110">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="7642d-111">Хранит сведения об определенном экземпляре исключительного предложения и связанном с ним кадре.</span><span class="sxs-lookup"><span data-stu-id="7642d-111">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="7642d-112">Структура COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="7642d-112">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="7642d-113">Выдает уникальное представление функции, объединяя ее идентификатор с идентификатором перекомпилированной версии этой функции.</span><span class="sxs-lookup"><span data-stu-id="7642d-113">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="7642d-114">Структура COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="7642d-114">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="7642d-115">Представляет аргументы функции слева направо.</span><span class="sxs-lookup"><span data-stu-id="7642d-115">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="7642d-116">Структура COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="7642d-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="7642d-117">Представляет блок аргументов функции, которые сохраняются в памяти последовательно слева направо.</span><span class="sxs-lookup"><span data-stu-id="7642d-117">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="7642d-118">Структура COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="7642d-118">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="7642d-119">Описывает диапазон (т. е., блок) памяти, который занимается сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="7642d-119">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  

 <span data-ttu-id="7642d-120">[Структура COR_PRF_EVENTPIPE_PROVIDER_CONFIG](cor-prf-eventpipe-provider-config-structure.md) Описание полей, необходимых для настройки поставщика Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="7642d-120">[COR_PRF_EVENTPIPE_PROVIDER_CONFIG Structure](cor-prf-eventpipe-provider-config-structure.md) Describes the fields necessary to configure an EventPipe provider.</span></span>

 <span data-ttu-id="7642d-121">[Структура COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) Описывает имя и тип параметра для события Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="7642d-121">[COR_PRF_EVENTPIPE_PARAM_DESC Structure](cor-prf-eventpipe-param-desc-structure.md) Describes the parameter name and type for an EventPipe event.</span></span>

 <span data-ttu-id="7642d-122">[Структура COR_PRF_EVENT_DATA](cor-prf-event-data-structure.md) Описывает данные события для записываемого события Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="7642d-122">[COR_PRF_EVENT_DATA Structure](cor-prf-event-data-structure.md) Describes the event data for an EventPipe event being written.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="7642d-123">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="7642d-123">Related Sections</span></span>  

 <span data-ttu-id="7642d-124">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="7642d-124">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="7642d-125">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="7642d-125">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="7642d-126">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="7642d-126">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="7642d-127">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="7642d-127">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="7642d-128">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="7642d-128">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="7642d-129">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="7642d-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
