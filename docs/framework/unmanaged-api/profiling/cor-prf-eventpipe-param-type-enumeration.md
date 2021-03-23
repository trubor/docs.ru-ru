---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_PARAM_TYPE'
title: Перечисление COR_PRF_EVENTPIPE_PARAM_TYPE
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805783"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a><span data-ttu-id="77836-103">Перечисление COR_PRF_EVENTPIPE_PARAM_TYPE</span><span class="sxs-lookup"><span data-stu-id="77836-103">COR_PRF_EVENTPIPE_PARAM_TYPE Enumeration</span></span>

<span data-ttu-id="77836-104">Описывает тип параметра для события Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="77836-104">Describes the type of a parameter for an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="77836-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77836-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a><span data-ttu-id="77836-106">Участники</span><span class="sxs-lookup"><span data-stu-id="77836-106">Members</span></span>  
  
|<span data-ttu-id="77836-107">Член</span><span class="sxs-lookup"><span data-stu-id="77836-107">Member</span></span>|<span data-ttu-id="77836-108">Описание</span><span class="sxs-lookup"><span data-stu-id="77836-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|<span data-ttu-id="77836-109">Тип параметра является самоописывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="77836-109">The parameter type is a self describing object.</span></span>|
|`COR_PRF_EVENTPIPE_BOOLEAN`|<span data-ttu-id="77836-110">Тип параметра — логическое значение.</span><span class="sxs-lookup"><span data-stu-id="77836-110">The parameter type is a boolean.</span></span>|
|`COR_PRF_EVENTPIPE_CHAR`|<span data-ttu-id="77836-111">Тип параметра является 16-разрядным расширенным символом.</span><span class="sxs-lookup"><span data-stu-id="77836-111">The parameter type is a 16 bit wide character.</span></span>|
|`COR_PRF_EVENTPIPE_SBYTE`|<span data-ttu-id="77836-112">Тип параметра — 8-разрядное целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="77836-112">The parameter type is a signed 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_BYTE`|<span data-ttu-id="77836-113">Тип параметра — 8-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="77836-113">The parameter type is an unsigned 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT16`|<span data-ttu-id="77836-114">Тип параметра представляет собой 16-разрядное целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="77836-114">The parameter type is a signed 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT16`|<span data-ttu-id="77836-115">Тип параметра представляет собой 16-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="77836-115">The parameter type is an unsigned 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT32`|<span data-ttu-id="77836-116">Тип параметра — это 32-разрядное целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="77836-116">The parameter type is a signed 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT32`|<span data-ttu-id="77836-117">Тип параметра — это 32-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="77836-117">The parameter type is an unsigned 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT64`|<span data-ttu-id="77836-118">Тип параметра — это 64-разрядное целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="77836-118">The parameter type is a signed 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT64`|<span data-ttu-id="77836-119">Тип параметра — это 64-разрядное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="77836-119">The parameter type is an unsigned 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_SINGLE`|<span data-ttu-id="77836-120">Тип параметра — 32-разрядное число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="77836-120">The parameter type is a 32 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DOUBLE`|<span data-ttu-id="77836-121">Тип параметра — 64-разрядное число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="77836-121">The parameter type is a 64 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DECIMAL`|<span data-ttu-id="77836-122">Тип параметра — 128-разрядное число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="77836-122">The parameter type is a 128 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DATETIME`|<span data-ttu-id="77836-123">Тип параметра является сериализованной структурой времени.</span><span class="sxs-lookup"><span data-stu-id="77836-123">The parameter type is a serialized DataTime structure.</span></span>|
|`COR_PRF_EVENTPIPE_GUID`|<span data-ttu-id="77836-124">Тип параметра — GUID.</span><span class="sxs-lookup"><span data-stu-id="77836-124">The parameter type is a GUID.</span></span>|
|`COR_PRF_EVENTPIPE_STRING`|<span data-ttu-id="77836-125">Тип параметра — это 16-разрядная строка расширенных символов, заканчивающаяся нулем.</span><span class="sxs-lookup"><span data-stu-id="77836-125">The parameter type is a 16 bit null terminated wide character string.</span></span>|
|`COR_PRF_EVENTPIPE_ARRAY`|<span data-ttu-id="77836-126">Тип параметра является массивом одного из перечисленных выше типов.</span><span class="sxs-lookup"><span data-stu-id="77836-126">The parameter type is an array of one of the preceding types.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="77836-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="77836-127">Remarks</span></span>  

 <span data-ttu-id="77836-128">`COR_PRF_EVENTPIPE_PARAM_TYPE`Перечисление используется структурой [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) для указания типа параметра.</span><span class="sxs-lookup"><span data-stu-id="77836-128">The `COR_PRF_EVENTPIPE_PARAM_TYPE` enumeration is used by the [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) structure to indicate the type of the parameter.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="77836-129">Требования</span><span class="sxs-lookup"><span data-stu-id="77836-129">Requirements</span></span>  

<span data-ttu-id="77836-130">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="77836-130">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="77836-131">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77836-131">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="77836-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="77836-132">See also</span></span>

- [<span data-ttu-id="77836-133">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="77836-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
