---
description: 'Дополнительные сведения: перечисление COR_PRF_STATIC_TYPE'
title: Перечисление COR_PRF_STATIC_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: b7171fe4e9c536d94109d46ae6cad9201a15bab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789043"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="70cf7-103">Перечисление COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="70cf7-103">COR_PRF_STATIC_TYPE Enumeration</span></span>

<span data-ttu-id="70cf7-104">Указывает, является ли поле статическим и, если да, относящееся к этому полю статическое качество.</span><span class="sxs-lookup"><span data-stu-id="70cf7-104">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="70cf7-105">Эти значения можно комбинировать с помощью побитовой операции OR, чтобы указать, что поле имеет несколько различных статических качеств.</span><span class="sxs-lookup"><span data-stu-id="70cf7-105">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cf7-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="70cf7-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="70cf7-107">Члены</span><span class="sxs-lookup"><span data-stu-id="70cf7-107">Members</span></span>  
  
|<span data-ttu-id="70cf7-108">Член</span><span class="sxs-lookup"><span data-stu-id="70cf7-108">Member</span></span>|<span data-ttu-id="70cf7-109">Описание</span><span class="sxs-lookup"><span data-stu-id="70cf7-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="70cf7-110">Поле не является статическим.</span><span class="sxs-lookup"><span data-stu-id="70cf7-110">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="70cf7-111">Поле является статическим в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="70cf7-111">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="70cf7-112">Поле является статическим для потока.</span><span class="sxs-lookup"><span data-stu-id="70cf7-112">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="70cf7-113">Поле является статическим по контексту.</span><span class="sxs-lookup"><span data-stu-id="70cf7-113">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="70cf7-114">Поле является относительным виртуальным адресом (RVA) — статическим.</span><span class="sxs-lookup"><span data-stu-id="70cf7-114">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70cf7-115">Требования</span><span class="sxs-lookup"><span data-stu-id="70cf7-115">Requirements</span></span>  

 <span data-ttu-id="70cf7-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cf7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cf7-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70cf7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70cf7-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70cf7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70cf7-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cf7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cf7-120">См. также</span><span class="sxs-lookup"><span data-stu-id="70cf7-120">See also</span></span>

- [<span data-ttu-id="70cf7-121">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="70cf7-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
