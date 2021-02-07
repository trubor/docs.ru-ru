---
description: Дополнительные сведения см. в статье Создание действий рабочего процесса с помощью класса Activity.
title: Разработка действий рабочих процессов с помощью класса Activity
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 0d3ffc88bacfd941dfa0c853991bf72045468323
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754944"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="dfcf2-103">Разработка действий рабочих процессов с помощью класса Activity</span><span class="sxs-lookup"><span data-stu-id="dfcf2-103">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="dfcf2-104">Самый простой способ создать действие с помощью Windows Workflow Foundation (WF) в [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] — создать класс, который наследует от класса <xref:System.Activities.Activity> , который создает функциональные возможности путем сборки пользовательских действий или действий из [встроенной библиотеки действий](net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="dfcf2-104">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="dfcf2-105">В этом разделе показано, как создать действие для вывода двух сообщений на консоль.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-105">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="dfcf2-106">Для создания пользовательского действия с помощью конструктора действий сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="dfcf2-106">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="dfcf2-107">Откройте Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-107">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="dfcf2-108">Выберите в меню «Файл» пункт «Создать», затем пункт «Создать проект».</span><span class="sxs-lookup"><span data-stu-id="dfcf2-108">Select File, New, Project.</span></span> <span data-ttu-id="dfcf2-109">Выберите **Рабочий процесс 4,0** в разделе **Visual C#** в окне **типы проектов** и выберите узел **v2010** .</span><span class="sxs-lookup"><span data-stu-id="dfcf2-109">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="dfcf2-110">В окне **шаблоны** выберите пункт **Библиотека действий** .</span><span class="sxs-lookup"><span data-stu-id="dfcf2-110">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="dfcf2-111">Задайте имя для нового проекта HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-111">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="dfcf2-112">Откройте окно создания нового действия.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-112">Open the new activity.</span></span>  <span data-ttu-id="dfcf2-113">Перетащите действие <xref:System.Activities.Statements.Sequence> из области элементов в область конструктора.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-113">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="dfcf2-114">Перетащите действие <xref:System.Activities.Statements.WriteLine> в действие <xref:System.Activities.Statements.Sequence> activity.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-114">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="dfcf2-115">Введите `"Hello World"` (с кавычками) в **текстовое** поле.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-115">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="dfcf2-116">Перетащите второе действие <xref:System.Activities.Statements.WriteLine> в действие <xref:System.Activities.Statements.Sequence> под первым.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-116">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="dfcf2-117">Введите `"Goodbye"` (с кавычками) в **текстовое** поле.</span><span class="sxs-lookup"><span data-stu-id="dfcf2-117">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
