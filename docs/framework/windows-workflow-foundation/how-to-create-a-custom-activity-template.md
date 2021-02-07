---
description: Дополнительные сведения о том, как создать настраиваемый шаблон действия.
title: Практическое руководство. Создание настраиваемого шаблона действий
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 06fda953110e36e46a91fda8697aadbcd6e6bf59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742112"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="94775-103">Практическое руководство. Создание настраиваемого шаблона действий</span><span class="sxs-lookup"><span data-stu-id="94775-103">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="94775-104">Настраиваемые шаблоны действий служат для настройки конфигурации действий, в том числе настраиваемых составных действий, чтобы позволяет не создавать отдельно каждое действие и не настраивать все свойства и другие параметры вручную.</span><span class="sxs-lookup"><span data-stu-id="94775-104">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="94775-105">Эти пользовательские шаблоны можно сделать доступными на **панели элементов** в конструктор рабочих процессов Windows или в конструкторе, где пользователи могут перетащить их в предварительно настроенную область конструктора.</span><span class="sxs-lookup"><span data-stu-id="94775-105">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="94775-106">Конструктор рабочих процессов поставляется с хорошим примером таких шаблонов: [конструктор шаблонов SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) и [конструктор шаблонов ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) в категории [Конструкторы действий обмена сообщениями](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="94775-106">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="94775-107">В первой процедуре в этом разделе описывается создание настраиваемого шаблона действия для действия **delay** , а во второй процедуре показано, как сделать ее доступной в конструктор рабочих процессов, чтобы убедиться в том, что настраиваемый шаблон работает.</span><span class="sxs-lookup"><span data-stu-id="94775-107">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="94775-108">В шаблонах настраиваемых действий должен быть реализован интерфейс <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="94775-108">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="94775-109">Интерфейс имеет один метод <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A>, с помощью которого можно создать и настроить экземпляры действий, используемые в шаблоны.</span><span class="sxs-lookup"><span data-stu-id="94775-109">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="94775-110">Создание шаблона для действия Delay</span><span class="sxs-lookup"><span data-stu-id="94775-110">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="94775-111">Запустите Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="94775-111">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="94775-112">В меню **Файл** последовательно выберите команды **Создать** и **Проект**.</span><span class="sxs-lookup"><span data-stu-id="94775-112">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="94775-113">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="94775-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="94775-114">На панели **типы проектов** выберите **Рабочий процесс** из проектов **Visual C#** или **Visual Basic** группирований в зависимости от предпочитаемого языка.</span><span class="sxs-lookup"><span data-stu-id="94775-114">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="94775-115">В области **шаблоны** выберите пункт **Библиотека действий**.</span><span class="sxs-lookup"><span data-stu-id="94775-115">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="94775-116">В поле **Имя** введите `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="94775-116">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="94775-117">Примите значения по умолчанию в текстовых полях **Расположение** и **имя решения** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="94775-117">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="94775-118">Щелкните правой кнопкой мыши каталог References проекта Делайактивититемплате в **Обозреватель решений** и выберите команду **Добавить ссылку** , чтобы открыть диалоговое окно **Добавление ссылки** .</span><span class="sxs-lookup"><span data-stu-id="94775-118">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="94775-119">Перейдите на вкладку **.NET** и выберите **PresentationFramework** в столбце **имя компонента** слева и нажмите кнопку **ок** , чтобы добавить ссылку на файл PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="94775-119">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="94775-120">Повторите процедуру для добавления ссылок на файлы System.Activities.Presentation.dll and the WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="94775-120">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="94775-121">Щелкните правой кнопкой мыши проект Делайактивититемплате в **Обозреватель решений** и выберите **Добавить** , а затем **новый элемент** , чтобы открыть диалоговое окно **Добавление нового элемента** .</span><span class="sxs-lookup"><span data-stu-id="94775-121">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="94775-122">Выберите шаблон **класса** , назовите его миделайтемплате и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="94775-122">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="94775-123">Откройте файл MyDelayTemplate.cs и добавьте следующие инструкции.</span><span class="sxs-lookup"><span data-stu-id="94775-123">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="94775-124">Реализуйте метод <xref:System.Activities.Presentation.IActivityTemplateFactory> с помощью класса `MyDelayActivity` со следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="94775-124">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="94775-125">Это настраивает задержку на длительность 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="94775-125">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="94775-126">В меню **Сборка** выберите пункт **собрать решение** , чтобы создать файл DelayActivityTemplate.dll.</span><span class="sxs-lookup"><span data-stu-id="94775-126">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="94775-127">Обеспечение доступности шаблона в конструкторе рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="94775-127">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="94775-128">Щелкните правой кнопкой мыши решение Делайактивититемплате в **Обозреватель решений** и выберите **Добавить** , а затем — **создать проект** , чтобы открыть диалоговое окно **Добавление нового проекта** .</span><span class="sxs-lookup"><span data-stu-id="94775-128">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="94775-129">Выберите шаблон **консольное приложение рабочего процесса** , присвойте ему имя `CustomActivityTemplateApp` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="94775-129">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="94775-130">Щелкните правой кнопкой мыши каталог References проекта Кустомактивититемплатеапп в **Обозреватель решений** и выберите команду **Добавить ссылку** , чтобы открыть диалоговое окно **Добавление ссылки** .</span><span class="sxs-lookup"><span data-stu-id="94775-130">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="94775-131">Перейдите на вкладку **проекты** и выберите **Делайактивититемплате** в столбце **имя проекта** слева и нажмите кнопку **ок** , чтобы добавить ссылку на файл DelayActivityTemplate.dll, созданный в первой процедуре.</span><span class="sxs-lookup"><span data-stu-id="94775-131">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="94775-132">Щелкните правой кнопкой мыши проект Кустомактивититемплатеапп в **Обозреватель решений** и выберите **Build (собрать** ), чтобы скомпилировать приложение.</span><span class="sxs-lookup"><span data-stu-id="94775-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="94775-133">Щелкните правой кнопкой мыши проект Кустомактивититемплатеапп в **Обозреватель решений** и выберите пункт **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="94775-133">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="94775-134">Выберите **Запуск без отладки** в меню **Отладка** и нажмите любую клавишу, чтобы продолжить при появлении запроса в окне cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="94775-134">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="94775-135">Откройте файл Workflow1. XAML и откройте **панель элементов**.</span><span class="sxs-lookup"><span data-stu-id="94775-135">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="94775-136">Откройте шаблон **миделайактивити** в категории **делайактивититемплате** .</span><span class="sxs-lookup"><span data-stu-id="94775-136">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="94775-137">Перетащите его в область конструктора.</span><span class="sxs-lookup"><span data-stu-id="94775-137">Drag it onto the design surface.</span></span> <span data-ttu-id="94775-138">В окне **Свойства** подтвердите, что `Duration` для свойства установлено значение 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="94775-138">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="94775-139">Пример</span><span class="sxs-lookup"><span data-stu-id="94775-139">Example</span></span>

 <span data-ttu-id="94775-140">Теперь файл MyDelayActivity.cs должен содержать следующий код.</span><span class="sxs-lookup"><span data-stu-id="94775-140">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="94775-141">См. также</span><span class="sxs-lookup"><span data-stu-id="94775-141">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="94775-142">Рекомендации по настройке конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="94775-142">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
