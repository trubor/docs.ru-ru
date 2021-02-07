---
description: 'Дополнительные сведения о: интерфейс ICLRDebugging'
title: Интерфейс ICLRDebugging
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 647b6f7634ef3b9f6ec6080aaff19476c027952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723339"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="b4145-103">Интерфейс ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="b4145-103">ICLRDebugging Interface</span></span>

<span data-ttu-id="b4145-104">Предоставляет методы, обрабатывающие загрузку и выгрузку модулей для отладки.</span><span class="sxs-lookup"><span data-stu-id="b4145-104">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4145-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b4145-105">Methods</span></span>  
  
|<span data-ttu-id="b4145-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b4145-106">Method</span></span>|<span data-ttu-id="b4145-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b4145-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4145-108">Метод OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="b4145-108">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="b4145-109">Возвращает интерфейс "ICorDebugProcess", соответствующий модулю среды CLR, загруженному в процессе.</span><span class="sxs-lookup"><span data-stu-id="b4145-109">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="b4145-110">Метод CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="b4145-110">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="b4145-111">Определяет, используется ли по-прежнему Библиотека, предоставленная интерфейсом [иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md) , или она может быть выгружена.</span><span class="sxs-lookup"><span data-stu-id="b4145-111">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4145-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4145-112">Remarks</span></span>  

 <span data-ttu-id="b4145-113">Экземпляр интерфейса можно получить с `ICLRDebugging` помощью функции [клркреатеинстанце](../hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b4145-113">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4145-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b4145-114">Requirements</span></span>  

 <span data-ttu-id="b4145-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4145-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4145-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4145-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4145-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4145-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4145-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4145-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4145-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b4145-119">See also</span></span>

- [<span data-ttu-id="b4145-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b4145-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b4145-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="b4145-121">Debugging</span></span>](index.md)
