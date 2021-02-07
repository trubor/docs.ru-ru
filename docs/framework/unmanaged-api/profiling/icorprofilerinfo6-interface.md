---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo6'
title: Интерфейс ICorProfilerInfo6
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: c093930b102ca99a8524e6d5d6129690f80a5353
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737159"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="5d745-103">Интерфейс ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="5d745-103">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="5d745-104">[Поддерживается в платформа .NET Framework 4,6 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="5d745-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="5d745-105">Подкласс [ICorProfilerInfo5](icorprofilerinfo5-interface.md) , предоставляющий перечислитель для всех методов, определенных в заданном модуле NGen, и встроенный метод.</span><span class="sxs-lookup"><span data-stu-id="5d745-105">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d745-106">Методы</span><span class="sxs-lookup"><span data-stu-id="5d745-106">Methods</span></span>  
  
|<span data-ttu-id="5d745-107">Метод</span><span class="sxs-lookup"><span data-stu-id="5d745-107">Method</span></span>|<span data-ttu-id="5d745-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5d745-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d745-109">Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="5d745-109">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="5d745-110">Возвращает перечислитель для всех методов, принадлежащих заданному модулю NGen и встроенных в тело данного метода.</span><span class="sxs-lookup"><span data-stu-id="5d745-110">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d745-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5d745-111">Requirements</span></span>  

 <span data-ttu-id="5d745-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d745-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d745-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d745-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d745-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d745-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d745-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5d745-115">See also</span></span>

- [<span data-ttu-id="5d745-116">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5d745-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
