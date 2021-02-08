---
description: 'Дополнительные сведения: Настройка проверки действия'
title: Настройка проверки действий
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 9e40842a18dd2afd9a5ec0104d66e8971d691b5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792756"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="52d8d-103">Настройка проверки действий</span><span class="sxs-lookup"><span data-stu-id="52d8d-103">Configuring Activity Validation</span></span>

<span data-ttu-id="52d8d-104">Проверка действия позволяет авторам и пользователям действий выявлять ошибки и сообщать о них в конфигурации любого действия до его выполнения.</span><span class="sxs-lookup"><span data-stu-id="52d8d-104">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="52d8d-105">Windows Workflow Foundation (WF) предоставляет следующие три типа проверки действий:</span><span class="sxs-lookup"><span data-stu-id="52d8d-105">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="52d8d-106">Атрибуты `RequiredArgument` и `OverloadGroup`.</span><span class="sxs-lookup"><span data-stu-id="52d8d-106">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="52d8d-107">Императивная, основанная на коде проверка.</span><span class="sxs-lookup"><span data-stu-id="52d8d-107">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="52d8d-108">Декларативные ограничения.</span><span class="sxs-lookup"><span data-stu-id="52d8d-108">Declarative constraints.</span></span>  
  
 <span data-ttu-id="52d8d-109">Атрибуты `RequiredArgument` и `OverloadGroup` указывают, что определенные аргументы в действии являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="52d8d-109">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="52d8d-110">Императивная, основанная на коде проверка предоставляет действию простой способ выполнения самопроверки, а декларативные ограничения позволяют выполнять проверку действия и его связи с рабочим процессом, содержащим это действие.</span><span class="sxs-lookup"><span data-stu-id="52d8d-110">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="52d8d-111">Если действие не настроено в соответствии с требованиями проверки, то возвращаются ошибки проверки и предупреждения.</span><span class="sxs-lookup"><span data-stu-id="52d8d-111">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="52d8d-112">Если рабочий процесс, содержащий действие, создан с использованием конструктора рабочих процессов, то все ошибки проверки и предупреждения отображаются в этом конструкторе.</span><span class="sxs-lookup"><span data-stu-id="52d8d-112">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="52d8d-113">Если рабочий процесс создан за пределами конструктора рабочих процессов, то все ошибки проверки возвращаются при вызове рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="52d8d-113">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="52d8d-114">Независимо от способа создания рабочего процесса, рабочий процесс, содержащий ошибки проверки, выполнен не будет.</span><span class="sxs-lookup"><span data-stu-id="52d8d-114">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="52d8d-115">В этом разделе представлены общие сведения об этих типах проверки действий и способах ее вызова.</span><span class="sxs-lookup"><span data-stu-id="52d8d-115">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52d8d-116">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="52d8d-116">In This Section</span></span>  

 [<span data-ttu-id="52d8d-117">Обязательные аргументы и группы перегруженных аргументов</span><span class="sxs-lookup"><span data-stu-id="52d8d-117">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="52d8d-118">Описывает процесс использования атрибутов `RequiredArgument` и `OverloadGroup` для выполнения проверки.</span><span class="sxs-lookup"><span data-stu-id="52d8d-118">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="52d8d-119">Принудительная проверка на уровне кода</span><span class="sxs-lookup"><span data-stu-id="52d8d-119">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="52d8d-120">Описывает процесс использования проверки на уровне коде для действий, основанных на <xref:System.Activities.CodeActivity> и <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="52d8d-120">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="52d8d-121">Декларативные ограничения</span><span class="sxs-lookup"><span data-stu-id="52d8d-121">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="52d8d-122">Описывает процесс использования декларативных ограничений для выполнения проверки сложных действий.</span><span class="sxs-lookup"><span data-stu-id="52d8d-122">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="52d8d-123">Вызов проверки действия</span><span class="sxs-lookup"><span data-stu-id="52d8d-123">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="52d8d-124">Описывает процесс автоматического вызова проверки действия и способы явного вызова проверки.</span><span class="sxs-lookup"><span data-stu-id="52d8d-124">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52d8d-125">Справочник</span><span class="sxs-lookup"><span data-stu-id="52d8d-125">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52d8d-126">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="52d8d-126">Related Sections</span></span>
