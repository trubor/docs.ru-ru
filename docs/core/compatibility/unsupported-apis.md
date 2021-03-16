---
title: Неподдерживаемые API в .NET Core и .NET версии 5 и более поздних
titleSuffix: ''
description: Узнайте, какие интерфейсы API .NET всегда вызывают исключение в .NET Core и .NET 5 и более поздних версиях.
ms.date: 10/13/2020
ms.openlocfilehash: b0dc425bf5f7d8f2a44f51ffe75ffcb0c8a5a7ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256261"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="0e4a4-103">API, которые всегда создают исключения в .NET Core и .NET версии 5 и более поздних</span><span class="sxs-lookup"><span data-stu-id="0e4a4-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="0e4a4-104">Следующие API всегда будут вызывать исключение <xref:System.PlatformNotSupportedException> в .NET версии 5 и более поздних (включая все версии .NET Core) на всех платформах или на их подмножестве.</span><span class="sxs-lookup"><span data-stu-id="0e4a4-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="0e4a4-105">В этой статье затронутые API упорядочиваются по пространствам имен.</span><span class="sxs-lookup"><span data-stu-id="0e4a4-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="0e4a4-106">Эта статья все еще находится в процессе написания.</span><span class="sxs-lookup"><span data-stu-id="0e4a4-106">This article is a work-in-progress.</span></span> <span data-ttu-id="0e4a4-107">Это не полный список API-интерфейсов, создающих исключения в .NET версии 5 и более поздних.</span><span class="sxs-lookup"><span data-stu-id="0e4a4-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="0e4a4-108">В этой статье не рассматриваются явные реализации интерфейса для двоичной сериализации, которые вызываются в .NET версии 5 и более поздних.</span><span class="sxs-lookup"><span data-stu-id="0e4a4-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="0e4a4-109">Дополнительные сведения см. в разделе [Двоичная сериализация в .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="0e4a4-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="0e4a4-110">Система</span><span class="sxs-lookup"><span data-stu-id="0e4a4-110">System</span></span>

| <span data-ttu-id="0e4a4-111">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-111">Member</span></span> | <span data-ttu-id="0e4a4-112">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-113">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-114">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-115">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-116">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-117">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-118">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-119">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-120">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-121">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-122">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="0e4a4-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="0e4a4-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="0e4a4-124">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-124">Member</span></span> | <span data-ttu-id="0e4a4-125">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-126">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-127">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-128">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="0e4a4-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="0e4a4-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="0e4a4-130">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-130">Member</span></span> | <span data-ttu-id="0e4a4-131">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-132">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-133">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-134">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="0e4a4-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="0e4a4-135">System.Configuration</span></span>

| <span data-ttu-id="0e4a4-136">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-136">Member</span></span> | <span data-ttu-id="0e4a4-137">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="0e4a4-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="0e4a4-139">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="0e4a4-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="0e4a4-140">System.Console</span></span>

| <span data-ttu-id="0e4a4-141">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-141">Member</span></span> | <span data-ttu-id="0e4a4-142">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-143">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-143">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-145">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-145">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-147">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-147">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-149">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-149">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="0e4a4-151">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-152">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-153">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-154">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-154">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-155"><xref:System.Console.Title?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="0e4a4-156">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-156">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-158">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-158">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-160">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-160">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-162">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-162">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-164">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="0e4a4-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="0e4a4-165">System.Data.Common</span></span>

| <span data-ttu-id="0e4a4-166">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-166">Member</span></span> | <span data-ttu-id="0e4a4-167">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="0e4a4-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (вызывает <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="0e4a4-169">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="0e4a4-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="0e4a4-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="0e4a4-171">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-171">Member</span></span> | <span data-ttu-id="0e4a4-172">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="0e4a4-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-174">Linux</span><span class="sxs-lookup"><span data-stu-id="0e4a4-174">Linux</span></span> |
| <span data-ttu-id="0e4a4-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-176">Linux</span><span class="sxs-lookup"><span data-stu-id="0e4a4-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-177">macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-178">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-179">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-180">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-181">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-182">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-183">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-184">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-184">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-186">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-186">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="0e4a4-188">macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-188">macOS</span></span> |
| <span data-ttu-id="0e4a4-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-190">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="0e4a4-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="0e4a4-191">System.IO</span></span>

| <span data-ttu-id="0e4a4-192">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-192">Member</span></span> | <span data-ttu-id="0e4a4-193">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-194">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-195">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="0e4a4-196">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="0e4a4-196">System.IO.Pipes</span></span>

| <span data-ttu-id="0e4a4-197">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-197">Member</span></span> | <span data-ttu-id="0e4a4-198">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-199">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-200">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-201">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-202">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-202">Linux and macOS</span></span> |
| <span data-ttu-id="0e4a4-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-204">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-205">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="0e4a4-206">System.Media</span><span class="sxs-lookup"><span data-stu-id="0e4a4-206">System.Media</span></span>

| <span data-ttu-id="0e4a4-207">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-207">Member</span></span> | <span data-ttu-id="0e4a4-208">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-209">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="0e4a4-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="0e4a4-210">System.Net</span></span>

| <span data-ttu-id="0e4a4-211">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-211">Member</span></span> | <span data-ttu-id="0e4a4-212">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-213">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-214">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-215">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-216">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-217">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-218">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-219">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-220">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-221">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-222">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-223">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-224">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-225">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-226">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-227">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-228">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-229">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="0e4a4-230">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="0e4a4-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="0e4a4-231">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-231">Member</span></span> | <span data-ttu-id="0e4a4-232">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="0e4a4-234">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="0e4a4-234">System.Net.Sockets</span></span>

| <span data-ttu-id="0e4a4-235">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-235">Member</span></span> | <span data-ttu-id="0e4a4-236">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="0e4a4-237">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-238">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="0e4a4-239">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="0e4a4-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="0e4a4-240">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-240">Member</span></span> | <span data-ttu-id="0e4a4-241">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-242">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="0e4a4-243">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="0e4a4-243">System.Reflection</span></span>

| <span data-ttu-id="0e4a4-244">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-244">Member</span></span> | <span data-ttu-id="0e4a4-245">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-246">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-247">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-248">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-249">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="0e4a4-250">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-251">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-252">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="0e4a4-253">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="0e4a4-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="0e4a4-254">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-254">Member</span></span> | <span data-ttu-id="0e4a4-255">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-256">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="0e4a4-257">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="0e4a4-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="0e4a4-258">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-258">Member</span></span> | <span data-ttu-id="0e4a4-259">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-260">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-261">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-262">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-263">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-264">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-265">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-266">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="0e4a4-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="0e4a4-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="0e4a4-268">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-268">Member</span></span> | <span data-ttu-id="0e4a4-269">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-270">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="0e4a4-271">System.Security</span><span class="sxs-lookup"><span data-stu-id="0e4a4-271">System.Security</span></span>

| <span data-ttu-id="0e4a4-272">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-272">Member</span></span> | <span data-ttu-id="0e4a4-273">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-274">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-275">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-276">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-277">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-278">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-279">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-280">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-281">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-282">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-283">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-284">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-285">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-286">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-287">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="0e4a4-288">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="0e4a4-288">System.Security.Claims</span></span>

| <span data-ttu-id="0e4a4-289">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-289">Member</span></span> | <span data-ttu-id="0e4a4-290">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-291">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-292">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="0e4a4-293">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-294">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-295">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="0e4a4-296">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="0e4a4-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="0e4a4-297">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-297">Member</span></span> | <span data-ttu-id="0e4a4-298">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-299">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="0e4a4-300">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-301">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-302">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-303">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-304">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-305">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-306">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-307">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-308">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-309">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-310">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-311">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-312">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-313">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-314">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-315">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-316">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-317">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-318">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-319">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-320">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-321">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-322">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="0e4a4-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-323">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-324">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-325">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-326">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="0e4a4-327">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="0e4a4-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="0e4a4-328">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-328">Member</span></span> | <span data-ttu-id="0e4a4-329">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="0e4a4-330">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-331">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="0e4a4-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="0e4a4-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="0e4a4-333">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-333">Member</span></span> | <span data-ttu-id="0e4a4-334">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-335">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-336">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-337">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-337">All</span></span> |
| <span data-ttu-id="0e4a4-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="0e4a4-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="0e4a4-339">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="0e4a4-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="0e4a4-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="0e4a4-341">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-341">Member</span></span> | <span data-ttu-id="0e4a4-342">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-343">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="0e4a4-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="0e4a4-344">System.Security.Policy</span></span>

| <span data-ttu-id="0e4a4-345">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-345">Member</span></span> | <span data-ttu-id="0e4a4-346">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-347">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="0e4a4-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="0e4a4-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="0e4a4-349">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-349">Member</span></span> | <span data-ttu-id="0e4a4-350">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="0e4a4-351">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="0e4a4-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="0e4a4-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="0e4a4-353">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-353">Member</span></span> | <span data-ttu-id="0e4a4-354">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-355">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="0e4a4-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="0e4a4-356">System.Threading</span></span>

| <span data-ttu-id="0e4a4-357">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-357">Member</span></span> | <span data-ttu-id="0e4a4-358">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-359">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-360">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-361">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-362">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-363">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-364">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="0e4a4-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="0e4a4-365">System.Xml</span></span>

| <span data-ttu-id="0e4a4-366">Участник</span><span class="sxs-lookup"><span data-stu-id="0e4a4-366">Member</span></span> | <span data-ttu-id="0e4a4-367">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="0e4a4-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-368">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-369">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="0e4a4-370">Все</span><span class="sxs-lookup"><span data-stu-id="0e4a4-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="0e4a4-371">См. также</span><span class="sxs-lookup"><span data-stu-id="0e4a4-371">See also</span></span>

- [<span data-ttu-id="0e4a4-372">Критические изменения для миграции с .NET Framework на .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e4a4-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="0e4a4-373">Двоичная сериализация в .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e4a4-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="0e4a4-374">Анализатор переносимости .NET</span><span class="sxs-lookup"><span data-stu-id="0e4a4-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
