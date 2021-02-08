---
description: 'Дополнительные сведения: интерфейсы размещения'
title: Интерфейсы размещения
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: 596de1e74fc9c80e5f8b63f40c91a9ef29abcc6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785189"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="a6d6c-103">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="a6d6c-103">Hosting Interfaces</span></span>

<span data-ttu-id="a6d6c-104">В этом разделе описываются интерфейсы, которые неуправляемые узлы могут использовать для интеграции среды CLR в свои приложения.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="a6d6c-105">Интерфейсы размещения платформа .NET Framework версии 2,0 заменяют интерфейсы платформа .NET Framework версии 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-105">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="a6d6c-106">Между двумя наборами интерфейсов существуют значительные различия.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-106">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="a6d6c-107">Смешивание этих параметров может привести к непредвиденному поведению и не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-107">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="a6d6c-108">Платформа .NET Framework версии 3,0 и 3,5 используют интерфейсы размещения платформа .NET Framework версии 2,0 и не предоставляют никаких функций размещения.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-108">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="a6d6c-109">Интерфейсы размещения платформа .NET Framework 4 заменяют интерфейсы платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-109">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a6d6c-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a6d6c-110">In This Section</span></span>  

 [<span data-ttu-id="a6d6c-111">Устаревшие интерфейсы размещения CLR и CoClasses</span><span class="sxs-lookup"><span data-stu-id="a6d6c-111">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a6d6c-112">Описание интерфейсов размещения, представленных в платформа .NET Framework версиях 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-112">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a6d6c-113">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="a6d6c-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="a6d6c-114">Описание интерфейсов размещения, представленных в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-114">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="a6d6c-115">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="a6d6c-115">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="a6d6c-116">Описание интерфейсов размещения, появившихся в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a6d6c-116">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6d6c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a6d6c-117">Related Sections</span></span>  

 [<span data-ttu-id="a6d6c-118">Размещение коклассов</span><span class="sxs-lookup"><span data-stu-id="a6d6c-118">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="a6d6c-119">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="a6d6c-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="a6d6c-120">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="a6d6c-120">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="a6d6c-121">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="a6d6c-121">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="a6d6c-122">Размещение</span><span class="sxs-lookup"><span data-stu-id="a6d6c-122">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="a6d6c-123">[Хост-приложения среды выполнения](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a6d6c-123">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
