---
description: 'Дополнительные сведения о методе: ICorProfilerInfo11:: GetEnvironmentVariable'
title: 'Метод ICorProfilerInfo11:: GetEnvironmentVariable'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805835"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a><span data-ttu-id="5487e-103">Метод ICorProfilerInfo11:: GetEnvironmentVariable</span><span class="sxs-lookup"><span data-stu-id="5487e-103">ICorProfilerInfo11::GetEnvironmentVariable Method</span></span>

<span data-ttu-id="5487e-104">Возвращает переменную среды из процесса.</span><span class="sxs-lookup"><span data-stu-id="5487e-104">Gets an environment variable from the process.</span></span> <span data-ttu-id="5487e-105">На платформах, отличных от Windows, среда выполнения сохраняет внутренний кэш переменных среды для обеспечения безопасности потоков.</span><span class="sxs-lookup"><span data-stu-id="5487e-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="5487e-106">Это означает, что вызов `getenv` не будет считывать новые или обновленные переменные среды, установленные управляемым кодом, который выполняется в процессе после запуска.</span><span class="sxs-lookup"><span data-stu-id="5487e-106">This means that calling `getenv` will not read any new or updated environment variables set by managed code running in the process after startup.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="5487e-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5487e-107">Syntax</span></span>  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="5487e-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="5487e-108">Parameters</span></span>

<span data-ttu-id="5487e-109">`szName` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую имя переменной среды для получения.</span><span class="sxs-lookup"><span data-stu-id="5487e-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to get.</span></span>

<span data-ttu-id="5487e-110">`cchValue` окне Длина в символах `szValue` .</span><span class="sxs-lookup"><span data-stu-id="5487e-110">`cchValue` [in] The length, in characters, of `szValue`.</span></span>

<span data-ttu-id="5487e-111">`pcchValue` заполняет Указатель на общую длину символов `szValue` .</span><span class="sxs-lookup"><span data-stu-id="5487e-111">`pcchValue` [out] A pointer to the total character length of `szValue`.</span></span>

<span data-ttu-id="5487e-112">`szValue` заполняет Вызывающий объект предоставил широкий буфер символов.</span><span class="sxs-lookup"><span data-stu-id="5487e-112">`szValue` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="5487e-113">Когда функция возвращает буфер, будет содержать значение переменной среды.</span><span class="sxs-lookup"><span data-stu-id="5487e-113">When the function returns the buffer will contain the value of the environment variable.</span></span>

## <a name="requirements"></a><span data-ttu-id="5487e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5487e-114">Requirements</span></span>  

<span data-ttu-id="5487e-115">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="5487e-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="5487e-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5487e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="5487e-117">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5487e-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5487e-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5487e-118">See also</span></span>

- [<span data-ttu-id="5487e-119">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5487e-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5487e-120">Интерфейс ICorProfilerInfo11</span><span class="sxs-lookup"><span data-stu-id="5487e-120">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)
