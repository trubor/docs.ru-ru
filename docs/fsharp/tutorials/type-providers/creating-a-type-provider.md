---
title: Учебник. Создание поставщика типов
description: 'Узнайте, как создавать собственные поставщики типов F # в F # 3,0, изучив несколько поставщиков простых типов, чтобы продемонстрировать основные понятия.'
ms.date: 11/04/2019
ms.openlocfilehash: 65cb9616f66b5850135dbfcdd9b9a9dad30421de
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739702"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="0f467-103">Учебник. Создание поставщика типов</span><span class="sxs-lookup"><span data-stu-id="0f467-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="0f467-104">Механизм поставщика типов в F # является важной частью поддержки многофункционального программирования информации.</span><span class="sxs-lookup"><span data-stu-id="0f467-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="0f467-105">В этом учебнике объясняется, как создавать собственные поставщики типов, проследуя разработку нескольких поставщиков простых типов, чтобы продемонстрировать основные понятия.</span><span class="sxs-lookup"><span data-stu-id="0f467-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="0f467-106">Дополнительные сведения о механизме поставщика типов в F # см. в разделе [Поставщики типов](index.md).</span><span class="sxs-lookup"><span data-stu-id="0f467-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="0f467-107">Экосистема F # содержит ряд поставщиков типов для часто используемых служб Интернет-и корпоративных данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="0f467-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="0f467-108">For example:</span></span>

