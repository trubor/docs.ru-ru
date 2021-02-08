---
description: Дополнительные сведения о перечислении Корфилефлагс
title: Перечисление CorFileFlags
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: 8ffad9bad9c656a10c2c556f5e06f9d510ccb45a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784487"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="cce08-103">Перечисление CorFileFlags</span><span class="sxs-lookup"><span data-stu-id="cce08-103">CorFileFlags Enumeration</span></span>

<span data-ttu-id="cce08-104">Содержит значения, описывающие тип файла, определенного в вызове [IMetaDataAssemblyEmit::D ефинефиле](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="cce08-104">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce08-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cce08-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cce08-106">Члены</span><span class="sxs-lookup"><span data-stu-id="cce08-106">Members</span></span>  
  
|<span data-ttu-id="cce08-107">Член</span><span class="sxs-lookup"><span data-stu-id="cce08-107">Member</span></span>|<span data-ttu-id="cce08-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cce08-108">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="cce08-109">Указывает, что файл не является файлом ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cce08-109">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="cce08-110">Указывает, что файл, возможно, файл ресурсов, не содержит метаданных.</span><span class="sxs-lookup"><span data-stu-id="cce08-110">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cce08-111">Требования</span><span class="sxs-lookup"><span data-stu-id="cce08-111">Requirements</span></span>  

 <span data-ttu-id="cce08-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cce08-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce08-113">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="cce08-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cce08-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce08-115">См. также</span><span class="sxs-lookup"><span data-stu-id="cce08-115">See also</span></span>

- [<span data-ttu-id="cce08-116">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="cce08-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
