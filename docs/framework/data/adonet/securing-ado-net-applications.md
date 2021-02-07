---
description: 'Дополнительные сведения: Защита приложений ADO.NET'
title: Защита приложений
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 4e4d219d1f4249846943d019e174abd6d43687c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718880"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="dd454-103">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd454-103">Securing ADO.NET applications</span></span>

<span data-ttu-id="dd454-104">При написании безопасного приложения ADO.NET следует не просто избегать обычных проблем кодирования, таких как отсутствие проверки входных данных пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd454-104">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="dd454-105">В приложении, имеющем доступ к данным, существует много потенциальных точек сбоя, которые злоумышленник может использовать для извлечения, манипуляции или разрушения конфиденциальных данных.</span><span class="sxs-lookup"><span data-stu-id="dd454-105">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="dd454-106">Поэтому важно понимать все аспекты безопасности, от моделирования угроз на этапе проектирования приложения до развертывания и текущего обслуживания.</span><span class="sxs-lookup"><span data-stu-id="dd454-106">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="dd454-107">.NET Framework предоставляет много полезных классов, служб и средств для обеспечения безопасности и администрирования приложений баз данных.</span><span class="sxs-lookup"><span data-stu-id="dd454-107">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="dd454-108">Среда CLR предоставляет средой типобезопасности для выполняющегося в ней кода. Управление доступом для кода (CAS) позволяет дополнительно ограничить разрешения для управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="dd454-108">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="dd454-109">Следующие приемы безопасного программирования доступа к данным ограничивают ущерб, который может быть нанесен возможным злоумышленником.</span><span class="sxs-lookup"><span data-stu-id="dd454-109">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="dd454-110">Написание безопасного кода не защищает от брешей в безопасности при работе с неуправляемыми ресурсами, такими как базы данных.</span><span class="sxs-lookup"><span data-stu-id="dd454-110">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="dd454-111">Большинство баз данных, таких как SQL Server, имеют свои собственные системы безопасности, повышающие защиту при правильной их реализации.</span><span class="sxs-lookup"><span data-stu-id="dd454-111">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="dd454-112">Но даже источник данных с надежной системой безопасности может быть подвержен атакам, если он не будет настроен должным образом.</span><span class="sxs-lookup"><span data-stu-id="dd454-112">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd454-113">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="dd454-113">In this section</span></span>

 [<span data-ttu-id="dd454-114">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="dd454-114">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="dd454-115">Предоставляет рекомендации по проектированию безопасных приложений ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="dd454-115">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="dd454-116">Безопасный доступ к данным</span><span class="sxs-lookup"><span data-stu-id="dd454-116">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="dd454-117">Описывает, как работать с данными из защищенного источника данных.</span><span class="sxs-lookup"><span data-stu-id="dd454-117">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="dd454-118">Безопасные клиентские приложения</span><span class="sxs-lookup"><span data-stu-id="dd454-118">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="dd454-119">Описывает вопросы безопасности для клиентских приложений.</span><span class="sxs-lookup"><span data-stu-id="dd454-119">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="dd454-120">Управление доступом для кода и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd454-120">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="dd454-121">Описывает, как CAS может способствовать защите кода ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="dd454-121">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="dd454-122">Также рассматриваются способы работы с частичным уровнем доверия.</span><span class="sxs-lookup"><span data-stu-id="dd454-122">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="dd454-123">Конфиденциальность и безопасность данных</span><span class="sxs-lookup"><span data-stu-id="dd454-123">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="dd454-124">Описывает параметры шифрования для приложений ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="dd454-124">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd454-125">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="dd454-125">Related sections</span></span>

 [<span data-ttu-id="dd454-126">Набор данных и руководство по безопасности DataTable</span><span class="sxs-lookup"><span data-stu-id="dd454-126">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="dd454-127">Предоставляет руководство по безопасности для <xref:System.Data.DataSet> и <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="dd454-127">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="dd454-128">Безопасность SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd454-128">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="dd454-129">Описывает средства безопасности SQL Server с точки зрения разработчика.</span><span class="sxs-lookup"><span data-stu-id="dd454-129">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="dd454-130">Вопросы безопасности</span><span class="sxs-lookup"><span data-stu-id="dd454-130">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="dd454-131">Описывает средства безопасности для приложений Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="dd454-131">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="dd454-132">Безопасность</span><span class="sxs-lookup"><span data-stu-id="dd454-132">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="dd454-133">Содержит ссылки на статьи с описанием всех аспектов безопасности в .NET.</span><span class="sxs-lookup"><span data-stu-id="dd454-133">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="dd454-134">[Средства обеспечения безопасности](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="dd454-134">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="dd454-135">Средства .NET Framework для безопасности и администрирования политики безопасности.</span><span class="sxs-lookup"><span data-stu-id="dd454-135">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="dd454-136">[Ресурсы для создания защищенных приложений](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd454-136">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="dd454-137">Содержит ссылки на статьи, посвященные созданию защищенных приложений.</span><span class="sxs-lookup"><span data-stu-id="dd454-137">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="dd454-138">Библиография по вопросам безопасности</span><span class="sxs-lookup"><span data-stu-id="dd454-138">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="dd454-139">Предоставляет ссылки на внешние ресурсы, доступные в Интернете и в печатной форме.</span><span class="sxs-lookup"><span data-stu-id="dd454-139">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd454-140">См. также</span><span class="sxs-lookup"><span data-stu-id="dd454-140">See also</span></span>

- [<span data-ttu-id="dd454-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd454-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="dd454-142">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd454-142">ADO.NET Overview</span></span>](ado-net-overview.md)
