---
description: Дополнительные сведения о перечислении Коррефтодефчекк
title: Перечисление CorRefToDefCheck
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ca9d1c7ceb3d9f82ef8d5f1f54d869db64053e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784253"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="72566-103">Перечисление CorRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="72566-103">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="72566-104">Задает флаги для элемента управления, на который ссылаются элементы, преобразуемые в их определения для оптимизации кода.</span><span class="sxs-lookup"><span data-stu-id="72566-104">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72566-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72566-105">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="72566-106">Члены</span><span class="sxs-lookup"><span data-stu-id="72566-106">Members</span></span>  
  
|<span data-ttu-id="72566-107">Член</span><span class="sxs-lookup"><span data-stu-id="72566-107">Member</span></span>|<span data-ttu-id="72566-108">Описание</span><span class="sxs-lookup"><span data-stu-id="72566-108">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="72566-109">Указывает, что ссылки на типы и ссылки на элементы должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="72566-109">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="72566-110">Это значение по умолчанию ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="72566-110">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="72566-111">Указывает, что все элементы, на которые указывают ссылки, должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="72566-111">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="72566-112">Указывает, что не нужно преобразовывать элементы, на которые имеются ссылки, в определения.</span><span class="sxs-lookup"><span data-stu-id="72566-112">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="72566-113">Указывает, что только ссылки на типы должны быть преобразованы в определения типов.</span><span class="sxs-lookup"><span data-stu-id="72566-113">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="72566-114">Указывает, что только ссылки на элементы должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="72566-114">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="72566-115">То есть ссылки на элементы должны быть преобразованы в определения методов или определения полей.</span><span class="sxs-lookup"><span data-stu-id="72566-115">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72566-116">Требования</span><span class="sxs-lookup"><span data-stu-id="72566-116">Requirements</span></span>  

 <span data-ttu-id="72566-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72566-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72566-118">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="72566-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72566-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72566-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72566-120">См. также</span><span class="sxs-lookup"><span data-stu-id="72566-120">See also</span></span>

- [<span data-ttu-id="72566-121">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="72566-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
