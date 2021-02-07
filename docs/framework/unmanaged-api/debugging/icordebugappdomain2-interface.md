---
description: 'Дополнительные сведения о: интерфейс ICorDebugAppDomain2'
title: Интерфейс ICorDebugAppDomain2
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 2f2fcc4166a0c825abaa04392f9905d17e286803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754192"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="819db-103">Интерфейс ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="819db-103">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="819db-104">Предоставляет методы для работы с массивами, указателями, указателями функций и ссылочными типами.</span><span class="sxs-lookup"><span data-stu-id="819db-104">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="819db-105">Этот интерфейс является расширением интерфейса ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="819db-105">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="819db-106">Методы</span><span class="sxs-lookup"><span data-stu-id="819db-106">Methods</span></span>  
  
|<span data-ttu-id="819db-107">Метод</span><span class="sxs-lookup"><span data-stu-id="819db-107">Method</span></span>|<span data-ttu-id="819db-108">Описание</span><span class="sxs-lookup"><span data-stu-id="819db-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="819db-109">Метод GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="819db-109">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="819db-110">Возвращает массив указанного типа или указатель или ссылку на указанный тип.</span><span class="sxs-lookup"><span data-stu-id="819db-110">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="819db-111">Метод GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="819db-111">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="819db-112">Возвращает указатель на функцию с заданной сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="819db-112">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="819db-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="819db-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="819db-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="819db-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="819db-115">Требования</span><span class="sxs-lookup"><span data-stu-id="819db-115">Requirements</span></span>  

 <span data-ttu-id="819db-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="819db-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="819db-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="819db-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="819db-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="819db-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="819db-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="819db-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819db-120">См. также</span><span class="sxs-lookup"><span data-stu-id="819db-120">See also</span></span>

- [<span data-ttu-id="819db-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="819db-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
