---
description: 'Дополнительные сведения: свойства выполнения рабочего процесса'
title: Свойства выполнения рабочего процесса
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: d6f83109da0a14382098322858a6e0493750a748
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754905"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="ec740-103">Свойства выполнения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="ec740-103">Workflow Execution Properties</span></span>

<span data-ttu-id="ec740-104">Через локальную память потока (TLS) CLR поддерживает контекст выполнения для каждого потока.</span><span class="sxs-lookup"><span data-stu-id="ec740-104">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="ec740-105">Этот контекст выполнения управляет хорошо известными свойствами потоков, например идентификатором потока, внешней транзакцией и текущим набором разрешений, а также пользовательскими свойствами потока, например именованными областями.</span><span class="sxs-lookup"><span data-stu-id="ec740-105">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="ec740-106">В отличие от программ, предназначенных для непосредственной работы в среде CLR, программы рабочих процессов представляют иерархические деревья действий, которые выполняются в среде, не поддерживающей разделение на потоки.</span><span class="sxs-lookup"><span data-stu-id="ec740-106">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="ec740-107">Это предполагает, что с помощью стандартных механизмов TLS нельзя непосредственно определить, какой контекст находится в области для данного рабочего элемента.</span><span class="sxs-lookup"><span data-stu-id="ec740-107">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="ec740-108">Например, две параллельные ветви выполнения могут использовать различные транзакции, но планировщик может чередовать их выполнение в одном потоке CLR.</span><span class="sxs-lookup"><span data-stu-id="ec740-108">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="ec740-109">Свойства выполнения рабочего процесса предоставляют механизм добавления определенных свойств контекста к среде действия.</span><span class="sxs-lookup"><span data-stu-id="ec740-109">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="ec740-110">Это позволяет действию объявлять, какие свойства находятся в области для его поддерева, а также предоставлять обработчики для установки или удаления TLS в целях правильного взаимодействия с объектами CLR.</span><span class="sxs-lookup"><span data-stu-id="ec740-110">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="ec740-111">Создание и использование свойств выполнения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="ec740-111">Creating and Using Workflow Execution Properties</span></span>  

 <span data-ttu-id="ec740-112">Свойства выполнения рабочего процесса обычно реализуют интерфейс <xref:System.Activities.IExecutionProperty>, хотя свойства, сфокусированные на обмене сообщениями, могут вместо этого реализовать <xref:System.ServiceModel.Activities.ISendMessageCallback> и <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="ec740-112">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="ec740-113">Чтобы создать свойство выполнения рабочего процесса, создайте класс, который реализует интерфейс <xref:System.Activities.IExecutionProperty>, а также реализует элементы <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> и <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec740-113">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="ec740-114">Эти элементы обеспечивают для свойства выполнения возможность правильной настройки локального хранилища потока на всех этапах выполнения действия, которое содержит свойство, включая все дочерние свойства.</span><span class="sxs-lookup"><span data-stu-id="ec740-114">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="ec740-115">В этом примере создается `ConsoleColorProperty`, который задает `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="ec740-115">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="ec740-116">Создатели действия могут использовать это свойство путем его регистрации в операции переопределения выполнения действия.</span><span class="sxs-lookup"><span data-stu-id="ec740-116">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="ec740-117">В этом примере определяется действие `ConsoleColorScope`, которое регистрирует свойство `ConsoleColorProperty` путем его добавления к коллекции <xref:System.Activities.NativeActivityContext.Properties%2A> текущего контекста <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="ec740-117">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ec740-118">С началом в тексте действия рабочего импульса вызывается метод <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> этого свойства, а после завершения рабочего импульса вызывается <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec740-118">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="ec740-119">В этом примере создается рабочий процесс, который использует действие <xref:System.Activities.Statements.Parallel> с тремя ветвями.</span><span class="sxs-lookup"><span data-stu-id="ec740-119">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="ec740-120">В первых двух ветвях используется действие `ConsoleColorScope`, а в третьей - нет.</span><span class="sxs-lookup"><span data-stu-id="ec740-120">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="ec740-121">Все три ветви содержат два действия <xref:System.Activities.Statements.WriteLine> и действие <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="ec740-121">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="ec740-122">При выполнении действия <xref:System.Activities.Statements.Parallel> те действия, которые содержатся в ветвях, выполняются с чередованием, но при выполнении каждого дочернего действия свойство `ConsoleColorProperty` применяет правильный цвет консоли.</span><span class="sxs-lookup"><span data-stu-id="ec740-122">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="ec740-123">При вызове рабочего процесса в окне консоли записываются следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="ec740-123">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="ec740-124">Хотя это не показано в предшествующих выходных данных, все строки текста в окне консоли отображаются с использованием указанного цвета.</span><span class="sxs-lookup"><span data-stu-id="ec740-124">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="ec740-125">Создатели настраиваемого действия могут использовать свойства выполнения рабочего процесса, а также предоставлять механизм управления обработкой для таких действий, как <xref:System.ServiceModel.Activities.CorrelationScope> и <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="ec740-125">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec740-126">См. также</span><span class="sxs-lookup"><span data-stu-id="ec740-126">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
