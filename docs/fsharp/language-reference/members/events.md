---
title: События
description: 'Узнайте, как события F # позволяют связывать вызовы функций с действиями пользователя, которые важны для программирования GUI.'
ms.date: 08/15/2020
ms.openlocfilehash: 17e0cc8840053bf24d5c69694fe94d544c44510d
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740345"
---
# <a name="events"></a><span data-ttu-id="e85e8-103">События</span><span class="sxs-lookup"><span data-stu-id="e85e8-103">Events</span></span>

<span data-ttu-id="e85e8-104">События позволяют связывать вызовы функций с действиями пользователя и являются важным элементом в программировании графического интерфейса пользователя.</span><span class="sxs-lookup"><span data-stu-id="e85e8-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="e85e8-105">События могут также инициироваться приложениями или операционной системой.</span><span class="sxs-lookup"><span data-stu-id="e85e8-105">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="e85e8-106">Обработка событий</span><span class="sxs-lookup"><span data-stu-id="e85e8-106">Handling Events</span></span>

<span data-ttu-id="e85e8-107">При использовании библиотеки графического интерфейса пользователя, такой как Windows Forms или Windows Presentation Foundation (WPF), значительная часть кода в приложении выполняется в ответ на события, предопределенные в библиотеке.</span><span class="sxs-lookup"><span data-stu-id="e85e8-107">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="e85e8-108">Эти предопределенные события являются членами классов графического интерфейса пользователя, таких как формы и элементы управления.</span><span class="sxs-lookup"><span data-stu-id="e85e8-108">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="e85e8-109">Можно добавить произвольное поведение к уже существующему событию, такому как нажатие кнопки, сославшись на интересующее именованное событие (например, событие `Click` класса `Form`) и вызвав метод `Add`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="e85e8-109">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="e85e8-110">При запуске этого кода из F# Interactive вызов метода `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` следует опустить.</span><span class="sxs-lookup"><span data-stu-id="e85e8-110">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="e85e8-111">Тип метода `Add` — `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="e85e8-111">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="e85e8-112">Следовательно, метод, обрабатывающий событие, принимает один параметр — обычно аргументы события — и возвращает значение типа `unit`.</span><span class="sxs-lookup"><span data-stu-id="e85e8-112">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="e85e8-113">В предыдущем примере обработчик события показан как лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="e85e8-113">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="e85e8-114">Обработчик события также может представлять собой значение функции, как в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="e85e8-114">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="e85e8-115">В следующем примере кода также показано использование параметров обработчика события, содержащих данные, зависящие от типа события.</span><span class="sxs-lookup"><span data-stu-id="e85e8-115">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="e85e8-116">Для события `MouseMove` система передает объект `System.Windows.Forms.MouseEventArgs`, содержащий координаты `X` и `Y` положения указателя.</span><span class="sxs-lookup"><span data-stu-id="e85e8-116">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="e85e8-117">Создание пользовательских событий</span><span class="sxs-lookup"><span data-stu-id="e85e8-117">Creating Custom Events</span></span>

<span data-ttu-id="e85e8-118">События f # представлены типом [события](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) f #, который реализует интерфейс [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) .</span><span class="sxs-lookup"><span data-stu-id="e85e8-118">F# events are represented by the F# [Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) type, which implements the [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) interface.</span></span> <span data-ttu-id="e85e8-119">`IEvent` является интерфейсом, объединяющим функциональность двух других интерфейсов `System.IObservable<'T>` и [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span><span class="sxs-lookup"><span data-stu-id="e85e8-119">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span></span> <span data-ttu-id="e85e8-120">Следовательно, события `Event` обладают функциональными возможностями, эквивалентными возможностям делегатов в других языках, и дополнительно функциональными возможностями интерфейса `IObservable`; это означает, что события F# поддерживают фильтрацию событий и использование функций первого класса и лямбда-выражений языка F# в качестве обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="e85e8-120">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="e85e8-121">Эта функция предоставляется в [модуле Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span><span class="sxs-lookup"><span data-stu-id="e85e8-121">This functionality is provided in the [Event module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span></span>

