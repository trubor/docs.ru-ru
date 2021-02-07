---
description: Дополнительные сведения о действиях примитивов в WF
title: Базовые действия в WF
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: 5f613eeb8f4153f349fad8232f6dec1123b1a8a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742073"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="66837-103">Базовые действия в WF</span><span class="sxs-lookup"><span data-stu-id="66837-103">Primitives Activities in WF</span></span>

<span data-ttu-id="66837-104">В [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] предусмотрено несколько предоставляемых системой действий, которые представляют собой удобный механизм выполнения общих задач.</span><span class="sxs-lookup"><span data-stu-id="66837-104">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="66837-105">Действие</span><span class="sxs-lookup"><span data-stu-id="66837-105">Activity</span></span>|<span data-ttu-id="66837-106">Описание</span><span class="sxs-lookup"><span data-stu-id="66837-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="66837-107">Назначает значение переменной в текущей области.</span><span class="sxs-lookup"><span data-stu-id="66837-107">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="66837-108">Переводит один путь выполнения в состояние бездействия, что может позволить выгрузить рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="66837-108">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="66837-109">Выполняет делегат, который является производным от <xref:System.Activities.ActivityDelegate> и доступен как свойство.</span><span class="sxs-lookup"><span data-stu-id="66837-109">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="66837-110">Выполняет открытый метод объекта CLR.</span><span class="sxs-lookup"><span data-stu-id="66837-110">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="66837-111">Отображает указанную строку на консоли или записывает в указанный объект <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="66837-111">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
