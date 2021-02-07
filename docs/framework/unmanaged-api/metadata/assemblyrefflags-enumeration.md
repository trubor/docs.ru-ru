---
description: Дополнительные сведения о перечислении Ассемблиреффлагс
title: Перечисление AssemblyRefFlags
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 1b33faf816194c8b386f34a63d885ba37c4329a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678904"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="65948-103">Перечисление AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="65948-103">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="65948-104">Содержит значения, описывающие функции ссылки на сборку.</span><span class="sxs-lookup"><span data-stu-id="65948-104">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65948-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65948-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="65948-106">Члены</span><span class="sxs-lookup"><span data-stu-id="65948-106">Members</span></span>  
  
|<span data-ttu-id="65948-107">Член</span><span class="sxs-lookup"><span data-stu-id="65948-107">Member</span></span>|<span data-ttu-id="65948-108">Описание</span><span class="sxs-lookup"><span data-stu-id="65948-108">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="65948-109">Указывает, что ссылка на сборку содержит полные нехэшированные сведения об издателе сборки.</span><span class="sxs-lookup"><span data-stu-id="65948-109">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65948-110">Требования</span><span class="sxs-lookup"><span data-stu-id="65948-110">Requirements</span></span>  

 <span data-ttu-id="65948-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65948-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65948-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="65948-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65948-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65948-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65948-114">См. также</span><span class="sxs-lookup"><span data-stu-id="65948-114">See also</span></span>

- [<span data-ttu-id="65948-115">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="65948-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="65948-116">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="65948-116">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="65948-117">Метод DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="65948-117">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
