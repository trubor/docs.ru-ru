---
description: 'Дополнительные сведения о: использование контекста редактирования ModelItem'
title: Использование контекста редактирования ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 7b6b9015f250d0e52f15e574f62386fa94a68e11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755022"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="ec9c1-103">Использование контекста редактирования ModelItem</span><span class="sxs-lookup"><span data-stu-id="ec9c1-103">Using the ModelItem Editing Context</span></span>

<span data-ttu-id="ec9c1-104">Контекст редактирования <xref:System.Activities.Presentation.Model.ModelItem> является объектом, используемым ведущим приложением для взаимодействия с конструктором.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-104">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="ec9c1-105"><xref:System.Activities.Presentation.EditingContext> предоставляет два метода, <xref:System.Activities.Presentation.EditingContext.Items%2A> и <xref:System.Activities.Presentation.EditingContext.Services%2A>, которые могут использоваться</span><span class="sxs-lookup"><span data-stu-id="ec9c1-105"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="ec9c1-106">Коллекция элементов</span><span class="sxs-lookup"><span data-stu-id="ec9c1-106">The Items collection</span></span>  

 <span data-ttu-id="ec9c1-107">Коллекция <xref:System.Activities.Presentation.EditingContext.Items%2A> служит для доступа к данным, совместно используемым ведущим приложением и конструктором, либо к данным, доступным для всех конструкторов.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-107">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="ec9c1-108">Эта коллекция имеет следующие возможности, доступ к которым осуществляется через класс <xref:System.Activities.Presentation.ContextItemManager>:</span><span class="sxs-lookup"><span data-stu-id="ec9c1-108">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="ec9c1-109">Коллекция служб</span><span class="sxs-lookup"><span data-stu-id="ec9c1-109">The Services collection</span></span>  

 <span data-ttu-id="ec9c1-110">Коллекция <xref:System.Activities.Presentation.EditingContext.Services%2A> предназначена для доступа к службам, используемым конструктором для взаимодействия с узлом, либо к службам, используемым всеми конструкторами.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-110">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="ec9c1-111">Эта коллекция содержит следующие методы, на которые нужно обратить внимание:</span><span class="sxs-lookup"><span data-stu-id="ec9c1-111">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="ec9c1-112">Назначение конструктора действию</span><span class="sxs-lookup"><span data-stu-id="ec9c1-112">Assigning a designer an activity</span></span>  

 <span data-ttu-id="ec9c1-113">Чтобы указать, какой конструктор используется действием, служит атрибут Designer.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-113">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="ec9c1-114">Создание службы</span><span class="sxs-lookup"><span data-stu-id="ec9c1-114">Creating a service</span></span>  

 <span data-ttu-id="ec9c1-115">Чтобы создать службу, которая служит каналом передачи между конструктором и узлом, необходимо создать интерфейс и реализацию.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-115">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="ec9c1-116">Этот интерфейс используется методом <xref:System.Activities.Presentation.ServiceManager.Publish%2A> для определения элементов службы, и реализация содержит логику для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-116">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="ec9c1-117">В следующем примере кода создаются интерфейс службы и реализация.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-117">In the following code example, a service interface and implementation are created.</span></span>  
  
```csharp  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {
                DisplayName + " One",
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a><span data-ttu-id="ec9c1-118">Публикация службы</span><span class="sxs-lookup"><span data-stu-id="ec9c1-118">Publishing a service</span></span>  

 <span data-ttu-id="ec9c1-119">Чтобы конструктор мог использовать службу, ее сначала необходимо опубликовать на узле с помощью метода <xref:System.Activities.Presentation.ServiceManager.Publish%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-119">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="ec9c1-120">Подписка на службу</span><span class="sxs-lookup"><span data-stu-id="ec9c1-120">Subscribing to a service</span></span>  

 <span data-ttu-id="ec9c1-121">Конструктор получает доступ к службе с помощью метода <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> в методе <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-121">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="ec9c1-122">В следующем фрагменте кода показана подписка на службу.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-122">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```csharp  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="ec9c1-123">Совместное использование данных с помощью коллекции элементов</span><span class="sxs-lookup"><span data-stu-id="ec9c1-123">Sharing data using the Items collection</span></span>  

 <span data-ttu-id="ec9c1-124">Работа с коллекцией элементов похожа на работу с коллекцией служб, за исключением того, что вместо Publish вызывается <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-124">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="ec9c1-125">Эта коллекция больше подходит для обмена простыми данными между конструкторами и узлом, чем для выполнения сложных функций.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-125">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="ec9c1-126">Ведущие элементы узла EditingContext и службы</span><span class="sxs-lookup"><span data-stu-id="ec9c1-126">EditingContext host items and services</span></span>  

 <span data-ttu-id="ec9c1-127">Платформа .NET Framework предоставляет ряд встроенных элементов и служб, доступ к которым осуществляется через контекст редактирования.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-127">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="ec9c1-128">Элементы:</span><span class="sxs-lookup"><span data-stu-id="ec9c1-128">Items:</span></span>  
  
