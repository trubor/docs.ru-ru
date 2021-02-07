---
description: 'Дополнительные сведения о: интерфейс Иклрдебуггинглибрарипровидер'
title: Интерфейс ICLRDebuggingLibraryProvider
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: 8aaec87e97d45c8b7b6f87aee64154ea3f48b133
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723287"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="d98d4-103">Интерфейс ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="d98d4-103">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="d98d4-104">Включает метод [метода ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) , который получает интерфейс обратного вызова поставщика библиотеки, который позволяет находить и загружать библиотеки отладки, относящиеся к конкретной версии среды CLR, по запросу.</span><span class="sxs-lookup"><span data-stu-id="d98d4-104">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d98d4-105">Методы</span><span class="sxs-lookup"><span data-stu-id="d98d4-105">Methods</span></span>  
  
|<span data-ttu-id="d98d4-106">Метод</span><span class="sxs-lookup"><span data-stu-id="d98d4-106">Method</span></span>|<span data-ttu-id="d98d4-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d98d4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d98d4-108">Метод ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="d98d4-108">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="d98d4-109">Позволяет отладчику предоставлять обработчик для модуля, который можно использовать для загрузки библиотеки отладки.</span><span class="sxs-lookup"><span data-stu-id="d98d4-109">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d98d4-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d98d4-110">Requirements</span></span>  

 <span data-ttu-id="d98d4-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98d4-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d98d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98d4-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d98d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98d4-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98d4-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d98d4-115">See also</span></span>

- [<span data-ttu-id="d98d4-116">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d98d4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d98d4-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="d98d4-117">Debugging</span></span>](index.md)
