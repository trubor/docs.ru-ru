---
title: Критическое изменение. API удаленного взаимодействия устарели
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где некоторые API, связанные с удаленным взаимодействием, помечены как устаревшие и приводят к созданию предупреждения с настраиваемым идентификатором диагностики.
ms.date: 11/01/2020
ms.openlocfilehash: 5687b1471028b077674cfd31cb77ce95dc51bef5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759750"
---
# <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="0e8e8-103">API удаленного взаимодействия устарели</span><span class="sxs-lookup"><span data-stu-id="0e8e8-103">Remoting APIs are obsolete</span></span>

<span data-ttu-id="0e8e8-104">Некоторые API, связанные с удаленным взаимодействием, помечены как устаревшие и приводят к созданию предупреждения `SYSLIB0010` во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-104">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="0e8e8-105">В последующей версии .NET эти API могут быть исключены.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-105">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="0e8e8-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0e8e8-106">Change description</span></span>

<span data-ttu-id="0e8e8-107">Следующие API удаленного взаимодействия помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-107">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="0e8e8-108">API</span><span class="sxs-lookup"><span data-stu-id="0e8e8-108">API</span></span> | <span data-ttu-id="0e8e8-109">Версия, в которой API помечен как устаревший...</span><span class="sxs-lookup"><span data-stu-id="0e8e8-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0e8e8-110">5.0 (RC1)</span><span class="sxs-lookup"><span data-stu-id="0e8e8-110">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0e8e8-111">5.0 (RC1)</span><span class="sxs-lookup"><span data-stu-id="0e8e8-111">5.0 RC1</span></span> |

<span data-ttu-id="0e8e8-112">В .NET Framework версий с 2.x по 4.x методы <xref:System.MarshalByRefObject.GetLifetimeService> и <xref:System.MarshalByRefObject.InitializeLifetimeService> управляют временем существования экземпляров, участвующих в удаленном взаимодействии .NET.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-112">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="0e8e8-113">В .NET Core версий с 2.x по 3.x эти методы всегда приводят к созданию исключения <xref:System.PlatformNotSupportedException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-113">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="0e8e8-114">В .NET 5.0 и более поздних версий методы <xref:System.MarshalByRefObject.GetLifetimeService> и <xref:System.MarshalByRefObject.InitializeLifetimeService> помечены как устаревшие с помощью предупреждения, но по-прежнему приводят к созданию исключения <xref:System.PlatformNotSupportedException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-114">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="0e8e8-115">Это изменение происходит только во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-115">This is a compile-time only change.</span></span> <span data-ttu-id="0e8e8-116">Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-116">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0e8e8-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="0e8e8-117">Reason for change</span></span>

<span data-ttu-id="0e8e8-118">Технология [удаленного взаимодействия .NET](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) устарела.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-118">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="0e8e8-119">Она позволяет создать экземпляр объекта в другом процессе (потенциально даже на другом компьютере) и взаимодействовать с этим объектом, как если бы он был обычным внутрипроцессным экземпляром объекта .NET.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-119">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="0e8e8-120">Инфраструктура удаленного взаимодействия .NET существует только в .NET Framework версий с 2.x по 4.x.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-120">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="0e8e8-121">.NET Core и .NET 5.0 и более поздних версий не поддерживают удаленное взаимодействие .NET, а API удаленного взаимодействия в них либо не существуют, либо всегда создают исключения в этих средах выполнения.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-121">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="0e8e8-122">Чтобы помочь разработчикам отказаться от этих API, некоторые связанные с удаленным взаимодействием API были помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-122">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="0e8e8-123">В последующей версии .NET эти API могут быть окончательно исключены.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-123">These APIs may be removed entirely in a future version of .NET.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0e8e8-124">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0e8e8-124">Version introduced</span></span>

<span data-ttu-id="0e8e8-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0e8e8-125">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0e8e8-126">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0e8e8-126">Recommended action</span></span>

- <span data-ttu-id="0e8e8-127">Для взаимодействия с объектами в других приложениях или на других компьютерах рекомендуется использовать WCF или службы RESTFUL на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-127">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="0e8e8-128">Дополнительные сведения см. в разделе [Технологии .NET Framework, недоступные в .NET Core](../../../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="0e8e8-128">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="0e8e8-129">Если вам по-прежнему требуется вызывать устаревшие API, вы можете отключить предупреждение `SYSLIB0010` в коде.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-129">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="0e8e8-130">Также вы можете отключить это предупреждение в файле проекта, что приведет к его отключению для всех исходных файлов в проекте.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-130">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="0e8e8-131">В случае отключения `SYSLIB0010` будет отключено только предупреждение об устаревшем API удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-131">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="0e8e8-132">Другие предупреждения не отключаются.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-132">It does not disable any other warnings.</span></span> <span data-ttu-id="0e8e8-133">Кроме того, при этом не изменяется жестко заданное поведение во время выполнения, которое во всех случаях подразумевает создание исключения <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="0e8e8-133">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0e8e8-134">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0e8e8-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
