---
description: Дополнительные сведения о перечислении CorDebugCodeInvokeKind
title: Перечисление CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
ms.openlocfilehash: d3fc3fe6f7568adcb2d1bbbe18c98d9d84bac337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747092"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="ed369-103">Перечисление CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="ed369-103">CorDebugCodeInvokeKind Enumeration</span></span>

<span data-ttu-id="ed369-104">Описывает, каким образом экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="ed369-104">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed369-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed369-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="ed369-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ed369-106">Members</span></span>  
  
|<span data-ttu-id="ed369-107">Член</span><span class="sxs-lookup"><span data-stu-id="ed369-107">Member</span></span>|<span data-ttu-id="ed369-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ed369-108">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="ed369-109">Если любой управляемый код вызывается этим методом, он должен находиться после явно заданных событий или точек останова.</span><span class="sxs-lookup"><span data-stu-id="ed369-109">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="ed369-110">— или —</span><span class="sxs-lookup"><span data-stu-id="ed369-110">--or--</span></span><br /><br /> <span data-ttu-id="ed369-111">Мы можем просто пропустить некоторую часть управляемого кода, который вызывает этот метод, так как не существует никакого простого способа останова на нем.</span><span class="sxs-lookup"><span data-stu-id="ed369-111">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="ed369-112">— или —</span><span class="sxs-lookup"><span data-stu-id="ed369-112">--or--</span></span><br /><br /> <span data-ttu-id="ed369-113">Метод может никогда не вызвать управляемый код.</span><span class="sxs-lookup"><span data-stu-id="ed369-113">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="ed369-114">Этот метод будет вызывать управляемый код с помощью инструкции return.</span><span class="sxs-lookup"><span data-stu-id="ed369-114">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="ed369-115">Режим пропуска должен начаться в следующем управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="ed369-115">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="ed369-116">Этот метод будет вызывать управляемый код с помощью вызова с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="ed369-116">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="ed369-117">Пошаговый режим и режим пропуска любых инструкций вызова должны поступать в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="ed369-117">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed369-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed369-118">Remarks</span></span>  

 <span data-ttu-id="ed369-119">Это перечисление используется методом [ICorDebugProcess6:: жетекспортстепинфо](icordebugprocess6-getexportstepinfo-method.md) для предоставления сведений о пошаговом выполнении управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="ed369-119">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed369-120">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ed369-120">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed369-121">Требования</span><span class="sxs-lookup"><span data-stu-id="ed369-121">Requirements</span></span>  

 <span data-ttu-id="ed369-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed369-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed369-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed369-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed369-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed369-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed369-125">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed369-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed369-126">См. также</span><span class="sxs-lookup"><span data-stu-id="ed369-126">See also</span></span>

- [<span data-ttu-id="ed369-127">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="ed369-127">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ed369-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="ed369-128">Debugging</span></span>](index.md)
