---
description: 'Подробнее: устаревшие типы в Windows Workflow Foundation'
title: Устаревшие типы в Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: a536f67708c5913040848df52f178dcc2a361f6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742437"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="c0532-103">Устаревшие типы в Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="c0532-103">Deprecated types in Windows Workflow Foundation</span></span>

<span data-ttu-id="c0532-104">В .NET 4 команда разработки по рабочим процессам представила полностью новую подсистему рабочих процессов в пространстве имен <xref:System.Activities>.</span><span class="sxs-lookup"><span data-stu-id="c0532-104">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="c0532-105">При выпуске бета-версии платформа .NET Framework 4,5 Мы помечаем большинство типов в "WF 3" <xref:System.Workflow.Activities> , <xref:System.Workflow.ComponentModel> и "  <xref:System.Workflow.Runtime> пространства имен" как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="c0532-105">With the release of .NET Framework 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>

## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="c0532-106">Устаревшие пространства имен и средства</span><span class="sxs-lookup"><span data-stu-id="c0532-106">Obsolete namespaces and tools</span></span>

 <span data-ttu-id="c0532-107">Следующие сборки содержат один и более открытых типов, которые станут устаревшими.</span><span class="sxs-lookup"><span data-stu-id="c0532-107">The following assemblies have one or more public types that will be deprecated:</span></span>

- <span data-ttu-id="c0532-108">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c0532-108">System.Workflow.Activities.dll</span></span>

- <span data-ttu-id="c0532-109">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="c0532-109">System.Workflow.ComponentModel.dll</span></span>

- <span data-ttu-id="c0532-110">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="c0532-110">System.Workflow.Runtime.dll</span></span>

- <span data-ttu-id="c0532-111">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="c0532-111">System.WorkflowServices.dll</span></span>

- <span data-ttu-id="c0532-112">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="c0532-112">Microsoft.Workflow.DebugController.dll</span></span>

- <span data-ttu-id="c0532-113">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="c0532-113">Microsoft.Workflow.Compiler.exe</span></span>

- <span data-ttu-id="c0532-114">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="c0532-114">Wfc.exe</span></span>

 <span data-ttu-id="c0532-115">В результате этого клиенты, использующие устаревшие API WF 3, увидят предупреждения при сборке с сообщением следующего вида:</span><span class="sxs-lookup"><span data-stu-id="c0532-115">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>

 <span data-ttu-id="c0532-116">**Предупреждение BC40000: X устарело: типы WF 3 являются устаревшими. Вместо этого используйте WF 4.**</span><span class="sxs-lookup"><span data-stu-id="c0532-116">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="c0532-117">В одном из последующих выпусков (не в 4.5) типы будут удалены из .NET Framework, но временной промежуток до этого еще не определен.</span><span class="sxs-lookup"><span data-stu-id="c0532-117">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="c0532-118">Текущий шаг позволяет донести наши планы до клиентов и дает им достаточно времени для перехода на новую модель WF4.</span><span class="sxs-lookup"><span data-stu-id="c0532-118">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="c0532-119">Конечно, мы будем продолжать поддерживать эти типы WF 3 в [политике жизненного цикла служба поддержки Майкрософт](/lifecycle/).</span><span class="sxs-lookup"><span data-stu-id="c0532-119">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](/lifecycle/).</span></span> <span data-ttu-id="c0532-120">Существующие приложения WF3 будут выполняться без проблем в платформа .NET Framework 4,5, а Visual Studio 2012 будет поддерживать новые и существующие решения на основе WF3.</span><span class="sxs-lookup"><span data-stu-id="c0532-120">Existing WF3 applications will run without issue on .NET Framework 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>

 <span data-ttu-id="c0532-121">Основанные на правилах типы в пространстве имен <xref:System.Workflow.Activities.Rules>, не имеющие замены в WF 4.5, не устарели.</span><span class="sxs-lookup"><span data-stu-id="c0532-121">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>

 <span data-ttu-id="c0532-122">Клиенты, желающие перенести свои приложения в WF 4, смогут найти справку в [руководстве по миграции рабочего процесса 4](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="c0532-122">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
