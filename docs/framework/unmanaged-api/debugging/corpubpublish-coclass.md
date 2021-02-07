---
description: 'Подробнее о: Корпубпублиш coclass'
title: Кокласс CorpubPublish
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: fdf4be6ff2d20391e989998cd0045ed27d602561
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661705"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="119bb-103">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="119bb-103">CorpubPublish Coclass</span></span>

<span data-ttu-id="119bb-104">Предоставляет интерфейсы для публикации сведений о доменах приложений и процессах.</span><span class="sxs-lookup"><span data-stu-id="119bb-104">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="119bb-105">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="119bb-106">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="119bb-106">Interfaces</span></span>  
  
|<span data-ttu-id="119bb-107">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="119bb-107">Interface</span></span>|<span data-ttu-id="119bb-108">Описание</span><span class="sxs-lookup"><span data-stu-id="119bb-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="119bb-109">Интерфейс ICorPublish</span><span class="sxs-lookup"><span data-stu-id="119bb-109">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="119bb-110">Предоставляет методы для публикации сведений о процессах и доменах приложений в этих процессах.</span><span class="sxs-lookup"><span data-stu-id="119bb-110">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="119bb-111">Интерфейс ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="119bb-111">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="119bb-112">Представляет и предоставляет сведения о домене приложения в процессе.</span><span class="sxs-lookup"><span data-stu-id="119bb-112">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="119bb-113">Интерфейс ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="119bb-113">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="119bb-114">Предоставляет методы, которые проходят через коллекцию доменов приложений, которые в данный момент существуют в процессе.</span><span class="sxs-lookup"><span data-stu-id="119bb-114">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="119bb-115">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="119bb-115">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="119bb-116">Представляет процесс, выполняющийся на компьютере.</span><span class="sxs-lookup"><span data-stu-id="119bb-116">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="119bb-117">Интерфейс ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="119bb-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="119bb-118">Предоставляет методы, которые проходят по коллекции процессов, выполняющихся на компьютере.</span><span class="sxs-lookup"><span data-stu-id="119bb-118">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="119bb-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="119bb-119">Remarks</span></span>  

 <span data-ttu-id="119bb-120">Типичный сценарий публикации включает в себя разработчика, желающего отлаживать управляемый код, выполняющийся на компьютере в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="119bb-120">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="119bb-121">Среда размещения может запускать несколько доменов приложений в рамках одного процесса.</span><span class="sxs-lookup"><span data-stu-id="119bb-121">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="119bb-122">Разработчику хотелось бы использовать графический пользовательский интерфейс или другие средства для перечисления всех процессов, запущенных на компьютере, и выбрать конкретный процесс.</span><span class="sxs-lookup"><span data-stu-id="119bb-122">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="119bb-123">Список должен включать все домены приложений в процессах, выполняющих управляемый код.</span><span class="sxs-lookup"><span data-stu-id="119bb-123">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="119bb-124">Затем разработчик может определить конкретный домен приложения и подключить к этому домену отладчик.</span><span class="sxs-lookup"><span data-stu-id="119bb-124">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119bb-125">Требования</span><span class="sxs-lookup"><span data-stu-id="119bb-125">Requirements</span></span>  

 <span data-ttu-id="119bb-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119bb-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119bb-127">**Заголовок:** Корпуб. idl</span><span class="sxs-lookup"><span data-stu-id="119bb-127">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="119bb-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="119bb-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="119bb-129">**Платформа .NET Framework версии:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119bb-129">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119bb-130">См. также</span><span class="sxs-lookup"><span data-stu-id="119bb-130">See also</span></span>

- [<span data-ttu-id="119bb-131">Отладка</span><span class="sxs-lookup"><span data-stu-id="119bb-131">Debugging</span></span>](index.md)
