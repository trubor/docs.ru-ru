---
description: Дополнительные сведения о перечислении CorTokenType
title: Перечисление CorTokenType
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 954bddccd8fe20be46080f8843bcf754e0cf1bbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678410"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="49d19-103">Перечисление CorTokenType</span><span class="sxs-lookup"><span data-stu-id="49d19-103">CorTokenType Enumeration</span></span>

<span data-ttu-id="49d19-104">Указывает тип маркера метаданных.</span><span class="sxs-lookup"><span data-stu-id="49d19-104">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d19-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49d19-105">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="49d19-106">Члены</span><span class="sxs-lookup"><span data-stu-id="49d19-106">Members</span></span>  
  
|<span data-ttu-id="49d19-107">Член</span><span class="sxs-lookup"><span data-stu-id="49d19-107">Member</span></span>|<span data-ttu-id="49d19-108">Описание</span><span class="sxs-lookup"><span data-stu-id="49d19-108">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="49d19-109">`mdModule`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-109">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="49d19-110">`mdTypeRef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-110">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="49d19-111">`mdTypeDef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-111">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="49d19-112">`mdFieldDef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-112">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="49d19-113">`mdMethodDef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-113">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="49d19-114">`mdParamDef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-114">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="49d19-115">`mdInterfaceImpl`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-115">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="49d19-116">`mdMemberRef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-116">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="49d19-117">`mdCustomAttribute`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-117">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="49d19-118">`mdPermission`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-118">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="49d19-119">`mdSignature`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-119">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="49d19-120">`mdEvent`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-120">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="49d19-121">`mdProperty`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-121">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="49d19-122">`mdModuleRef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-122">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="49d19-123">`mdTypeSpec`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-123">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="49d19-124">`mdAssembly`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-124">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="49d19-125">`mdAssemblyRef`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-125">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="49d19-126">`mdFile`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-126">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="49d19-127">`mdExportedType`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-127">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="49d19-128">`mdManifestResource`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-128">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="49d19-129">`mdGenericParam`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-129">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="49d19-130">`mdMethodSpec`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-130">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="49d19-131">`mdGenericParamConstraint`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-131">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="49d19-132">`mdString`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-132">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="49d19-133">`mdName`Токен.</span><span class="sxs-lookup"><span data-stu-id="49d19-133">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="49d19-134">Не используется.</span><span class="sxs-lookup"><span data-stu-id="49d19-134">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49d19-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="49d19-135">Remarks</span></span>  

 <span data-ttu-id="49d19-136">Каждое значение равно значению верхнего байта в соответствующем маркере метаданных.</span><span class="sxs-lookup"><span data-stu-id="49d19-136">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d19-137">Требования</span><span class="sxs-lookup"><span data-stu-id="49d19-137">Requirements</span></span>  

 <span data-ttu-id="49d19-138">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d19-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d19-139">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="49d19-139">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="49d19-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d19-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d19-141">См. также</span><span class="sxs-lookup"><span data-stu-id="49d19-141">See also</span></span>

- [<span data-ttu-id="49d19-142">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="49d19-142">Metadata Enumerations</span></span>](metadata-enumerations.md)
