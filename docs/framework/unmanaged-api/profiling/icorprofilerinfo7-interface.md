---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo7'
title: Интерфейс ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 7a33472d5562ad57d38291c64f8da7021ae2fe91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737081"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="c1b51-103">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="c1b51-103">ICorProfilerInfo7 Interface</span></span>

<span data-ttu-id="c1b51-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="c1b51-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c1b51-105">Подкласс [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , предоставляющий метод для применения вновь заданных метаданных к модулю и предоставляющий доступ к потоку символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="c1b51-105">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1b51-106">Методы</span><span class="sxs-lookup"><span data-stu-id="c1b51-106">Methods</span></span>  
  
|<span data-ttu-id="c1b51-107">Метод</span><span class="sxs-lookup"><span data-stu-id="c1b51-107">Method</span></span>|<span data-ttu-id="c1b51-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c1b51-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1b51-109">Метод ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="c1b51-109">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="c1b51-110">Применяет метаданные, которые были недавно определены `IMetadataEmit::Define*` методами, к указанному модулю.</span><span class="sxs-lookup"><span data-stu-id="c1b51-110">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="c1b51-111">Метод GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="c1b51-111">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="c1b51-112">Возвращает длину потока символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="c1b51-112">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="c1b51-113">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="c1b51-113">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="c1b51-114">Считывает байты из потока символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="c1b51-114">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1b51-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c1b51-115">Requirements</span></span>  

 <span data-ttu-id="c1b51-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b51-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b51-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1b51-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1b51-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b51-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b51-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c1b51-119">See also</span></span>

- [<span data-ttu-id="c1b51-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c1b51-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
