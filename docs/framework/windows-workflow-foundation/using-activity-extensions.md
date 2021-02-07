---
description: Дополнительные сведения см. в статье Использование расширений действий.
title: Использование модулей действий
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: d0286850bf685497d3a2471a3b4e0db4630070b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755074"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="f7f6e-103">Использование модулей действий</span><span class="sxs-lookup"><span data-stu-id="f7f6e-103">Using Activity Extensions</span></span>

<span data-ttu-id="f7f6e-104">Действия могут взаимодействовать с расширениями приложений рабочих процессов. Благодаря этому узел может предоставлять дополнительные возможности, которые не были явно смоделированы в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-104">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="f7f6e-105">В этом разделе описывается создание расширений для подсчета количества выполнений действия.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-105">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="f7f6e-106">Использования расширения действия для подсчета выполнений</span><span class="sxs-lookup"><span data-stu-id="f7f6e-106">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="f7f6e-107">Откройте Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-107">Open Visual Studio 2010.</span></span> <span data-ttu-id="f7f6e-108">Выберите **создать**, **проект**.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-108">Select **New**, **Project**.</span></span> <span data-ttu-id="f7f6e-109">В узле **Visual C#** выберите **Рабочий процесс**.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-109">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="f7f6e-110">Выберите **консольное приложение рабочего процесса** из списка шаблонов.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-110">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="f7f6e-111">Задайте для проекта имя `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-111">Name the project `Extensions`.</span></span> <span data-ttu-id="f7f6e-112">Чтобы создать проект, нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="f7f6e-112">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="f7f6e-113">Добавьте `using` инструкцию в файл Program.cs для пространства имен **System. Collections. Generic** .</span><span class="sxs-lookup"><span data-stu-id="f7f6e-113">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="f7f6e-114">В файле Program.cs создайте новый класс с именем **ексекутионкаунтекстенсион**.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-114">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="f7f6e-115">Следующий код создает расширение рабочего процесса, которое отслеживает идентификаторы экземпляров при вызове метода **Register** .</span><span class="sxs-lookup"><span data-stu-id="f7f6e-115">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="f7f6e-116">Создайте действие, которое использует **ексекутионкаунтекстенсион**.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-116">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="f7f6e-117">В следующем коде определяется действие, которое получает объект **ексекутионкаунтекстенсион** из среды выполнения и вызывает его метод **Register** при выполнении действия.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-117">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="f7f6e-118">Реализуйте действие в методе **Main** файла Program.cs.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-118">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="f7f6e-119">В следующем коде содержатся методы для создания двух различных рабочих процессов, выполнения всех процессов по несколько раз и отображения полученных данных, содержащихся в расширении.</span><span class="sxs-lookup"><span data-stu-id="f7f6e-119">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
