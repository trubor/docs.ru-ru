---
description: 'Дополнительные сведения: декларативные ограничения'
title: Декларативные ограничения
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 7eeee5577e9c98db52af579749a59bc76a59b411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742515"
---
# <a name="declarative-constraints"></a><span data-ttu-id="b7af8-103">Декларативные ограничения</span><span class="sxs-lookup"><span data-stu-id="b7af8-103">Declarative Constraints</span></span>

<span data-ttu-id="b7af8-104">Декларативные ограничения - это мощный метод проверки допустимости действия и его связей с другими действиями.</span><span class="sxs-lookup"><span data-stu-id="b7af8-104">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="b7af8-105">Ограничения для действий настраиваются во время процесса создания, однако дополнительные ограничения также могут задаваться ведущим приложением рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b7af8-105">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="b7af8-106">В этом разделе приводятся общие сведения об использовании декларативных ограничений для обеспечения проверки допустимости действий.</span><span class="sxs-lookup"><span data-stu-id="b7af8-106">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="b7af8-107">Использование декларативных ограничений</span><span class="sxs-lookup"><span data-stu-id="b7af8-107">Using Declarative Constraints</span></span>  

 <span data-ttu-id="b7af8-108">Ограничение - это действие, содержащее логику проверки допустимости.</span><span class="sxs-lookup"><span data-stu-id="b7af8-108">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="b7af8-109">Это действие ограничения может быть создано в коде или в XAML.</span><span class="sxs-lookup"><span data-stu-id="b7af8-109">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="b7af8-110">После создания действия ограничения автор действия добавляет данное ограничение в свойство <xref:System.Activities.Activity.Constraints%2A> действия, которое должно быть проверено, или использует ограничение для реализации дополнительной проверки с помощью свойства <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> экземпляра <xref:System.Activities.Validation.ValidationSettings>.</span><span class="sxs-lookup"><span data-stu-id="b7af8-110">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="b7af8-111">Логика проверки допустимости может состоять из простых проверок допустимости, например проверки метаданных действия, но она также может выполнять проверку допустимости, учитывающую связь текущего действия с его родительскими, дочерними и одноуровневыми действиями.</span><span class="sxs-lookup"><span data-stu-id="b7af8-111">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="b7af8-112">Ограничения создаются посредством использования действия <xref:System.Activities.Validation.Constraint%601>; кроме того, предоставляются несколько дополнительных действий проверки допустимости, облегчающие создание ошибок и предупреждений проверки допустимости и выдачу сведений о связанных действиях в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="b7af8-112">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="b7af8-113">AssertValidation и AddValidationError</span><span class="sxs-lookup"><span data-stu-id="b7af8-113">AssertValidation and AddValidationError</span></span>  

 <span data-ttu-id="b7af8-114">Действие <xref:System.Activities.Validation.AssertValidation> вычисляет выражение, на которое ссылается его свойство <xref:System.Activities.Validation.AssertValidation.Assertion%2A>, и, если в результате вычисления получается значение `false`, к <xref:System.Activities.Validation.ValidationResults> добавляется ошибка или предупреждение проверки допустимости.</span><span class="sxs-lookup"><span data-stu-id="b7af8-114">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="b7af8-115">Свойство <xref:System.Activities.Validation.AssertValidation.Message%2A> описывает ошибку проверки допустимости; свойство <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> указывает, является ли неудачная проверка допустимости ошибкой или предупреждением.</span><span class="sxs-lookup"><span data-stu-id="b7af8-115">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="b7af8-116">По умолчанию для объекта <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> установлено значение `false`.</span><span class="sxs-lookup"><span data-stu-id="b7af8-116">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="b7af8-117">В следующем примере объявляется ограничение, возвращающее предупреждение проверки допустимости, если длина <xref:System.Activities.Activity.DisplayName%2A> действия, для которого выполняется проверка, меньше или равна двум символам.</span><span class="sxs-lookup"><span data-stu-id="b7af8-117">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="b7af8-118">Параметр универсального типа, используемый для <xref:System.Activities.Validation.Constraint%601>, задает тип действия, проверяемого ограничением.</span><span class="sxs-lookup"><span data-stu-id="b7af8-118">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="b7af8-119">Это ограничение использует действие <xref:System.Activities.Activity> в качестве универсального типа. Оно может использоваться для проверки допустимости всех типов действий.</span><span class="sxs-lookup"><span data-stu-id="b7af8-119">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 <span data-ttu-id="b7af8-120">Чтобы задать данное ограничение для действия, его следует добавить в <xref:System.Activities.Activity.Constraints%2A> для действия, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="b7af8-120">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 <span data-ttu-id="b7af8-121">Ведущее приложение может также задавать это ограничение для действий в рабочем процессе посредством использования <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Этот вариант описывается в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="b7af8-121">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="b7af8-122">Действие <xref:System.Activities.Validation.AddValidationError> используется для создания ошибки или предупреждения проверки допустимости без необходимости вычисления выражения.</span><span class="sxs-lookup"><span data-stu-id="b7af8-122">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="b7af8-123">Его свойства подобны свойствам <xref:System.Activities.Validation.AssertValidation>; оно может использоваться совместно с действиями управления потоком ограничения, например с действием <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="b7af8-123">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="b7af8-124">Действия связей рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="b7af8-124">Workflow Relationship Activities</span></span>

