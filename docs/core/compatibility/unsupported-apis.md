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
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a>API, которые всегда создают исключения в .NET Core и .NET версии 5 и более поздних

Следующие API всегда будут вызывать исключение <xref:System.PlatformNotSupportedException> в .NET версии 5 и более поздних (включая все версии .NET Core) на всех платформах или на их подмножестве.

В этой статье затронутые API упорядочиваются по пространствам имен.

> [!NOTE]
>
> - Эта статья все еще находится в процессе написания. Это не полный список API-интерфейсов, создающих исключения в .NET версии 5 и более поздних.
> - В этой статье не рассматриваются явные реализации интерфейса для двоичной сериализации, которые вызываются в .NET версии 5 и более поздних. Дополнительные сведения см. в разделе [Двоичная сериализация в .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>Система

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Все |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Все |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Все |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Все |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Все |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Все |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Compiler

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Все |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Все |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Все |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Все |

## <a name="systemconfiguration"></a>System.Configuration

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (все члены) | Все |

## <a name="systemconsole"></a>System.Console

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (только получение) | Linux и macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (только получение) | Linux и macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> (только установка) | Linux и macOS |

## <a name="systemdatacommon"></a>System.Data.Common

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (вызывает <xref:System.NotSupportedException>) | Все |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (только установка) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (только установка) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (только получение) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (только установка) | Linux и macOS |

## <a name="systemio"></a>System.IO

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |

## <a name="systemiopipes"></a>System.IO.Pipes

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (только установка) | Linux и macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux и macOS |

## <a name="systemmedia"></a>System.Media

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |

## <a name="systemnet"></a>System.Net

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Все |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Все |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Все |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Все |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System.Net.Sockets

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Все |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Все |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Все |

## <a name="systemreflection"></a>System.Reflection

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Все |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Все |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Все |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Все |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Все |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Все |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Все |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Все |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Все |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Все |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux и macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Все |

## <a name="systemsecurity"></a>System.Security

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Все |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Все |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Все |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Все |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Все |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Все |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Все |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux и macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Все |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Все |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Все |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certificates

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Все |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (только установка) | Все |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |

## <a name="systemsecuritypolicy"></a>System.Security.Policy

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Все |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Все |

## <a name="systemthreading"></a>System.Threading

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Все |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Все |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Все |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Все |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Все |

## <a name="systemxml"></a>System.Xml

| Участник | Платформы, которые вызывают исключение |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Все |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Все |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Все |

## <a name="see-also"></a>См. также

- [Критические изменения для миграции с .NET Framework на .NET Core](fx-core.md)
- [Двоичная сериализация в .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Анализатор переносимости .NET](../../standard/analyzers/portability-analyzer.md)
