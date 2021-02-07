---
description: 'Дополнительные сведения о: интерфейс ICorDebugExceptionObjectValue'
title: Интерфейс ICorDebugExceptionObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: 67672f9921bab31019a42b742480176e6d0bf3d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693204"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="02992-103">Интерфейс ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="02992-103">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="02992-104">Расширяет интерфейс "ICorDebugObjectValue" для предоставления сведений о трассировке стека из управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="02992-104">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02992-105">Методы</span><span class="sxs-lookup"><span data-stu-id="02992-105">Methods</span></span>  
  
|<span data-ttu-id="02992-106">Метод</span><span class="sxs-lookup"><span data-stu-id="02992-106">Method</span></span>|<span data-ttu-id="02992-107">Описание</span><span class="sxs-lookup"><span data-stu-id="02992-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02992-108">Метод EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="02992-108">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="02992-109">Возвращает перечислитель для стека вызовов, внедренного в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="02992-109">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02992-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="02992-110">Remarks</span></span>  

 <span data-ttu-id="02992-111">Вызов метода `QueryInterface` будет выполнен для управляемых объектов, производных от <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="02992-111">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02992-112">Требования</span><span class="sxs-lookup"><span data-stu-id="02992-112">Requirements</span></span>  

 <span data-ttu-id="02992-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02992-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02992-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02992-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02992-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02992-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02992-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02992-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02992-117">См. также</span><span class="sxs-lookup"><span data-stu-id="02992-117">See also</span></span>

- [<span data-ttu-id="02992-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="02992-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="02992-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="02992-119">Debugging</span></span>](index.md)
