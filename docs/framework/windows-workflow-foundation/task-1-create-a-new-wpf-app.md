---
description: 'Дополнительные сведения: задача 1. Создание нового приложения Windows Presentation Foundation'
title: Задача 1. Создание нового приложения Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755243"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="62a49-103">Задача 1. Создание нового приложения Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="62a49-103">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="62a49-104">В этой задаче вы создадите пустое приложение Windows Presentation Foundation (WPF) с помощью шаблона WPF Application Visual Studio и добавите ссылки на соответствующие [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] сборки рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="62a49-104">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="62a49-105">Создание проекта приложения WPF</span><span class="sxs-lookup"><span data-stu-id="62a49-105">To create the WPF Application project</span></span>

1. <span data-ttu-id="62a49-106">Откройте Visual Studio и в меню **файл** наведите указатель на пункт **создать** и выберите **проект**.</span><span class="sxs-lookup"><span data-stu-id="62a49-106">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="62a49-107">В диалоговом окне **Новый проект** выберите либо **Visual C#** , либо **Visual Basic** на панели **Установленные шаблоны** в левой части окна.</span><span class="sxs-lookup"><span data-stu-id="62a49-107">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="62a49-108">Если нужный язык не отображается, просмотрите раздел **другие языки**.</span><span class="sxs-lookup"><span data-stu-id="62a49-108">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="62a49-109">В области **Установленные шаблоны** выберите **Windows** .</span><span class="sxs-lookup"><span data-stu-id="62a49-109">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="62a49-110">В верхней области убедитесь, что в раскрывающемся списке выбрано (значение по умолчанию) **платформа .NET Framework 4** , а затем выберите **приложение WPF**.</span><span class="sxs-lookup"><span data-stu-id="62a49-110">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="62a49-111">В нижней части окна задайте имя проекта **хостингаппликатион** .</span><span class="sxs-lookup"><span data-stu-id="62a49-111">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="62a49-112">Задайте для имени решения значение **рехостингседесигнер**.</span><span class="sxs-lookup"><span data-stu-id="62a49-112">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="62a49-113">Нажмите кнопку **ОК** , чтобы создать проект приложения.</span><span class="sxs-lookup"><span data-stu-id="62a49-113">Click **OK** to create the application project.</span></span> <span data-ttu-id="62a49-114">Visual Studio создает базовый пользовательский интерфейс WPF для приложения и включает соответствующие файлы XAML и кода программной части.</span><span class="sxs-lookup"><span data-stu-id="62a49-114">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="62a49-115">Добавьте ссылки на сборки **воркфловмодел** .</span><span class="sxs-lookup"><span data-stu-id="62a49-115">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="62a49-116">Для этого в **Обозреватель решений** щелкните правой кнопкой мыши проект **хостингаппликатион** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="62a49-116">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="62a49-117">В диалоговом окне **Добавление ссылки** перейдите на вкладку **.NET** , нажмите и удерживайте клавишу CTRL, выберите следующие сборки, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="62a49-117">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="62a49-118">System.Activities</span><span class="sxs-lookup"><span data-stu-id="62a49-118">System.Activities</span></span>
    - <span data-ttu-id="62a49-119">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="62a49-119">System.Activities.Presentation</span></span>
    - <span data-ttu-id="62a49-120">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="62a49-120">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="62a49-121">См. раздел [Задача 2. размещение конструктор рабочих процессов](task-2-host-the-workflow-designer.md) , чтобы узнать, как разместить холст конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="62a49-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="62a49-122">См. также</span><span class="sxs-lookup"><span data-stu-id="62a49-122">See also</span></span>

- [<span data-ttu-id="62a49-123">Повторное размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="62a49-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="62a49-124">Задача 2. Размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="62a49-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
