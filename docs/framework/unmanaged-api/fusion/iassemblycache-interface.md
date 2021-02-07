---
description: 'Дополнительные сведения о: интерфейс IAssemblyCache'
title: Интерфейс IAssemblyCache
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: 29c042fc101180085a697e02376b91b0e1ffd19f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760931"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="63f1b-103">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="63f1b-103">IAssemblyCache Interface</span></span>

<span data-ttu-id="63f1b-104">Представляет глобальный кэш сборок для использования технологией Fusion.</span><span class="sxs-lookup"><span data-stu-id="63f1b-104">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63f1b-105">Методы</span><span class="sxs-lookup"><span data-stu-id="63f1b-105">Methods</span></span>  
  
|<span data-ttu-id="63f1b-106">Метод</span><span class="sxs-lookup"><span data-stu-id="63f1b-106">Method</span></span>|<span data-ttu-id="63f1b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="63f1b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63f1b-108">Метод CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="63f1b-108">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="63f1b-109">Возвращает ссылку на новый [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="63f1b-109">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="63f1b-110">Метод CreateAssemblyScavenger</span><span class="sxs-lookup"><span data-stu-id="63f1b-110">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="63f1b-111">Зарезервировано для внутреннего использования технологией Fusion.</span><span class="sxs-lookup"><span data-stu-id="63f1b-111">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="63f1b-112">Метод InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="63f1b-112">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="63f1b-113">Устанавливает указанную сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="63f1b-113">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="63f1b-114">Метод QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="63f1b-114">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="63f1b-115">Возвращает запрошенные данные о указанной сборке.</span><span class="sxs-lookup"><span data-stu-id="63f1b-115">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="63f1b-116">Метод UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="63f1b-116">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="63f1b-117">Удаляет указанную сборку из глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="63f1b-117">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63f1b-118">Требования</span><span class="sxs-lookup"><span data-stu-id="63f1b-118">Requirements</span></span>  

 <span data-ttu-id="63f1b-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f1b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f1b-120">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="63f1b-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="63f1b-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f1b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f1b-122">См. также</span><span class="sxs-lookup"><span data-stu-id="63f1b-122">See also</span></span>

- [<span data-ttu-id="63f1b-123">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="63f1b-123">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="63f1b-124">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="63f1b-124">Global Assembly Cache</span></span>](../../app-domains/gac.md)
