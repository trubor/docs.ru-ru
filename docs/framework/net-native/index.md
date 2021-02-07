---
description: 'Дополнительные сведения: компиляция приложений с помощью .NET Native'
title: Компиляция приложений с помощью машинного кода .NET
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 2626daf17fda751edd7915f15fd4b68ffb623dff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747664"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="a01c2-103">Компиляция приложений с помощью машинного кода .NET</span><span class="sxs-lookup"><span data-stu-id="a01c2-103">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="a01c2-104">.NET Native — это технология предварительной компиляции для создания и развертывания приложений Windows, которые входят в состав Visual Studio 2015 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="a01c2-104">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="a01c2-105">Она автоматически компилирует окончательные версии приложений, написанных в форме управляемого кода (C# или Visual Basic) и предназначенных для .NET Framework и Windows 10, в машинный код.</span><span class="sxs-lookup"><span data-stu-id="a01c2-105">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="a01c2-106">Как правило приложения, предназначенные для платформа.NET Framework компилируются в промежуточный язык (IL).</span><span class="sxs-lookup"><span data-stu-id="a01c2-106">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="a01c2-107">Во время выполнения JIT-компилятор преобразует инструкции IL в машинный код.</span><span class="sxs-lookup"><span data-stu-id="a01c2-107">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="a01c2-108">Напротив, .NET Native компилирует приложения Windows непосредственно в машинный код.</span><span class="sxs-lookup"><span data-stu-id="a01c2-108">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="a01c2-109">Для разработчиков это означает:</span><span class="sxs-lookup"><span data-stu-id="a01c2-109">For developers, this means:</span></span>

- <span data-ttu-id="a01c2-110">Приложения имеют производительность машинного кода.</span><span class="sxs-lookup"><span data-stu-id="a01c2-110">Your apps feature the performance of native code.</span></span> <span data-ttu-id="a01c2-111">Как правило, производительность будет представлять собой код, который сначала компилируется в IL, а затем компилируется в машинный код JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="a01c2-111">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="a01c2-112">Можно продолжить программировать в C# или Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a01c2-112">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="a01c2-113">Можно продолжать использовать преимущества ресурсов платформы .NET Framework, включая библиотеки классов, сбор мусора, автоматическое управление памяти и обработку исключений.</span><span class="sxs-lookup"><span data-stu-id="a01c2-113">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="a01c2-114">Для пользователей приложений .NET Native предоставляет следующие преимущества:</span><span class="sxs-lookup"><span data-stu-id="a01c2-114">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="a01c2-115">Более быстрое время выполнения большинства приложений и сценариев.</span><span class="sxs-lookup"><span data-stu-id="a01c2-115">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="a01c2-116">Ускоренное время запуска большинства приложений и сценариев.</span><span class="sxs-lookup"><span data-stu-id="a01c2-116">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="a01c2-117">Низкая стоимость развертывания и обновления.</span><span class="sxs-lookup"><span data-stu-id="a01c2-117">Low deployment and update costs.</span></span>

- <span data-ttu-id="a01c2-118">Оптимизированное использование памяти приложением.</span><span class="sxs-lookup"><span data-stu-id="a01c2-118">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a01c2-119">Для большинства приложений и сценариев .NET Native предлагает значительно более быстрое время запуска и высокую производительность по сравнению с приложением, скомпилированным в IL или на образ NGEN.</span><span class="sxs-lookup"><span data-stu-id="a01c2-119">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="a01c2-120">Однако результаты могут отличаться.</span><span class="sxs-lookup"><span data-stu-id="a01c2-120">However, your results may vary.</span></span> <span data-ttu-id="a01c2-121">Чтобы обеспечить преимущество приложения от улучшения производительности .NET Native, необходимо сравнить его производительность с non-.NET собственной версией приложения, используемой в собственном коде.</span><span class="sxs-lookup"><span data-stu-id="a01c2-121">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="a01c2-122">Дополнительные сведения см. в разделе [Обзор сеанса анализа производительности](/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="a01c2-122">For more information, see [Performance Session Overview](/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="a01c2-123">Но .NET Native включает в себя больше, чем компиляция в машинный код.</span><span class="sxs-lookup"><span data-stu-id="a01c2-123">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="a01c2-124">Он преобразует способ построения и выполнения приложений на платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a01c2-124">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="a01c2-125">В частности:</span><span class="sxs-lookup"><span data-stu-id="a01c2-125">In particular:</span></span>

