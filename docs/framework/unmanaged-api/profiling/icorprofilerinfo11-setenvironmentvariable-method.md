---
description: 'Дополнительные сведения о методе: ICorProfilerInfo11:: SetEnvironmentVariable'
title: 'Метод ICorProfilerInfo11:: SetEnvironmentVariable'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805612"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a><span data-ttu-id="a17e7-103">Метод ICorProfilerInfo11:: SetEnvironmentVariable</span><span class="sxs-lookup"><span data-stu-id="a17e7-103">ICorProfilerInfo11::SetEnvironmentVariable Method</span></span>

<span data-ttu-id="a17e7-104">Задает переменную среды в процессе.</span><span class="sxs-lookup"><span data-stu-id="a17e7-104">Sets an environment variable in the process.</span></span> <span data-ttu-id="a17e7-105">На платформах, отличных от Windows, среда выполнения сохраняет внутренний кэш переменных среды для обеспечения безопасности потоков.</span><span class="sxs-lookup"><span data-stu-id="a17e7-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="a17e7-106">Это означает, что если профилировщик вызывает `setenv` новую переменную среды, управляемый код, выполняющийся в процессе, не будет выбран.</span><span class="sxs-lookup"><span data-stu-id="a17e7-106">This means that if the profiler calls `setenv` the new environment variable will not be picked up by managed code running in the process.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="a17e7-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a17e7-107">Syntax</span></span>  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a><span data-ttu-id="a17e7-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a17e7-108">Parameters</span></span>

<span data-ttu-id="a17e7-109">`szName` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую имя заданной переменной среды.</span><span class="sxs-lookup"><span data-stu-id="a17e7-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to set.</span></span>

<span data-ttu-id="a17e7-110">`szValue` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую значение заданной переменной среды.</span><span class="sxs-lookup"><span data-stu-id="a17e7-110">`szValue` [in] A pointer to a null terminated wide character string containing the value of the environment variable to set.</span></span>

## <a name="requirements"></a><span data-ttu-id="a17e7-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a17e7-111">Requirements</span></span>  

<span data-ttu-id="a17e7-112">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a17e7-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="a17e7-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a17e7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a17e7-114">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17e7-114">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17e7-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a17e7-115">See also</span></span>

- [<span data-ttu-id="a17e7-116">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a17e7-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a17e7-117">Интерфейс ICorProfilerInfo11</span><span class="sxs-lookup"><span data-stu-id="a17e7-117">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)
