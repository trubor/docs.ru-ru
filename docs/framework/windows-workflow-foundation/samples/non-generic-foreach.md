---
description: 'Дополнительные сведения: неуниверсальный оператор ForEach'
title: Неуниверсальное действие ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 16635da4ef57ff7b59e178f5954465d8b86bf488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741956"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="7b680-103">Неуниверсальное действие ForEach</span><span class="sxs-lookup"><span data-stu-id="7b680-103">Non-Generic ForEach</span></span>

<span data-ttu-id="7b680-104">В область элементов [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] входит набор действий потока управления, включая элемент <xref:System.Activities.Statements.ForEach%601>, который позволяет проходить по коллекциям <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7b680-104">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="7b680-105">Свойство <xref:System.Activities.Statements.ForEach%601> элемента <xref:System.Activities.Statements.ForEach%601.Values%2A> должно иметь тип <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7b680-105"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="7b680-106">Это запрещает пользователям проходить по структурам данных, в которых реализован интерфейс <xref:System.Collections.Generic.IEnumerable%601> (например, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="7b680-106">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="7b680-107">Неуниверсальная версия <xref:System.Activities.Statements.ForEach%601> выполняет это требование за счет большей гибкости во время выполнения, чтобы обеспечить совместимость типов значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="7b680-107">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="7b680-108">В этом образце показано, как реализовать неуниверсальное действие <xref:System.Activities.Statements.ForEach%601> и конструктор для него.</span><span class="sxs-lookup"><span data-stu-id="7b680-108">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="7b680-109">Это действие позволяет проходить по <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="7b680-109">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="7b680-110">Действие ForEach</span><span class="sxs-lookup"><span data-stu-id="7b680-110">ForEach Activity</span></span>  

 <span data-ttu-id="7b680-111">Инструкция C#/Visual Basic `foreach` перечисляет элементы коллекции, выполняя внедренный оператор для каждого элемента коллекции.</span><span class="sxs-lookup"><span data-stu-id="7b680-111">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="7b680-112">Действиями [!INCLUDE[wf1](../../../../includes/wf1-md.md)], эквивалентными `foreach`, являются действия <xref:System.Activities.Statements.ForEach%601> и <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="7b680-112">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="7b680-113">Действие <xref:System.Activities.Statements.ForEach%601> содержит список значений и содержимое.</span><span class="sxs-lookup"><span data-stu-id="7b680-113">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="7b680-114">Во время выполнения действие проходит по списку, и текст действия выполняется для каждого значения в списке.</span><span class="sxs-lookup"><span data-stu-id="7b680-114">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="7b680-115">Для большинства случаев универсальная версия действия является предпочтительной, поскольку она охватывает большинство сценариев, в которых будет использоваться действие, и предоставляет возможность проверки соответствия типов во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="7b680-115">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="7b680-116">Неуниверсальная версия позволяет проходить по типам, где реализован неуниверсальный интерфейс <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="7b680-116">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="7b680-117">Определение класса</span><span class="sxs-lookup"><span data-stu-id="7b680-117">Class Definition</span></span>  

 <span data-ttu-id="7b680-118">В следующем примере кода показано определение неуниверсального действия `ForEach`.</span><span class="sxs-lookup"><span data-stu-id="7b680-118">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="7b680-119">Содержание (необязательно)</span><span class="sxs-lookup"><span data-stu-id="7b680-119">Body (optional)</span></span>  
 <span data-ttu-id="7b680-120">Действие <xref:System.Activities.ActivityAction> типа <xref:System.Object>, которое выполняется для каждого элемента в коллекции.</span><span class="sxs-lookup"><span data-stu-id="7b680-120">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="7b680-121">Каждый отдельный элемент передается в текст через свойство `Argument`.</span><span class="sxs-lookup"><span data-stu-id="7b680-121">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="7b680-122">Значения (необязательно)</span><span class="sxs-lookup"><span data-stu-id="7b680-122">Values (optional)</span></span>  
 <span data-ttu-id="7b680-123">Коллекция элементов, по которой выполняется проход.</span><span class="sxs-lookup"><span data-stu-id="7b680-123">The collection of elements that are iterated over.</span></span> <span data-ttu-id="7b680-124">Проверка совместимости типов для всех элементов коллекции проводится во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="7b680-124">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="7b680-125">Пример использования ForEach</span><span class="sxs-lookup"><span data-stu-id="7b680-125">Example of Using ForEach</span></span>  

 <span data-ttu-id="7b680-126">В следующем кода демонстрируется использование в приложении действия ForEach.</span><span class="sxs-lookup"><span data-stu-id="7b680-126">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|<span data-ttu-id="7b680-127">Условие</span><span class="sxs-lookup"><span data-stu-id="7b680-127">Condition</span></span>|<span data-ttu-id="7b680-128">Сообщение</span><span class="sxs-lookup"><span data-stu-id="7b680-128">Message</span></span>|<span data-ttu-id="7b680-129">Severity</span><span class="sxs-lookup"><span data-stu-id="7b680-129">Severity</span></span>|<span data-ttu-id="7b680-130">Тип исключения</span><span class="sxs-lookup"><span data-stu-id="7b680-130">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="7b680-131">Значением является `null`</span><span class="sxs-lookup"><span data-stu-id="7b680-131">Values is `null`</span></span>|<span data-ttu-id="7b680-132">Не указано значение необходимого аргумента действия "Values".</span><span class="sxs-lookup"><span data-stu-id="7b680-132">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="7b680-133">Ошибка</span><span class="sxs-lookup"><span data-stu-id="7b680-133">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="7b680-134">Конструктор ForEach</span><span class="sxs-lookup"><span data-stu-id="7b680-134">ForEach Designer</span></span>  

 <span data-ttu-id="7b680-135">Конструктор действий для образца аналогичен конструктору, предоставляемому для встроенного действия <xref:System.Activities.Statements.ForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="7b680-135">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="7b680-136">Конструктор появится в области элементов в категории **примеры**, **неуниверсальные действия** .</span><span class="sxs-lookup"><span data-stu-id="7b680-136">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="7b680-137">Конструктор называется **фореачвисбодифактори** на панели элементов, так как действие предоставляет объект <xref:System.Activities.Presentation.IActivityTemplateFactory> в области элементов, который создает действие с правильной настройкой <xref:System.Activities.ActivityAction> .</span><span class="sxs-lookup"><span data-stu-id="7b680-137">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="7b680-138">Запуск образца</span><span class="sxs-lookup"><span data-stu-id="7b680-138">To run this sample</span></span>  
  
1. <span data-ttu-id="7b680-139">Установите выбранный проект в качестве проекта для запуска решения.</span><span class="sxs-lookup"><span data-stu-id="7b680-139">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="7b680-140">**Кодетестклиент** показывает, как использовать действие с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="7b680-140">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="7b680-141">**Десигнертестклиент** показывает, как использовать действие в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="7b680-141">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="7b680-142">Постройте и запустите проект.</span><span class="sxs-lookup"><span data-stu-id="7b680-142">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b680-143">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7b680-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b680-144">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7b680-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7b680-145">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7b680-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b680-146">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7b680-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
