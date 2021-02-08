---
description: 'Дополнительные сведения о: закладки'
title: Закладки — WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: b4f0e68e0868ecd4eb97673ff6c09ee8c806cf43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787933"
---
# <a name="bookmarks"></a><span data-ttu-id="da68a-103">Закладки</span><span class="sxs-lookup"><span data-stu-id="da68a-103">Bookmarks</span></span>

<span data-ttu-id="da68a-104">Закладки - это механизм, позволяющий действиям пассивно ожидать ввода, не останавливая поток рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="da68a-104">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="da68a-105">Когда действие сообщает об ожидании внешнего воздействия, оно может создать закладку.</span><span class="sxs-lookup"><span data-stu-id="da68a-105">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="da68a-106">Это сообщает среде выполнения, что выполнение действия не должно считаться завершенным даже в случае возвращения управления из выполняющегося в данный момент метода (создавшего закладку <xref:System.Activities.Bookmark>).</span><span class="sxs-lookup"><span data-stu-id="da68a-106">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="da68a-107">Основные сведения о закладках</span><span class="sxs-lookup"><span data-stu-id="da68a-107">Bookmark Basics</span></span>  

 <span data-ttu-id="da68a-108">Закладка <xref:System.Activities.Bookmark> представляет точку, с которой может быть продолжено выполнение (и через которую могут быть переданы входные данные) в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="da68a-108">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="da68a-109">Обычно закладке <xref:System.Activities.Bookmark> присваиваются имя и внешний код (ведущего приложения или расширения), используемый для продолжения работы с точки закладки с соответствующими данными.</span><span class="sxs-lookup"><span data-stu-id="da68a-109">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="da68a-110">При возобновлении закладки <xref:System.Activities.Bookmark> среда выполнения рабочего процесса планирует делегат <xref:System.Activities.BookmarkCallback>, который был связан с этой закладкой <xref:System.Activities.Bookmark> на момент ее создания.</span><span class="sxs-lookup"><span data-stu-id="da68a-110">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="da68a-111">Параметры закладки</span><span class="sxs-lookup"><span data-stu-id="da68a-111">Bookmark Options</span></span>  

 <span data-ttu-id="da68a-112">В классе <xref:System.Activities.BookmarkOptions> указывается тип создаваемой закладки <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-112">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="da68a-113">Возможны следующие (не исключающие друг друга) значения: <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume> и <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="da68a-113">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="da68a-114">При создании закладки <xref:System.Activities.BookmarkOptions.None>, которая будет возобновлена ровно один раз, рекомендуется использовать вариант по умолчанию <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-114">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="da68a-115">При создании закладки <xref:System.Activities.BookmarkOptions.MultipleResume>, которая может быть возобновлена несколько раз, следует использовать вариант <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-115">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="da68a-116">При создании закладки <xref:System.Activities.BookmarkOptions.NonBlocking>, которая может быть не продолжена вообще, следует использовать параметр <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-116">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="da68a-117">В отличие от закладок, созданных с использованием параметров <xref:System.Activities.BookmarkOptions> по умолчанию, закладки типа <xref:System.Activities.BookmarkOptions.NonBlocking> не мешают завершению работы действия.</span><span class="sxs-lookup"><span data-stu-id="da68a-117">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="da68a-118">Возобновление закладок</span><span class="sxs-lookup"><span data-stu-id="da68a-118">Bookmark Resumption</span></span>  

 <span data-ttu-id="da68a-119">Закладки могут возобновляться кодом извне рабочего процесса с использованием одного из перегруженных методов <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="da68a-119">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="da68a-120">В этом примере создается действие `ReadLine`.</span><span class="sxs-lookup"><span data-stu-id="da68a-120">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="da68a-121">При выполнении действие `ReadLine` создает <xref:System.Activities.Bookmark>, регистрирует обратный вызов и ждет возобновления чтения с закладки <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-121">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="da68a-122">После возобновления чтения с закладки действие `ReadLine` присваивает данные, переданные с закладкой <xref:System.Activities.Bookmark>, своему аргументу <xref:System.Activities.Activity%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="da68a-122">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="da68a-123">В следующем примере создается рабочий процесс, использующий действие `ReadLine` для получения имени пользователя и его отображения в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="da68a-123">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="da68a-124">Ведущее приложение выполняет действительную работу по сбору входных данных и передает их в рабочий процесс, возобновляя закладку <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-124">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="da68a-125">При выполнении действие `ReadLine` создает закладку <xref:System.Activities.Bookmark> с именем `UserName` и ждет возобновления чтения с этой закладки.</span><span class="sxs-lookup"><span data-stu-id="da68a-125">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="da68a-126">Узел собирает необходимые данные и возобновляет чтение с закладки <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="da68a-126">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="da68a-127">Рабочий процесс возобновляется, отображает имя и затем завершается.</span><span class="sxs-lookup"><span data-stu-id="da68a-127">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="da68a-128">Следует заметить, что для возобновления закладки не требуется наличие кода синхронизации.</span><span class="sxs-lookup"><span data-stu-id="da68a-128">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="da68a-129">Закладка <xref:System.Activities.Bookmark> может быть возобновлена только при простое рабочего процесса; если рабочий процесс не простаивает, вызов <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> блокируется, пока рабочий процесс не перейдет в состояние простоя.</span><span class="sxs-lookup"><span data-stu-id="da68a-129">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="da68a-130">Результат возобновления закладки</span><span class="sxs-lookup"><span data-stu-id="da68a-130">Bookmark Resumption Result</span></span>  

 <span data-ttu-id="da68a-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> возвращает значение перечисления <xref:System.Activities.BookmarkResumptionResult>, сообщая о результате выполнения запроса возобновления закладки.</span><span class="sxs-lookup"><span data-stu-id="da68a-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="da68a-132">Возможны следующие возвращаемые значения: <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady> и <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="da68a-132">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="da68a-133">Ведущие приложения и расширения могут использовать эти значения для определения дальнейших действий.</span><span class="sxs-lookup"><span data-stu-id="da68a-133">Hosts and extensions can use this value to determine how to proceed.</span></span>
