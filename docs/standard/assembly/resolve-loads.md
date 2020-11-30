---
title: Разрешение загрузки сборок
description: В этой статье описывается событие .NET AppDomain.AssemblyResolve. Используйте это событие для приложений, которым требуется контроль над загрузкой сборок.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: edd101e57793668d71d44db08f191ae412c6d998
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720910"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="73537-104">Разрешение загрузки сборок</span><span class="sxs-lookup"><span data-stu-id="73537-104">Resolve assembly loads</span></span>

<span data-ttu-id="73537-105">В .NET имеется событие <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> для приложений, требующих дополнительного управления загрузкой сборок.</span><span class="sxs-lookup"><span data-stu-id="73537-105">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="73537-106">Обрабатывая это событие, приложение может загружать сборку в контекст загрузки не из каталогов, где обычно осуществляется поиск, выбирать, какую из версий сборки загрузить, создавать динамическую сборку и возвращать ее и многое другое.</span><span class="sxs-lookup"><span data-stu-id="73537-106">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="73537-107">В этом разделе описывается использование события <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="73537-107">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73537-108">Для разрешения загрузки сборок в контексте только для отражения используйте событие <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73537-108">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="73537-109">Принцип действия события AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="73537-109">How the AssemblyResolve event works</span></span>  

 <span data-ttu-id="73537-110">При регистрации обработчика для события <xref:System.AppDomain.AssemblyResolve> обработчик вызывается каждый раз, когда среда выполнения не может связать сборку по имени.</span><span class="sxs-lookup"><span data-stu-id="73537-110">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="73537-111">Например, вызов следующих методов из пользовательского кода может привести к возникновению события <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="73537-111">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="73537-112">Перегрузка метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или перегрузка метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, где первым аргументом является строка, представляющая отображаемое имя загружаемой сборки (то есть строка, возвращаемая свойством <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="73537-112">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="73537-113">Перегрузка метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или перегрузка метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, где первым аргументом является объект <xref:System.Reflection.AssemblyName>, идентифицирующий загружаемую сборку.</span><span class="sxs-lookup"><span data-stu-id="73537-113">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="73537-114">Перегрузка метода <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73537-114">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="73537-115">Перегрузка метода <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> или <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>, создающая объект в другом домене приложения.</span><span class="sxs-lookup"><span data-stu-id="73537-115">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="73537-116">Действия обработчика событий</span><span class="sxs-lookup"><span data-stu-id="73537-116">What the event handler does</span></span>  

 <span data-ttu-id="73537-117">Обработчик события <xref:System.AppDomain.AssemblyResolve> получает отображаемое имя сборки, которую необходимо загрузить, в свойстве <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73537-117">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="73537-118">Если обработчик не распознает имя сборки, он возвращает значение `null` (C#), `Nothing` (Visual Basic) или `nullptr` (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="73537-118">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="73537-119">Если обработчик распознает имя сборки, он может загрузить и вернуть сборку, отвечающую запросу.</span><span class="sxs-lookup"><span data-stu-id="73537-119">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="73537-120">Ниже перечислены некоторые возможные сценарии.</span><span class="sxs-lookup"><span data-stu-id="73537-120">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="73537-121">Если обработчик знает место расположения версии сборки, он может загрузить сборку с помощью метода <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> и, если все прошло удачно, вернуть загруженную сборку.</span><span class="sxs-lookup"><span data-stu-id="73537-121">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="73537-122">Если у обработчика есть доступ к базе данных сборок, хранимых в виде массивов байтов, он может загрузить массив байтов с помощью одной из перегрузок метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, принимающих массив байтов.</span><span class="sxs-lookup"><span data-stu-id="73537-122">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="73537-123">Обработчик может создать динамическую сборку и вернуть ее.</span><span class="sxs-lookup"><span data-stu-id="73537-123">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73537-124">Обработчик должен загружать сборку в контекст, из которого ведется загрузка, в контекст загрузки или без контекста. Если обработчик загружает сборку в контекст только для отражения с помощью метода <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, попытка загрузки, вызвавшая событие <xref:System.AppDomain.AssemblyResolve>, завершается неудачно.</span><span class="sxs-lookup"><span data-stu-id="73537-124">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="73537-125">Ответственность за возврат подходящей сборки лежит на обработчике событий.</span><span class="sxs-lookup"><span data-stu-id="73537-125">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="73537-126">Обработчик может обработать отображаемое имя запрошенной сборки, передав значение свойства <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> в конструктор <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="73537-126">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="73537-127">Начиная с .NET Framework 4, обработчик может использовать свойство <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> для определения, находится ли текущий запрос в зависимости от другой сборки.</span><span class="sxs-lookup"><span data-stu-id="73537-127">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="73537-128">Эта информация может помочь найти сборку, которая удовлетворит зависимость.</span><span class="sxs-lookup"><span data-stu-id="73537-128">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="73537-129">Обработчик событий может вернуть версию сборки, отличную от запрошенной.</span><span class="sxs-lookup"><span data-stu-id="73537-129">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="73537-130">В большинстве случаев сборка, возвращенная обработчиком, появляется в контексте загрузки, независимо от контекста, в который загружает ее обработчик.</span><span class="sxs-lookup"><span data-stu-id="73537-130">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="73537-131">Например, если обработчик использует метод <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> для загрузки сборки в контекст, из которого ведется загрузка, сборка появляется в контексте загрузки, когда обработчик возвращает ее.</span><span class="sxs-lookup"><span data-stu-id="73537-131">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="73537-132">Но в следующем случае возвращенная обработчиком сборка появится без контекста.</span><span class="sxs-lookup"><span data-stu-id="73537-132">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="73537-133">Обработчик загружает сборку без контекста.</span><span class="sxs-lookup"><span data-stu-id="73537-133">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="73537-134">Значение свойства <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> отличается от NULL.</span><span class="sxs-lookup"><span data-stu-id="73537-134">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="73537-135">Запрашивающая сборка (то есть сборка, возвращенная свойством <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) загружена без контекста.</span><span class="sxs-lookup"><span data-stu-id="73537-135">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="73537-136">Сведения о контекстах см. в разделе о перегрузке метода <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73537-136">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="73537-137">Несколько версий одной сборки можно загрузить в один домен приложения.</span><span class="sxs-lookup"><span data-stu-id="73537-137">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="73537-138">Делать так не рекомендуется, так как это может привести к проблемам назначения типа.</span><span class="sxs-lookup"><span data-stu-id="73537-138">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="73537-139">См. раздел [Рекомендации для загрузки сборок](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="73537-139">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="73537-140">Чего не должен делать обработчик событий</span><span class="sxs-lookup"><span data-stu-id="73537-140">What the event handler should not do</span></span>  

<span data-ttu-id="73537-141">Основное правило обработки события <xref:System.AppDomain.AssemblyResolve> заключается в том, что не следует пытаться вернуть сборку, которая не распознается.</span><span class="sxs-lookup"><span data-stu-id="73537-141">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="73537-142">При написании обработчика следует учитывать, какие сборки могут вызвать событие.</span><span class="sxs-lookup"><span data-stu-id="73537-142">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="73537-143">Обработчик должен возвращать значение NULL для других сборок.</span><span class="sxs-lookup"><span data-stu-id="73537-143">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="73537-144">Начиная с .NET Framework 4 событие <xref:System.AppDomain.AssemblyResolve> вызывается для вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="73537-144">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="73537-145">Это изменение затрагивает обработчик событий, написанный для более ранней версии .NET Framework, если обработчик пытается разрешить все запросы на загрузку сборок.</span><span class="sxs-lookup"><span data-stu-id="73537-145">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="73537-146">Это изменение не затрагивает обработчики событий, игнорирующие нераспознанные сборки. Такие обработчики возвращают значение NULL, и срабатывают обычные резервные механизмы.</span><span class="sxs-lookup"><span data-stu-id="73537-146">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="73537-147">При загрузке сборки обработчик событий не должен использовать какую-либо из перегрузок метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, которые могут вызвать рекурсивное возникновение события <xref:System.AppDomain.AssemblyResolve>, так как это может привести к переполнению стека.</span><span class="sxs-lookup"><span data-stu-id="73537-147">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="73537-148">(См. список выше в этом разделе.) Это происходит, даже если обрабатывать исключения, так как исключение не создается, пока все обработчики событий не закончат возврат.</span><span class="sxs-lookup"><span data-stu-id="73537-148">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="73537-149">Таким образом, следующий код приведет к переполнению стека, если объект `MyAssembly` не будет найден.</span><span class="sxs-lookup"><span data-stu-id="73537-149">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="73537-150">См. также</span><span class="sxs-lookup"><span data-stu-id="73537-150">See also</span></span>

- [<span data-ttu-id="73537-151">Рекомендации для загрузки сборок</span><span class="sxs-lookup"><span data-stu-id="73537-151">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="73537-152">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="73537-152">Use application domains</span></span>](../../framework/app-domains/use.md)
