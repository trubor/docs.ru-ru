---
title: Практическое руководство. Подключение делегата с помощью отражения
description: Узнайте, как подключить делегата с помощью отражения в .NET. Подключите существующий метод к событию посредством получения всех необходимых типов через отражение.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: 9a92afd1c2aeadeb0cf7bc1e626b5bd1fb3cecea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263429"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="e0e5a-104">Практическое руководство. Подключение делегата с помощью отражения</span><span class="sxs-lookup"><span data-stu-id="e0e5a-104">How to: Hook Up a Delegate Using Reflection</span></span>

<span data-ttu-id="e0e5a-105">При использовании отражения для загрузки и запуска сборок невозможно использовать функциональные возможности языка, такие как оператор C# `+=` или [оператор AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="e0e5a-106">В следующих процедурах показано, как подключить существующий метод к событию посредством получения всех необходимых типов через отражение и как создать динамический метод с помощью порожденного отражения и подключить этот метод к событию.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0e5a-107">Другой способ подключения делегата, обрабатывающего события, см. в примере кода для метода <xref:System.Reflection.EventInfo.AddEventHandler%2A> класса <xref:System.Reflection.EventInfo>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="e0e5a-108">Подключение делегата с помощью отражения</span><span class="sxs-lookup"><span data-stu-id="e0e5a-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="e0e5a-109">Загрузите сборку, которая содержит тип, создающий события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="e0e5a-110">Как правило, сборки загружаются с помощью метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e0e5a-111">Чтобы не усложнять этот пример, используется производная форма из текущей сборки, чтобы для загрузки текущей сборки использовался метод <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="e0e5a-112">Получите объект <xref:System.Type>, который представляет тип, и создайте экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="e0e5a-113">Метод <xref:System.Activator.CreateInstance%28System.Type%29> используется в следующем коде, так как эта форма имеет конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="e0e5a-114">Существует несколько других перегрузок метода <xref:System.Activator.CreateInstance%2A>, которые можно использовать, если создаваемый тип не имеет конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="e0e5a-115">Новый экземпляр сохраняется как тип <xref:System.Object> для поддержки утверждения, что об этой сборке ничего не известно.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="e0e5a-116">(Отражение позволяет получить типы в сборке, заведомо не зная их имена.)</span><span class="sxs-lookup"><span data-stu-id="e0e5a-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="e0e5a-117">Получите объект <xref:System.Reflection.EventInfo>, который представляет событие, и используйте свойство <xref:System.Reflection.EventInfo.EventHandlerType%2A> для получения типа делегата, используемого для обработки события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="e0e5a-118">В следующем коде получается объект <xref:System.Reflection.EventInfo> для события <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="e0e5a-119">Получите объект <xref:System.Reflection.MethodInfo>, который представляет метод, обрабатывающий событие.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="e0e5a-120">Полный код программы в подразделе "Пример" этого раздела содержит метод, который соответствует сигнатуре делегата <xref:System.EventHandler>, который обрабатывает событие <xref:System.Windows.Forms.Control.Click>, однако также можно создавать динамические методы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="e0e5a-121">Дополнительные сведения о создании обработчика события во время выполнения с использованием динамического метода см. в описании сопутствующей процедуры.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="e0e5a-122">Создайте экземпляр делегата с помощью метода <xref:System.Delegate.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="e0e5a-123">Этот метод является статическим (`Shared` в Visual Basic), поэтому следует предоставить тип делегата.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="e0e5a-124">Рекомендуется использовать перегрузки метода <xref:System.Delegate.CreateDelegate%2A>, принимающие <xref:System.Reflection.MethodInfo>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="e0e5a-125">Получите метод доступа `add` и вызовите его для подключения события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="e0e5a-126">Все события имеют метод доступа `add` и метод доступа `remove`, которые скрыты с помощью синтаксиса в высокоуровневых языках.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="e0e5a-127">Например, в C# используется оператор `+=` для подключения событий, а в Visual Basic используется [оператор AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e0e5a-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="e0e5a-128">В следующем коде получается метод доступа `add` для события <xref:System.Windows.Forms.Control.Click> и вызывается с поздней привязкой, передавая в него экземпляр делегата.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="e0e5a-129">Аргументы должны передаваться в качестве массива.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="e0e5a-130">Проверьте событие.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-130">Test the event.</span></span> <span data-ttu-id="e0e5a-131">В следующем фрагменте кода показана форма, определенная в примере кода.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="e0e5a-132">Щелчок формы приводит к вызову обработчика события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>

### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="e0e5a-133">Создание обработчика событий во время выполнения с помощью динамического метода</span><span class="sxs-lookup"><span data-stu-id="e0e5a-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="e0e5a-134">Методы обработчика события могут быть созданы во время выполнения с помощью облегченных динамических методов и порождения отражения.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="e0e5a-135">Чтобы создать обработчик событий, будут необходимы тип возвращаемого значения и типы параметров делегата.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="e0e5a-136">Их можно получить, просмотрев метод `Invoke`, относящийся к делегату.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="e0e5a-137">В следующем примере кода используются методы `GetDelegateReturnType` и `GetDelegateParameterTypes` для получения этих сведений.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="e0e5a-138">Код для этих методов можно найти в подразделе "Пример" этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="e0e5a-139">Нет необходимости называть <xref:System.Reflection.Emit.DynamicMethod>, поэтому можно использовать пустую строку.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="e0e5a-140">В следующем коде последний аргумент связывает динамический метод с текущим типом, предоставляя доступ делегата ко всем открытым и закрытым элементам класса `Example`.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="e0e5a-141">Создайте основную часть метода.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-141">Generate a method body.</span></span> <span data-ttu-id="e0e5a-142">Этот метод загружает строку, вызывает перегрузку метода <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>, которая принимает строку, берет возвращаемое значение из стека (потому что обработчик не имеет типа возвращаемого значения) и возвращается.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="e0e5a-143">Дополнительные сведения о выпуске динамических методов см. в разделе [Практическое руководство. Определение и выполнение динамических методов](how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e0e5a-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="e0e5a-144">Завершите динамический метод посредством вызова метода <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="e0e5a-145">Используйте метод доступа `add` для добавления делегата в список вызова для этого события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="e0e5a-146">Проверьте событие.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-146">Test the event.</span></span> <span data-ttu-id="e0e5a-147">В следующем фрагменте кода загружается форма, определенная в примере кода.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="e0e5a-148">Щелчок этой формы приводит к вызову предварительно определенного обработчика события и выпущенного обработчика события.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="e0e5a-149">Пример</span><span class="sxs-lookup"><span data-stu-id="e0e5a-149">Example</span></span>  

 <span data-ttu-id="e0e5a-150">В следующем примере кода показано, как подключить существующий метод к событию с помощью отражения, а также как использовать класс <xref:System.Reflection.Emit.DynamicMethod> для выпуска метода во время выполнения и подключить его к событию.</span><span class="sxs-lookup"><span data-stu-id="e0e5a-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e5a-151">См. также</span><span class="sxs-lookup"><span data-stu-id="e0e5a-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="e0e5a-152">Практическое руководство. Определение и выполнение динамических методов</span><span class="sxs-lookup"><span data-stu-id="e0e5a-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="e0e5a-153">Отражение</span><span class="sxs-lookup"><span data-stu-id="e0e5a-153">Reflection</span></span>](reflection.md)
