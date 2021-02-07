---
description: 'Дополнительные сведения о: интерфейс Икордебугаппдомаиненум'
title: Интерфейс ICorDebugAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: dfea6254e6cf4f162e44d057fb4126a67a087b61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754164"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="1e591-103">Интерфейс ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="1e591-103">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="1e591-104">Предоставляет `Next` метод, возвращающий указанное число значений, `ICorDebugAppDomainEnum` начиная с следующего расположения в перечислении.</span><span class="sxs-lookup"><span data-stu-id="1e591-104">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="1e591-105">Этот интерфейс является подклассом "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="1e591-105">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e591-106">Методы</span><span class="sxs-lookup"><span data-stu-id="1e591-106">Methods</span></span>  
  
|<span data-ttu-id="1e591-107">Метод</span><span class="sxs-lookup"><span data-stu-id="1e591-107">Method</span></span>|<span data-ttu-id="1e591-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1e591-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e591-109">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="1e591-109">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="1e591-110">Возвращает указанное число доменов приложений из коллекции, начиная с текущей позиции курсора.</span><span class="sxs-lookup"><span data-stu-id="1e591-110">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e591-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e591-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e591-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="1e591-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e591-113">Требования</span><span class="sxs-lookup"><span data-stu-id="1e591-113">Requirements</span></span>  

 <span data-ttu-id="1e591-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e591-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e591-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e591-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e591-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e591-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e591-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e591-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e591-118">См. также</span><span class="sxs-lookup"><span data-stu-id="1e591-118">See also</span></span>

- [<span data-ttu-id="1e591-119">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1e591-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="1e591-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1e591-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
