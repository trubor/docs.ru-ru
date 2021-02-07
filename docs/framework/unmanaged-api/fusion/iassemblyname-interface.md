---
description: Дополнительные сведения о интерфейсе IAssemblyName
title: Интерфейс IAssemblyName
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: fb5949572adc533bab5ed26ee969267f430f36ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760710"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="c724e-103">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c724e-103">IAssemblyName Interface</span></span>

<span data-ttu-id="c724e-104">Предоставляет методы для описания и работы с уникальным удостоверением сборки.</span><span class="sxs-lookup"><span data-stu-id="c724e-104">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c724e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="c724e-105">Methods</span></span>  
  
|<span data-ttu-id="c724e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="c724e-106">Method</span></span>|<span data-ttu-id="c724e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c724e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c724e-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="c724e-108">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="c724e-109">Создает неполную копию этого `IAssemblyName` объекта.</span><span class="sxs-lookup"><span data-stu-id="c724e-109">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c724e-110">Метод Finalize</span><span class="sxs-lookup"><span data-stu-id="c724e-110">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="c724e-111">Разрешает этому `IAssemblyName` объекту освобождать ресурсы и выполнять другие операции очистки перед вызовом деструктора.</span><span class="sxs-lookup"><span data-stu-id="c724e-111">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="c724e-112">Метод GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="c724e-112">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="c724e-113">Возвращает удобное для восприятия имя сборки, на которую ссылается этот `IAssemblyName` объект.</span><span class="sxs-lookup"><span data-stu-id="c724e-113">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c724e-114">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="c724e-114">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="c724e-115">Возвращает простое незашифрованное имя сборки, на которую ссылается этот `IAssemblyName` объект.</span><span class="sxs-lookup"><span data-stu-id="c724e-115">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c724e-116">Метод Property</span><span class="sxs-lookup"><span data-stu-id="c724e-116">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="c724e-117">Возвращает указатель на свойство, на которое ссылается указанный объект `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="c724e-117">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="c724e-118">Метод GetVersion</span><span class="sxs-lookup"><span data-stu-id="c724e-118">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="c724e-119">Возвращает сведения о версии для сборки, на которую ссылается этот `IAssemblyName` объект.</span><span class="sxs-lookup"><span data-stu-id="c724e-119">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c724e-120">Метод IsEqual</span><span class="sxs-lookup"><span data-stu-id="c724e-120">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="c724e-121">Определяет `IAssemblyName` , равен ли указанный объект этому объекту `IAssemblyName` на основе указанных флагов сравнения.</span><span class="sxs-lookup"><span data-stu-id="c724e-121">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="c724e-122">Метод SetProperty</span><span class="sxs-lookup"><span data-stu-id="c724e-122">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="c724e-123">Задает значение свойства, на которое ссылается указанный объект `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="c724e-123">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c724e-124">Требования</span><span class="sxs-lookup"><span data-stu-id="c724e-124">Requirements</span></span>  

 <span data-ttu-id="c724e-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c724e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c724e-126">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c724e-126">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c724e-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c724e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c724e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="c724e-128">See also</span></span>

- [<span data-ttu-id="c724e-129">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c724e-129">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="c724e-130">Интерфейс IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="c724e-130">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
