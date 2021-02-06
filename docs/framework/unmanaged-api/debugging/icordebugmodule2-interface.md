---
description: 'Дополнительные сведения о: интерфейс ICorDebugModule2'
title: Интерфейс ICorDebugModule2
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 28de1f0d3411218ac92991d4fceda0612c8199bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659937"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="77a33-103">Интерфейс ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="77a33-103">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="77a33-104">Служит логическим расширением интерфейса ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="77a33-104">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77a33-105">Методы</span><span class="sxs-lookup"><span data-stu-id="77a33-105">Methods</span></span>  
  
|<span data-ttu-id="77a33-106">Метод</span><span class="sxs-lookup"><span data-stu-id="77a33-106">Method</span></span>|<span data-ttu-id="77a33-107">Описание</span><span class="sxs-lookup"><span data-stu-id="77a33-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77a33-108">Метод ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="77a33-108">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="77a33-109">Применяет изменения в метаданных и изменения в коде промежуточного языка MSIL к выполняющемуся процессу.</span><span class="sxs-lookup"><span data-stu-id="77a33-109">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="77a33-110">Метод GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="77a33-110">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="77a33-111">Возвращает флаги, управляющие JIT-компиляцией для этого `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="77a33-111">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="77a33-112">Метод ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="77a33-112">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="77a33-113">Разрешает сборку, на которую ссылается указанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="77a33-113">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="77a33-114">Метод SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="77a33-114">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="77a33-115">Задает флаги, управляющие JIT-компиляцией для этого `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="77a33-115">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="77a33-116">Метод SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="77a33-116">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="77a33-117">Устанавливает состояние Только мой код (JMC) всех методов всех классов в данном `ICorDebugModule2` значении, за исключением тех, которые заданы в `pTokens` массиве, для которого задано обратное значение.</span><span class="sxs-lookup"><span data-stu-id="77a33-117">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77a33-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="77a33-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77a33-119">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="77a33-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a33-120">Требования</span><span class="sxs-lookup"><span data-stu-id="77a33-120">Requirements</span></span>  

 <span data-ttu-id="77a33-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a33-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a33-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77a33-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77a33-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77a33-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77a33-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a33-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a33-125">См. также</span><span class="sxs-lookup"><span data-stu-id="77a33-125">See also</span></span>

- [<span data-ttu-id="77a33-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="77a33-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
