---
description: 'Дополнительные сведения: структура COR_PRF_ASSEMBLY_REFERENCE_INFO'
title: Структура COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: fc384e0a302c83af510deefc6f9f3b9cd5a2f77f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649225"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="218ae-103">Структура COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="218ae-103">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="218ae-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="218ae-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="218ae-105">Обеспечивает среду CLR информацией о ссылке на сборку, которую ей следует учитывать при выполнении обхода замыкания.</span><span class="sxs-lookup"><span data-stu-id="218ae-105">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218ae-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="218ae-106">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="218ae-107">Члены</span><span class="sxs-lookup"><span data-stu-id="218ae-107">Members</span></span>  
  
|<span data-ttu-id="218ae-108">Член</span><span class="sxs-lookup"><span data-stu-id="218ae-108">Member</span></span>|<span data-ttu-id="218ae-109">Описание</span><span class="sxs-lookup"><span data-stu-id="218ae-109">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="218ae-110">Указатель на открытый ключ или маркер сборки.</span><span class="sxs-lookup"><span data-stu-id="218ae-110">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="218ae-111">Количество байтов в открытом ключе или маркере.</span><span class="sxs-lookup"><span data-stu-id="218ae-111">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="218ae-112">Имя сборки, на которую дается ссылка.</span><span class="sxs-lookup"><span data-stu-id="218ae-112">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="218ae-113">Указатель на метаданные сборки.</span><span class="sxs-lookup"><span data-stu-id="218ae-113">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="218ae-114">Указатель на хэшированный большой двоичный объект (BLOB).</span><span class="sxs-lookup"><span data-stu-id="218ae-114">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="218ae-115">Количество байтов в хэшированном BLOB.</span><span class="sxs-lookup"><span data-stu-id="218ae-115">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="218ae-116">Флаги сборки.</span><span class="sxs-lookup"><span data-stu-id="218ae-116">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="218ae-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="218ae-117">Remarks</span></span>  

 <span data-ttu-id="218ae-118">Структура `COR_PRF_EX_CLAUSE_INFO` заполняется профилировщиком при его объявлении дополнительных ссылок на сборку, которые среда CLR должна учитывать при выполнении обхода замыкания.</span><span class="sxs-lookup"><span data-stu-id="218ae-118">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="218ae-119">Если профилировщик регистрируется для метода обратного вызова [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , среда выполнения передает путь и имя загружаемой сборки вместе с указателем на объект интерфейса [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) для этого метода.</span><span class="sxs-lookup"><span data-stu-id="218ae-119">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="218ae-120">Затем профилировщик может вызвать метод [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) с `COR_PRF_ASSEMBLY_REFERENCE_INFO` объектом для каждой целевой сборки, на которую планируется ссылаться из сборки, указанной в обратном вызове [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="218ae-120">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218ae-121">Требования</span><span class="sxs-lookup"><span data-stu-id="218ae-121">Requirements</span></span>  

 <span data-ttu-id="218ae-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="218ae-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="218ae-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="218ae-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="218ae-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="218ae-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="218ae-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="218ae-125">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218ae-126">См. также</span><span class="sxs-lookup"><span data-stu-id="218ae-126">See also</span></span>

- [<span data-ttu-id="218ae-127">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="218ae-127">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="218ae-128">Метод GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="218ae-128">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="218ae-129">Метод AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="218ae-129">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
