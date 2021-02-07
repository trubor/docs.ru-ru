---
description: Дополнительные сведения о перечислении Корчеккдупликатесфор
title: Перечисление CorCheckDuplicatesFor
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 5649fc6bc66dd282b64fb5064e302a9f77420cd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678439"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="ac8c5-103">Перечисление CorCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="ac8c5-103">CorCheckDuplicatesFor Enumeration</span></span>

<span data-ttu-id="ac8c5-104">Указывает маркеры метаданных, которые будут проверяться на наличие дубликатов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-104">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ac8c5-105">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="ac8c5-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ac8c5-106">Members</span></span>  
  
|<span data-ttu-id="ac8c5-107">Член</span><span class="sxs-lookup"><span data-stu-id="ac8c5-107">Member</span></span>|<span data-ttu-id="ac8c5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ac8c5-108">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="ac8c5-109">Проверьте все маркеры метаданных на наличие дубликатов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-109">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="ac8c5-110">Не используется.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-110">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="ac8c5-111">Не проверяйте маркеры метаданных для дубликатов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-111">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="ac8c5-112">Проверьте наличие дубликатов `mdTypeDef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-112">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="ac8c5-113">Проверьте наличие дубликатов `mdInterfaceImpl` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-113">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="ac8c5-114">Проверьте наличие дубликатов `mdMethodDef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-114">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="ac8c5-115">Проверьте наличие дубликатов `mdTypeRef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-115">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="ac8c5-116">Проверьте наличие дубликатов `mdMemberRef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-116">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="ac8c5-117">Проверьте наличие дубликатов `mdCustomAttribute` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-117">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="ac8c5-118">Проверьте наличие дубликатов `mdParamDef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-118">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="ac8c5-119">Проверьте наличие дубликатов `mdPermission` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-119">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="ac8c5-120">Проверьте наличие дубликатов `mdProperty` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-120">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="ac8c5-121">Проверьте наличие дубликатов `mdEvent` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-121">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="ac8c5-122">Проверьте наличие дубликатов `mdFieldDef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-122">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="ac8c5-123">Проверьте наличие дубликатов `mdSignature` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-123">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="ac8c5-124">Проверьте наличие дубликатов `mdModuleRef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-124">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="ac8c5-125">Проверьте наличие дубликатов `mdTypeSpec` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-125">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="ac8c5-126">Проверьте наличие дубликатов `mdImplMap` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-126">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="ac8c5-127">Проверьте наличие дубликатов `mdAssemblyRef` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-127">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="ac8c5-128">Проверьте наличие дубликатов `mdFile` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-128">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="ac8c5-129">Проверьте наличие дубликатов `mdExportedType` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-129">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="ac8c5-130">Проверьте наличие дубликатов `mdManifestResource` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-130">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="ac8c5-131">Проверьте наличие дубликатов `mdGenericParam` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-131">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="ac8c5-132">Проверьте наличие дубликатов `mdMethodSpec` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-132">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="ac8c5-133">Проверьте наличие дубликатов `mdGenericParamConstraint` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-133">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="ac8c5-134">Проверьте наличие дубликатов `mdAssembly` токенов.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-134">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="ac8c5-135">Проверьте наличие дубликатов `mdMemberRef` `mdTypeRef` `mdSignature` токенов,,, `mdTypeSpec` и `mdMethodSpec` .</span><span class="sxs-lookup"><span data-stu-id="ac8c5-135">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac8c5-136">Требования</span><span class="sxs-lookup"><span data-stu-id="ac8c5-136">Requirements</span></span>  

 <span data-ttu-id="ac8c5-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac8c5-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac8c5-138">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="ac8c5-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ac8c5-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac8c5-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8c5-140">См. также</span><span class="sxs-lookup"><span data-stu-id="ac8c5-140">See also</span></span>

- [<span data-ttu-id="ac8c5-141">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="ac8c5-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
