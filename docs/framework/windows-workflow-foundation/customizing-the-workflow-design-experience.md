---
description: 'Дополнительные сведения: Настройка интерфейса рабочего процесса'
title: Рекомендации по настройке конструктора рабочих процессов
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 02049f8b42de3de6e4dfdfe8a4151be1500bcca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742658"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="ebfaf-103">Рекомендации по настройке конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="ebfaf-103">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="ebfaf-104">Сценарии разработки пользовательских действий и для повторного размещения конструктор рабочих процессов Windows были значительно упрощены в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-104">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="ebfaf-105">Разработка и развертывание упрощены и являются более гибкими по сравнению с предыдущими версиями.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-105">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="ebfaf-106">Основное инфраструктуры изменение заключается в том, что новая модель программирования конструктора действий строится на основе Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ebfaf-106">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="ebfaf-107">Это дает возможность декларативно определять конструкторы действий и повторно размещать конструктор рабочих процессов в других приложениях с помощью сравнительно простой.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-107">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="ebfaf-108">При повторном размещении может быть создан редактор пользовательских выражений, поддерживающий IntelliSense, или упрощенный домен выражений.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-108">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="ebfaf-109">Интеграция с Windows Communication Foundation (WCF) стала более простой в использовании служб рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-109">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="ebfaf-110">Конструкторы пользовательских действий и дерево элементов модели могут быть использованы для улучшения действий во время разработки во вновь размещенных конструкторах рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-110">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ebfaf-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="ebfaf-111">In This Section</span></span>

 [<span data-ttu-id="ebfaf-112">Использование шаблонов и конструкторов настраиваемых действий</span><span class="sxs-lookup"><span data-stu-id="ebfaf-112">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="ebfaf-113">Описывается порядок создания новых конструкторов и шаблонов пользовательских действий.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-113">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="ebfaf-114">Повторное размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="ebfaf-114">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="ebfaf-115">В этой статье описывается, как повторно разместить конструктор рабочих процессов Windows за пределами Visual Studio и как отобразить ошибки проверки.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-115">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="ebfaf-116">Использование редактора настраиваемых выражений</span><span class="sxs-lookup"><span data-stu-id="ebfaf-116">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="ebfaf-117">Описание реализации пользовательского редактора выражений для использования с конструкторами рабочих процессов, которые перемещаются вне Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-117">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="ebfaf-118">Справочник</span><span class="sxs-lookup"><span data-stu-id="ebfaf-118">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="ebfaf-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ebfaf-119">See also</span></span>

- [<span data-ttu-id="ebfaf-120">Расширение Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="ebfaf-120">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="ebfaf-121">Designer</span><span class="sxs-lookup"><span data-stu-id="ebfaf-121">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="ebfaf-122">Пользовательские конструкторы действий</span><span class="sxs-lookup"><span data-stu-id="ebfaf-122">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="ebfaf-123">Повторное размещение конструктора</span><span class="sxs-lookup"><span data-stu-id="ebfaf-123">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
