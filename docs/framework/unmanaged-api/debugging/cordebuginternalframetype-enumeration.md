---
description: Дополнительные сведения о перечислении CorDebugInternalFrameType
title: Перечисление CorDebugInternalFrameType
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 0479ae7602224e03086b9dacf91d360253b61818
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662004"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="c0357-103">Перечисление CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="c0357-103">CorDebugInternalFrameType Enumeration</span></span>

<span data-ttu-id="c0357-104">Указывает тип кадра стека.</span><span class="sxs-lookup"><span data-stu-id="c0357-104">Identifies the type of stack frame.</span></span> <span data-ttu-id="c0357-105">Это перечисление используется методом [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0357-105">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0357-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0357-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="c0357-107">Члены</span><span class="sxs-lookup"><span data-stu-id="c0357-107">Members</span></span>  
  
|<span data-ttu-id="c0357-108">Член</span><span class="sxs-lookup"><span data-stu-id="c0357-108">Member</span></span>|<span data-ttu-id="c0357-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c0357-109">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="c0357-110">Значение Null.</span><span class="sxs-lookup"><span data-stu-id="c0357-110">A null value.</span></span> <span data-ttu-id="c0357-111">`ICorDebugInternalFrame::GetFrameType`Метод никогда не возвращает это значение.</span><span class="sxs-lookup"><span data-stu-id="c0357-111">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="c0357-112">Фрейм заглушки "управляемый-к-неуправляемый".</span><span class="sxs-lookup"><span data-stu-id="c0357-112">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="c0357-113">Неуправляемый фрейм заглушки.</span><span class="sxs-lookup"><span data-stu-id="c0357-113">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="c0357-114">Переход между доменами приложений.</span><span class="sxs-lookup"><span data-stu-id="c0357-114">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="c0357-115">Вызов упрощенного метода.</span><span class="sxs-lookup"><span data-stu-id="c0357-115">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="c0357-116">Начало вычисления функции.</span><span class="sxs-lookup"><span data-stu-id="c0357-116">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="c0357-117">Внутренний вызов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="c0357-117">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="c0357-118">Начало инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="c0357-118">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="c0357-119">Порождается исключение.</span><span class="sxs-lookup"><span data-stu-id="c0357-119">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="c0357-120">Кадр, используемый для управления доступом для кода.</span><span class="sxs-lookup"><span data-stu-id="c0357-120">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="c0357-121">Среда выполнения — это JIT-компиляция метода.</span><span class="sxs-lookup"><span data-stu-id="c0357-121">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0357-122">Требования</span><span class="sxs-lookup"><span data-stu-id="c0357-122">Requirements</span></span>  

 <span data-ttu-id="c0357-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0357-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0357-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0357-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0357-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0357-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0357-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0357-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0357-127">См. также</span><span class="sxs-lookup"><span data-stu-id="c0357-127">See also</span></span>

- [<span data-ttu-id="c0357-128">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="c0357-128">Debugging Enumerations</span></span>](debugging-enumerations.md)
