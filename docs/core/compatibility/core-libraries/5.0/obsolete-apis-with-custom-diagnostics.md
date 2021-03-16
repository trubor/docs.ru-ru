---
title: Критическое изменение. Устаревшие API с отличными от заданных по умолчанию идентификаторами диагностики
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где некоторые API были помечены как устаревшие с помощью настраиваемого идентификатора диагностики.
ms.date: 11/01/2020
ms.openlocfilehash: 9aa4543ae6660f2d2fceac2419340bc6c90f1c54
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257379"
---
# <a name="api-obsoletions-with-non-default-diagnostic-ids"></a><span data-ttu-id="47c42-103">Устаревшие API с отличными от заданных по умолчанию идентификаторами диагностики</span><span class="sxs-lookup"><span data-stu-id="47c42-103">API obsoletions with non-default diagnostic IDs</span></span>

<span data-ttu-id="47c42-104">Некоторые API были помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="47c42-104">Some APIs have been marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="47c42-105">Это критическое изменение относится к API, которые были помечены как устаревшие *с помощью пользовательского идентификатора диагностики*.</span><span class="sxs-lookup"><span data-stu-id="47c42-105">This breaking change is specific to APIs that have been marked as obsolete *with a custom diagnostic ID*.</span></span> <span data-ttu-id="47c42-106">В случае отключения идентификатора диагностики устаревших элементов по умолчанию ([CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) для компилятора C#) не отключаются предупреждения, создаваемые компилятором при использовании этих API.</span><span class="sxs-lookup"><span data-stu-id="47c42-106">Suppressing the default obsoletion diagnostic ID, which is [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) for the C# compiler, does not suppress the warnings that the compiler generates when these APIs are used.</span></span>

## <a name="change-description"></a><span data-ttu-id="47c42-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="47c42-107">Change description</span></span>

<span data-ttu-id="47c42-108">В предыдущих версиях .NET эти API можно использовать без каких-либо предупреждений сборки.</span><span class="sxs-lookup"><span data-stu-id="47c42-108">In previous .NET versions, these APIs can be used without any build warning.</span></span> <span data-ttu-id="47c42-109">В .NET 5 и более поздних версий при использовании этих API во время компиляции создается предупреждение или ошибка с пользовательским идентификатором диагностики.</span><span class="sxs-lookup"><span data-stu-id="47c42-109">In .NET 5 and later versions, use of these APIS produces a compile-time warning or error with a custom diagnostic ID.</span></span> <span data-ttu-id="47c42-110">Применение пользовательских идентификаторов диагностики позволяет отключать предупреждения об устаревших элементах по отдельности вместо общего запрета всех таких предупреждений.</span><span class="sxs-lookup"><span data-stu-id="47c42-110">The use of custom diagnostic IDs allows you to suppress the obsoletion warnings individually instead of blanket-suppressing all obsoletion warnings.</span></span>

<span data-ttu-id="47c42-111">В следующей таблице перечислены пользовательские идентификаторы диагностики и соответствующие им предупреждающие сообщения для устаревших API.</span><span class="sxs-lookup"><span data-stu-id="47c42-111">The following table lists the custom diagnostic IDs and their corresponding warning messages for obsoleted APIs.</span></span>

| <span data-ttu-id="47c42-112">ИД диагностики</span><span class="sxs-lookup"><span data-stu-id="47c42-112">Diagnostic ID</span></span> | <span data-ttu-id="47c42-113">Описание</span><span class="sxs-lookup"><span data-stu-id="47c42-113">Description</span></span> | <span data-ttu-id="47c42-114">Severity</span><span class="sxs-lookup"><span data-stu-id="47c42-114">Severity</span></span> |
| - | - |
| `SYSLIB0001` | <span data-ttu-id="47c42-115">Кодировка UTF-7 небезопасна и не должна использоваться.</span><span class="sxs-lookup"><span data-stu-id="47c42-115">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="47c42-116">Вместо нее рекомендуется использовать UTF-8.</span><span class="sxs-lookup"><span data-stu-id="47c42-116">Consider using UTF-8 instead.</span></span> | <span data-ttu-id="47c42-117">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-117">Warning</span></span> |
| `SYSLIB0002` | <span data-ttu-id="47c42-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> не учитывается средой выполнения и не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="47c42-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> | <span data-ttu-id="47c42-119">Ошибка</span><span class="sxs-lookup"><span data-stu-id="47c42-119">Error</span></span> |
| `SYSLIB0003` | <span data-ttu-id="47c42-120">Управление доступом для кода (CAS) не поддерживается или не учитывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="47c42-120">Code access security (CAS) is not supported or honored by the runtime.</span></span> | <span data-ttu-id="47c42-121">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-121">Warning</span></span> |
| `SYSLIB0004` | <span data-ttu-id="47c42-122">Функция области ограниченного выполнения (CER) не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="47c42-122">The constrained execution region (CER) feature is not supported.</span></span> | <span data-ttu-id="47c42-123">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-123">Warning</span></span> |
| `SYSLIB0005` | <span data-ttu-id="47c42-124">Глобальный кэш сборок не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="47c42-124">The global assembly cache (GAC) is not supported.</span></span> | <span data-ttu-id="47c42-125">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-125">Warning</span></span> |
| `SYSLIB0006` | <span data-ttu-id="47c42-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> не поддерживается и вызывает <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="47c42-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="47c42-127">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-127">Warning</span></span> |
| `SYSLIB0007` | <span data-ttu-id="47c42-128">Реализации этого алгоритма шифрования по умолчанию не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="47c42-128">The default implementation of this cryptography algorithm is not supported.</span></span> | <span data-ttu-id="47c42-129">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-129">Warning</span></span> |
| `SYSLIB0008` | <span data-ttu-id="47c42-130">API <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> не поддерживается и вызывает <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="47c42-130">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="47c42-131">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-131">Warning</span></span> |
| `SYSLIB0009` | <span data-ttu-id="47c42-132">Методы <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> и <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> не поддерживаются и вызывают <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="47c42-132">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="47c42-133">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-133">Warning</span></span> |
| `SYSLIB0010`| <span data-ttu-id="47c42-134">Некоторые API удаленного взаимодействия не поддерживаются и вызывают <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="47c42-134">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="47c42-135">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-135">Warning</span></span> |
| `SYSLIB0011` | <span data-ttu-id="47c42-136">Сериализация <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> устарела и не должна использоваться.</span><span class="sxs-lookup"><span data-stu-id="47c42-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> | <span data-ttu-id="47c42-137">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-137">Warning</span></span> |
| `SYSLIB0012` | <span data-ttu-id="47c42-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> и <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> включены только для обеспечения совместимости с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47c42-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="47c42-139">Взамен рекомендуется использовать <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47c42-139">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> | <span data-ttu-id="47c42-140">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="47c42-140">Warning</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="47c42-141">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="47c42-141">Version introduced</span></span>

<span data-ttu-id="47c42-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="47c42-142">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="47c42-143">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="47c42-143">Recommended action</span></span>

- <span data-ttu-id="47c42-144">Следуйте указаниям, приведенным для каждого идентификатора диагностики, используя URL, предоставленный в предупреждении.</span><span class="sxs-lookup"><span data-stu-id="47c42-144">Follow the specific guidance provided for the each diagnostic ID using the URL link provided on the warning.</span></span>

- <span data-ttu-id="47c42-145">Предупреждения или ошибки об этих устаревших элементах нельзя отключить с помощью стандартного идентификатора диагностики для устаревших типов или членов. Используйте вместо него пользовательский идентификатор диагностики `SYSLIBxxxx`.</span><span class="sxs-lookup"><span data-stu-id="47c42-145">Warnings or errors for these obsoletions can't be suppressed using the standard diagnostic ID for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID value instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="47c42-146">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="47c42-146">Affected APIs</span></span>

### <a name="syslib0001"></a><span data-ttu-id="47c42-147">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="47c42-147">SYSLIB0001</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>
- <xref:System.Text.UTF7Encoding.%23ctor%2A>

### <a name="syslib0002"></a><span data-ttu-id="47c42-148">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="47c42-148">SYSLIB0002</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute.%23ctor(System.Security.Permissions.SecurityAction)>

### <a name="syslib0003"></a><span data-ttu-id="47c42-149">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="47c42-149">SYSLIB0003</span></span>

<span data-ttu-id="47c42-150">Классы в пространстве имен `System.Security.Permissions`:</span><span class="sxs-lookup"><span data-stu-id="47c42-150">Classes in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="47c42-151">Классы, производные от `CodeAccessSecurityAttribute`:</span><span class="sxs-lookup"><span data-stu-id="47c42-151">Classes that derive from `CodeAccessSecurityAttribute`:</span></span>

- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="47c42-152">Интерфейсы:</span><span class="sxs-lookup"><span data-stu-id="47c42-152">Interfaces:</span></span>

- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>

<span data-ttu-id="47c42-153">Классы, реализующие `IStackWalk`:</span><span class="sxs-lookup"><span data-stu-id="47c42-153">Classes that implement `IStackWalk`:</span></span>

- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>

<span data-ttu-id="47c42-154">Классы, реализующие `IPermission`:</span><span class="sxs-lookup"><span data-stu-id="47c42-154">Classes that implement `IPermission`:</span></span>

- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>

<span data-ttu-id="47c42-155">Классы, производные от `CodeAccessPermission`:</span><span class="sxs-lookup"><span data-stu-id="47c42-155">Classes that derive from `CodeAccessPermission`:</span></span>

- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

<span data-ttu-id="47c42-156">Классы, производные от `ResourcePermissionBase`:</span><span class="sxs-lookup"><span data-stu-id="47c42-156">Classes that derive from `ResourcePermissionBase`:</span></span>

- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>

<span data-ttu-id="47c42-157">Перечисления в пространстве имен `System.Security.Permissions`:</span><span class="sxs-lookup"><span data-stu-id="47c42-157">Enums in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>

<span data-ttu-id="47c42-158">Классы и члены, зависящие от типов управления доступом для кода:</span><span class="sxs-lookup"><span data-stu-id="47c42-158">Classes and members that depend on code access security types:</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- [<span data-ttu-id="47c42-159">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span><span class="sxs-lookup"><span data-stu-id="47c42-159">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=nameWithType>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>

### <a name="syslib0004"></a><span data-ttu-id="47c42-160">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="47c42-160">SYSLIB0004</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

### <a name="syslib0005"></a><span data-ttu-id="47c42-161">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="47c42-161">SYSLIB0005</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

### <a name="syslib0006"></a><span data-ttu-id="47c42-162">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="47c42-162">SYSLIB0006</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

### <a name="syslib0007"></a><span data-ttu-id="47c42-163">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="47c42-163">SYSLIB0007</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

### <a name="syslib0008"></a><span data-ttu-id="47c42-164">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="47c42-164">SYSLIB0008</span></span>

- <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>

### <a name="syslib0009"></a><span data-ttu-id="47c42-165">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="47c42-165">SYSLIB0009</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

### <a name="syslib0010"></a><span data-ttu-id="47c42-166">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="47c42-166">SYSLIB0010</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

### <a name="syslib0011"></a><span data-ttu-id="47c42-167">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="47c42-167">SYSLIB0011</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

### <a name="syslib0012"></a><span data-ttu-id="47c42-168">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="47c42-168">SYSLIB0012</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>
