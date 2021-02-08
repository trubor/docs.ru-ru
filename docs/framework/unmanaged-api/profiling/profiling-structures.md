---
description: 'Дополнительные сведения: Профилирование структур'
title: Структуры профилирования
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 7a76c49aaa301ba45c41fb2eb3f7770539dcc6c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798892"
---
# <a name="profiling-structures"></a><span data-ttu-id="d2547-103">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="d2547-103">Profiling Structures</span></span>

<span data-ttu-id="d2547-104">В этом разделе описаны неуправляемые структуры, которые использует API профилирования.</span><span class="sxs-lookup"><span data-stu-id="d2547-104">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2547-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d2547-105">In This Section</span></span>  

 [<span data-ttu-id="d2547-106">Структура COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="d2547-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="d2547-107">Обеспечивает среду CLR информацией о ссылке на сборку, которую ей следует учитывать при выполнении обхода замыкания.</span><span class="sxs-lookup"><span data-stu-id="d2547-107">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="d2547-108">Структура COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="d2547-108">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="d2547-109">Представляет один непрерывный блок машинного кода, хранящийся в памяти.</span><span class="sxs-lookup"><span data-stu-id="d2547-109">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="d2547-110">Структура COR_PRF_EX_CLAUSE_INFO</span><span class="sxs-lookup"><span data-stu-id="d2547-110">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="d2547-111">Хранит сведения об определенном экземпляре исключительного предложения и связанном с ним кадре.</span><span class="sxs-lookup"><span data-stu-id="d2547-111">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="d2547-112">Структура COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="d2547-112">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="d2547-113">Выдает уникальное представление функции, объединяя ее идентификатор с идентификатором перекомпилированной версии этой функции.</span><span class="sxs-lookup"><span data-stu-id="d2547-113">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="d2547-114">Структура COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="d2547-114">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="d2547-115">Представляет аргументы функции слева направо.</span><span class="sxs-lookup"><span data-stu-id="d2547-115">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="d2547-116">Структура COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="d2547-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="d2547-117">Представляет блок аргументов функции, которые сохраняются в памяти последовательно слева направо.</span><span class="sxs-lookup"><span data-stu-id="d2547-117">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="d2547-118">Структура COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="d2547-118">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="d2547-119">Описывает диапазон (т. е., блок) памяти, который занимается сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="d2547-119">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d2547-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d2547-120">Related Sections</span></span>  

 <span data-ttu-id="d2547-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="d2547-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="d2547-122">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="d2547-122">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="d2547-123">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="d2547-123">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="d2547-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="d2547-124">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="d2547-125">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="d2547-125">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="d2547-126">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="d2547-126">Profiling Enumerations</span></span>](profiling-enumerations.md)
