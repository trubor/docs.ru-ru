---
title: Неподдерживаемые API в .NET Core и .NET версии 5 и более поздних
titleSuffix: ''
description: Узнайте, какие интерфейсы API .NET всегда вызывают исключение в .NET Core и .NET 5.0 и более поздних версиях.
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593270"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="39979-103">API, которые всегда создают исключения в .NET Core и .NET версии 5 и более поздних</span><span class="sxs-lookup"><span data-stu-id="39979-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="39979-104">Следующие API всегда будут вызывать исключение <xref:System.PlatformNotSupportedException> в .NET версии 5.0 и более поздних (включая все версии .NET Core) на всех платформах или на их подмножестве.</span><span class="sxs-lookup"><span data-stu-id="39979-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="39979-105">В этой статье затронутые API упорядочиваются по пространствам имен.</span><span class="sxs-lookup"><span data-stu-id="39979-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="39979-106">Эта статья все еще находится в процессе написания.</span><span class="sxs-lookup"><span data-stu-id="39979-106">This article is a work-in-progress.</span></span> <span data-ttu-id="39979-107">Это не полный список API-интерфейсов, создающих исключения в .NET версии 5 и более поздних.</span><span class="sxs-lookup"><span data-stu-id="39979-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="39979-108">В этой статье не рассматриваются явные реализации интерфейса для двоичной сериализации, которые вызываются в .NET версии 5 и более поздних.</span><span class="sxs-lookup"><span data-stu-id="39979-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="39979-109">Дополнительные сведения см. в разделе [Двоичная сериализация в .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="39979-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="39979-110">Система</span><span class="sxs-lookup"><span data-stu-id="39979-110">System</span></span>

| <span data-ttu-id="39979-111">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-111">Member</span></span> | <span data-ttu-id="39979-112">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-113">Все</span><span class="sxs-lookup"><span data-stu-id="39979-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="39979-114">Все</span><span class="sxs-lookup"><span data-stu-id="39979-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="39979-115">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="39979-116">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-117">Все</span><span class="sxs-lookup"><span data-stu-id="39979-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="39979-118">Все</span><span class="sxs-lookup"><span data-stu-id="39979-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="39979-119">Все</span><span class="sxs-lookup"><span data-stu-id="39979-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="39979-120">Все</span><span class="sxs-lookup"><span data-stu-id="39979-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-121">Все</span><span class="sxs-lookup"><span data-stu-id="39979-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="39979-122">Все</span><span class="sxs-lookup"><span data-stu-id="39979-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="39979-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="39979-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="39979-124">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-124">Member</span></span> | <span data-ttu-id="39979-125">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-126">Все</span><span class="sxs-lookup"><span data-stu-id="39979-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-127">Все</span><span class="sxs-lookup"><span data-stu-id="39979-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-128">Все</span><span class="sxs-lookup"><span data-stu-id="39979-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="39979-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="39979-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="39979-130">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-130">Member</span></span> | <span data-ttu-id="39979-131">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-132">Все</span><span class="sxs-lookup"><span data-stu-id="39979-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-133">Все</span><span class="sxs-lookup"><span data-stu-id="39979-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="39979-134">Все</span><span class="sxs-lookup"><span data-stu-id="39979-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="39979-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="39979-135">System.Configuration</span></span>

| <span data-ttu-id="39979-136">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-136">Member</span></span> | <span data-ttu-id="39979-137">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="39979-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (все члены)</span><span class="sxs-lookup"><span data-stu-id="39979-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="39979-139">Все</span><span class="sxs-lookup"><span data-stu-id="39979-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="39979-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="39979-140">System.Console</span></span>

| <span data-ttu-id="39979-141">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-141">Member</span></span> | <span data-ttu-id="39979-142">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="39979-143">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-143">Linux and macOS</span></span> |
| <span data-ttu-id="39979-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-145">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-145">Linux and macOS</span></span> |
| <span data-ttu-id="39979-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-147">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-147">Linux and macOS</span></span> |
| <span data-ttu-id="39979-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-149">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-149">Linux and macOS</span></span> |
| <span data-ttu-id="39979-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="39979-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="39979-151">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-152">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-153">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-154">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-154">Linux and macOS</span></span> |
| <span data-ttu-id="39979-155"><xref:System.Console.Title?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="39979-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="39979-156">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-156">Linux and macOS</span></span> |
| <span data-ttu-id="39979-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-158">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-158">Linux and macOS</span></span> |
| <span data-ttu-id="39979-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-160">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-160">Linux and macOS</span></span> |
| <span data-ttu-id="39979-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-162">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-162">Linux and macOS</span></span> |
| <span data-ttu-id="39979-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-164">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="39979-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="39979-165">System.Data.Common</span></span>

| <span data-ttu-id="39979-166">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-166">Member</span></span> | <span data-ttu-id="39979-167">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="39979-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (вызывает <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="39979-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="39979-169">Все</span><span class="sxs-lookup"><span data-stu-id="39979-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="39979-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="39979-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="39979-171">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-171">Member</span></span> | <span data-ttu-id="39979-172">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="39979-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-174">Linux</span><span class="sxs-lookup"><span data-stu-id="39979-174">Linux</span></span> |
| <span data-ttu-id="39979-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-176">Linux</span><span class="sxs-lookup"><span data-stu-id="39979-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="39979-177">macOS</span><span class="sxs-lookup"><span data-stu-id="39979-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="39979-178">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-179">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-180">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="39979-181">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="39979-182">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="39979-183">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="39979-184">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-184">Linux and macOS</span></span> |
| <span data-ttu-id="39979-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-186">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-186">Linux and macOS</span></span> |
| <span data-ttu-id="39979-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только получение)</span><span class="sxs-lookup"><span data-stu-id="39979-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="39979-188">macOS</span><span class="sxs-lookup"><span data-stu-id="39979-188">macOS</span></span> |
| <span data-ttu-id="39979-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-190">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="39979-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="39979-191">System.IO</span></span>

| <span data-ttu-id="39979-192">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-192">Member</span></span> | <span data-ttu-id="39979-193">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-194">Все</span><span class="sxs-lookup"><span data-stu-id="39979-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-195">Все</span><span class="sxs-lookup"><span data-stu-id="39979-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="39979-196">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="39979-196">System.IO.Pipes</span></span>

| <span data-ttu-id="39979-197">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-197">Member</span></span> | <span data-ttu-id="39979-198">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="39979-199">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="39979-200">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="39979-201">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="39979-202">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-202">Linux and macOS</span></span> |
| <span data-ttu-id="39979-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-204">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="39979-205">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="39979-206">System.Media</span><span class="sxs-lookup"><span data-stu-id="39979-206">System.Media</span></span>

| <span data-ttu-id="39979-207">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-207">Member</span></span> | <span data-ttu-id="39979-208">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-209">Все</span><span class="sxs-lookup"><span data-stu-id="39979-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="39979-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="39979-210">System.Net</span></span>

| <span data-ttu-id="39979-211">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-211">Member</span></span> | <span data-ttu-id="39979-212">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="39979-213">Все</span><span class="sxs-lookup"><span data-stu-id="39979-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="39979-214">Все</span><span class="sxs-lookup"><span data-stu-id="39979-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-215">Все</span><span class="sxs-lookup"><span data-stu-id="39979-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-216">Все</span><span class="sxs-lookup"><span data-stu-id="39979-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-217">Все</span><span class="sxs-lookup"><span data-stu-id="39979-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-218">Все</span><span class="sxs-lookup"><span data-stu-id="39979-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-219">Все</span><span class="sxs-lookup"><span data-stu-id="39979-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-220">Все</span><span class="sxs-lookup"><span data-stu-id="39979-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-221">Все</span><span class="sxs-lookup"><span data-stu-id="39979-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-222">Все</span><span class="sxs-lookup"><span data-stu-id="39979-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-223">Все</span><span class="sxs-lookup"><span data-stu-id="39979-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="39979-224">Все</span><span class="sxs-lookup"><span data-stu-id="39979-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-225">Все</span><span class="sxs-lookup"><span data-stu-id="39979-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-226">Все</span><span class="sxs-lookup"><span data-stu-id="39979-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-227">Все</span><span class="sxs-lookup"><span data-stu-id="39979-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-228">Все</span><span class="sxs-lookup"><span data-stu-id="39979-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-229">Все</span><span class="sxs-lookup"><span data-stu-id="39979-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="39979-230">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="39979-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="39979-231">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-231">Member</span></span> | <span data-ttu-id="39979-232">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="39979-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="39979-234">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="39979-234">System.Net.Sockets</span></span>

| <span data-ttu-id="39979-235">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-235">Member</span></span> | <span data-ttu-id="39979-236">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="39979-237">Все</span><span class="sxs-lookup"><span data-stu-id="39979-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="39979-238">Все</span><span class="sxs-lookup"><span data-stu-id="39979-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="39979-239">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="39979-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="39979-240">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-240">Member</span></span> | <span data-ttu-id="39979-241">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="39979-242">Все</span><span class="sxs-lookup"><span data-stu-id="39979-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="39979-243">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="39979-243">System.Reflection</span></span>

| <span data-ttu-id="39979-244">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-244">Member</span></span> | <span data-ttu-id="39979-245">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-246">Все</span><span class="sxs-lookup"><span data-stu-id="39979-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-247">Все</span><span class="sxs-lookup"><span data-stu-id="39979-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-248">Все</span><span class="sxs-lookup"><span data-stu-id="39979-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="39979-249">Все</span><span class="sxs-lookup"><span data-stu-id="39979-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="39979-250">Все</span><span class="sxs-lookup"><span data-stu-id="39979-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-251">Все</span><span class="sxs-lookup"><span data-stu-id="39979-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="39979-252">Все</span><span class="sxs-lookup"><span data-stu-id="39979-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="39979-253">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="39979-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="39979-254">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-254">Member</span></span> | <span data-ttu-id="39979-255">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="39979-256">Все</span><span class="sxs-lookup"><span data-stu-id="39979-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="39979-257">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="39979-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="39979-258">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-258">Member</span></span> | <span data-ttu-id="39979-259">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="39979-260">Все</span><span class="sxs-lookup"><span data-stu-id="39979-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="39979-261">Все</span><span class="sxs-lookup"><span data-stu-id="39979-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="39979-262">Все</span><span class="sxs-lookup"><span data-stu-id="39979-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="39979-263">Все</span><span class="sxs-lookup"><span data-stu-id="39979-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-264">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="39979-265">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="39979-266">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="39979-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="39979-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="39979-268">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-268">Member</span></span> | <span data-ttu-id="39979-269">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="39979-270">Все</span><span class="sxs-lookup"><span data-stu-id="39979-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="39979-271">System.Security</span><span class="sxs-lookup"><span data-stu-id="39979-271">System.Security</span></span>

| <span data-ttu-id="39979-272">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-272">Member</span></span> | <span data-ttu-id="39979-273">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="39979-274">Все</span><span class="sxs-lookup"><span data-stu-id="39979-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="39979-275">Все</span><span class="sxs-lookup"><span data-stu-id="39979-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-276">Все</span><span class="sxs-lookup"><span data-stu-id="39979-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="39979-277">Все</span><span class="sxs-lookup"><span data-stu-id="39979-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="39979-278">Все</span><span class="sxs-lookup"><span data-stu-id="39979-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="39979-279">Все</span><span class="sxs-lookup"><span data-stu-id="39979-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="39979-280">Все</span><span class="sxs-lookup"><span data-stu-id="39979-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="39979-281">Все</span><span class="sxs-lookup"><span data-stu-id="39979-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="39979-282">Все</span><span class="sxs-lookup"><span data-stu-id="39979-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="39979-283">Все</span><span class="sxs-lookup"><span data-stu-id="39979-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="39979-284">Все</span><span class="sxs-lookup"><span data-stu-id="39979-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="39979-285">Все</span><span class="sxs-lookup"><span data-stu-id="39979-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="39979-286">Все</span><span class="sxs-lookup"><span data-stu-id="39979-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="39979-287">Все</span><span class="sxs-lookup"><span data-stu-id="39979-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="39979-288">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="39979-288">System.Security.Claims</span></span>

| <span data-ttu-id="39979-289">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-289">Member</span></span> | <span data-ttu-id="39979-290">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-291">Все</span><span class="sxs-lookup"><span data-stu-id="39979-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-292">Все</span><span class="sxs-lookup"><span data-stu-id="39979-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="39979-293">Все</span><span class="sxs-lookup"><span data-stu-id="39979-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-294">Все</span><span class="sxs-lookup"><span data-stu-id="39979-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-295">Все</span><span class="sxs-lookup"><span data-stu-id="39979-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="39979-296">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="39979-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="39979-297">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-297">Member</span></span> | <span data-ttu-id="39979-298">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-299">Все</span><span class="sxs-lookup"><span data-stu-id="39979-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="39979-300">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="39979-301">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="39979-302">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="39979-303">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="39979-304">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="39979-305">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="39979-306">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="39979-307">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="39979-308">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="39979-309">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="39979-310">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="39979-311">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="39979-312">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="39979-313">Все</span><span class="sxs-lookup"><span data-stu-id="39979-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="39979-314">Все</span><span class="sxs-lookup"><span data-stu-id="39979-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-315">Все</span><span class="sxs-lookup"><span data-stu-id="39979-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-316">Все</span><span class="sxs-lookup"><span data-stu-id="39979-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-317">Все</span><span class="sxs-lookup"><span data-stu-id="39979-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-318">Все</span><span class="sxs-lookup"><span data-stu-id="39979-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="39979-319">Все</span><span class="sxs-lookup"><span data-stu-id="39979-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-320">Все</span><span class="sxs-lookup"><span data-stu-id="39979-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-321">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-322">Linux и macOS</span><span class="sxs-lookup"><span data-stu-id="39979-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-323">Все</span><span class="sxs-lookup"><span data-stu-id="39979-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-324">Все</span><span class="sxs-lookup"><span data-stu-id="39979-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="39979-325">Все</span><span class="sxs-lookup"><span data-stu-id="39979-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="39979-326">Все</span><span class="sxs-lookup"><span data-stu-id="39979-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="39979-327">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="39979-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="39979-328">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-328">Member</span></span> | <span data-ttu-id="39979-329">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="39979-330">Все</span><span class="sxs-lookup"><span data-stu-id="39979-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="39979-331">Все</span><span class="sxs-lookup"><span data-stu-id="39979-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="39979-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="39979-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="39979-333">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-333">Member</span></span> | <span data-ttu-id="39979-334">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-335">Все</span><span class="sxs-lookup"><span data-stu-id="39979-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-336">Все</span><span class="sxs-lookup"><span data-stu-id="39979-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-337">Все</span><span class="sxs-lookup"><span data-stu-id="39979-337">All</span></span> |
| <span data-ttu-id="39979-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (только установка)</span><span class="sxs-lookup"><span data-stu-id="39979-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="39979-339">Все</span><span class="sxs-lookup"><span data-stu-id="39979-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="39979-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="39979-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="39979-341">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-341">Member</span></span> | <span data-ttu-id="39979-342">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-343">Все</span><span class="sxs-lookup"><span data-stu-id="39979-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="39979-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="39979-344">System.Security.Policy</span></span>

| <span data-ttu-id="39979-345">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-345">Member</span></span> | <span data-ttu-id="39979-346">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-347">Все</span><span class="sxs-lookup"><span data-stu-id="39979-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="39979-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="39979-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="39979-349">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-349">Member</span></span> | <span data-ttu-id="39979-350">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="39979-351">Все</span><span class="sxs-lookup"><span data-stu-id="39979-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="39979-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="39979-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="39979-353">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-353">Member</span></span> | <span data-ttu-id="39979-354">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-355">Все</span><span class="sxs-lookup"><span data-stu-id="39979-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="39979-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="39979-356">System.Threading</span></span>

| <span data-ttu-id="39979-357">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-357">Member</span></span> | <span data-ttu-id="39979-358">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-359">Все</span><span class="sxs-lookup"><span data-stu-id="39979-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="39979-360">Все</span><span class="sxs-lookup"><span data-stu-id="39979-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="39979-361">Все</span><span class="sxs-lookup"><span data-stu-id="39979-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="39979-362">Все</span><span class="sxs-lookup"><span data-stu-id="39979-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="39979-363">Все</span><span class="sxs-lookup"><span data-stu-id="39979-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="39979-364">Все</span><span class="sxs-lookup"><span data-stu-id="39979-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="39979-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="39979-365">System.Xml</span></span>

| <span data-ttu-id="39979-366">Участник</span><span class="sxs-lookup"><span data-stu-id="39979-366">Member</span></span> | <span data-ttu-id="39979-367">Платформы, которые вызывают исключение</span><span class="sxs-lookup"><span data-stu-id="39979-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="39979-368">Все</span><span class="sxs-lookup"><span data-stu-id="39979-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="39979-369">Все</span><span class="sxs-lookup"><span data-stu-id="39979-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="39979-370">Все</span><span class="sxs-lookup"><span data-stu-id="39979-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="39979-371">См. также</span><span class="sxs-lookup"><span data-stu-id="39979-371">See also</span></span>

- [<span data-ttu-id="39979-372">Критические изменения для миграции с .NET Framework на .NET Core</span><span class="sxs-lookup"><span data-stu-id="39979-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="39979-373">Двоичная сериализация в .NET Core</span><span class="sxs-lookup"><span data-stu-id="39979-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="39979-374">Анализатор переносимости .NET</span><span class="sxs-lookup"><span data-stu-id="39979-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
