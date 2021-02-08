---
description: Дополнительные сведения о перечислении Вариаблелокатионтипе
title: Перечисление VariableLocationType
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 8561077b9f3f4d318eeb743d51538b2a9a22a217
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800530"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="f5039-103">Перечисление VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="f5039-103">VariableLocationType Enumeration</span></span>

<span data-ttu-id="f5039-104">Указывает тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="f5039-104">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5039-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5039-105">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="f5039-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f5039-106">Members</span></span>  
  
|<span data-ttu-id="f5039-107">Член</span><span class="sxs-lookup"><span data-stu-id="f5039-107">Member</span></span>|<span data-ttu-id="f5039-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f5039-108">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="f5039-109">Переменная находится в регистре.</span><span class="sxs-lookup"><span data-stu-id="f5039-109">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="f5039-110">Переменная находится в расположении в памяти относительно регистра.</span><span class="sxs-lookup"><span data-stu-id="f5039-110">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="f5039-111">Переменная не хранится в регистре или расположении в памяти относительно регистра.</span><span class="sxs-lookup"><span data-stu-id="f5039-111">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5039-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5039-112">Remarks</span></span>  

 <span data-ttu-id="f5039-113">Член `VariableLocationType` перечисления возвращается методом [ICorDebugVariableHome:: жетлокатионтипе](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f5039-113">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5039-114">Требования</span><span class="sxs-lookup"><span data-stu-id="f5039-114">Requirements</span></span>  

 <span data-ttu-id="f5039-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5039-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5039-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5039-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5039-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5039-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5039-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5039-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5039-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f5039-119">See also</span></span>

- [<span data-ttu-id="f5039-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="f5039-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
