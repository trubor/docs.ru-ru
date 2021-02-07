---
description: 'Дополнительные сведения: безопасность интеграции со средой CLR в SQL Server'
title: Безопасность интеграции CLR в SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 5de552c0f5b869712d2038b53abd50b8ded04747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718542"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="6a739-103">Безопасность интеграции CLR в SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a739-103">CLR Integration Security in SQL Server</span></span>

<span data-ttu-id="6a739-104">Microsoft SQL Server обеспечивает интеграцию компонентов среды CLR платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a739-104">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="6a739-105">Интеграция со средой CLR позволяет записывать хранимые процедуры, триггеры, определяемые пользователем типы, определяемые пользователем функции и потоковые возвращающие табличное значение функции, используя любой язык NET Framework, например Microsoft Visual Basic .NET или Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6a739-105">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="6a739-106">Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS).</span><span class="sxs-lookup"><span data-stu-id="6a739-106">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="6a739-107">В этой модели разрешения предоставляются сборкам на основе свидетельства, поставляемого кодом в метаданных.</span><span class="sxs-lookup"><span data-stu-id="6a739-107">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="6a739-108">SQL Server интегрирует пользовательскую модель безопасности SQL Server с кодом модели безопасности на основе доступа среды CLR.</span><span class="sxs-lookup"><span data-stu-id="6a739-108">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6a739-109">Внешние ресурсы</span><span class="sxs-lookup"><span data-stu-id="6a739-109">External Resources</span></span>  

 <span data-ttu-id="6a739-110">Дополнительные сведения об интеграции со средой CLR в SQL Server см. в следующих ресурсах.</span><span class="sxs-lookup"><span data-stu-id="6a739-110">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="6a739-111">Ресурс</span><span class="sxs-lookup"><span data-stu-id="6a739-111">Resource</span></span>|<span data-ttu-id="6a739-112">Описание</span><span class="sxs-lookup"><span data-stu-id="6a739-112">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="6a739-113">Управление доступом для кода</span><span class="sxs-lookup"><span data-stu-id="6a739-113">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="6a739-114">Содержит подразделы, описывающие средства CAS на платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a739-114">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="6a739-115">Безопасность интеграции со средой CLR</span><span class="sxs-lookup"><span data-stu-id="6a739-115">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="6a739-116">Содержит обсуждение модели безопасности для управляемого кода, выполняемого внутри SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a739-116">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a739-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6a739-117">See also</span></span>

- [<span data-ttu-id="6a739-118">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a739-118">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="6a739-119">Сценарии безопасности приложений в SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a739-119">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="6a739-120">Интеграция среды CLR и SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a739-120">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="6a739-121">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a739-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
