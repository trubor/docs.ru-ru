---
title: Поведение маршалинга по умолчанию
description: Сведения о стандартном поведении маршалинга в .NET. Узнайте, как управлять памятью с помощью маршалинга взаимодействия, и о стандартном поведении маршалинга для классов, делегатов и типов значений.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 3e18bb5c4caa43a8e951eed3fc6992ec1b2d2afb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256662"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="96b42-104">Поведение маршалинга по умолчанию</span><span class="sxs-lookup"><span data-stu-id="96b42-104">Default Marshaling Behavior</span></span>

<span data-ttu-id="96b42-105">Маршалинг взаимодействия работает по правилам, которые определяют поведение данных, связанных с параметрами метода, при их передаче между управляемой и неуправляемой памятью.</span><span class="sxs-lookup"><span data-stu-id="96b42-105">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="96b42-106">Эти встроенные правила определяют такие операции маршалинга, как преобразования типов данных, возможность изменения вызываемым объектом переданных ему данных и возврата этих изменений вызывающему объекту, а также обстоятельства, при которых упаковщик обеспечивает оптимизацию производительности.</span><span class="sxs-lookup"><span data-stu-id="96b42-106">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="96b42-107">В этом разделе описаны стандартные характеристики службы маршалинга взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="96b42-107">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="96b42-108">Представлены подробные сведения о маршалинге массивов, логических типов, символьных типов, делегатов, классов, объектов, строк и структур.</span><span class="sxs-lookup"><span data-stu-id="96b42-108">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b42-109">Маршалинг универсальных типов не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="96b42-109">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="96b42-110">Дополнительные сведения см. в разделе [Взаимодействие с помощью универсальных типов](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="96b42-110">For more information see, [Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="96b42-111">Управление памятью с помощью упаковщика взаимодействия</span><span class="sxs-lookup"><span data-stu-id="96b42-111">Memory management with the interop marshaler</span></span>  

 <span data-ttu-id="96b42-112">Упаковщик взаимодействия всегда пытается освободить память, распределенную неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="96b42-112">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="96b42-113">Такое поведение согласуется с правилами управления памятью COM, но отличается от правил, присущих C++.</span><span class="sxs-lookup"><span data-stu-id="96b42-113">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="96b42-114">Путаница может возникать, если ожидается поведение в стиле C++ (память не освобождается) при вызове неуправляемого кода, при котором память автоматически освобождается для указателей.</span><span class="sxs-lookup"><span data-stu-id="96b42-114">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="96b42-115">Например, вызов приведенного ниже неуправляемого метода из библиотеки DLL C++ не освобождает память автоматически.</span><span class="sxs-lookup"><span data-stu-id="96b42-115">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="96b42-116">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="96b42-116">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="96b42-117">Однако если при определении метода в качестве прототипа вызова неуправляемого кода заменить каждый тип **BSTR** на тип <xref:System.String> и вызвать `MethodOne`, среда CLR дважды попытается освободить `b`.</span><span class="sxs-lookup"><span data-stu-id="96b42-117">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="96b42-118">Поведение маршалинга можно изменить с помощью типов <xref:System.IntPtr>, а не типов **String**.</span><span class="sxs-lookup"><span data-stu-id="96b42-118">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="96b42-119">Среда выполнения всегда использует метод **CoTaskMemFree** для освобождения памяти.</span><span class="sxs-lookup"><span data-stu-id="96b42-119">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="96b42-120">Если память, с которой работает программа, не была выделена с помощью метода **CoTaskMemAlloc**, то необходимо использовать **IntPtr** и освободить память вручную с применением подходящего метода.</span><span class="sxs-lookup"><span data-stu-id="96b42-120">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="96b42-121">Аналогичным образом можно избежать автоматического освобождения памяти в ситуациях, когда память ни при каких обстоятельствах не должна освобождаться, например при использовании функции **GetCommandLine** из Kernel32.dll, которая возвращает указатель в память ядра.</span><span class="sxs-lookup"><span data-stu-id="96b42-121">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="96b42-122">Подробнее об освобождении памяти вручную см. в разделе [Пример буферов](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="96b42-122">For details on manually freeing memory, see the [Buffers Sample](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="96b42-123">Маршалинг по умолчанию для классов</span><span class="sxs-lookup"><span data-stu-id="96b42-123">Default marshaling for classes</span></span>  

 <span data-ttu-id="96b42-124">Маршалинг классов может выполняться только с помощью COM-взаимодействия и только в качестве интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="96b42-124">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="96b42-125">Иногда интерфейс, используемый для маршалинга класса, называют интерфейсом класса.</span><span class="sxs-lookup"><span data-stu-id="96b42-125">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="96b42-126">Подробнее о переопределении интерфейса класса другим выбранным интерфейсом см. в статье [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса).</span><span class="sxs-lookup"><span data-stu-id="96b42-126">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="96b42-127">Передача классов в COM</span><span class="sxs-lookup"><span data-stu-id="96b42-127">Passing Classes to COM</span></span>  

 <span data-ttu-id="96b42-128">При передаче управляемого класса в COM упаковщик взаимодействия автоматически инкапсулирует этот класс, используя COM-прокси, и передает интерфейс класса, полученный с помощью прокси, в вызов метода COM.</span><span class="sxs-lookup"><span data-stu-id="96b42-128">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="96b42-129">Затем прокси делегирует все вызовы для интерфейса класса назад в управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="96b42-129">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="96b42-130">Прокси также предоставляет другие интерфейсы, которые не реализованы классом явным образом.</span><span class="sxs-lookup"><span data-stu-id="96b42-130">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="96b42-131">Прокси от имени класса автоматически реализует такие интерфейсы, как **IUnknown** и **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="96b42-131">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="96b42-132">Передача классов в код .NET</span><span class="sxs-lookup"><span data-stu-id="96b42-132">Passing Classes to .NET Code</span></span>  

 <span data-ttu-id="96b42-133">В COM коклассы обычно не используются в качестве аргументов метода.</span><span class="sxs-lookup"><span data-stu-id="96b42-133">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="96b42-134">Вместо кокласса обычно передается интерфейс по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="96b42-134">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="96b42-135">При передаче интерфейса в управляемый код упаковщик взаимодействия отвечает за инкапсуляцию интерфейса в соответствующую оболочку и за передачу этой оболочки в управляемый метод.</span><span class="sxs-lookup"><span data-stu-id="96b42-135">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="96b42-136">Выбор используемой оболочки может вызывать затруднения.</span><span class="sxs-lookup"><span data-stu-id="96b42-136">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="96b42-137">У каждого экземпляра COM-объекта есть одна уникальная оболочка вне зависимости от числа интерфейсов, реализуемых объектом.</span><span class="sxs-lookup"><span data-stu-id="96b42-137">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="96b42-138">Например, COM-объект, реализующий пять различных интерфейсов, имеет только одну оболочку.</span><span class="sxs-lookup"><span data-stu-id="96b42-138">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="96b42-139">Одна и та же оболочка предоставляет все пять интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="96b42-139">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="96b42-140">Если создаются два экземпляра COM-объекта, то создаются и два экземпляра оболочки.</span><span class="sxs-lookup"><span data-stu-id="96b42-140">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="96b42-141">Чтобы тип оболочки не менялся в течение всего времени ее существования, упаковщик взаимодействия должен выбрать правильную оболочку при первой передаче интерфейса, предоставляемого данным объектом, через упаковщик.</span><span class="sxs-lookup"><span data-stu-id="96b42-141">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="96b42-142">Упаковщик идентифицирует объект, просматривая один из интерфейсов, реализуемых объектом.</span><span class="sxs-lookup"><span data-stu-id="96b42-142">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="96b42-143">Например, упаковщик определяет, что оболочка класса должна использоваться для инкапсуляции интерфейса, переданного в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="96b42-143">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="96b42-144">При первой передаче этого интерфейса через упаковщик последний проверяет, поступил ли этот интерфейс от известного объекта.</span><span class="sxs-lookup"><span data-stu-id="96b42-144">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="96b42-145">Эта проверка выполняется в двух случаях:</span><span class="sxs-lookup"><span data-stu-id="96b42-145">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="96b42-146">Интерфейс реализуется другим управляемым объектом, переданным в COM где-то в другом месте.</span><span class="sxs-lookup"><span data-stu-id="96b42-146">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="96b42-147">Упаковщик может легко идентифицировать интерфейсы, предоставляемые управляемыми объектами, и может находить соответствие между интерфейсом и управляемым объектом, предоставившим реализацию.</span><span class="sxs-lookup"><span data-stu-id="96b42-147">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="96b42-148">Затем управляемый объект передается в метод, и никакой оболочки не требуется.</span><span class="sxs-lookup"><span data-stu-id="96b42-148">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="96b42-149">Интерфейс реализуется объектом, который уже инкапсулирован.</span><span class="sxs-lookup"><span data-stu-id="96b42-149">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="96b42-150">Чтобы определить, так ли это, упаковщик запрашивает у объекта его интерфейс **IUnknown** и сравнивает возвращенный интерфейс с интерфейсами других, уже инкапсулированных объектов.</span><span class="sxs-lookup"><span data-stu-id="96b42-150">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="96b42-151">Если интерфейс совпадает с интерфейсом другой оболочки, то объекты имеют одинаковые идентификаторы и существующая оболочка передается методу.</span><span class="sxs-lookup"><span data-stu-id="96b42-151">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="96b42-152">Если интерфейс не является интерфейсом известного объекта, упаковщик выполняет указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="96b42-152">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="96b42-153">Упаковщик запрашивает у объекта интерфейс **IProvideClassInfo2**.</span><span class="sxs-lookup"><span data-stu-id="96b42-153">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="96b42-154">Если он предоставлен, то упаковщик использует значение CLSID, возвращенное из **IProvideClassInfo2.GetGUID**, для идентификации кокласса, предоставляющего интерфейс.</span><span class="sxs-lookup"><span data-stu-id="96b42-154">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="96b42-155">Используя идентификатор CLSID, упаковщик может найти оболочку в реестре, если перед этим сборка была зарегистрирована.</span><span class="sxs-lookup"><span data-stu-id="96b42-155">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="96b42-156">Упаковщик запрашивает у этого интерфейса интерфейс **IProvideClassInfo**.</span><span class="sxs-lookup"><span data-stu-id="96b42-156">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="96b42-157">Если он предоставлен, упаковщик использует интерфейс **ITypeInfo**, возвращенный из метода **IProvideClassInfo.GetClassinfo**, для определения значения CLSID класса, предоставляющего интерфейс.</span><span class="sxs-lookup"><span data-stu-id="96b42-157">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="96b42-158">Упаковщик может использовать значение CLSID для нахождения метаданных оболочки.</span><span class="sxs-lookup"><span data-stu-id="96b42-158">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="96b42-159">Если упаковщик все еще не может идентифицировать класс, то он инкапсулирует интерфейс в оболочку универсального класса с именем **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="96b42-159">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="96b42-160">Маршалинг по умолчанию для делегатов</span><span class="sxs-lookup"><span data-stu-id="96b42-160">Default marshaling for delegates</span></span>  

 <span data-ttu-id="96b42-161">Управляемый делегат маршалируется как COM-интерфейс или как указатель на функцию на основе описанного ниже механизма вызовов.</span><span class="sxs-lookup"><span data-stu-id="96b42-161">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="96b42-162">Для вызова неуправляемого кода делегат по умолчанию маршалируется как указатель на функцию.</span><span class="sxs-lookup"><span data-stu-id="96b42-162">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="96b42-163">Для COM-взаимодействия делегат по умолчанию маршалируется как COM-интерфейс типа **_Delegate**.</span><span class="sxs-lookup"><span data-stu-id="96b42-163">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="96b42-164">Интерфейс **_Delegate** определяется в библиотеке типов Mscorlib.tlb и содержит метод <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType>, который позволяет вызывать метод, на который ссылается делегат.</span><span class="sxs-lookup"><span data-stu-id="96b42-164">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="96b42-165">В таблице ниже показаны варианты маршалинга для типа данных управляемого делегата.</span><span class="sxs-lookup"><span data-stu-id="96b42-165">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="96b42-166">Атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> предоставляет несколько значений перечисления <xref:System.Runtime.InteropServices.UnmanagedType> для маршалинга делегатов.</span><span class="sxs-lookup"><span data-stu-id="96b42-166">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="96b42-167">Тип перечисления</span><span class="sxs-lookup"><span data-stu-id="96b42-167">Enumeration type</span></span>|<span data-ttu-id="96b42-168">Описание неуправляемого формата</span><span class="sxs-lookup"><span data-stu-id="96b42-168">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="96b42-169">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="96b42-169">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="96b42-170">Указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="96b42-170">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="96b42-171">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="96b42-171">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="96b42-172">Интерфейс типа **_Delegate**, как определено в Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="96b42-172">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="96b42-173">Рассмотрим пример кода, в котором методы `DelegateTestInterface` экспортируются в библиотеку типов COM.</span><span class="sxs-lookup"><span data-stu-id="96b42-173">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="96b42-174">Обратите внимание на то, что только делегаты, помеченные ключевым словом **ref** (или **ByRef**), передаются как параметры In/Out.</span><span class="sxs-lookup"><span data-stu-id="96b42-174">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="96b42-175">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="96b42-175">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="96b42-176">Указатель на функцию может быть разыменован, так же как и любой другой указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="96b42-176">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="96b42-177">В этом примере при маршалировании двух делегатов в качестве <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> будет получен результат `int` и указатель на `int`.</span><span class="sxs-lookup"><span data-stu-id="96b42-177">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="96b42-178">Поскольку типы делегатов маршалируются, `int` здесь представляет указатель на void (`void*`), то есть адрес делегата в памяти.</span><span class="sxs-lookup"><span data-stu-id="96b42-178">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="96b42-179">Другими словами, этот результат относится к 32-разрядным системам Windows, поскольку `int` здесь представляет размер указателя на функцию.</span><span class="sxs-lookup"><span data-stu-id="96b42-179">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="96b42-180">Ссылка на указатель на функцию в управляемом делегате, хранимая в неуправляемом коде, не препятствует выполнению средой CLR сборки мусора для управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="96b42-180">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="96b42-181">Например, приведенный ниже код некорректен, так как ссылка на объект `cb`, передаваемая методу `SetChangeHandler`, не сохраняет объект `cb` в активном состоянии по окончании времени существования метода `Test`.</span><span class="sxs-lookup"><span data-stu-id="96b42-181">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="96b42-182">После применения к объекту `cb` процедуры сборки мусора указатель на функцию, переданный в `SetChangeHandler`, становится недействительным.</span><span class="sxs-lookup"><span data-stu-id="96b42-182">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 <span data-ttu-id="96b42-183">Чтобы компенсировать неожиданную сборку мусора, вызывающий объект должен гарантировать, что объект `cb` будет находиться в активном состоянии до тех пор, пока используется указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="96b42-183">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="96b42-184">Как показано в примере ниже, при необходимости можно настроить передачу уведомлений от неуправляемого кода в управляемый о том, что указатель на функцию больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="96b42-184">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="96b42-185">Маршалинг по умолчанию для типов значений</span><span class="sxs-lookup"><span data-stu-id="96b42-185">Default marshaling for value types</span></span>  

 <span data-ttu-id="96b42-186">Большинство типов значений, такие как целые числа и числа с плавающей запятой, являются [непреобразуемыми](blittable-and-non-blittable-types.md) и не требуют маршалинга.</span><span class="sxs-lookup"><span data-stu-id="96b42-186">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="96b42-187">[Преобразуемые](blittable-and-non-blittable-types.md) типы представлены в управляемой и неуправляемой памяти по-разному и требуют маршалинга.</span><span class="sxs-lookup"><span data-stu-id="96b42-187">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="96b42-188">Другие типы требуют явного форматирования при пересечении границы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="96b42-188">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="96b42-189">В этом разделе представлены сведения о следующих форматированных типах значений:</span><span class="sxs-lookup"><span data-stu-id="96b42-189">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="96b42-190">Типы значений, используемые в вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="96b42-190">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="96b42-191">Типы значений, используемые в COM-взаимодействии</span><span class="sxs-lookup"><span data-stu-id="96b42-191">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="96b42-192">Кроме описания форматированных типов, в этом разделе определяются [системные типы значений](#system-value-types), имеющие нестандартное поведение маршалинга.</span><span class="sxs-lookup"><span data-stu-id="96b42-192">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="96b42-193">Форматированный тип — это сложный тип, который содержит информацию, явным образом определяющую размещение его членов в памяти.</span><span class="sxs-lookup"><span data-stu-id="96b42-193">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="96b42-194">Сведения о размещении членов предоставляются с помощью атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="96b42-194">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="96b42-195">Размещение может принимать одно из указанных ниже значений перечисления <xref:System.Runtime.InteropServices.LayoutKind>.</span><span class="sxs-lookup"><span data-stu-id="96b42-195">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="96b42-196">**LayoutKind.Auto**</span><span class="sxs-lookup"><span data-stu-id="96b42-196">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="96b42-197">Указывает, что среда CLR для повышения эффективности может свободно изменять порядок членов типа.</span><span class="sxs-lookup"><span data-stu-id="96b42-197">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="96b42-198">Тем не менее, когда тип значения передается в неуправляемый код, размещение членов является предсказуемым.</span><span class="sxs-lookup"><span data-stu-id="96b42-198">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="96b42-199">При попытке маршалинга такой структуры автоматически вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="96b42-199">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="96b42-200">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="96b42-200">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="96b42-201">Указывает, что члены типа должны размещаться в неуправляемой памяти в том же порядке, в котором они появляются в определении управляемого типа.</span><span class="sxs-lookup"><span data-stu-id="96b42-201">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="96b42-202">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="96b42-202">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="96b42-203">Указывает, что члены располагаются в соответствии с атрибутом <xref:System.Runtime.InteropServices.FieldOffsetAttribute>, предоставляемым с каждым полем.</span><span class="sxs-lookup"><span data-stu-id="96b42-203">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="96b42-204">Типы значений, используемые в вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="96b42-204">Value Types Used in Platform Invoke</span></span>  

 <span data-ttu-id="96b42-205">В примере ниже типы `Point` и `Rect` предоставляют сведения о размещении членов с помощью атрибута **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="96b42-205">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="96b42-206">При маршалинге в неуправляемый код эти форматированные типы маршалируются как структуры стиля C.</span><span class="sxs-lookup"><span data-stu-id="96b42-206">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="96b42-207">Это обеспечивает простой способ вызова неуправляемого интерфейса API с аргументами в виде структур.</span><span class="sxs-lookup"><span data-stu-id="96b42-207">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="96b42-208">Например, структуры `POINT` и `RECT` могут передаваться в функцию **PtInRect** Microsoft Windows API следующим образом:</span><span class="sxs-lookup"><span data-stu-id="96b42-208">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="96b42-209">Вы можете передать структуры с помощью следующего определения вызова неуправляемого кода:</span><span class="sxs-lookup"><span data-stu-id="96b42-209">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="96b42-210">Тип значения `Rect` должен передаваться по ссылке, потому что неуправляемый интерфейс API ожидает, что в функцию будет передан указатель на `RECT`.</span><span class="sxs-lookup"><span data-stu-id="96b42-210">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="96b42-211">Тип значения `Point` передается по значению, так как неуправляемый интерфейс API ожидает, что `POINT` будет передан в стек.</span><span class="sxs-lookup"><span data-stu-id="96b42-211">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="96b42-212">Это небольшое различие очень важно.</span><span class="sxs-lookup"><span data-stu-id="96b42-212">This subtle difference is very important.</span></span> <span data-ttu-id="96b42-213">Ссылки передаются в неуправляемый код как указатели.</span><span class="sxs-lookup"><span data-stu-id="96b42-213">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="96b42-214">Значения передаются в неуправляемый код в стеке.</span><span class="sxs-lookup"><span data-stu-id="96b42-214">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b42-215">При маршалинге форматированного типа в виде структуры доступны только поля внутри этого типа.</span><span class="sxs-lookup"><span data-stu-id="96b42-215">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="96b42-216">Если у типа есть методы, свойства или события, то они недоступны из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="96b42-216">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="96b42-217">Классы тоже можно маршалировать в неуправляемый код как структуры стиля языка С при условии, что они имеют фиксированное размещение членов.</span><span class="sxs-lookup"><span data-stu-id="96b42-217">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="96b42-218">Сведения о размещении членов класса также предоставляются с помощью атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="96b42-218">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="96b42-219">Основное различие между типами значений с фиксированным размещением и классами с фиксированным размещением заключает в способе маршалинга в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="96b42-219">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="96b42-220">Типы значений передаются по значению (в стеке), поэтому любые изменения, внесенные в члены этого типа вызываемым объектом, не видны вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="96b42-220">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="96b42-221">Ссылочные типы передаются по ссылке (ссылка на тип передается в стеке). Поэтому все изменения, внесенные в члены непреобразуемого типа вызываемым объектом, видны вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="96b42-221">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b42-222">Если ссылочный тип содержит члены преобразуемого типа, преобразование должно выполняться дважды: первый раз — при передаче аргумента неуправляемой стороне, а второй раз — при возврате из вызова.</span><span class="sxs-lookup"><span data-stu-id="96b42-222">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="96b42-223">В связи с появлением дополнительных издержек параметры In/Out необходимо применять к аргументу в явном виде, если вызывающий объект должен учитывать изменения, внесенные вызываемым объектом.</span><span class="sxs-lookup"><span data-stu-id="96b42-223">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="96b42-224">В примере ниже класс `SystemTime` имеет последовательное размещение членов и может быть передан в функцию **GetSystemTime** API Windows.</span><span class="sxs-lookup"><span data-stu-id="96b42-224">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 <span data-ttu-id="96b42-225">Функция **GetSystemTime** определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="96b42-225">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="96b42-226">Эквивалентное определение вызова неуправляемого кода **GetSystemTime** выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="96b42-226">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="96b42-227">Обратите внимание на то, что аргумент `SystemTime` не типизирован как ссылочный аргумент, потому что `SystemTime` — это класс, а не тип значения.</span><span class="sxs-lookup"><span data-stu-id="96b42-227">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="96b42-228">В отличие от типов значений, классы всегда передаются по ссылке.</span><span class="sxs-lookup"><span data-stu-id="96b42-228">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="96b42-229">В примере кода ниже показан другой класс `Point`, который содержит метод с именем `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="96b42-229">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="96b42-230">Так как этот тип имеет последовательную компоновку, он может быть передан в неуправляемый код и маршалирован как структура.</span><span class="sxs-lookup"><span data-stu-id="96b42-230">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="96b42-231">Однако член `SetXY` нельзя вызвать из неуправляемого кода, даже когда объект передается по ссылке.</span><span class="sxs-lookup"><span data-stu-id="96b42-231">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="96b42-232">Типы значений, используемые во COM-взаимодействии</span><span class="sxs-lookup"><span data-stu-id="96b42-232">Value Types Used in COM Interop</span></span>  

 <span data-ttu-id="96b42-233">Форматированные типы могут также передаваться в вызовы метода COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="96b42-233">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="96b42-234">Фактически при экспорте в библиотеку типов типы значений автоматически преобразуются в структуры.</span><span class="sxs-lookup"><span data-stu-id="96b42-234">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="96b42-235">Как показано в примере ниже, тип значения `Point` становится определением типа (typedef) с именем `Point`.</span><span class="sxs-lookup"><span data-stu-id="96b42-235">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="96b42-236">Все ссылки на тип значения `Point` в любом другом месте библиотеки типов заменяются на определение типа typedef `Point`.</span><span class="sxs-lookup"><span data-stu-id="96b42-236">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="96b42-237">**Представление библиотеки типов**</span><span class="sxs-lookup"><span data-stu-id="96b42-237">**Type library representation**</span></span>  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="96b42-238">Те же самые правила, которые используются для маршалинга значений и ссылок в вызовы неуправляемого кода, применяются и при маршалинге через COM-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="96b42-238">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="96b42-239">Например, когда экземпляр типа значения `Point` передается из .NET Framework в COM, `Point` передается по значению.</span><span class="sxs-lookup"><span data-stu-id="96b42-239">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="96b42-240">Если тип значения `Point` передается по ссылке, указатель на `Point` передается в стеке.</span><span class="sxs-lookup"><span data-stu-id="96b42-240">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="96b42-241">Упаковщик взаимодействия не поддерживает более высокие уровни косвенного обращения (**Point** \*\*) в любом направлении.</span><span class="sxs-lookup"><span data-stu-id="96b42-241">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b42-242">Структуры, для которых значение перечисления <xref:System.Runtime.InteropServices.LayoutKind> установлено равным **Explicit**, не могут использоваться в COM-взаимодействии, так как экспортированная библиотека типов не может представлять явное размещение.</span><span class="sxs-lookup"><span data-stu-id="96b42-242">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="96b42-243">Системные типы значений</span><span class="sxs-lookup"><span data-stu-id="96b42-243">System Value Types</span></span>  

 <span data-ttu-id="96b42-244">Пространство имен <xref:System> содержит несколько типов значений, представляющих собой упакованную форму простых типов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="96b42-244">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="96b42-245">Например, структура типов значений <xref:System.Int32?displayProperty=nameWithType> представляет собой упакованную форму **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="96b42-245">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="96b42-246">Вместо маршалинга этих типов в качестве структур, как в случае с другими форматированными типами, их следует маршалировать так же, как и соответствующие простые типы.</span><span class="sxs-lookup"><span data-stu-id="96b42-246">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="96b42-247">Соответственно, **System.Int32** маршалируется как **ELEMENT_TYPE_I4**, а не как структура, содержащая один член типа **long**.</span><span class="sxs-lookup"><span data-stu-id="96b42-247">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="96b42-248">В таблице ниже приведен список типов значений в пространстве имен **System**, являющихся упакованными представлениями простых типов.</span><span class="sxs-lookup"><span data-stu-id="96b42-248">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="96b42-249">Системный тип значения</span><span class="sxs-lookup"><span data-stu-id="96b42-249">System value type</span></span>|<span data-ttu-id="96b42-250">Тип элемента</span><span class="sxs-lookup"><span data-stu-id="96b42-250">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="96b42-251">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="96b42-251">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="96b42-252">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="96b42-252">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="96b42-253">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="96b42-253">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="96b42-254">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="96b42-254">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="96b42-255">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="96b42-255">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="96b42-256">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="96b42-256">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="96b42-257">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="96b42-257">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="96b42-258">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="96b42-258">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="96b42-259">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="96b42-259">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="96b42-260">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="96b42-260">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="96b42-261">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="96b42-261">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="96b42-262">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="96b42-262">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="96b42-263">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="96b42-263">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="96b42-264">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="96b42-264">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="96b42-265">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="96b42-265">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="96b42-266">Некоторые типы значений в пространстве имен **System** обрабатываются по-другому.</span><span class="sxs-lookup"><span data-stu-id="96b42-266">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="96b42-267">Так как неуправляемый код уже имеет хорошо определенные форматы для таких типов, у упаковщика есть специальные правила для их маршалинга.</span><span class="sxs-lookup"><span data-stu-id="96b42-267">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="96b42-268">В таблице ниже представлен список этих специальных типов значений в пространстве имен **System**, а также неуправляемых типов, в которые они маршалируются.</span><span class="sxs-lookup"><span data-stu-id="96b42-268">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="96b42-269">Системный тип значения</span><span class="sxs-lookup"><span data-stu-id="96b42-269">System value type</span></span>|<span data-ttu-id="96b42-270">Тип IDL</span><span class="sxs-lookup"><span data-stu-id="96b42-270">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="96b42-271">**DATE**</span><span class="sxs-lookup"><span data-stu-id="96b42-271">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="96b42-272">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="96b42-272">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="96b42-273">**GUID**</span><span class="sxs-lookup"><span data-stu-id="96b42-273">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="96b42-274">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="96b42-274">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="96b42-275">В приведенном ниже коде показано определение неуправляемых типов **DATE**, **GUID**, **DECIMAL** и **OLE_COLOR** в библиотеке типов Stdole2.</span><span class="sxs-lookup"><span data-stu-id="96b42-275">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="96b42-276">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="96b42-276">Type library representation</span></span>  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="96b42-277">В коде ниже показаны соответствующие определения в управляемом интерфейсе `IValueTypes`.</span><span class="sxs-lookup"><span data-stu-id="96b42-277">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="96b42-278">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="96b42-278">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="96b42-279">См. также</span><span class="sxs-lookup"><span data-stu-id="96b42-279">See also</span></span>

- [<span data-ttu-id="96b42-280">Преобразуемые и непреобразуемые типы</span><span class="sxs-lookup"><span data-stu-id="96b42-280">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="96b42-281">Копирование и закрепление</span><span class="sxs-lookup"><span data-stu-id="96b42-281">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="96b42-282">Маршалинг по умолчанию для массивов</span><span class="sxs-lookup"><span data-stu-id="96b42-282">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="96b42-283">Маршалинг по умолчанию для объектов</span><span class="sxs-lookup"><span data-stu-id="96b42-283">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="96b42-284">Маршалинг по умолчанию для строк</span><span class="sxs-lookup"><span data-stu-id="96b42-284">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
