---
description: 'Дополнительные сведения о: структура Квструкт'
title: Структура CVStruct
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 25e8073f75620bca0737b11499d318cd57d6101c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707219"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="398b8-103">Структура CVStruct</span><span class="sxs-lookup"><span data-stu-id="398b8-103">CVStruct Structure</span></span>

<span data-ttu-id="398b8-104">Содержит сведения, используемые при установке модуля или составного образа.</span><span class="sxs-lookup"><span data-stu-id="398b8-104">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="398b8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="398b8-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="398b8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="398b8-106">Members</span></span>  
  
|<span data-ttu-id="398b8-107">Член</span><span class="sxs-lookup"><span data-stu-id="398b8-107">Member</span></span>|<span data-ttu-id="398b8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="398b8-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="398b8-109">Значительно</span><span class="sxs-lookup"><span data-stu-id="398b8-109">Major</span></span>|<span data-ttu-id="398b8-110">Номер сборки основного номера версии.</span><span class="sxs-lookup"><span data-stu-id="398b8-110">Major version build number.</span></span>|  
|<span data-ttu-id="398b8-111">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="398b8-111">Minor</span></span>|<span data-ttu-id="398b8-112">Номер сборки дополнительного номера версии.</span><span class="sxs-lookup"><span data-stu-id="398b8-112">Minor version build number.</span></span>|  
|<span data-ttu-id="398b8-113">Sub</span><span class="sxs-lookup"><span data-stu-id="398b8-113">Sub</span></span>|<span data-ttu-id="398b8-114">Номер подсборки.</span><span class="sxs-lookup"><span data-stu-id="398b8-114">Sub-build number.</span></span>|  
|<span data-ttu-id="398b8-115">Сборка</span><span class="sxs-lookup"><span data-stu-id="398b8-115">Build</span></span>|<span data-ttu-id="398b8-116">Номер сборки.</span><span class="sxs-lookup"><span data-stu-id="398b8-116">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="398b8-117">Требования</span><span class="sxs-lookup"><span data-stu-id="398b8-117">Requirements</span></span>  

 <span data-ttu-id="398b8-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="398b8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="398b8-119">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="398b8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="398b8-120">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="398b8-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="398b8-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="398b8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398b8-122">См. также</span><span class="sxs-lookup"><span data-stu-id="398b8-122">See also</span></span>

- [<span data-ttu-id="398b8-123">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="398b8-123">Metadata Structures</span></span>](metadata-structures.md)