<span data-ttu-id="b7af8-125">Доступны несколько действий проверки допустимости, которые предоставляют сведения о других действиях в рабочем процессе относительно проверяемого действия.</span><span class="sxs-lookup"><span data-stu-id="b7af8-125">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="b7af8-126"><xref:System.Activities.Validation.GetParentChain> возвращает коллекцию действий, содержащую все действия, лежащие между текущим и корневым действиями.</span><span class="sxs-lookup"><span data-stu-id="b7af8-126"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="b7af8-127"><xref:System.Activities.Validation.GetChildSubtree> предоставляет коллекцию действий, содержащую дочерние действия в рекурсивном шаблоне, и <xref:System.Activities.Validation.GetWorkflowTree> возвращает все действия в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="b7af8-127"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="b7af8-128">В следующем примере определяется действие `CreateState` .</span><span class="sxs-lookup"><span data-stu-id="b7af8-128">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="b7af8-129">Действие `CreateState` должно содержаться в действии `CreateCountry`; метод `GetParent` возвращает ограничение, принудительно реализующее это требование.</span><span class="sxs-lookup"><span data-stu-id="b7af8-129">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="b7af8-130">`GetParent` использует действие <xref:System.Activities.Validation.GetParentChain> совместно с действием <xref:System.Activities.Statements.ForEach%601> для проверки родительских действий действия `CreateState`, чтобы определить, удовлетворяется ли это требование.</span><span class="sxs-lookup"><span data-stu-id="b7af8-130">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {
            Body = new ActivityAction<CreateState,ValidationContext>  
            {
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context
                            },  
                            Body = new ActivityAction<Activity>  
                            {
                                Argument = parent,
                                Handler = new If()  
                                {
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a><span data-ttu-id="b7af8-131">Дополнительные ограничения</span><span class="sxs-lookup"><span data-stu-id="b7af8-131">Additional Constraints</span></span>  

 <span data-ttu-id="b7af8-132">Авторы ведущих приложений рабочих процессов могут задавать дополнительные ограничения проверки допустимости для действий в рабочем процессе, создавая ограничения и добавляя их к словарю <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> экземпляра <xref:System.Activities.Validation.ValidationSettings>.</span><span class="sxs-lookup"><span data-stu-id="b7af8-132">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="b7af8-133">Каждый элемент в <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> содержит тип действия, к которому применяются ограничения, а также список дополнительных ограничений для этого типа действия.</span><span class="sxs-lookup"><span data-stu-id="b7af8-133">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="b7af8-134">При вызове проверки допустимости для рабочего процесса каждое действие указанного типа, включая производные классы, проверяется на соответствие ограничениям.</span><span class="sxs-lookup"><span data-stu-id="b7af8-134">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="b7af8-135">В этом примере ограничение `ActivityDisplayNameIsNotSetWarning` из предыдущего раздела применяется ко всем действиям в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="b7af8-135">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="b7af8-136">Если свойство <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> у <xref:System.Activities.Validation.ValidationSettings> имеет значение `true`, то при вызове проверки допустимости путем вызова <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> выполняется проверка только дополнительных ограничений.</span><span class="sxs-lookup"><span data-stu-id="b7af8-136">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="b7af8-137">Это может быть полезно при проверке рабочих процессов по отдельным конфигурациям проверки.</span><span class="sxs-lookup"><span data-stu-id="b7af8-137">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="b7af8-138">Необходимо отметить, что при вызове рабочего процесса выполняется проверка логики проверки, настроенной в рабочем процессе; для запуска рабочего процесса проверка должна быть пройдена успешно.</span><span class="sxs-lookup"><span data-stu-id="b7af8-138">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="b7af8-139">Дополнительные сведения о вызове проверки см. в разделе [вызов проверки активности](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="b7af8-139">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