- <span data-ttu-id="a01c2-126">Во время предварительной компиляции необходимые части платформы .NET Framework статически связываются с приложением.</span><span class="sxs-lookup"><span data-stu-id="a01c2-126">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="a01c2-127">Это позволяет приложению работать с библиотеками локальных приложений платформы.NET Framework, а компилятору — выполнять глобальный анализ для улучшения производительности.</span><span class="sxs-lookup"><span data-stu-id="a01c2-127">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="a01c2-128">В результате приложения постоянно запускаются быстрее даже после обновлений платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a01c2-128">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="a01c2-129">Среда выполнения .NET Native оптимизирована для статической предварительной компиляции, и в подавляющем большинстве случаев обеспечивается высочайшая производительность.</span><span class="sxs-lookup"><span data-stu-id="a01c2-129">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="a01c2-130">В то же время она сохраняет основные функции отражения, которые разработчики считают такими полезными.</span><span class="sxs-lookup"><span data-stu-id="a01c2-130">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="a01c2-131">.NET Native использует ту же серверную части, что и компилятор C++, оптимизированный для сценариев статической предварительной компиляции.</span><span class="sxs-lookup"><span data-stu-id="a01c2-131">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="a01c2-132">.NET Native может повысить производительность C++ для разработчиков управляемого кода, поскольку в нем используются те же или аналогичные средства, что и C++, как показано в этой таблице.</span><span class="sxs-lookup"><span data-stu-id="a01c2-132">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="a01c2-133">.NET Native</span><span class="sxs-lookup"><span data-stu-id="a01c2-133">.NET Native</span></span>|<span data-ttu-id="a01c2-134">C++</span><span class="sxs-lookup"><span data-stu-id="a01c2-134">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="a01c2-135">Библиотеки</span><span class="sxs-lookup"><span data-stu-id="a01c2-135">Libraries</span></span>|<span data-ttu-id="a01c2-136">Платформа.NET Framework + среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="a01c2-136">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="a01c2-137">Win32 + среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="a01c2-137">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="a01c2-138">Компилятор</span><span class="sxs-lookup"><span data-stu-id="a01c2-138">Compiler</span></span>|<span data-ttu-id="a01c2-139">Оптимизирующий компилятор UTC</span><span class="sxs-lookup"><span data-stu-id="a01c2-139">UTC optimizing compiler</span></span>|<span data-ttu-id="a01c2-140">Оптимизирующий компилятор UTC</span><span class="sxs-lookup"><span data-stu-id="a01c2-140">UTC optimizing compiler</span></span>|
|<span data-ttu-id="a01c2-141">Развернут</span><span class="sxs-lookup"><span data-stu-id="a01c2-141">Deployed</span></span>|<span data-ttu-id="a01c2-142">Готов к запуску двоичных файлов</span><span class="sxs-lookup"><span data-stu-id="a01c2-142">Ready-to-run binaries</span></span>|<span data-ttu-id="a01c2-143">Готов к запуску двоичных файлов (ASM)</span><span class="sxs-lookup"><span data-stu-id="a01c2-143">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="a01c2-144">Параметры выполнения</span><span class="sxs-lookup"><span data-stu-id="a01c2-144">Runtime</span></span>|<span data-ttu-id="a01c2-145">MRT.dll (минимальной среды CLR)</span><span class="sxs-lookup"><span data-stu-id="a01c2-145">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="a01c2-146">CRT.dll (среда выполнения C)</span><span class="sxs-lookup"><span data-stu-id="a01c2-146">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="a01c2-147">Для приложений, предназначенных для Windows 10, выполняется передача двоичных файлов компиляции машинного кода .NET в пакетах приложений (файлы APPX) в Магазин Windows.</span><span class="sxs-lookup"><span data-stu-id="a01c2-147">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a01c2-148">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a01c2-148">In This Section</span></span>

<span data-ttu-id="a01c2-149">Дополнительные сведения о разработке приложений при использовании компиляции машинного кода .NET см. в следующих разделах</span><span class="sxs-lookup"><span data-stu-id="a01c2-149">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="a01c2-150">Приступая к компиляции кода с помощью машинного кода .NET: пошаговое руководство разработчика</span><span class="sxs-lookup"><span data-stu-id="a01c2-150">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="a01c2-151">[Машинный код .NET и компиляция](net-native-and-compilation.md) — как проект компилируется в машинный код .NET.</span><span class="sxs-lookup"><span data-stu-id="a01c2-151">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="a01c2-152">Отражение и машинный код .NET</span><span class="sxs-lookup"><span data-stu-id="a01c2-152">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="a01c2-153">API-интерфейсы, основанные на отражении</span><span class="sxs-lookup"><span data-stu-id="a01c2-153">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="a01c2-154">Справочник по API отражения</span><span class="sxs-lookup"><span data-stu-id="a01c2-154">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="a01c2-155">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a01c2-155">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="a01c2-156">Сериализация и метаданные</span><span class="sxs-lookup"><span data-stu-id="a01c2-156">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="a01c2-157">Миграция приложения для магазина Windows в машинный код .NET</span><span class="sxs-lookup"><span data-stu-id="a01c2-157">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="a01c2-158">Машинный код .NET: Устранение общих неполадок</span><span class="sxs-lookup"><span data-stu-id="a01c2-158">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
