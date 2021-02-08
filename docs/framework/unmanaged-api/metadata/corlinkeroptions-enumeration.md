---
description: Дополнительные сведения о перечислении CorLinkerOptions
title: Перечисление CorLinkerOptions
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 40f8ba6382fc937a072e01f9b3f6f89056f628db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784435"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="bc8fd-103">Перечисление CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="bc8fd-103">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="bc8fd-104">Задает флаги для выбора параметров компоновщика метаданных.</span><span class="sxs-lookup"><span data-stu-id="bc8fd-104">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bc8fd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="bc8fd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="bc8fd-106">Members</span></span>  
  
|<span data-ttu-id="bc8fd-107">Член</span><span class="sxs-lookup"><span data-stu-id="bc8fd-107">Member</span></span>|<span data-ttu-id="bc8fd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bc8fd-108">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="bc8fd-109">Закрытые типы и глобальные функции не сохраняются.</span><span class="sxs-lookup"><span data-stu-id="bc8fd-109">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="bc8fd-110">Закрытые типы и глобальные функции сохраняются.</span><span class="sxs-lookup"><span data-stu-id="bc8fd-110">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc8fd-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bc8fd-111">Requirements</span></span>  

 <span data-ttu-id="bc8fd-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc8fd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc8fd-113">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="bc8fd-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bc8fd-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc8fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8fd-115">См. также</span><span class="sxs-lookup"><span data-stu-id="bc8fd-115">See also</span></span>

- [<span data-ttu-id="bc8fd-116">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="bc8fd-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
