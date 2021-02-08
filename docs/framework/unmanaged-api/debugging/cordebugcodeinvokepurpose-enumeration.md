---
description: Дополнительные сведения о перечислении Кордебугкодеинвокепурпосе
title: Перечисление CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 1402343cc15e451975567564e6ce353900454bf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801726"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="d5b52-103">Перечисление CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="d5b52-103">CorDebugCodeInvokePurpose Enumeration</span></span>

<span data-ttu-id="d5b52-104">Описывает, почему экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="d5b52-104">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b52-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5b52-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="d5b52-106">Члены</span><span class="sxs-lookup"><span data-stu-id="d5b52-106">Members</span></span>  
  
|<span data-ttu-id="d5b52-107">Член</span><span class="sxs-lookup"><span data-stu-id="d5b52-107">Member</span></span>|<span data-ttu-id="d5b52-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d5b52-108">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="d5b52-109">Отсутствует или неизвестно.</span><span class="sxs-lookup"><span data-stu-id="d5b52-109">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="d5b52-110">Управляемый код будет выполнять любую управляемую точку входа, например, обратный p-invoke.</span><span class="sxs-lookup"><span data-stu-id="d5b52-110">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="d5b52-111">Любые дополнительные цели неизвестны среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="d5b52-111">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="d5b52-112">Управляемый код будет выполнять статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="d5b52-112">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="d5b52-113">Управляемый код будет выполнять реализацию некоторого метода интерфейса, который был вызван.</span><span class="sxs-lookup"><span data-stu-id="d5b52-113">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5b52-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5b52-114">Remarks</span></span>  

 <span data-ttu-id="d5b52-115">Это перечисление используется методом [ICorDebugProcess6:: жетекспортстепинфо](icordebugprocess6-getexportstepinfo-method.md) для предоставления сведений о пошаговом выполнении управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="d5b52-115">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5b52-116">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d5b52-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b52-117">Требования</span><span class="sxs-lookup"><span data-stu-id="d5b52-117">Requirements</span></span>  

 <span data-ttu-id="d5b52-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b52-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b52-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5b52-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5b52-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5b52-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5b52-121">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b52-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b52-122">См. также</span><span class="sxs-lookup"><span data-stu-id="d5b52-122">See also</span></span>

- [<span data-ttu-id="d5b52-123">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="d5b52-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="d5b52-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="d5b52-124">Debugging</span></span>](index.md)