- <span data-ttu-id="0f467-109">[FSharp. Data](https://fsharp.github.io/FSharp.Data/) включает поставщики типов для форматов документов JSON, XML, CSV и HTML.</span><span class="sxs-lookup"><span data-stu-id="0f467-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="0f467-110">[Дескриптора SqlProvider](https://fsprojects.github.io/SQLProvider/) предоставляет строго типизированный доступ к базам данных SQL с помощью сопоставления объектов и запросов LINQ F # к этим источникам данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="0f467-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) имеет набор поставщиков типов для проверки внедрения T-SQL во время компиляции в F#.</span><span class="sxs-lookup"><span data-stu-id="0f467-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="0f467-112">[FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) — это старый набор поставщиков типов для использования только с .NET Frameworkным программированием для доступа к службам данных SQL, Entity Framework, ODATA и WSDL.</span><span class="sxs-lookup"><span data-stu-id="0f467-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="0f467-113">При необходимости можно создавать пользовательские поставщики типов или ссылаться на поставщики типов, созданные другими пользователями.</span><span class="sxs-lookup"><span data-stu-id="0f467-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="0f467-114">Например, в Организации может быть служба данных, предоставляющая большое и увеличивающееся количество именованных наборов данных, каждый из которых имеет собственную стабильную схему данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="0f467-115">Можно создать поставщик типов, который считывает схемы и представляет текущие наборы данных программисту строго типизированным способом.</span><span class="sxs-lookup"><span data-stu-id="0f467-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0f467-116">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="0f467-116">Before You Start</span></span>

<span data-ttu-id="0f467-117">Механизм поставщика типов в основном предназначен для внедрения стабильных данных и пространств сведений о службах в интерфейс программирования F #.</span><span class="sxs-lookup"><span data-stu-id="0f467-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="0f467-118">Этот механизм не предназначен для внедрения информационных пространств, изменения схемы которых производятся во время выполнения программы, в целях, относящихся к логике программы.</span><span class="sxs-lookup"><span data-stu-id="0f467-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="0f467-119">Кроме того, механизм не предназначен для мета-программирования внутри языка, хотя этот домен содержит некоторые допустимые варианты использования.</span><span class="sxs-lookup"><span data-stu-id="0f467-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="0f467-120">Этот механизм следует использовать только в том случае, если это необходимо, а разработка поставщика типов дает очень высокое значение.</span><span class="sxs-lookup"><span data-stu-id="0f467-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="0f467-121">Не следует писать поставщик типов, если схема недоступна.</span><span class="sxs-lookup"><span data-stu-id="0f467-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="0f467-122">Аналогично, следует избегать написания поставщика типов, где достаточно обычной (или даже существующей) библиотеки .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="0f467-123">Прежде чем начать, вы можете задать следующие вопросы:</span><span class="sxs-lookup"><span data-stu-id="0f467-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="0f467-124">У вас есть схема для источника информации?</span><span class="sxs-lookup"><span data-stu-id="0f467-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="0f467-125">Если да, то каково сопоставление в системе типов F # и .NET?</span><span class="sxs-lookup"><span data-stu-id="0f467-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="0f467-126">Можно ли использовать существующий (динамически типизированный) API в качестве отправной точки для реализации?</span><span class="sxs-lookup"><span data-stu-id="0f467-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="0f467-127">Будет ли ваша организация иметь достаточный объем использования поставщика типов, чтобы писать его целесообразным?</span><span class="sxs-lookup"><span data-stu-id="0f467-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="0f467-128">Будет ли нормальная библиотека .NET соответствовать вашим потребностям?</span><span class="sxs-lookup"><span data-stu-id="0f467-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="0f467-129">Сколько будет изменено в схеме?</span><span class="sxs-lookup"><span data-stu-id="0f467-129">How much will your schema change?</span></span>

- <span data-ttu-id="0f467-130">Будет ли оно изменяться во время кодирования?</span><span class="sxs-lookup"><span data-stu-id="0f467-130">Will it change during coding?</span></span>

- <span data-ttu-id="0f467-131">Будет ли он изменяться между сеансами кодирования?</span><span class="sxs-lookup"><span data-stu-id="0f467-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="0f467-132">Будет ли оно изменяться во время выполнения программы?</span><span class="sxs-lookup"><span data-stu-id="0f467-132">Will it change during program execution?</span></span>

<span data-ttu-id="0f467-133">Поставщики типов лучше всего подходят для ситуаций, когда схема является стабильной во время выполнения и в течение времени существования скомпилированного кода.</span><span class="sxs-lookup"><span data-stu-id="0f467-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="0f467-134">Поставщик простых типов</span><span class="sxs-lookup"><span data-stu-id="0f467-134">A Simple Type Provider</span></span>

<span data-ttu-id="0f467-135">Этот пример — Samples. Хелловорлдтипепровидер, аналогичный образцам в `examples` каталоге [пакета SDK поставщика типов F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="0f467-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="0f467-136">Поставщик делает доступным "пространство типа", которое содержит 100 удаленных типов, как показано в следующем примере кода с помощью синтаксиса подписи F # и пропуска сведений для всех, кроме `Type1` .</span><span class="sxs-lookup"><span data-stu-id="0f467-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="0f467-137">Дополнительные сведения о стирании типов см. Далее в подразделе [сведения о стирании указанных типов](#details-about-erased-provided-types) .</span><span class="sxs-lookup"><span data-stu-id="0f467-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="0f467-138">Обратите внимание, что набор типов и членов является статически известным.</span><span class="sxs-lookup"><span data-stu-id="0f467-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="0f467-139">Этот пример не использует возможности поставщиков для предоставления типов, зависящих от схемы.</span><span class="sxs-lookup"><span data-stu-id="0f467-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="0f467-140">Реализация поставщика типов описана в следующем коде, а сведения приведены в последующих разделах этой статьи.</span><span class="sxs-lookup"><span data-stu-id="0f467-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="0f467-141">Между этим кодом и примерами в сети могут быть различия.</span><span class="sxs-lookup"><span data-stu-id="0f467-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="0f467-142">Чтобы использовать этот поставщик, откройте отдельный экземпляр Visual Studio, создайте скрипт F #, а затем добавьте ссылку на поставщик из скрипта с помощью #r, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0f467-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="0f467-143">Затем найдите типы в `Samples.HelloWorldTypeProvider` пространстве имен, созданном поставщиком типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="0f467-144">Прежде чем перекомпилировать поставщик, убедитесь, что все экземпляры Visual Studio и F# Interactive, использующие библиотеку DLL поставщика, закрыты.</span><span class="sxs-lookup"><span data-stu-id="0f467-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="0f467-145">В противном случае произойдет ошибка сборки, так как выходная библиотека DLL будет заблокирована.</span><span class="sxs-lookup"><span data-stu-id="0f467-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="0f467-146">Чтобы отладить этот поставщик с помощью инструкций Print, создайте сценарий, который предоставляет проблему с поставщиком, а затем используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="0f467-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="0f467-147">Чтобы отладить этот поставщик с помощью Visual Studio, откройте Командная строка разработчика для Visual Studio с учетными данными администратора и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="0f467-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="0f467-148">В качестве альтернативы откройте Visual Studio, откройте меню Отладка, выберите `Debug/Attach to process…` и подключитесь к другому `devenv` процессу, в котором выполняется редактирование сценария.</span><span class="sxs-lookup"><span data-stu-id="0f467-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="0f467-149">С помощью этого метода можно легко ориентироваться на определенную логику в поставщике типов путем интерактивного ввода выражений во второй экземпляр (с полной технологией IntelliSense и другими функциями).</span><span class="sxs-lookup"><span data-stu-id="0f467-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="0f467-150">Можно отключить отладку Только мой код для лучшего обнаружения ошибок в созданном коде.</span><span class="sxs-lookup"><span data-stu-id="0f467-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="0f467-151">Сведения о том, как включить или отключить эту функцию, см. [в разделе Навигация по коду с помощью отладчика](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="0f467-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="0f467-152">Кроме того, можно также задать перехват первого шанса исключений, открыв `Debug` меню, а затем выбрав `Exceptions` или нажав клавиши CTRL + ALT + E, чтобы открыть `Exceptions` диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="0f467-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="0f467-153">В этом диалоговом окне в разделе `Common Language Runtime Exceptions` выберите `Thrown` флажок.</span><span class="sxs-lookup"><span data-stu-id="0f467-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="0f467-154">Реализация поставщика типов</span><span class="sxs-lookup"><span data-stu-id="0f467-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="0f467-155">В этом разделе описываются основные разделы реализации поставщика типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="0f467-156">Сначала необходимо определить тип самого поставщика пользовательского типа:</span><span class="sxs-lookup"><span data-stu-id="0f467-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="0f467-157">Этот тип должен быть открытым, и его необходимо пометить атрибутом [типепровидер](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) , чтобы компилятор распознал поставщик типов, если отдельный проект F # ссылается на сборку, содержащую тип.</span><span class="sxs-lookup"><span data-stu-id="0f467-157">This type must be public, and you must mark it with the [TypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="0f467-158">Параметр *config* является необязательным, и, если он имеется, содержит контекстные сведения о конфигурации для экземпляра поставщика типов, создаваемого компилятором F #.</span><span class="sxs-lookup"><span data-stu-id="0f467-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="0f467-159">Далее вы реализуете интерфейс [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) .</span><span class="sxs-lookup"><span data-stu-id="0f467-159">Next, you implement the [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) interface.</span></span> <span data-ttu-id="0f467-160">В этом случае вы используете `TypeProviderForNamespaces` тип из `ProvidedTypes` API в качестве базового типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="0f467-161">Этот вспомогательный тип может предоставить конечную коллекцию предопределенных пространств имен, каждый из которых непосредственно содержит конечное количество фиксированных, предпредоставленных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="0f467-162">В этом контексте поставщик *заранее* создает типы, даже если они не нужны или не используются.</span><span class="sxs-lookup"><span data-stu-id="0f467-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="0f467-163">Затем определите локальные закрытые значения, задающие пространство имен для указанных типов, и найдите саму сборку поставщика типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="0f467-164">В дальнейшем эта сборка используется как логический тип родительского объекта для указанных удаленных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="0f467-165">Затем создайте функцию для предоставления каждого типа Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="0f467-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="0f467-166">Эта функция более подробно описана далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0f467-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="0f467-167">Затем создайте типы, предоставленные 100:</span><span class="sxs-lookup"><span data-stu-id="0f467-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="0f467-168">Затем добавьте типы в качестве предоставленного пространства имен:</span><span class="sxs-lookup"><span data-stu-id="0f467-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="0f467-169">Наконец, добавьте атрибут сборки, указывающий, что создается библиотека DLL поставщика типов:</span><span class="sxs-lookup"><span data-stu-id="0f467-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="0f467-170">Предоставление одного типа и его членов</span><span class="sxs-lookup"><span data-stu-id="0f467-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="0f467-171">`makeOneProvidedType`Функция выполняет реальную работу по предоставлению одного из типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="0f467-172">Этот шаг описывает реализацию этой функции.</span><span class="sxs-lookup"><span data-stu-id="0f467-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="0f467-173">Сначала создайте предоставленный тип (например, тип1, если n = 1 или Type57, если n = 57).</span><span class="sxs-lookup"><span data-stu-id="0f467-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="0f467-174">Обратите внимание на следующие моменты:</span><span class="sxs-lookup"><span data-stu-id="0f467-174">You should note the following points:</span></span>

- <span data-ttu-id="0f467-175">Указанный тип стерт.</span><span class="sxs-lookup"><span data-stu-id="0f467-175">This provided type is erased.</span></span>  <span data-ttu-id="0f467-176">Так как вы указываете, что базовый тип — `obj` , экземпляры будут отображаться в виде значений типа [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) в скомпилированном коде.</span><span class="sxs-lookup"><span data-stu-id="0f467-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) in compiled code.</span></span>

- <span data-ttu-id="0f467-177">При указании невложенного типа необходимо указать сборку и пространство имен.</span><span class="sxs-lookup"><span data-stu-id="0f467-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="0f467-178">Для удаленных типов сборка должна быть самой сборкой поставщика типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="0f467-179">Затем добавьте XML-документацию в тип.</span><span class="sxs-lookup"><span data-stu-id="0f467-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="0f467-180">Эта документация является отложенной, то есть вычисленной по запросу, если она требуется компилятору узла.</span><span class="sxs-lookup"><span data-stu-id="0f467-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> $"""This provided type {"Type" + string n}""")
```

<span data-ttu-id="0f467-181">Далее вы добавите в тип предоставленное статическое свойство:</span><span class="sxs-lookup"><span data-stu-id="0f467-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="0f467-182">При получении этого свойства всегда будет вычислена строка "Hello!".</span><span class="sxs-lookup"><span data-stu-id="0f467-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="0f467-183">`GetterCode`Для свойства используется цитата F #, представляющая код, формируемый компилятором хоста для получения свойства.</span><span class="sxs-lookup"><span data-stu-id="0f467-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="0f467-184">Дополнительные сведения о предложениях см. в разделе [цитирование кода (F #)](../../language-reference/code-quotations.md).</span><span class="sxs-lookup"><span data-stu-id="0f467-184">For more information about quotations, see [Code Quotations (F#)](../../language-reference/code-quotations.md).</span></span>

<span data-ttu-id="0f467-185">Добавьте XML-документацию в свойство.</span><span class="sxs-lookup"><span data-stu-id="0f467-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="0f467-186">Теперь присоедините предоставленное свойство к предоставленному типу.</span><span class="sxs-lookup"><span data-stu-id="0f467-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="0f467-187">Необходимо присоединить предоставленный элемент к одному и только одному типу.</span><span class="sxs-lookup"><span data-stu-id="0f467-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="0f467-188">В противном случае член никогда не будет доступен.</span><span class="sxs-lookup"><span data-stu-id="0f467-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="0f467-189">Теперь создайте предоставленный конструктор, не принимающий параметров.</span><span class="sxs-lookup"><span data-stu-id="0f467-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="0f467-190">`InvokeCode`Для конструктора возвращает предложение F #, которое представляет код, создаваемый компилятором хоста при вызове конструктора.</span><span class="sxs-lookup"><span data-stu-id="0f467-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="0f467-191">Например, можно использовать следующий конструктор:</span><span class="sxs-lookup"><span data-stu-id="0f467-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="0f467-192">Экземпляр предоставленного типа будет создан с базовыми данными "данные объекта".</span><span class="sxs-lookup"><span data-stu-id="0f467-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="0f467-193">Код в кавычках включает преобразование в [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) , так как этот тип является очистки данного предоставленного типа (как указано при объявлении предоставленного типа).</span><span class="sxs-lookup"><span data-stu-id="0f467-193">The quoted code includes a conversion to [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="0f467-194">Добавьте XML-документацию в конструктор и добавьте предоставленный конструктор в предоставленный тип:</span><span class="sxs-lookup"><span data-stu-id="0f467-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="0f467-195">Создайте второй предоставленный конструктор, который принимает один параметр:</span><span class="sxs-lookup"><span data-stu-id="0f467-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="0f467-196">`InvokeCode`Для конструктора снова возвращает предложение F #, которое представляет код, созданный компилятором узла для вызова метода.</span><span class="sxs-lookup"><span data-stu-id="0f467-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="0f467-197">Например, можно использовать следующий конструктор:</span><span class="sxs-lookup"><span data-stu-id="0f467-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="0f467-198">Экземпляр предоставленного типа создается с базовыми данными «десять».</span><span class="sxs-lookup"><span data-stu-id="0f467-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="0f467-199">Возможно, вы уже заметили, что `InvokeCode` функция возвращает предложение.</span><span class="sxs-lookup"><span data-stu-id="0f467-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="0f467-200">Входными данными для этой функции является список выражений, по одному на каждый параметр конструктора.</span><span class="sxs-lookup"><span data-stu-id="0f467-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="0f467-201">В этом случае выражение, представляющее единственное значение параметра, доступно в `args.[0]` .</span><span class="sxs-lookup"><span data-stu-id="0f467-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="0f467-202">Код для вызова конструктора приводит возвращаемое значение к удаленному типу `obj` .</span><span class="sxs-lookup"><span data-stu-id="0f467-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="0f467-203">После добавления второго предоставленного конструктора к типу вы создадите предоставленное свойство экземпляра:</span><span class="sxs-lookup"><span data-stu-id="0f467-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="0f467-204">Получение этого свойства возвратит длину строки, которая является объектом представления.</span><span class="sxs-lookup"><span data-stu-id="0f467-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="0f467-205">`GetterCode`Свойство возвращает предложение F #, которое указывает код, формируемый компилятором узла для получения свойства.</span><span class="sxs-lookup"><span data-stu-id="0f467-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="0f467-206">Например `InvokeCode` , `GetterCode` функция возвращает предложение.</span><span class="sxs-lookup"><span data-stu-id="0f467-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="0f467-207">Компилятор узла вызывает эту функцию со списком аргументов.</span><span class="sxs-lookup"><span data-stu-id="0f467-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="0f467-208">В этом случае аргументы включают только одно выражение, представляющее экземпляр, на основе которого вызывается метод получения, к которому можно получить доступ с помощью `args.[0]` .</span><span class="sxs-lookup"><span data-stu-id="0f467-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="0f467-209">После этого реализация присоединения к `GetterCode` результирующей цитате на удаленном типе `obj` , а приведение используется для удовлетворения механизма компилятора для проверки типов, которые объект является строковым.</span><span class="sxs-lookup"><span data-stu-id="0f467-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="0f467-210">Следующая часть `makeOneProvidedType` предоставляет метод экземпляра с одним параметром.</span><span class="sxs-lookup"><span data-stu-id="0f467-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="0f467-211">Наконец, создайте вложенный тип, содержащий 100 вложенных свойств.</span><span class="sxs-lookup"><span data-stu-id="0f467-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="0f467-212">Создание этого вложенного типа и его свойств отложено, то есть вычисленное по запросу.</span><span class="sxs-lookup"><span data-stu-id="0f467-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  $"This is StaticProperty{i} on NestedType")

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="0f467-213">Сведения о стирании указанных типов</span><span class="sxs-lookup"><span data-stu-id="0f467-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="0f467-214">Пример в этом разделе содержит только *Удаленные предоставленные типы*, которые особенно полезны в следующих ситуациях.</span><span class="sxs-lookup"><span data-stu-id="0f467-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="0f467-215">При создании поставщика для информационного пространства, содержащего только данные и методы.</span><span class="sxs-lookup"><span data-stu-id="0f467-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="0f467-216">При написании поставщика, где точная семантика типа среды выполнения не критична для практического использования информационного пространства.</span><span class="sxs-lookup"><span data-stu-id="0f467-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="0f467-217">При написании поставщика для информационного пространства настолько крупным и взаимосвязанным, что не рекомендуется создавать реальные типы .NET для информационного пространства.</span><span class="sxs-lookup"><span data-stu-id="0f467-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="0f467-218">В этом примере каждый предоставленный тип удаляется в тип `obj` , и все варианты использования типа будут отображаться как тип `obj` в скомпилированном коде.</span><span class="sxs-lookup"><span data-stu-id="0f467-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="0f467-219">Фактически, базовые объекты в этих примерах являются строками, но тип будет выглядеть как `System.Object` в скомпилированном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="0f467-220">Как и при использовании типа очистки, можно использовать явную упаковку, распаковку и приведение к обходят удаленным типам.</span><span class="sxs-lookup"><span data-stu-id="0f467-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="0f467-221">В этом случае при использовании объекта может возникнуть исключение приведения, которое является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="0f467-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="0f467-222">Среда выполнения поставщика может определять собственный частный тип представления для защиты от ложных представлений.</span><span class="sxs-lookup"><span data-stu-id="0f467-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="0f467-223">Вы не можете определять удаленные типы в самом F #.</span><span class="sxs-lookup"><span data-stu-id="0f467-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="0f467-224">Только указанные типы могут быть стерты.</span><span class="sxs-lookup"><span data-stu-id="0f467-224">Only provided types may be erased.</span></span> <span data-ttu-id="0f467-225">Необходимо понимать последствия, как практичные, так и семантические, используя либо стертые типы для поставщика типов, либо поставщик, предоставляющий стертые типы.</span><span class="sxs-lookup"><span data-stu-id="0f467-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="0f467-226">У стирания типа нет действительного типа .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="0f467-227">Таким образом, невозможно выполнить точное отражение для типа, и вы можете обходят стереть типы при использовании приведений во время выполнения и других методов, зависящих от семантики типов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0f467-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="0f467-228">Подверсия стертых типов часто приводит к исключениям приведения типов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0f467-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="0f467-229">Выбор представлений для удаленных предоставленных типов</span><span class="sxs-lookup"><span data-stu-id="0f467-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="0f467-230">Для некоторых применений удаленных предоставленных типов представление не требуется.</span><span class="sxs-lookup"><span data-stu-id="0f467-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="0f467-231">Например, стертный предоставленный тип может содержать только статические свойства и члены без конструкторов, а методы и свойства не возвращают экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="0f467-232">Если можно достичь экземпляров удаленных предоставленных типов, необходимо учитывать следующие вопросы.</span><span class="sxs-lookup"><span data-stu-id="0f467-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="0f467-233">**Что такое очистки указанного типа?**</span><span class="sxs-lookup"><span data-stu-id="0f467-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="0f467-234">Очистки предоставленного типа — это то, как тип отображается в скомпилированном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="0f467-235">Очистки указанного типа очищенного класса всегда является первым нестертым базовым типом в цепочке наследования типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="0f467-236">Очистки указанного типа удаленных интерфейсов всегда имеет значение `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="0f467-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="0f467-237">**Какие представления предоставленного типа?**</span><span class="sxs-lookup"><span data-stu-id="0f467-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="0f467-238">Набор возможных объектов для очищенного предоставленного типа называется его представлениями.</span><span class="sxs-lookup"><span data-stu-id="0f467-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="0f467-239">В примере в этом документе представления всех удаленных предоставленных типов `Type1..Type100` всегда являются строковыми объектами.</span><span class="sxs-lookup"><span data-stu-id="0f467-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="0f467-240">Все представления указанного типа должны быть совместимы с очистки указанного типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="0f467-241">(В противном случае либо компилятор F # выдаст ошибку для использования поставщика типов, либо будет создан недопустимый недействительный код .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="0f467-242">Поставщик типов является недопустимым, если он возвращает код, предоставляющий Недопустимое представление.)</span><span class="sxs-lookup"><span data-stu-id="0f467-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="0f467-243">Можно выбрать представление для предоставленных объектов с помощью любого из следующих подходов, которые являются очень распространенными:</span><span class="sxs-lookup"><span data-stu-id="0f467-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="0f467-244">Если вы просто предоставляете строго типизированную оболочку для существующего типа .NET, часто имеет смысл стереть этот тип, использовать экземпляры этого типа как представления или и то, и другое.</span><span class="sxs-lookup"><span data-stu-id="0f467-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="0f467-245">Этот подход подходит, если большинство существующих методов этого типа все еще имеет смысл при использовании строго типизированной версии.</span><span class="sxs-lookup"><span data-stu-id="0f467-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="0f467-246">Если вы хотите создать API, который значительно отличается от существующего API-интерфейса .NET, имеет смысл создать типы среды выполнения, которые будут очистки типа и представления для предоставленных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="0f467-247">В примере в этом документе строки используются как представления предоставленных объектов.</span><span class="sxs-lookup"><span data-stu-id="0f467-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="0f467-248">Часто может быть целесообразно использовать другие объекты для представления.</span><span class="sxs-lookup"><span data-stu-id="0f467-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="0f467-249">Например, словарь можно использовать в качестве контейнера свойств:</span><span class="sxs-lookup"><span data-stu-id="0f467-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="0f467-250">В качестве альтернативы можно определить тип в поставщике типов, который будет использоваться во время выполнения для формирования представления, а также одной или нескольких операций среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="0f467-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="0f467-251">Указанные члены могут затем создавать экземпляры этого типа объектов:</span><span class="sxs-lookup"><span data-stu-id="0f467-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="0f467-252">В этом случае вы можете (необязательно) использовать этот тип в качестве типа очистки, указав этот тип в качестве `baseType` при создании `ProvidedTypeDefinition` :</span><span class="sxs-lookup"><span data-stu-id="0f467-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="0f467-253">Ключевые уроки</span><span class="sxs-lookup"><span data-stu-id="0f467-253">Key Lessons</span></span>

<span data-ttu-id="0f467-254">В предыдущем разделе было объяснено, как создать простой поставщик типов стирания, предоставляющий ряд типов, свойств и методов.</span><span class="sxs-lookup"><span data-stu-id="0f467-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="0f467-255">В этом разделе также объяснено понятие типа очистки, в том числе некоторые преимущества и недостатки предоставления удаленных типов от поставщика типов и обсуждаются представления удаленных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="0f467-256">Поставщик типов, использующий статические параметры</span><span class="sxs-lookup"><span data-stu-id="0f467-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="0f467-257">Возможность параметризации поставщиков типов статическими данными позволяет реализовать множество интересных сценариев, даже если поставщику не требуется доступ к локальным или удаленным данным.</span><span class="sxs-lookup"><span data-stu-id="0f467-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="0f467-258">В этом разделе вы узнаете о некоторых основных методах совместного размещения таких поставщиков.</span><span class="sxs-lookup"><span data-stu-id="0f467-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="0f467-259">Тип проверенного поставщика регулярных выражений</span><span class="sxs-lookup"><span data-stu-id="0f467-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="0f467-260">Представьте, что необходимо реализовать поставщик типов для регулярных выражений, которые создают оболочку для <xref:System.Text.RegularExpressions.Regex> библиотек .NET в интерфейсе, который предоставляет следующие гарантии времени компиляции:</span><span class="sxs-lookup"><span data-stu-id="0f467-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="0f467-261">Проверка того, является ли регулярное выражение допустимым.</span><span class="sxs-lookup"><span data-stu-id="0f467-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="0f467-262">Предоставление именованных свойств в совпадениях, основанных на именах групп в регулярном выражении.</span><span class="sxs-lookup"><span data-stu-id="0f467-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="0f467-263">В этом разделе показано, как использовать поставщики типов для создания `RegexTyped` типа, который параметризация шаблона регулярного выражения предоставляет эти преимущества.</span><span class="sxs-lookup"><span data-stu-id="0f467-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="0f467-264">Компилятор сообщит об ошибке, если предоставленный шаблон недействителен, и поставщик типов может извлекать группы из шаблона, чтобы к ним можно было обращаться с помощью именованных свойств в совпадениях.</span><span class="sxs-lookup"><span data-stu-id="0f467-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="0f467-265">При проектировании поставщика типов следует учитывать, как предоставляемый API должен выглядеть для конечных пользователей и как этот проект будет преобразован в код .NET.</span><span class="sxs-lookup"><span data-stu-id="0f467-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="0f467-266">В следующем примере показано, как использовать такой API для получения компонентов кода области:</span><span class="sxs-lookup"><span data-stu-id="0f467-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="0f467-267">В следующем примере показано, как поставщик типов преобразует эти вызовы:</span><span class="sxs-lookup"><span data-stu-id="0f467-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="0f467-268">Обратите внимание на следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="0f467-268">Note the following points:</span></span>

- <span data-ttu-id="0f467-269">Стандартный тип Regex представляет параметризованный `RegexTyped` тип.</span><span class="sxs-lookup"><span data-stu-id="0f467-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="0f467-270">`RegexTyped`Конструктор приводит к вызову конструктора Regex, передавая аргумент статического типа для шаблона.</span><span class="sxs-lookup"><span data-stu-id="0f467-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="0f467-271">Результаты `Match` метода представлены стандартным <xref:System.Text.RegularExpressions.Match> типом.</span><span class="sxs-lookup"><span data-stu-id="0f467-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="0f467-272">Каждая именованная группа приводит к предоставленному свойству, а доступ к свойству приводит к использованию индексатора для `Groups` коллекции соответствия.</span><span class="sxs-lookup"><span data-stu-id="0f467-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="0f467-273">Следующий код является основой логики для реализации такого поставщика, и в этом примере Добавление всех элементов к предоставленному типу не производится.</span><span class="sxs-lookup"><span data-stu-id="0f467-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="0f467-274">Сведения о каждом добавленном члене см. в соответствующем разделе далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0f467-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="0f467-275">Чтобы получить полный код, Скачайте пример из [образца пакета F # 3,0](https://archive.codeplex.com/?p=fsharp3sample) на веб-сайте CodePlex.</span><span class="sxs-lookup"><span data-stu-id="0f467-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="0f467-276">Обратите внимание на следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="0f467-276">Note the following points:</span></span>

- <span data-ttu-id="0f467-277">Поставщик типов принимает два статических параметра: `pattern` , который является обязательным, и `options` , который является необязательным (поскольку предоставляется значение по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="0f467-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="0f467-278">После того как будут указаны статические аргументы, создается экземпляр регулярного выражения.</span><span class="sxs-lookup"><span data-stu-id="0f467-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="0f467-279">Этот экземпляр вызывает исключение, если регулярное выражение имеет неправильный формат, и эта ошибка будет передана пользователям.</span><span class="sxs-lookup"><span data-stu-id="0f467-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="0f467-280">В `DefineStaticParameters` обратном вызове определяется тип, который будет возвращен после указания аргументов.</span><span class="sxs-lookup"><span data-stu-id="0f467-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="0f467-281">Этот код задает `HideObjectMethods` значение true, чтобы технология IntelliSense оставалась оптимизированной.</span><span class="sxs-lookup"><span data-stu-id="0f467-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="0f467-282">Этот атрибут заставляет `Equals` элементы, `GetHashCode` , `Finalize` и `GetType` быть подавлены из списков IntelliSense для предоставленного объекта.</span><span class="sxs-lookup"><span data-stu-id="0f467-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="0f467-283">Используется в `obj` качестве базового типа метода, но в `Regex` качестве представления среды выполнения для этого типа используется объект, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0f467-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="0f467-284">Вызов `Regex` конструктора вызывает исключение, <xref:System.ArgumentException> Если регулярное выражение является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="0f467-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="0f467-285">Компилятор перехватывает это исключение и сообщает пользователю сообщение об ошибке во время компиляции или в редакторе Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f467-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="0f467-286">Это исключение позволяет проверять регулярные выражения без запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="0f467-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="0f467-287">Указанный выше тип не полезен, так как он не содержит значимых методов или свойств.</span><span class="sxs-lookup"><span data-stu-id="0f467-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="0f467-288">Сначала добавьте статический `IsMatch` метод:</span><span class="sxs-lookup"><span data-stu-id="0f467-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="0f467-289">Предыдущий код определяет метод `IsMatch` , который принимает строку в качестве входных данных и возвращает `bool` .</span><span class="sxs-lookup"><span data-stu-id="0f467-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="0f467-290">Единственная сложная часть — использование `args` аргумента в `InvokeCode` определении.</span><span class="sxs-lookup"><span data-stu-id="0f467-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="0f467-291">В этом примере `args` — это список предложений, представляющих аргументы для этого метода.</span><span class="sxs-lookup"><span data-stu-id="0f467-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="0f467-292">Если метод является методом экземпляра, первый аргумент представляет `this` аргумент.</span><span class="sxs-lookup"><span data-stu-id="0f467-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="0f467-293">Однако для статического метода аргументы являются только явными аргументами метода.</span><span class="sxs-lookup"><span data-stu-id="0f467-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="0f467-294">Обратите внимание, что тип значения в кавычках должен соответствовать указанному возвращаемому типу (в данном случае `bool` ).</span><span class="sxs-lookup"><span data-stu-id="0f467-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="0f467-295">Также обратите внимание, что этот код использует `AddXmlDoc` метод, чтобы убедиться, что предоставленный метод также имеет полезную документацию, которую можно передать с помощью IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0f467-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="0f467-296">Затем добавьте метод Match для экземпляра.</span><span class="sxs-lookup"><span data-stu-id="0f467-296">Next, add an instance Match method.</span></span> <span data-ttu-id="0f467-297">Однако этот метод должен возвращать значение предоставленного типа, `Match` чтобы обеспечить доступ к группам строго типизированным образом.</span><span class="sxs-lookup"><span data-stu-id="0f467-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="0f467-298">Поэтому сначала объявите `Match` тип.</span><span class="sxs-lookup"><span data-stu-id="0f467-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="0f467-299">Поскольку этот тип зависит от шаблона, который был передан как статический аргумент, этот тип должен быть вложен в определение параметризованного типа:</span><span class="sxs-lookup"><span data-stu-id="0f467-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="0f467-300">Затем добавьте одно свойство в тип сопоставления для каждой группы.</span><span class="sxs-lookup"><span data-stu-id="0f467-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="0f467-301">Во время выполнения соответствие представлено как <xref:System.Text.RegularExpressions.Match> значение, поэтому для получения соответствующей группы в предложении, определяющем свойство, необходимо использовать <xref:System.Text.RegularExpressions.Match.Groups> индексированное свойство.</span><span class="sxs-lookup"><span data-stu-id="0f467-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc($"""Gets the ""{group}"" group from this match""")
    matchTy.AddMember prop
```

<span data-ttu-id="0f467-302">Обратите внимание, что вы добавляете XML-документацию к предоставленному свойству.</span><span class="sxs-lookup"><span data-stu-id="0f467-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="0f467-303">Также обратите внимание, что свойство может быть считано, если `GetterCode` предоставлена функция, а свойство может быть записано `SetterCode` , если предоставлена функция, поэтому полученное свойство доступно только для чтения.</span><span class="sxs-lookup"><span data-stu-id="0f467-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="0f467-304">Теперь можно создать метод экземпляра, возвращающий значение этого `Match` типа:</span><span class="sxs-lookup"><span data-stu-id="0f467-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="0f467-305">Поскольку создается метод экземпляра, `args.[0]` представляет `RegexTyped` экземпляр, на котором вызывается метод, и `args.[1]` является входным аргументом.</span><span class="sxs-lookup"><span data-stu-id="0f467-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="0f467-306">Наконец, предоставьте конструктор, чтобы можно было создать экземпляры указанного типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="0f467-307">Конструктор просто стирает до создания стандартного экземпляра Regex .NET, который снова упаковывается в объект, так как `obj` является очисткиом указанного типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="0f467-308">С этим изменением пример использования API, указанный ранее в разделе, работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="0f467-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="0f467-309">Следующий код является полным и окончательным:</span><span class="sxs-lookup"><span data-stu-id="0f467-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="0f467-310">Ключевые уроки</span><span class="sxs-lookup"><span data-stu-id="0f467-310">Key Lessons</span></span>

<span data-ttu-id="0f467-311">В этом разделе описано, как создать поставщик типов, который работает с его статическими параметрами.</span><span class="sxs-lookup"><span data-stu-id="0f467-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="0f467-312">Поставщик проверяет статический параметр и предоставляет операции на основе его значения.</span><span class="sxs-lookup"><span data-stu-id="0f467-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="0f467-313">Поставщик типов, который поддерживается локальными данными</span><span class="sxs-lookup"><span data-stu-id="0f467-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="0f467-314">Зачастую может потребоваться, чтобы поставщики типов представим интерфейсы API на основе не только статических параметров, но и информации из локальных или удаленных систем.</span><span class="sxs-lookup"><span data-stu-id="0f467-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="0f467-315">В этом разделе обсуждаются поставщики типов, основанные на локальных данных, например локальные файлы данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="0f467-316">Поставщик простых CSV-файлов</span><span class="sxs-lookup"><span data-stu-id="0f467-316">Simple CSV File Provider</span></span>

<span data-ttu-id="0f467-317">В качестве простого примера рассмотрим поставщик типов для доступа к научных данным в формате CSV (с разделителями-запятыми).</span><span class="sxs-lookup"><span data-stu-id="0f467-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="0f467-318">В этом разделе предполагается, что CSV-файлы содержат строку заголовка, за которой следуют данные с плавающей запятой, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="0f467-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="0f467-319">Расстояние (счетчик)</span><span class="sxs-lookup"><span data-stu-id="0f467-319">Distance (meter)</span></span>|<span data-ttu-id="0f467-320">Время (секунд)</span><span class="sxs-lookup"><span data-stu-id="0f467-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="0f467-321">50,0</span><span class="sxs-lookup"><span data-stu-id="0f467-321">50.0</span></span>|<span data-ttu-id="0f467-322">3,7</span><span class="sxs-lookup"><span data-stu-id="0f467-322">3.7</span></span>|
|<span data-ttu-id="0f467-323">100.0</span><span class="sxs-lookup"><span data-stu-id="0f467-323">100.0</span></span>|<span data-ttu-id="0f467-324">5,2</span><span class="sxs-lookup"><span data-stu-id="0f467-324">5.2</span></span>|
|<span data-ttu-id="0f467-325">150.0</span><span class="sxs-lookup"><span data-stu-id="0f467-325">150.0</span></span>|<span data-ttu-id="0f467-326">6.4</span><span class="sxs-lookup"><span data-stu-id="0f467-326">6.4</span></span>|

<span data-ttu-id="0f467-327">В этом разделе показано, как предоставить тип, который можно использовать для получения строк со `Distance` свойством типа `float<meter>` и `Time` свойством типа `float<second>` .</span><span class="sxs-lookup"><span data-stu-id="0f467-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="0f467-328">Для простоты выполняются следующие предположения.</span><span class="sxs-lookup"><span data-stu-id="0f467-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="0f467-329">Имена заголовков не должны содержать запятые или имеют форму "имя (единица)".</span><span class="sxs-lookup"><span data-stu-id="0f467-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="0f467-330">Единицы — это все международные единицы (SI), в которых определяется модуль [FSharp. Data. унитсистемс. si. UnitNames (F #)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) .</span><span class="sxs-lookup"><span data-stu-id="0f467-330">Units are all System International (SI) units as the [FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) module defines.</span></span>

- <span data-ttu-id="0f467-331">Все единицы являются простыми (например, счетчик), а не составными (например, измерение/секунда).</span><span class="sxs-lookup"><span data-stu-id="0f467-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="0f467-332">Все столбцы содержат данные с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="0f467-332">All columns contain floating point data.</span></span>

<span data-ttu-id="0f467-333">Более полный поставщик расставит эти ограничения.</span><span class="sxs-lookup"><span data-stu-id="0f467-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="0f467-334">Первый шаг — определить, как должен выглядеть API.</span><span class="sxs-lookup"><span data-stu-id="0f467-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="0f467-335">При наличии `info.csv` файла с содержимым из предыдущей таблицы (в формате с разделителями-запятыми) Пользователи поставщика должны иметь возможность написать код, похожий на следующий пример:</span><span class="sxs-lookup"><span data-stu-id="0f467-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn $"{float time}"
```

<span data-ttu-id="0f467-336">В этом случае компилятор должен преобразовать эти вызовы в что-то, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0f467-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn $"%f{float time}"
```

<span data-ttu-id="0f467-337">Для оптимального перевода необходимо, чтобы поставщик типов определял реальный `CsvFile` тип в сборке поставщика типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="0f467-338">Поставщики типов часто используют несколько вспомогательных типов и методов для создания оболочки для важной логики.</span><span class="sxs-lookup"><span data-stu-id="0f467-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="0f467-339">Поскольку меры удаляются во время выполнения, можно использовать `float[]` как тип стирания для строки.</span><span class="sxs-lookup"><span data-stu-id="0f467-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="0f467-340">Компилятор будет обрабатывать различные столбцы с разными типами мер.</span><span class="sxs-lookup"><span data-stu-id="0f467-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="0f467-341">Например, первый столбец в нашем примере имеет тип `float<meter>` , а второй — `float<second>` .</span><span class="sxs-lookup"><span data-stu-id="0f467-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="0f467-342">Однако удаленное представление может остаться довольно простым.</span><span class="sxs-lookup"><span data-stu-id="0f467-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="0f467-343">В следующем коде показано ядро реализации.</span><span class="sxs-lookup"><span data-stu-id="0f467-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="0f467-344">Обратите внимание на следующие моменты реализации:</span><span class="sxs-lookup"><span data-stu-id="0f467-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="0f467-345">Перегруженные конструкторы позволяют считывать либо исходный файл, либо тот, который имеет идентичную схему.</span><span class="sxs-lookup"><span data-stu-id="0f467-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="0f467-346">Этот шаблон часто используется при написании поставщика типов для локальных или удаленных источников данных, и этот шаблон позволяет использовать локальный файл в качестве шаблона для удаленных данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="0f467-347">Значение [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) , передаваемое в конструктор поставщика типов, можно использовать для разрешения относительных имен файлов.</span><span class="sxs-lookup"><span data-stu-id="0f467-347">You can use the [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="0f467-348">`AddDefinitionLocation`Для определения расположения предоставленных свойств можно использовать метод.</span><span class="sxs-lookup"><span data-stu-id="0f467-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="0f467-349">Поэтому при использовании `Go To Definition` для предоставленного свойства CSV-файл будет открыт в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f467-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="0f467-350">Тип можно использовать `ProvidedMeasureBuilder` для поиска единиц СИ и создания соответствующих `float<_>` типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="0f467-351">Ключевые уроки</span><span class="sxs-lookup"><span data-stu-id="0f467-351">Key Lessons</span></span>

<span data-ttu-id="0f467-352">В этом разделе описано, как создать поставщик типов для локального источника данных с простой схемой, содержащейся в самом источнике данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="0f467-353">Дальнейшая работа</span><span class="sxs-lookup"><span data-stu-id="0f467-353">Going Further</span></span>

<span data-ttu-id="0f467-354">В следующих разделах приведены рекомендации для дальнейшего изучения.</span><span class="sxs-lookup"><span data-stu-id="0f467-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="0f467-355">Взгляните на скомпилированный код для удаленных типов</span><span class="sxs-lookup"><span data-stu-id="0f467-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="0f467-356">Чтобы получить представление о том, как использование поставщика типов соответствует коду, который выдается, рассмотрим следующую функцию, используя ту `HelloWorldTypeProvider` , которая использовалась ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0f467-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="0f467-357">Ниже приведен образ результирующего кода, декомпилированного с помощью ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="0f467-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="0f467-358">Как видно из примера, все упоминания типа `Type1` и свойства были удалены, что приводит к `InstanceProperty` включению только операций с задействованными типами среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0f467-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="0f467-359">Соглашения о проектировании и именовании для поставщиков типов</span><span class="sxs-lookup"><span data-stu-id="0f467-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="0f467-360">При создании поставщиков типов Обратите внимание на следующие соглашения.</span><span class="sxs-lookup"><span data-stu-id="0f467-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="0f467-361">**Поставщики протоколов подключения** Как правило, имена большинства библиотек DLL поставщика для протоколов подключения к данным и служб, таких как подключения OData или SQL, должны заканчиваться на `TypeProvider` или `TypeProviders` .</span><span class="sxs-lookup"><span data-stu-id="0f467-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="0f467-362">Например, используйте имя библиотеки DLL, которое напоминает следующую строку:</span><span class="sxs-lookup"><span data-stu-id="0f467-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="0f467-363">Убедитесь, что предоставленные типы являются членами соответствующего пространства имен, и укажите протокол подключения, который вы реализовали:</span><span class="sxs-lookup"><span data-stu-id="0f467-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="0f467-364">**Поставщики служебных программ для общего программирования**.</span><span class="sxs-lookup"><span data-stu-id="0f467-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="0f467-365">Для поставщика типов служебной программы, например для регулярных выражений, поставщик типов может быть частью базовой библиотеки, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0f467-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="0f467-366">В этом случае предоставленный тип будет отображаться в соответствующей точке в соответствии с обычными соглашениями проектирования .NET:</span><span class="sxs-lookup"><span data-stu-id="0f467-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="0f467-367">**Одноэлементные источники данных**.</span><span class="sxs-lookup"><span data-stu-id="0f467-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="0f467-368">Некоторые поставщики типов подключаются к одному выделенному источнику данных и предоставляют только данные.</span><span class="sxs-lookup"><span data-stu-id="0f467-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="0f467-369">В этом случае следует удалить `TypeProvider` суффикс и использовать обычные соглашения для именования .NET:</span><span class="sxs-lookup"><span data-stu-id="0f467-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="0f467-370">Дополнительные сведения см `GetConnection` . в описании соглашения о проектировании, которое описано далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0f467-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="0f467-371">Конструктивные шаблоны для поставщиков типов</span><span class="sxs-lookup"><span data-stu-id="0f467-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="0f467-372">В следующих разделах описываются шаблоны разработки, которые можно использовать при создании поставщиков типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="0f467-373">Шаблон проектирования соединения</span><span class="sxs-lookup"><span data-stu-id="0f467-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="0f467-374">Большинство поставщиков типов должны быть написаны для использования `GetConnection` шаблона, используемого поставщиками типов в FSharp.Data.TypeProviders.dll, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0f467-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="0f467-375">Поставщики типов, которые поддерживают удаленные данные и службы</span><span class="sxs-lookup"><span data-stu-id="0f467-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="0f467-376">Перед созданием поставщика типов, обеспечиваемого удаленными данными и службами, необходимо учитывать ряд проблем, связанных с подключенным программированием.</span><span class="sxs-lookup"><span data-stu-id="0f467-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="0f467-377">Ниже приведены рекомендации по следующим вопросам.</span><span class="sxs-lookup"><span data-stu-id="0f467-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="0f467-378">сопоставление схем</span><span class="sxs-lookup"><span data-stu-id="0f467-378">schema mapping</span></span>

- <span data-ttu-id="0f467-379">динамическое и недействительность при изменении схемы</span><span class="sxs-lookup"><span data-stu-id="0f467-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="0f467-380">кэширование схемы</span><span class="sxs-lookup"><span data-stu-id="0f467-380">schema caching</span></span>

- <span data-ttu-id="0f467-381">асинхронные реализации операций доступа к данным</span><span class="sxs-lookup"><span data-stu-id="0f467-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="0f467-382">Поддержка запросов, включая запросы LINQ</span><span class="sxs-lookup"><span data-stu-id="0f467-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="0f467-383">учетные данные и проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="0f467-383">credentials and authentication</span></span>

<span data-ttu-id="0f467-384">В этом разделе больше не рассматриваются эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="0f467-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="0f467-385">Дополнительные методы разработки</span><span class="sxs-lookup"><span data-stu-id="0f467-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="0f467-386">При написании собственных поставщиков типов может потребоваться использовать следующие дополнительные методы.</span><span class="sxs-lookup"><span data-stu-id="0f467-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="0f467-387">Создание типов и членов по запросу</span><span class="sxs-lookup"><span data-stu-id="0f467-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="0f467-388">API Провидедтипе имеет отложенные версии Аддмембер.</span><span class="sxs-lookup"><span data-stu-id="0f467-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="0f467-389">Эти версии используются для создания пробелов по запросу типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="0f467-390">Предоставление типов массивов и создание экземпляров универсальных типов</span><span class="sxs-lookup"><span data-stu-id="0f467-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="0f467-391">Вы предоставили члены (чьи подписи включают типы массивов, типы ByRef и экземпляры универсальных типов), используя обычные `MakeArrayType` , `MakePointerType` и `MakeGenericType` на любом экземпляре <xref:System.Type> , включая `ProvidedTypeDefinitions` .</span><span class="sxs-lookup"><span data-stu-id="0f467-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="0f467-392">В некоторых случаях может потребоваться использовать вспомогательный метод в `ProvidedTypeBuilder.MakeGenericType` .</span><span class="sxs-lookup"><span data-stu-id="0f467-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="0f467-393">Дополнительные сведения см. в [документации по поставщику типов SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .</span><span class="sxs-lookup"><span data-stu-id="0f467-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="0f467-394">Предоставление заметок единиц измерения</span><span class="sxs-lookup"><span data-stu-id="0f467-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="0f467-395">API Провидедтипес предоставляет вспомогательные методы для предоставления заметок мер.</span><span class="sxs-lookup"><span data-stu-id="0f467-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="0f467-396">Например, чтобы предоставить тип `float<kg>` , используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="0f467-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="0f467-397">Чтобы указать тип `Nullable<decimal<kg/m^2>>` , используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="0f467-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="0f467-398">Доступ к ресурсам Project-Local или Script-Local</span><span class="sxs-lookup"><span data-stu-id="0f467-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="0f467-399">Каждому экземпляру поставщика типов может быть присвоено `TypeProviderConfig` значение во время создания.</span><span class="sxs-lookup"><span data-stu-id="0f467-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="0f467-400">Это значение содержит "папку разрешения" для поставщика (то есть папка проекта для компиляции или каталога, содержащего скрипт), список сборок, на которые имеются ссылки, и другие сведения.</span><span class="sxs-lookup"><span data-stu-id="0f467-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="0f467-401">Недействительность</span><span class="sxs-lookup"><span data-stu-id="0f467-401">Invalidation</span></span>

<span data-ttu-id="0f467-402">Поставщики могут создавать сигналы недействительности, чтобы уведомить службу языка F # о том, что допущение схемы могло измениться.</span><span class="sxs-lookup"><span data-stu-id="0f467-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="0f467-403">При возникновении недействительности типечекк выполняется повторно, если поставщик размещается в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f467-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="0f467-404">Этот сигнал будет проигнорирован, если поставщик размещается в F# Interactive или компиляторе F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="0f467-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="0f467-405">Кэширование сведений о схеме</span><span class="sxs-lookup"><span data-stu-id="0f467-405">Caching Schema Information</span></span>

<span data-ttu-id="0f467-406">Поставщики часто должны кэшировать доступ к сведениям о схеме.</span><span class="sxs-lookup"><span data-stu-id="0f467-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="0f467-407">Кэшированные данные должны храниться с использованием имени файла, заданного статическим параметром или в виде пользовательских данных.</span><span class="sxs-lookup"><span data-stu-id="0f467-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="0f467-408">Примером кэширования схемы является `LocalSchemaFile` параметр в поставщиках типов в `FSharp.Data.TypeProviders` сборке.</span><span class="sxs-lookup"><span data-stu-id="0f467-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="0f467-409">В реализации этих поставщиков этот статический параметр направляет поставщику типов сведения о схеме в указанный локальный файл, а не на доступ к источнику данных по сети.</span><span class="sxs-lookup"><span data-stu-id="0f467-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="0f467-410">Чтобы использовать кэшированные данные схемы, необходимо также присвоить статическому параметру значение `ForceUpdate` `false` .</span><span class="sxs-lookup"><span data-stu-id="0f467-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="0f467-411">Аналогичную методику можно использовать для включения доступа к данным в сети и автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="0f467-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="0f467-412">Резервная сборка</span><span class="sxs-lookup"><span data-stu-id="0f467-412">Backing Assembly</span></span>

<span data-ttu-id="0f467-413">При компиляции `.dll` файла или файл `.exe` резервной копии. dll для созданных типов статически связывается с результирующей сборкой.</span><span class="sxs-lookup"><span data-stu-id="0f467-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="0f467-414">Эта ссылка создается путем копирования определений типов промежуточного языка (IL) и всех управляемых ресурсов из резервной сборки в окончательную сборку.</span><span class="sxs-lookup"><span data-stu-id="0f467-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="0f467-415">При использовании F# Interactive файл резервной копии. dll не копируется, а загружается непосредственно в процесс F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="0f467-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="0f467-416">Исключения и диагностика из поставщиков типов</span><span class="sxs-lookup"><span data-stu-id="0f467-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="0f467-417">Все варианты использования всех членов предоставленных типов могут вызывать исключения.</span><span class="sxs-lookup"><span data-stu-id="0f467-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="0f467-418">Во всех случаях, если поставщик типов создает исключение, компилятор узла сообщает об ошибке конкретному поставщику типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="0f467-419">Исключения поставщика типов не должны приводить к внутренним ошибкам компилятора.</span><span class="sxs-lookup"><span data-stu-id="0f467-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="0f467-420">Поставщики типов не могут сообщать о предупреждениях.</span><span class="sxs-lookup"><span data-stu-id="0f467-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="0f467-421">Если поставщик типов размещается в компиляторе F #, среде разработки F # или F# Interactive, перехватываются все исключения из этого поставщика.</span><span class="sxs-lookup"><span data-stu-id="0f467-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="0f467-422">Свойство Message всегда является текстом ошибки, и трассировка стека не отображается.</span><span class="sxs-lookup"><span data-stu-id="0f467-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="0f467-423">Если будет создано исключение, можно создать следующие примеры: `System.NotSupportedException` , `System.IO.IOException` , `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="0f467-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="0f467-424">Предоставление созданных типов</span><span class="sxs-lookup"><span data-stu-id="0f467-424">Providing Generated Types</span></span>

<span data-ttu-id="0f467-425">На данный момент в этом документе было объяснено, как предоставить удаленные типы.</span><span class="sxs-lookup"><span data-stu-id="0f467-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="0f467-426">Можно также использовать механизм поставщика типов в F # для предоставления сформированных типов, которые добавляются как реальные определения типов .NET в программу пользователя.</span><span class="sxs-lookup"><span data-stu-id="0f467-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="0f467-427">Необходимо обращаться к созданным предоставленным типам с помощью определения типа.</span><span class="sxs-lookup"><span data-stu-id="0f467-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="0f467-428">Вспомогательный код Провидедтипес-0,2, который является частью выпуска F # 3,0, имеет ограниченную поддержку для предоставления сформированных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="0f467-429">Для созданного определения типа должны быть справедливы следующие инструкции:</span><span class="sxs-lookup"><span data-stu-id="0f467-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="0f467-430">Для параметра `isErased` нужно задать значение `false`.</span><span class="sxs-lookup"><span data-stu-id="0f467-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="0f467-431">Созданный тип должен быть добавлен к вновь созданному типу `ProvidedAssembly()` , который представляет контейнер для созданных фрагментов кода.</span><span class="sxs-lookup"><span data-stu-id="0f467-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="0f467-432">Поставщик должен иметь сборку, имеющую фактический резервный файл .NET. dll с совпадающим DLL-файлом на диске.</span><span class="sxs-lookup"><span data-stu-id="0f467-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="0f467-433">Правила и ограничения</span><span class="sxs-lookup"><span data-stu-id="0f467-433">Rules and Limitations</span></span>

<span data-ttu-id="0f467-434">При записи поставщиков типов учитывайте следующие правила и ограничения.</span><span class="sxs-lookup"><span data-stu-id="0f467-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="0f467-435">Предоставленные типы должны быть доступны</span><span class="sxs-lookup"><span data-stu-id="0f467-435">Provided types must be reachable</span></span>

<span data-ttu-id="0f467-436">Все предоставленные типы должны быть доступны из невложенных типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="0f467-437">Невложенные типы задаются в вызове `TypeProviderForNamespaces` конструктора или при вызове метода `AddNamespace` .</span><span class="sxs-lookup"><span data-stu-id="0f467-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="0f467-438">Например, если поставщик предоставляет тип `StaticClass.P : T` , необходимо убедиться, что T является либо невложенным типом, либо вложенным в один.</span><span class="sxs-lookup"><span data-stu-id="0f467-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="0f467-439">Например, некоторые поставщики имеют статический класс, такой как `DataTypes` , который содержит эти `T1, T2, T3, ...` типы.</span><span class="sxs-lookup"><span data-stu-id="0f467-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="0f467-440">В противном случае ошибка говорит о том, что обнаружена ссылка на тип T в сборке A, но тип не найден в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="0f467-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="0f467-441">Если возникает эта ошибка, убедитесь, что все подтипы доступны из типов поставщиков.</span><span class="sxs-lookup"><span data-stu-id="0f467-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="0f467-442">Примечание. Эти `T1, T2, T3...` типы называются *оперативными* типами.</span><span class="sxs-lookup"><span data-stu-id="0f467-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="0f467-443">Не забудьте разместить их в доступном пространстве имен или родительском типе.</span><span class="sxs-lookup"><span data-stu-id="0f467-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="0f467-444">Ограничения механизма поставщика типов</span><span class="sxs-lookup"><span data-stu-id="0f467-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="0f467-445">Механизм поставщика типов в F # имеет следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="0f467-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="0f467-446">Базовая инфраструктура для поставщиков типов в F # не поддерживает предоставленные универсальные типы или предоставленные универсальные методы.</span><span class="sxs-lookup"><span data-stu-id="0f467-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="0f467-447">Механизм не поддерживает вложенные типы со статическими параметрами.</span><span class="sxs-lookup"><span data-stu-id="0f467-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="0f467-448">Советы по разработке</span><span class="sxs-lookup"><span data-stu-id="0f467-448">Development Tips</span></span>

<span data-ttu-id="0f467-449">Во время разработки могут оказаться полезными следующие советы:</span><span class="sxs-lookup"><span data-stu-id="0f467-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="0f467-450">Запуск двух экземпляров Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f467-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="0f467-451">Вы можете разработать поставщик типов в одном экземпляре и протестировать его в другом, так как тестовая среда IDE заблокирует DLL-файл, который предотвращает перестроение поставщика типов.</span><span class="sxs-lookup"><span data-stu-id="0f467-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="0f467-452">Поэтому необходимо закрыть второй экземпляр Visual Studio, пока поставщик построен в первом экземпляре, а затем повторно открыть второй экземпляр после сборки поставщика.</span><span class="sxs-lookup"><span data-stu-id="0f467-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="0f467-453">Отладка поставщиков типов с помощью вызовов fsc.exe</span><span class="sxs-lookup"><span data-stu-id="0f467-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="0f467-454">Поставщики типов можно вызывать с помощью следующих средств:</span><span class="sxs-lookup"><span data-stu-id="0f467-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="0f467-455">fsc.exe (компилятор командной строки F #)</span><span class="sxs-lookup"><span data-stu-id="0f467-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="0f467-456">fsi.exe (компилятор F# Interactive)</span><span class="sxs-lookup"><span data-stu-id="0f467-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="0f467-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0f467-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="0f467-458">Часто отладку поставщиков типов можно упростить с помощью fsc.exe в файле скрипта теста (например, Script. fsx).</span><span class="sxs-lookup"><span data-stu-id="0f467-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="0f467-459">Отладчик можно запустить из командной строки.</span><span class="sxs-lookup"><span data-stu-id="0f467-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="0f467-460">Можно использовать ведение журнала печати в stdout.</span><span class="sxs-lookup"><span data-stu-id="0f467-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f467-461">См. также</span><span class="sxs-lookup"><span data-stu-id="0f467-461">See also</span></span>

- [<span data-ttu-id="0f467-462">Поставщики типов</span><span class="sxs-lookup"><span data-stu-id="0f467-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="0f467-463">Пакет SDK поставщика типов</span><span class="sxs-lookup"><span data-stu-id="0f467-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
