---
description: Дополнительные сведения о перечислении Корнативелинктипе
title: Перечисление CorNativeLinkType
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 40efc75a793da8b024eff3d7c2c620123eca08b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784344"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="267e8-103">Перечисление CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="267e8-103">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="267e8-104">Предоставляет значения, указывающие тип, связанный в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="267e8-104">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267e8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="267e8-105">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="267e8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="267e8-106">Members</span></span>  
  
|<span data-ttu-id="267e8-107">Член</span><span class="sxs-lookup"><span data-stu-id="267e8-107">Member</span></span>|<span data-ttu-id="267e8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="267e8-108">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="267e8-109">Указывает, что ни одно из ключевых слов не указано.</span><span class="sxs-lookup"><span data-stu-id="267e8-109">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="267e8-110">Указывает, что указано ключевое слово ANSI.</span><span class="sxs-lookup"><span data-stu-id="267e8-110">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="267e8-111">Указывает, что указано ключевое слово Юникода</span><span class="sxs-lookup"><span data-stu-id="267e8-111">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="267e8-112">Указывает, что указано ключевое слово auto.</span><span class="sxs-lookup"><span data-stu-id="267e8-112">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="267e8-113">Указывает, что указано ключевое слово OLE.</span><span class="sxs-lookup"><span data-stu-id="267e8-113">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="267e8-114">Не используется.</span><span class="sxs-lookup"><span data-stu-id="267e8-114">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="267e8-115">Требования</span><span class="sxs-lookup"><span data-stu-id="267e8-115">Requirements</span></span>  

 <span data-ttu-id="267e8-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="267e8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267e8-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="267e8-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="267e8-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="267e8-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="267e8-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="267e8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267e8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="267e8-120">See also</span></span>

- [<span data-ttu-id="267e8-121">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="267e8-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
