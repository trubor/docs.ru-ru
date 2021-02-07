---
description: Дополнительные сведения о перечислении Коррегфлагс
title: Перечисление CorRegFlags
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 534b7b4b170d1f586e967807c4cc8a9c82648e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753668"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="c4e21-103">Перечисление CorRegFlags</span><span class="sxs-lookup"><span data-stu-id="c4e21-103">CorRegFlags Enumeration</span></span>

<span data-ttu-id="c4e21-104">Предоставляет значения флагов, используемые для регистрации при установке модуля или составного образа.</span><span class="sxs-lookup"><span data-stu-id="c4e21-104">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e21-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4e21-105">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c4e21-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c4e21-106">Members</span></span>  
  
|<span data-ttu-id="c4e21-107">Член</span><span class="sxs-lookup"><span data-stu-id="c4e21-107">Member</span></span>|<span data-ttu-id="c4e21-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c4e21-108">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="c4e21-109">Указывает, что файлы не должны копироваться в место назначения.</span><span class="sxs-lookup"><span data-stu-id="c4e21-109">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="c4e21-110">Указывает, что модуль или составной является конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="c4e21-110">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="c4e21-111">Указывает, что модуль или составная ссылка содержит ссылки на классы.</span><span class="sxs-lookup"><span data-stu-id="c4e21-111">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4e21-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c4e21-112">Requirements</span></span>  

 <span data-ttu-id="c4e21-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e21-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e21-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c4e21-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4e21-115">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4e21-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4e21-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e21-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e21-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c4e21-117">See also</span></span>

- [<span data-ttu-id="c4e21-118">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="c4e21-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
