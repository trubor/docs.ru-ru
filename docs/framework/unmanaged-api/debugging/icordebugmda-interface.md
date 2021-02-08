---
description: 'Дополнительные сведения о: интерфейс ICorDebugMDA'
title: Интерфейс ICorDebugMDA
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 8e6e779c58d71b07edc9b63dff72aef728ebe050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801129"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="32014-103">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="32014-103">ICorDebugMDA Interface</span></span>

<span data-ttu-id="32014-104">Представляет сообщение управляемого помощника по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="32014-104">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32014-105">Методы</span><span class="sxs-lookup"><span data-stu-id="32014-105">Methods</span></span>  
  
|<span data-ttu-id="32014-106">Метод</span><span class="sxs-lookup"><span data-stu-id="32014-106">Method</span></span>|<span data-ttu-id="32014-107">Описание</span><span class="sxs-lookup"><span data-stu-id="32014-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32014-108">Метод GetDescription</span><span class="sxs-lookup"><span data-stu-id="32014-108">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="32014-109">Возвращает строку, содержащую описание этого MDA.</span><span class="sxs-lookup"><span data-stu-id="32014-109">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="32014-110">Метод GetFlags</span><span class="sxs-lookup"><span data-stu-id="32014-110">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="32014-111">Возвращает флаги, связанные с этим MDA.</span><span class="sxs-lookup"><span data-stu-id="32014-111">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="32014-112">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="32014-112">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="32014-113">Возвращает строку, содержащую имя этого MDA.</span><span class="sxs-lookup"><span data-stu-id="32014-113">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="32014-114">Метод GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="32014-114">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="32014-115">Возвращает идентификатор потока операционной системы, в котором выполняется этот MDA.</span><span class="sxs-lookup"><span data-stu-id="32014-115">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="32014-116">Метод GetXML</span><span class="sxs-lookup"><span data-stu-id="32014-116">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="32014-117">Возвращает полный XML-поток, связанный с этим MDA.</span><span class="sxs-lookup"><span data-stu-id="32014-117">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32014-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="32014-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32014-119">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="32014-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32014-120">Требования</span><span class="sxs-lookup"><span data-stu-id="32014-120">Requirements</span></span>  

 <span data-ttu-id="32014-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32014-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32014-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32014-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32014-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32014-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32014-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32014-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32014-125">См. также</span><span class="sxs-lookup"><span data-stu-id="32014-125">See also</span></span>

- [<span data-ttu-id="32014-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="32014-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="32014-127">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="32014-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
