---
description: 'Дополнительные сведения о: интерфейс ICorDebugAssembly'
title: Интерфейс ICorDebugAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: 746b5f4b2f26550788708d93bf0dd50f5f495041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711951"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="a7ba9-103">Интерфейс ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="a7ba9-103">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="a7ba9-104">Представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-104">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7ba9-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a7ba9-105">Methods</span></span>  
  
|<span data-ttu-id="a7ba9-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a7ba9-106">Method</span></span>|<span data-ttu-id="a7ba9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a7ba9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7ba9-108">Метод EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="a7ba9-108">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="a7ba9-109">Возвращает перечислитель для модулей, содержащихся в сборке.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-109">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="a7ba9-110">Метод GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7ba9-110">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="a7ba9-111">Возвращает указатель интерфейса на домен приложения, содержащий данный `ICorDebugAssembly` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-111">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="a7ba9-112">Метод GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="a7ba9-112">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="a7ba9-113">Не реализовано в текущей версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-113">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="a7ba9-114">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="a7ba9-114">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="a7ba9-115">Возвращает имя сборки.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-115">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="a7ba9-116">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="a7ba9-116">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="a7ba9-117">Возвращает экземпляр ICorDebugProcess, в котором выполняется сборка.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-117">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ba9-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7ba9-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7ba9-119">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="a7ba9-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ba9-120">Требования</span><span class="sxs-lookup"><span data-stu-id="a7ba9-120">Requirements</span></span>  

 <span data-ttu-id="a7ba9-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ba9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ba9-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ba9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ba9-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ba9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ba9-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ba9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ba9-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a7ba9-125">See also</span></span>

- [<span data-ttu-id="a7ba9-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a7ba9-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
