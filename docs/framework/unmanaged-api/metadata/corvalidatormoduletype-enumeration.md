---
description: Дополнительные сведения о перечислении Корвалидатормодулетипе
title: Перечисление CorValidatorModuleType
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 13792c461660ddd8cfd530f5b34d642d806cdea4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707258"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="f5b49-103">Перечисление CorValidatorModuleType</span><span class="sxs-lookup"><span data-stu-id="f5b49-103">CorValidatorModuleType Enumeration</span></span>

<span data-ttu-id="f5b49-104">Указывает тип модуля.</span><span class="sxs-lookup"><span data-stu-id="f5b49-104">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b49-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5b49-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="f5b49-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f5b49-106">Members</span></span>  
  
|<span data-ttu-id="f5b49-107">Член</span><span class="sxs-lookup"><span data-stu-id="f5b49-107">Member</span></span>|<span data-ttu-id="f5b49-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f5b49-108">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="f5b49-109">Недопустимый тип модуля.</span><span class="sxs-lookup"><span data-stu-id="f5b49-109">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="f5b49-110">Минимальное значение `CorValidatorModuleType` перечисления.</span><span class="sxs-lookup"><span data-stu-id="f5b49-110">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="f5b49-111">Модуль является переносимым исполняемым файлом (PE).</span><span class="sxs-lookup"><span data-stu-id="f5b49-111">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="f5b49-112">Модуль является OBJ-файлом.</span><span class="sxs-lookup"><span data-stu-id="f5b49-112">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="f5b49-113">Модуль является сеансом отладчика "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="f5b49-113">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="f5b49-114">Модуль — это один из инкрементно построенных.</span><span class="sxs-lookup"><span data-stu-id="f5b49-114">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="f5b49-115">Максимальное значение `CorValidatorModuleType` перечисления.</span><span class="sxs-lookup"><span data-stu-id="f5b49-115">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5b49-116">Требования</span><span class="sxs-lookup"><span data-stu-id="f5b49-116">Requirements</span></span>  

 <span data-ttu-id="f5b49-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b49-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b49-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f5b49-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5b49-119">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5b49-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5b49-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b49-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b49-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f5b49-121">See also</span></span>

- [<span data-ttu-id="f5b49-122">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="f5b49-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