<span data-ttu-id="e85e8-122">Чтобы создать для класса событие, которое ведет себя точно так же, как любое другое событие платформы .NET Framework, добавьте в класс привязку `let`, определяющую событие `Event` как поле в классе.</span><span class="sxs-lookup"><span data-stu-id="e85e8-122">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="e85e8-123">В качестве аргумента типа можно указать требуемый тип аргумента события или оставить его пустым, чтобы соответствующий тип был выведен компилятором.</span><span class="sxs-lookup"><span data-stu-id="e85e8-123">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="e85e8-124">Необходимо также определить член события, предоставляющего это событие как событие CLI.</span><span class="sxs-lookup"><span data-stu-id="e85e8-124">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="e85e8-125">Этот элемент должен иметь атрибут [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="e85e8-125">This member should have the [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) attribute.</span></span> <span data-ttu-id="e85e8-126">Он объявляется как свойство, а его реализация — просто вызовом свойства [публикации](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) события.</span><span class="sxs-lookup"><span data-stu-id="e85e8-126">It is declared like a property and its implementation is just a call to the [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) property of the event.</span></span> <span data-ttu-id="e85e8-127">Пользователи класса могут использовать метод `Add` опубликованного события для добавления обработчика.</span><span class="sxs-lookup"><span data-stu-id="e85e8-127">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="e85e8-128">Аргумент метода `Add` может быть лямбда-выражением.</span><span class="sxs-lookup"><span data-stu-id="e85e8-128">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="e85e8-129">Для вызова события можно использовать его свойство `Trigger`, передавая аргументы функции обработчика.</span><span class="sxs-lookup"><span data-stu-id="e85e8-129">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="e85e8-130">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="e85e8-130">The following code example illustrates this.</span></span> <span data-ttu-id="e85e8-131">В этом примере выведенный аргумент типа для события — кортеж, представляющий аргументы для лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="e85e8-131">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="e85e8-132">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e85e8-132">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="e85e8-133">Здесь иллюстрируется дополнительная функциональная возможность, обеспечиваемая модулем `Event`.</span><span class="sxs-lookup"><span data-stu-id="e85e8-133">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="e85e8-134">Следующий пример кода иллюстрирует основное использование функции `Event.create` для создания события и метода-триггера, добавления двух обработчиков события в виде лямбда-выражений и последующего инициирования события для выполнения обоих лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="e85e8-134">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="e85e8-135">Результат выполнения приведенного кода будет следующим.</span><span class="sxs-lookup"><span data-stu-id="e85e8-135">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="e85e8-136">Обработка потоков событий</span><span class="sxs-lookup"><span data-stu-id="e85e8-136">Processing Event Streams</span></span>

<span data-ttu-id="e85e8-137">Вместо добавления обработчика событий для события с помощью функции [Event. Add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) можно использовать функции в `Event` модуле для обработки потоков событий в очень настраиваемых способах.</span><span class="sxs-lookup"><span data-stu-id="e85e8-137">Instead of just adding an event handler for an event by using the [Event.add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="e85e8-138">Это делается путем использования оператора прямого конвейера (`|>`) вместе с событием в качестве первого значения в серии вызовов функций и функций модуля `Event` в качестве последующих вызовов функций.</span><span class="sxs-lookup"><span data-stu-id="e85e8-138">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="e85e8-139">В следующем примере кода демонстрируется, как настроить событие, обработчик которого вызывается только при определенных условиях.</span><span class="sxs-lookup"><span data-stu-id="e85e8-139">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="e85e8-140">[Наблюдаемый модуль](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) содержит аналогичные функции, которые работают с наблюдаемыми объектами.</span><span class="sxs-lookup"><span data-stu-id="e85e8-140">The [Observable module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="e85e8-141">Наблюдаемые объекты аналогичны событиям, но они активно подписываются на события только при создании подписки на такой объект.</span><span class="sxs-lookup"><span data-stu-id="e85e8-141">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="e85e8-142">Реализация события интерфейса</span><span class="sxs-lookup"><span data-stu-id="e85e8-142">Implementing an Interface Event</span></span>

<span data-ttu-id="e85e8-143">Разработка компонентов пользовательского интерфейса часто начинается с создания новой формы или нового элемента управления, наследуемых от существующих формы или элемента управления.</span><span class="sxs-lookup"><span data-stu-id="e85e8-143">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="e85e8-144">События часто определяются в интерфейсе. В этом случае для реализации события необходимо реализовать интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e85e8-144">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="e85e8-145">Интерфейс `System.ComponentModel.INotifyPropertyChanged` определяет одно событие `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="e85e8-145">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="e85e8-146">В представленном ниже коде показана реализация события, которое определил этот унаследованный интерфейс:</span><span class="sxs-lookup"><span data-stu-id="e85e8-146">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="e85e8-147">Если требуется подключить событие в конструкторе, код будет несколько сложнее, поскольку подключение события должно находиться в блоке `then` дополнительного конструктора, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="e85e8-147">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="e85e8-148">См. также</span><span class="sxs-lookup"><span data-stu-id="e85e8-148">See also</span></span>

- [<span data-ttu-id="e85e8-149">Члены</span><span class="sxs-lookup"><span data-stu-id="e85e8-149">Members</span></span>](index.md)
- [<span data-ttu-id="e85e8-150">Обработка и вызов событий</span><span class="sxs-lookup"><span data-stu-id="e85e8-150">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="e85e8-151">Лямбда-выражения: `fun` ключевое слово</span><span class="sxs-lookup"><span data-stu-id="e85e8-151">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
