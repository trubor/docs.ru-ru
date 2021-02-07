---
description: Дополнительные сведения о действиях конечного автомата в WF
title: Действия конечного автомата в WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 4571bdbabc30e721523ae18449454627c0bf7319
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755256"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="4dfa1-103">Действия конечного автомата в WF</span><span class="sxs-lookup"><span data-stu-id="4dfa1-103">State Machine Activities in WF</span></span>

<span data-ttu-id="4dfa1-104">Платформа .NET Framework 4,5 предоставляет несколько предоставляемых системой действий и конструкторов действий для создания рабочих процессов конечного автомата.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-104">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="4dfa1-105">Выполняет включенные действия на основе известной парадигмы конечного автомата.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-105">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="4dfa1-106">Представляет состояние в конечном компьютере.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-106">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="4dfa1-107">Представляет завершающее состояние в конечном автомате.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-107">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="4dfa1-108"><xref:System.Activities.Core.Presentation.FinalState> - конструктор действий, который при использовании создает <xref:System.Activities.Statements.State>, предварительно настроенное как завершающие состояние.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-108"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="4dfa1-109">Дополнительные сведения см. в статье [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="4dfa1-109">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="4dfa1-110">Представляет переход между двумя состояниями.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-110">Represents the transition between two states.</span></span> <span data-ttu-id="4dfa1-111">Отсутствует элемент **панели элементов** для <xref:System.Activities.Statements.Transition> ; переходы создаются в конструкторе рабочих процессов путем перетаскивания строки между двумя состояниями или путем удаления состояния на треугольниках, появляющихся при наведении указателя мыши на другое состояние.</span><span class="sxs-lookup"><span data-stu-id="4dfa1-111">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="4dfa1-112">Дополнительные сведения см. в разделе [конструктор действий перехода](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="4dfa1-112">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dfa1-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4dfa1-113">See also</span></span>

- [<span data-ttu-id="4dfa1-114">Учебник по началу работы</span><span class="sxs-lookup"><span data-stu-id="4dfa1-114">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
