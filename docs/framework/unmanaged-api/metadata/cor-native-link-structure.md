---
description: 'Дополнительные сведения: структура COR_NATIVE_LINK'
title: Структура COR_NATIVE_LINK
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 09c715af698a0614fd4a9a17679df6908a1497a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678579"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="0cab7-103">Структура COR_NATIVE_LINK</span><span class="sxs-lookup"><span data-stu-id="0cab7-103">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="0cab7-104">Содержит сведения, используемые для связи с машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="0cab7-104">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cab7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0cab7-105">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="0cab7-106">Члены</span><span class="sxs-lookup"><span data-stu-id="0cab7-106">Members</span></span>  
  
|<span data-ttu-id="0cab7-107">Член</span><span class="sxs-lookup"><span data-stu-id="0cab7-107">Member</span></span>|<span data-ttu-id="0cab7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0cab7-108">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="0cab7-109">Тип, который должен быть связан в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="0cab7-109">The type to be linked in native code.</span></span> <span data-ttu-id="0cab7-110">Это значение является одним из значений [корнативелинктипе](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0cab7-110">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="0cab7-111">Флаги, используемые компоновщиком при связывании машинного кода.</span><span class="sxs-lookup"><span data-stu-id="0cab7-111">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="0cab7-112">Это значение является одним из значений [CorNativeLinkFlags](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0cab7-112">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="0cab7-113">Токен метаданных MemberRef, представляющий точку входа.</span><span class="sxs-lookup"><span data-stu-id="0cab7-113">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="0cab7-114">Формат — `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="0cab7-114">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cab7-115">Требования</span><span class="sxs-lookup"><span data-stu-id="0cab7-115">Requirements</span></span>  

 <span data-ttu-id="0cab7-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cab7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cab7-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0cab7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0cab7-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0cab7-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0cab7-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cab7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cab7-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0cab7-120">See also</span></span>

- [<span data-ttu-id="0cab7-121">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="0cab7-121">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="0cab7-122">Перечисление CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="0cab7-122">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="0cab7-123">Перечисление CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="0cab7-123">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
