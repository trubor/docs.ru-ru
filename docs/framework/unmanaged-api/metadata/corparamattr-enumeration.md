---
description: Дополнительные сведения о перечислении Корпараматтр
title: Перечисление CorParamAttr
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: c07569d3fb92b20a7985dbfeb2205af727866051
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784292"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="c7f25-103">Перечисление CorParamAttr</span><span class="sxs-lookup"><span data-stu-id="c7f25-103">CorParamAttr Enumeration</span></span>

<span data-ttu-id="c7f25-104">Содержит значения, описывающие метаданные параметра метода.</span><span class="sxs-lookup"><span data-stu-id="c7f25-104">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f25-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c7f25-105">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c7f25-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c7f25-106">Members</span></span>  
  
|<span data-ttu-id="c7f25-107">Член</span><span class="sxs-lookup"><span data-stu-id="c7f25-107">Member</span></span>|<span data-ttu-id="c7f25-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c7f25-108">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="c7f25-109">Указывает, что параметр передается в вызов метода.</span><span class="sxs-lookup"><span data-stu-id="c7f25-109">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="c7f25-110">Указывает, что параметр передается из возвращаемого методом значения.</span><span class="sxs-lookup"><span data-stu-id="c7f25-110">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="c7f25-111">Указывает, что данный параметр не обязателен.</span><span class="sxs-lookup"><span data-stu-id="c7f25-111">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="c7f25-112">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="c7f25-112">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="c7f25-113">Указывает, что параметр имеет стандартное значение.</span><span class="sxs-lookup"><span data-stu-id="c7f25-113">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="c7f25-114">Указывает, что параметр содержит сведения об упаковке.</span><span class="sxs-lookup"><span data-stu-id="c7f25-114">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="c7f25-115">Не используется.</span><span class="sxs-lookup"><span data-stu-id="c7f25-115">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7f25-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c7f25-116">Requirements</span></span>  

 <span data-ttu-id="c7f25-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7f25-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f25-118">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="c7f25-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c7f25-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f25-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f25-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c7f25-120">See also</span></span>

- [<span data-ttu-id="c7f25-121">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="c7f25-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
