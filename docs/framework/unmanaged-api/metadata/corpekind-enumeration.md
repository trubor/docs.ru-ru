---
description: Дополнительные сведения о перечислении CorPEKind
title: Перечисление CorPEKind
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 6d1f29a220ce9d4be4151d8eff6557fa8c693ed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784279"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="b3fdf-103">Перечисление CorPEKind</span><span class="sxs-lookup"><span data-stu-id="b3fdf-103">CorPEKind Enumeration</span></span>

<span data-ttu-id="b3fdf-104">Содержит значения, описывающие переносимый исполняемый файл (PE), возвращенный при вызове [IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3fdf-104">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3fdf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3fdf-105">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="b3fdf-106">Члены</span><span class="sxs-lookup"><span data-stu-id="b3fdf-106">Members</span></span>  
  
|<span data-ttu-id="b3fdf-107">Член</span><span class="sxs-lookup"><span data-stu-id="b3fdf-107">Member</span></span>|<span data-ttu-id="b3fdf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b3fdf-108">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="b3fdf-109">Указывает, что этот файл не является PE-файлом.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-109">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="b3fdf-110">Указывает, что этот PE файл содержит только управляемый код.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-110">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="b3fdf-111">Указывает, что этот PE файл выполняет вызовы Win32.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-111">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="b3fdf-112">Указывает, что этот PE-файл выполняется на 64-разрядной платформе.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-112">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="b3fdf-113">Указывает, что этот PE-файл является машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-113">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="b3fdf-114">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="b3fdf-114">pe32BitPreferred</span></span>|<span data-ttu-id="b3fdf-115">Указывает, что этот PE-файл является нейтральным к платформе и предпочитает загрузку в 32-разрядной среде.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-115">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3fdf-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3fdf-116">Remarks</span></span>  

 <span data-ttu-id="b3fdf-117">Эти значения можно использовать в побитовых сочетаниях.</span><span class="sxs-lookup"><span data-stu-id="b3fdf-117">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3fdf-118">Требования</span><span class="sxs-lookup"><span data-stu-id="b3fdf-118">Requirements</span></span>  

 <span data-ttu-id="b3fdf-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3fdf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3fdf-120">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="b3fdf-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b3fdf-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3fdf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fdf-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b3fdf-122">See also</span></span>

- [<span data-ttu-id="b3fdf-123">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="b3fdf-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
