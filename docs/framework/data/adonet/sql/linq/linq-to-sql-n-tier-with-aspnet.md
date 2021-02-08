---
description: 'Дополнительные сведения: LINQ to SQL N-Tiered with ASP.NET'
title: N-уровневое использование LINQ to SQL с ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: a455525f8f0bbef38487b058d89fd2c9b4dda377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803806"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="1141d-103">N-уровневое использование LINQ to SQL с ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1141d-103">LINQ to SQL N-Tier with ASP.NET</span></span>

<span data-ttu-id="1141d-104">В приложениях ASP.NET, использующих [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , используется <xref:System.Web.UI.WebControls.LinqDataSource> Серверный веб-элемент управления.</span><span class="sxs-lookup"><span data-stu-id="1141d-104">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="1141d-105">Элемент управления обрабатывает большую часть логики, которую необходимо выполнить для запроса [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , передачи данных в браузер, их извлечения и отправки в, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> который затем обновляет базу данных.</span><span class="sxs-lookup"><span data-stu-id="1141d-105">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="1141d-106">Чтобы элемент управления полностью обрабатывал передачу данных между [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] и браузером, достаточно настроить его в разметке.</span><span class="sxs-lookup"><span data-stu-id="1141d-106">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="1141d-107">Поскольку элемент управления обрабатывает взаимодействие с уровнем представления и [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] обрабатывает связь с уровнем данных, основное внимание в ASP.NET многоуровневых приложениях заключается в написании пользовательской бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="1141d-107">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="1141d-108">Дополнительные сведения о `LINQDataSource` см. в разделе [Общие сведения о серверном веб-элементе управления LinqDataSource](/previous-versions/aspnet/bb547113(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1141d-108">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1141d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="1141d-109">See also</span></span>

- [<span data-ttu-id="1141d-110">N-уровневые и удаленные приложения с LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1141d-110">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
