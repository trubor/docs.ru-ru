---
description: Дополнительные сведения см. в статье поддержка запросов.
title: Поддержка запросов
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 418e511e8b845653b9f3ec86d90c6cbfb25d5671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755217"
---
# <a name="support-for-queries"></a><span data-ttu-id="8b1a8-103">Поддержка запросов</span><span class="sxs-lookup"><span data-stu-id="8b1a8-103">Support for Queries</span></span>

<span data-ttu-id="8b1a8-104">Хранилище экземпляров рабочих процессов SQL записывает набор известных свойств в хранилище.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-104">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="8b1a8-105">Пользователи могут выполнить запрос экземпляров на основе этих свойств.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-105">Users can query for instances based on these properties.</span></span> <span data-ttu-id="8b1a8-106">В следующем списке приведены некоторые из этих известных свойств.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-106">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="8b1a8-107">**Имя сайта.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-107">**Site Name.**</span></span> <span data-ttu-id="8b1a8-108">Имя веб-узла, содержащего службу.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-108">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="8b1a8-109">**Относительный путь приложения.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-109">**Relative Application Path.**</span></span> <span data-ttu-id="8b1a8-110">Путь приложения относительно веб-узла.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-110">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="8b1a8-111">**Относительный путь службы.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-111">**Relative Service Path.**</span></span> <span data-ttu-id="8b1a8-112">Путь службы относительно приложения.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-112">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="8b1a8-113">**Имя службы.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-113">**Service Name.**</span></span> <span data-ttu-id="8b1a8-114">Имя службы.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-114">Name of the service.</span></span>  
  
- <span data-ttu-id="8b1a8-115">**Пространство имен службы.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-115">**Service Namespace.**</span></span> <span data-ttu-id="8b1a8-116">Имя пространства имен, которое использует служба.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-116">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="8b1a8-117">**Текущий компьютер.**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-117">**Current Machine.**</span></span>  
  
- <span data-ttu-id="8b1a8-118">**Последний компьютер**.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-118">**Last Machine**.</span></span> <span data-ttu-id="8b1a8-119">Компьютер, на котором экземпляр службы рабочего процесса был запущен последний раз.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-119">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b1a8-120">Для резидентных сценариев, использующих узел службы рабочего процесса, заполняются только последние четыре свойства.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-120">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="8b1a8-121">Для сценариев приложения рабочего процесса заполняется только последнее свойство.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-121">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="8b1a8-122">Среда выполнения рабочего процесса предоставляет значения для первых трех свойств.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-122">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="8b1a8-123">Узел службы рабочего процесса предоставляет значение для свойства **Причина приостановки** .</span><span class="sxs-lookup"><span data-stu-id="8b1a8-123">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="8b1a8-124">Хранилище экземпляров рабочих процессов SQL предоставляет значения для **последнего обновленного свойства компьютера** .</span><span class="sxs-lookup"><span data-stu-id="8b1a8-124">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="8b1a8-125">Возможность хранилища экземпляров рабочих процессов SQL также позволяет указать пользовательские свойства, значения которых требуется сохранять в базе данных сохраняемости и которые будут в дальнейшем использованы в запросах.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-125">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="8b1a8-126">Дополнительные сведения о пользовательских рекламных акциях см. в разделе [Хранение расширяемости](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="8b1a8-126">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="8b1a8-127">Представления</span><span class="sxs-lookup"><span data-stu-id="8b1a8-127">Views</span></span>  

 <span data-ttu-id="8b1a8-128">Хранилище экземпляров содержит следующие представления.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-128">The instance store contains the following views.</span></span> <span data-ttu-id="8b1a8-129">Дополнительные сведения см. в разделе [схема базы данных сохраняемости](persistence-database-schema.md) .</span><span class="sxs-lookup"><span data-stu-id="8b1a8-129">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="8b1a8-130">Представление экземпляров</span><span class="sxs-lookup"><span data-stu-id="8b1a8-130">The Instances View</span></span>  

 <span data-ttu-id="8b1a8-131">Представление экземпляров содержит следующие поля:</span><span class="sxs-lookup"><span data-stu-id="8b1a8-131">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="8b1a8-132">**Id**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-132">**Id**</span></span>  
  
2. <span data-ttu-id="8b1a8-133">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-133">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="8b1a8-134">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-134">**CreationTime**</span></span>  
  
4. <span data-ttu-id="8b1a8-135">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-135">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="8b1a8-136">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-136">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="8b1a8-137">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-137">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="8b1a8-138">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-138">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="8b1a8-139">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-139">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="8b1a8-140">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-140">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="8b1a8-141">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-141">**LastMachine**</span></span>  
  
11. <span data-ttu-id="8b1a8-142">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-142">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="8b1a8-143">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-143">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="8b1a8-144">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-144">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="8b1a8-145">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-145">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="8b1a8-146">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-146">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="8b1a8-147">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-147">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="8b1a8-148">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-148">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="8b1a8-149">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-149">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="8b1a8-150">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-150">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="8b1a8-151">Представление ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="8b1a8-151">The ServiceDeployments view</span></span>  

 <span data-ttu-id="8b1a8-152">Представление ServiceDeployments содержит следующие поля:</span><span class="sxs-lookup"><span data-stu-id="8b1a8-152">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="8b1a8-153">**Значением**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-153">**SiteName**</span></span>  
  
2. <span data-ttu-id="8b1a8-154">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-154">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="8b1a8-155">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-155">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="8b1a8-156">**Служба**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-156">**ServiceName**</span></span>  
  
5. <span data-ttu-id="8b1a8-157">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-157">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="8b1a8-158">Представление InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="8b1a8-158">The InstancePromotedProperties view</span></span>  

 <span data-ttu-id="8b1a8-159">Представление InstancePromotedProperties содержит следующие поля.</span><span class="sxs-lookup"><span data-stu-id="8b1a8-159">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="8b1a8-160">Дополнительные сведения о повышенных свойствах см. в статье о [расширении хранилища](store-extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="8b1a8-160">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="8b1a8-161">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-161">**InstanceId**</span></span>  
  
2. <span data-ttu-id="8b1a8-162">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-162">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="8b1a8-163">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="8b1a8-163">**PromotionName**</span></span>  
  
4. <span data-ttu-id="8b1a8-164">**Значение #** (диапазон полей от **Значение1** до **Value64**).</span><span class="sxs-lookup"><span data-stu-id="8b1a8-164">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
