---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипежетпровидеринфо'
title: 'Метод ICorProfilerInfo12:: Евентпипежетпровидеринфо'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805705"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a><span data-ttu-id="14378-103">Метод ICorProfilerInfo12:: Евентпипежетпровидеринфо</span><span class="sxs-lookup"><span data-stu-id="14378-103">ICorProfilerInfo12::EventPipeGetProviderInfo Method</span></span>

<span data-ttu-id="14378-104">Создает поставщик Евентпипе, который профилировщик может использовать для записи событий для получения других прослушивателей Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="14378-104">Creates an EventPipe provider that the profiler can use to write events for other EventPipe listeners to receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="14378-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14378-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="14378-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="14378-106">Parameters</span></span>

<span data-ttu-id="14378-107">`provider` окне Идентификатор поставщика, для которого необходимо предоставить имя.</span><span class="sxs-lookup"><span data-stu-id="14378-107">`provider` [in] The ID of the provider to provide the name for.</span></span>

<span data-ttu-id="14378-108">`cchName` окне Размер (в символах) `providerName` .</span><span class="sxs-lookup"><span data-stu-id="14378-108">`cchName` [in] The size, in characters, of `providerName`.</span></span>

<span data-ttu-id="14378-109">`pcchName` заполняет Указатель на общую длину символов `providerName` .</span><span class="sxs-lookup"><span data-stu-id="14378-109">`pcchName` [out] A pointer to the total character length of `providerName`.</span></span>

<span data-ttu-id="14378-110">`providerName` заполняет Вызывающий объект предоставил широкий буфер символов.</span><span class="sxs-lookup"><span data-stu-id="14378-110">`providerName` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="14378-111">Когда функция возвращает буфер, будет содержать имя поставщика.</span><span class="sxs-lookup"><span data-stu-id="14378-111">When the function returns the buffer will contain the name of the provider.</span></span>

## <a name="requirements"></a><span data-ttu-id="14378-112">Требования</span><span class="sxs-lookup"><span data-stu-id="14378-112">Requirements</span></span>  

<span data-ttu-id="14378-113">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="14378-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="14378-114">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14378-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="14378-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="14378-115">See also</span></span>

- [<span data-ttu-id="14378-116">Общие сведения об EventPipe</span><span class="sxs-lookup"><span data-stu-id="14378-116">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="14378-117">Хорошо известные Евентпровидерс</span><span class="sxs-lookup"><span data-stu-id="14378-117">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="14378-118">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="14378-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="14378-119">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="14378-119">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="14378-120">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="14378-120">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
