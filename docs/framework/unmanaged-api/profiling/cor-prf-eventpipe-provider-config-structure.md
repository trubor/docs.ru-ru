---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG'
title: Перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PROVIDER_CONFIG
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2a7a5e720e9468b44e6504d24a3b9ad836e13693
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805848"
---
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a><span data-ttu-id="71a04-103">Перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG</span><span class="sxs-lookup"><span data-stu-id="71a04-103">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Enumeration</span></span>

<span data-ttu-id="71a04-104">Описание полей, необходимых для настройки поставщика Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="71a04-104">Describes the fields necessary to configure an EventPipe provider.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="71a04-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71a04-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a><span data-ttu-id="71a04-106">Участники</span><span class="sxs-lookup"><span data-stu-id="71a04-106">Members</span></span>  
  
|<span data-ttu-id="71a04-107">Член</span><span class="sxs-lookup"><span data-stu-id="71a04-107">Member</span></span>|<span data-ttu-id="71a04-108">Описание</span><span class="sxs-lookup"><span data-stu-id="71a04-108">Description</span></span>|  
|------------|-----------------|  
|`providerName`|<span data-ttu-id="71a04-109">Имя поставщика, который необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="71a04-109">The name of the provider to enable.</span></span>|  
|`keywords`|<span data-ttu-id="71a04-110">Ключевые слова, которые должны быть включены для поставщика.</span><span class="sxs-lookup"><span data-stu-id="71a04-110">The keywords to enable on the provider.</span></span>|  
|`loggingLevel`|<span data-ttu-id="71a04-111">Уровень, который должен быть включен для поставщика.</span><span class="sxs-lookup"><span data-stu-id="71a04-111">The level to enable on the provider.</span></span>|  
|`filterData`|<span data-ttu-id="71a04-112">Строка расширенных символов, содержащая FilterData, используемый при включении поставщика.</span><span class="sxs-lookup"><span data-stu-id="71a04-112">A wide character string containing the filterdata to use when enabling the provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71a04-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="71a04-113">Remarks</span></span>  

 <span data-ttu-id="71a04-114">`COR_PRF_EVENTPIPE_PROVIDER_CONFIG`Структура используется методом [ICorProfilerInfo12:: евентпипеаддпровидертосессион](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) для указания конфигурации поставщика, добавляемого в сеанс.</span><span class="sxs-lookup"><span data-stu-id="71a04-114">The `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` structure is used by the [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) method to indicate the configuration for the provider being added to the session.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="71a04-115">Требования</span><span class="sxs-lookup"><span data-stu-id="71a04-115">Requirements</span></span>  

<span data-ttu-id="71a04-116">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="71a04-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="71a04-117">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71a04-117">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="71a04-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="71a04-118">See also</span></span>

- [<span data-ttu-id="71a04-119">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="71a04-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="71a04-120">ICorProfilerInfo12:: Евентпипеаддпровидертосессион</span><span class="sxs-lookup"><span data-stu-id="71a04-120">ICorProfilerInfo12::EventPipeAddProviderToSession</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