- <span data-ttu-id="ec9c1-129"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem> - управляет списком локальных сборок, на которые указывают ссылки и которые будут использоваться в рабочем процессе для элементов управления (например, в редакторе выражений).</span><span class="sxs-lookup"><span data-stu-id="ec9c1-129"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="ec9c1-130"><xref:System.Activities.Presentation.Hosting.ReadOnlyState> - указывает, находится ли конструктор в режиме только для чтения.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-130"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="ec9c1-131"><xref:System.Activities.Presentation.View.Selection> - определяет коллекцию выбранных в настоящий момент объектов.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-131"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="ec9c1-132"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="ec9c1-132"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="ec9c1-133"><xref:System.Activities.Presentation.WorkflowFileItem> - предоставляет сведения о файле, на основе которого выполняется текущий сеанс редактирования.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-133"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="ec9c1-134">Службы.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-134">Services:</span></span>  
  
- <span data-ttu-id="ec9c1-135"><xref:System.Activities.Presentation.Model.AttachedPropertiesService> - позволяет добавлять свойства в текущий экземпляр с помощью <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-135"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="ec9c1-136"><xref:System.Activities.Presentation.View.DesignerView> - разрешает доступ к свойствам полотна конструктора.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-136"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="ec9c1-137"><xref:System.Activities.Presentation.IActivityToolboxService> - позволяет обновлять содержимое области элементов.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-137"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="ec9c1-138"><xref:System.Activities.Presentation.Hosting.ICommandService> - предназначен для интеграции команд конструктора (например, пунктов контекстного меню) с пользовательскими реализациями службы.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-138"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="ec9c1-139"><xref:System.Activities.Presentation.Debug.IDesignerDebugView> - обеспечивает функциональность отладчика конструктора.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-139"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="ec9c1-140"><xref:System.Activities.Presentation.View.IExpressionEditorService> - обеспечивает доступ к диалоговому окну редактора выражений.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-140"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="ec9c1-141"><xref:System.Activities.Presentation.IIntegratedHelpService> - реализует в конструкторе функциональность встроенной справки.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-141"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="ec9c1-142"><xref:System.Activities.Presentation.Validation.IValidationErrorService> - обеспечивает доступ к ошибкам проверки через <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-142"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="ec9c1-143"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService> - реализует внутреннюю службу для хранения и извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-143"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="ec9c1-144">Эта служба используется на внутреннем уровне платформа .NET Framework и не предназначена для внешнего использования.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-144">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="ec9c1-145"><xref:System.Activities.Presentation.IXamlLoadErrorService> - предоставляет доступ к коллекции ошибок загрузки XAML через <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-145"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="ec9c1-146"><xref:System.Activities.Presentation.Services.ModelService> - используется конструктором для взаимодействия с редактируемой моделью рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-146"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="ec9c1-147"><xref:System.Activities.Presentation.Model.ModelTreeManager> - обеспечивает доступ к корневому элементу дерева элементов модели через <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-147"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="ec9c1-148"><xref:System.Activities.Presentation.UndoEngine> - реализует функциональность отмены и повтора операций.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-148"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="ec9c1-149"><xref:System.Activities.Presentation.Services.ViewService> - сопоставляет визуальные элементы с элементами базовой модели.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-149"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="ec9c1-150"><xref:System.Activities.Presentation.View.ViewStateService> - сохраняет состояния представления для элементов модели.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-150"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="ec9c1-151"><xref:System.Activities.Presentation.View.VirtualizedContainerService> - используется для настройки поведения пользовательского интерфейса виртуального контейнера.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-151"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="ec9c1-152"><xref:System.Activities.Presentation.Hosting.WindowHelperService> - служит для регистрации и отмены регистрации делегатов для уведомления о событиях.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-152"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="ec9c1-153">Кроме того, позволяет задавать владельца окна.</span><span class="sxs-lookup"><span data-stu-id="ec9c1-153">Also allows a window owner to be set.</span></span>
