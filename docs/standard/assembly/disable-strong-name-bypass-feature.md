---
title: Практическое руководство. Отключение функции пропуска строгих имен
description: Обход строгого имени пропускает проверку подписи в полностью доверенных доменах в .NET. Эту функцию можно переопределить для одного или всех приложений.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 2846efbbd76cf677a42a7031e53661d302c6c964
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687467"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="e32bc-104">Практическое руководство. Отключение функции пропуска строгих имен</span><span class="sxs-lookup"><span data-stu-id="e32bc-104">How to: Disable the strong-name bypass feature</span></span>

<span data-ttu-id="e32bc-105">Начиная с версии .NET Framework 3.5 с пакетом обновления 1 (SP1), подписи строгого имени не проходили проверку при загрузке сборки в объект <xref:System.AppDomain> с полным доверием, например в `MyComputer` по умолчанию для зоны <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e32bc-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="e32bc-106">Это называется возможностью обхода строгих имен.</span><span class="sxs-lookup"><span data-stu-id="e32bc-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="e32bc-107">В среде с полным доверием всегда успешно обрабатываются запросы <xref:System.Security.Permissions.StrongNameIdentityPermission> для подписанных сборок с полным доверием независимо от их подписи.</span><span class="sxs-lookup"><span data-stu-id="e32bc-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="e32bc-108">Единственное исключение связано с тем, что сборка должна иметь полное доверие, потому что полное доверие имеет ее зона.</span><span class="sxs-lookup"><span data-stu-id="e32bc-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="e32bc-109">Так как в этом случае наличие строгого имени не является решающим фактором, смысла в проверке подписи нет.</span><span class="sxs-lookup"><span data-stu-id="e32bc-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="e32bc-110">Пропуск проверки подписей строгого имени позволяет значительно повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="e32bc-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="e32bc-111">Функция пропуска применяется ко всем сборкам с полным доверием, если у них нет отложенных подписей и они загружены в любой домен <xref:System.AppDomain> с полным доверием из каталога, заданным свойством <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="e32bc-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="e32bc-112">Можно отключить пропуск для всех приложений на компьютере, если изменить значение параметра реестра.</span><span class="sxs-lookup"><span data-stu-id="e32bc-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="e32bc-113">Для отключения пропуска для отдельного приложения необходимо внести соответствующие изменения в файл конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="e32bc-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="e32bc-114">Если функция пропуска строгих имен отключена в реестре, ее невозможно включить для отдельного приложения.</span><span class="sxs-lookup"><span data-stu-id="e32bc-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="e32bc-115">При отключении функции пропуска строгие имена проверяются только на правильность; наличие разрешения <xref:System.Security.Permissions.StrongNameIdentityPermission> не проверяется.</span><span class="sxs-lookup"><span data-stu-id="e32bc-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="e32bc-116">Если требуется подтвердить то или иное строгое имя, такую проверку необходимо выполнять отдельно.</span><span class="sxs-lookup"><span data-stu-id="e32bc-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e32bc-117">Возможность принудительного проведения проверки строгого имени зависит от значения параметра реестра, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="e32bc-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="e32bc-118">Если приложение выполняется от имени учетной записи, для которой в списке управления доступом не выделено разрешение на доступ к этому параметру реестра, проведение проверки невозможно.</span><span class="sxs-lookup"><span data-stu-id="e32bc-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="e32bc-119">Необходимо настроить права ACL для данного раздела так, чтобы к нему могла получить доступ любая сборка.</span><span class="sxs-lookup"><span data-stu-id="e32bc-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="e32bc-120">Отключение функции обхода строгих имен для всех приложений</span><span class="sxs-lookup"><span data-stu-id="e32bc-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="e32bc-121">На 32-разрядных компьютерах в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework системного реестра создайте запись DWORD со значением 0 и именем `AllowStrongNameBypass`.</span><span class="sxs-lookup"><span data-stu-id="e32bc-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="e32bc-122">На 64-разрядных компьютерах в разделах системного реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework и HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework создать запись типа DWORD со значением 0 с именем `AllowStrongNameBypass`.</span><span class="sxs-lookup"><span data-stu-id="e32bc-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="e32bc-123">Отключение функции обхода строгих имен для отдельного приложения</span><span class="sxs-lookup"><span data-stu-id="e32bc-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="e32bc-124">Откройте или создайте файл конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="e32bc-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="e32bc-125">Дополнительные сведения об этом файле см. в разделе "Файлы конфигурации приложений" документа [Настройка приложений](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="e32bc-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="e32bc-126">Добавьте следующую запись:</span><span class="sxs-lookup"><span data-stu-id="e32bc-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="e32bc-127">Функцию пропуска строгих имен для приложения можно снова включить, удалив соответствующий элемент из файла конфигурации или установив для атрибута значение `true`.</span><span class="sxs-lookup"><span data-stu-id="e32bc-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e32bc-128">Функцию проверки строгих имен можно включать и отключать на уровне приложения, если пропуск строгих имен включен на уровне компьютера.</span><span class="sxs-lookup"><span data-stu-id="e32bc-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="e32bc-129">Если функция пропуска на уровне компьютера отключена, строгие имена будут проверяться для всех приложений и пропустить проверку для отдельного приложения будет невозможно.</span><span class="sxs-lookup"><span data-stu-id="e32bc-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32bc-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e32bc-130">See also</span></span>

- [<span data-ttu-id="e32bc-131">Sn.exe (средство строгих имен)</span><span class="sxs-lookup"><span data-stu-id="e32bc-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="e32bc-132">Элемент \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="e32bc-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="e32bc-133">Создание и использование сборок со строгими именами</span><span class="sxs-lookup"><span data-stu-id="e32bc-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
