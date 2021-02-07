---
description: 'Дополнительные сведения о: интерфейс ICorDebugStringValue'
title: Интерфейс ICorDebugStringValue
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: b4e762d8c0a62c1b76b59364e9d29c4b8d2386fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717334"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="e6b26-103">Интерфейс ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="e6b26-103">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="e6b26-104">Подкласс ICorDebugHeapValue, который применяется к строковым значениям.</span><span class="sxs-lookup"><span data-stu-id="e6b26-104">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6b26-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e6b26-105">Methods</span></span>  
  
|<span data-ttu-id="e6b26-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e6b26-106">Method</span></span>|<span data-ttu-id="e6b26-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e6b26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6b26-108">Метод GetLength</span><span class="sxs-lookup"><span data-stu-id="e6b26-108">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="e6b26-109">Возвращает число символов в строке, на которую ссылается this `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="e6b26-109">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="e6b26-110">Метод GetString</span><span class="sxs-lookup"><span data-stu-id="e6b26-110">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="e6b26-111">Возвращает строку, на которую ссылается this `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="e6b26-111">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b26-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e6b26-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6b26-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="e6b26-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b26-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e6b26-114">Requirements</span></span>  

 <span data-ttu-id="e6b26-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b26-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b26-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6b26-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6b26-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6b26-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6b26-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b26-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b26-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e6b26-119">See also</span></span>

- [<span data-ttu-id="e6b26-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e6b26-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
