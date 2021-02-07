---
description: 'Дополнительные сведения: перечисление CREATE_ASM_NAME_OBJ_FLAGS'
title: Перечисление CREATE_ASM_NAME_OBJ_FLAGS
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: b68eed0671d57893e7ffbfbd8127c7ef872d5eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761204"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="ec09f-103">Перечисление CREATE_ASM_NAME_OBJ_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ec09f-103">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="ec09f-104">Задает атрибуты объекта [интерфейса IAssemblyName](iassemblyname-interface.md) при создании с помощью функции [креатеассемблинамеобжект](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ec09f-104">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec09f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec09f-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ec09f-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ec09f-106">Members</span></span>  
  
|<span data-ttu-id="ec09f-107">Член</span><span class="sxs-lookup"><span data-stu-id="ec09f-107">Member</span></span>|<span data-ttu-id="ec09f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ec09f-108">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="ec09f-109">Указывает, что переданный параметр является текстовым идентификатором.</span><span class="sxs-lookup"><span data-stu-id="ec09f-109">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="ec09f-110">Задает несколько значений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ec09f-110">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="ec09f-111">Проверяет правило дружественной сборки (только имя и открытый ключ).</span><span class="sxs-lookup"><span data-stu-id="ec09f-111">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="ec09f-112">Этот член предназначен только для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="ec09f-112">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="ec09f-113">Сочетание `CANOF_PARSE_DISPLAY_NAME` `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` флагов и.</span><span class="sxs-lookup"><span data-stu-id="ec09f-113">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="ec09f-114">Этот член предназначен только для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="ec09f-114">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec09f-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ec09f-115">Requirements</span></span>  

 <span data-ttu-id="ec09f-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec09f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec09f-117">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ec09f-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ec09f-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec09f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec09f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ec09f-119">See also</span></span>

- [<span data-ttu-id="ec09f-120">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="ec09f-120">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="ec09f-121">Функция CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="ec09f-121">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="ec09f-122">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="ec09f-122">Fusion Enumerations</span></span>](fusion-enumerations.md)
