---
description: 'Дополнительные сведения о: интерфейс ICorDebugVariableSymbol'
title: Интерфейс ICorDebugVariableSymbol
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: fa3fc1f318627e9175a3066c3bd3eac00929ea60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790546"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="6d224-103">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="6d224-103">ICorDebugVariableSymbol Interface</span></span>

<span data-ttu-id="6d224-104">Извлекает сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="6d224-104">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d224-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6d224-105">Methods</span></span>  
  
|<span data-ttu-id="6d224-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6d224-106">Method</span></span>|<span data-ttu-id="6d224-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6d224-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d224-108">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="6d224-108">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="6d224-109">Получает имя переменной.</span><span class="sxs-lookup"><span data-stu-id="6d224-109">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="6d224-110">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="6d224-110">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="6d224-111">Получает размер переменной в байтах.</span><span class="sxs-lookup"><span data-stu-id="6d224-111">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="6d224-112">Метод GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="6d224-112">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="6d224-113">Возвращает управляемый индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="6d224-113">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="6d224-114">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="6d224-114">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="6d224-115">Возвращает значение переменной в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="6d224-115">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="6d224-116">Метод SetValue</span><span class="sxs-lookup"><span data-stu-id="6d224-116">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="6d224-117">Присваивает переменной значение массива байтов.</span><span class="sxs-lookup"><span data-stu-id="6d224-117">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d224-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d224-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d224-119">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d224-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6d224-120">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6d224-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d224-121">Требования</span><span class="sxs-lookup"><span data-stu-id="6d224-121">Requirements</span></span>  

 <span data-ttu-id="6d224-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d224-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d224-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d224-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d224-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d224-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d224-125">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d224-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d224-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6d224-126">See also</span></span>

- [<span data-ttu-id="6d224-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6d224-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6d224-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="6d224-128">Debugging</span></span>](index.md)
