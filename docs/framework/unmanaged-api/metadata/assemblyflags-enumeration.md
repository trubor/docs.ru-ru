---
description: Дополнительные сведения о перечислении AssemblyFlags
title: Перечисление AssemblyFlags
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 17cc0dec305c21d21693fe8f4f8d82c039f73278
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679008"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="bb498-103">Перечисление AssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="bb498-103">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="bb498-104">Содержит значения, описывающие функции времени выполнения сборки.</span><span class="sxs-lookup"><span data-stu-id="bb498-104">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb498-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb498-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bb498-106">Члены</span><span class="sxs-lookup"><span data-stu-id="bb498-106">Members</span></span>  
  
|<span data-ttu-id="bb498-107">Член</span><span class="sxs-lookup"><span data-stu-id="bb498-107">Member</span></span>|<span data-ttu-id="bb498-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bb498-108">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="bb498-109">Указывает, что экспортированные определения типа являются неявными в файлах, составляющих сборку.</span><span class="sxs-lookup"><span data-stu-id="bb498-109">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="bb498-110">В платформа .NET Framework версиях 1,0 и 1,1 это значение всегда считается установленным.</span><span class="sxs-lookup"><span data-stu-id="bb498-110">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="bb498-111">Указывает, что определения ресурсов являются неявными в файлах, составляющих сборку.</span><span class="sxs-lookup"><span data-stu-id="bb498-111">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="bb498-112">В платформа .NET Framework 1,0 и 1,1 предполагается, что это значение всегда задано.</span><span class="sxs-lookup"><span data-stu-id="bb498-112">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="bb498-113">Указывает, что сборка не может выполняться с другими версиями, если они выполняются в одном домене приложения.</span><span class="sxs-lookup"><span data-stu-id="bb498-113">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="bb498-114">Указывает, что сборка не может выполняться с другими версиями, если они выполняются в одном процессе.</span><span class="sxs-lookup"><span data-stu-id="bb498-114">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="bb498-115">Указывает, что сборка не может выполняться с другими версиями, если они выполняются на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="bb498-115">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb498-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb498-116">Remarks</span></span>  

 <span data-ttu-id="bb498-117">Значения между 0x0010 и 0x0070 (включительно) используются для описания возможностей параллельной совместимости сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="bb498-117">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="bb498-118">Если ни одно из этих значений не задано, предполагается, что сборка совместима параллельно.</span><span class="sxs-lookup"><span data-stu-id="bb498-118">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb498-119">Требования</span><span class="sxs-lookup"><span data-stu-id="bb498-119">Requirements</span></span>  

 <span data-ttu-id="bb498-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb498-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb498-121">**Заголовок:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb498-121">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="bb498-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb498-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb498-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb498-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb498-124">См. также</span><span class="sxs-lookup"><span data-stu-id="bb498-124">See also</span></span>

- [<span data-ttu-id="bb498-125">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="bb498-125">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="bb498-126">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="bb498-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
