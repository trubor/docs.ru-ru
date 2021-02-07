---
description: Дополнительные сведения об интерфейсах Fusion
title: Fusion-интерфейсы
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 3b6ca64b40ebc1a7b38129d897059ca628d3914c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761069"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="c8034-103">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c8034-103">Fusion Interfaces</span></span>

<span data-ttu-id="c8034-104">В этом разделе описываются неуправляемые интерфейсы, используемые API Fusion для доступа к свойствам ресурсов приложения и для размещения правильных версий этих ресурсов для приложения.</span><span class="sxs-lookup"><span data-stu-id="c8034-104">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8034-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c8034-105">In This Section</span></span>  

 [<span data-ttu-id="c8034-106">Интерфейс IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="c8034-106">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="c8034-107">Предоставляет методы, создающие и сравнивающие ключи для удостоверений приложений и ссылок.</span><span class="sxs-lookup"><span data-stu-id="c8034-107">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="c8034-108">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="c8034-108">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="c8034-109">Предоставляет представление глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="c8034-109">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="c8034-110">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="c8034-110">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="c8034-111">Представляет отдельную сборку в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="c8034-111">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="c8034-112">Интерфейс IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="c8034-112">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="c8034-113">Представляет перечислитель для массива `IAssemblyName` объектов.</span><span class="sxs-lookup"><span data-stu-id="c8034-113">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="c8034-114">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c8034-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="c8034-115">Предоставляет методы для описания и работы с уникальным удостоверением сборки.</span><span class="sxs-lookup"><span data-stu-id="c8034-115">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="c8034-116">Интерфейс IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="c8034-116">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="c8034-117">Представляет уникальный идентификатор для кода, определяющего приложение в текущей области.</span><span class="sxs-lookup"><span data-stu-id="c8034-117">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="c8034-118">Интерфейс IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="c8034-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="c8034-119">Представляет уникальную сигнатуру кода, определяющего приложение в текущей области.</span><span class="sxs-lookup"><span data-stu-id="c8034-119">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="c8034-120">Интерфейс IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="c8034-120">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="c8034-121">Служит в качестве перечислителя для коллекции `IDefinitionIdentity` объектов.</span><span class="sxs-lookup"><span data-stu-id="c8034-121">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="c8034-122">Интерфейс IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="c8034-122">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="c8034-123">Служит в качестве перечислителя для атрибутов объекта Code в текущей области.</span><span class="sxs-lookup"><span data-stu-id="c8034-123">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="c8034-124">Интерфейс IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="c8034-124">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="c8034-125">Служит в качестве перечислителя для коллекции `IReferenceIdentity` объектов.</span><span class="sxs-lookup"><span data-stu-id="c8034-125">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="c8034-126">Интерфейс IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="c8034-126">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="c8034-127">Управляет ключами удостоверений для объектов кода.</span><span class="sxs-lookup"><span data-stu-id="c8034-127">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="c8034-128">Интерфейс IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="c8034-128">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="c8034-129">Представляет перечислитель для сборок, на которые имеются ссылки, установленных в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="c8034-129">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="c8034-130">Интерфейс IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="c8034-130">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="c8034-131">Представляет элемент, установленный в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="c8034-131">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="c8034-132">Интерфейс IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="c8034-132">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="c8034-133">Представляет ссылку на уникальный идентификатор приложения в текущей области.</span><span class="sxs-lookup"><span data-stu-id="c8034-133">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="c8034-134">Интерфейс IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="c8034-134">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="c8034-135">Представляет ссылку на уникальную сигнатуру объекта кода.</span><span class="sxs-lookup"><span data-stu-id="c8034-135">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c8034-136">Справочник</span><span class="sxs-lookup"><span data-stu-id="c8034-136">Reference</span></span>  

 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="c8034-137">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="c8034-137">Related Sections</span></span>  

 [<span data-ttu-id="c8034-138">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="c8034-138">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="c8034-139">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="c8034-139">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="c8034-140">Структуры Fusion</span><span class="sxs-lookup"><span data-stu-id="c8034-140">Fusion Structures</span></span>](fusion-structures.md)
